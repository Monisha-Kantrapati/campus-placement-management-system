# 🔄 Campus Placement System - Unified Data Flow Architecture

## Overview
The system now uses a **DataContext** that acts as a centralized database manager. All data flows automatically between modules without duplication or manual synchronization.

## System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     DataContext (Centralized)               │
│  - Approved Students                                        │
│  - Pending Student Registrations                            │
│  - Approved Recruiters                                       │
│  - Pending Recruiter Registrations                          │
│  - Active Job Postings                                       │
│  - Auto-syncs with localStorage                             │
└─────────────────────────────────────────────────────────────┘
                              ↓
        ┌─────────────────────┴─────────────────────┐
        ↓                     ↓                     ↓
   ┌────────┐         ┌──────────┐         ┌──────────┐
   │ Student│         │  Admin   │         │ Recruiter│
   │ Module │         │ Module   │         │  Module  │
   └────────┘         └──────────┘         └──────────┘
```

## Data Flow Examples

### 1️⃣ Student Registration Flow

```
Student Fills Form
        ↓
StudentRegistration Component
        ↓
Calls DataContext.registerStudent()
        ↓
Data Saved to:
  - pendingStudents state
  - localStorage (auto-sync)
        ↓
Admin Sees in StudentRequests.jsx
  - Pending registrations appear automatically
  - No manual refresh needed
```

### 2️⃣ Admin Approval & Student Visibility Flow

```
Admin Clicks "Approve"
        ↓
Calls DataContext.approveStudent(studentId)
        ↓
Data Moved:
  - Removed from pendingStudents
  - Added to approvedStudents
  - localStorage updated
        ↓
Student Can Now:
  - Login (verified email count)
  - Apply for jobs
  - Upload resume
        ↓
Recruiter Can See:
  - Student appears in SkillSearch
  - Search by skills, CGPA, department
  - Download resume
```

### 3️⃣ Job Posting to Application Flow

```
Job Posted by Recruiter
        ↓
Stored in DataContext.jobs
        ↓
Available in Student Job Portal
  - Automatic filtering
  - Package/CGPA matching
        ↓
Student Applies
        ↓
Updated in:
  - Student's appliedJobs list
  - Job's applicants list
  - localStorage synced
        ↓
Recruiter Can See:
  - List of all applications
  - Student profiles & resumes
```

## State Management Details

### DataContext Provides:

#### Student Management
```javascript
- approvedStudents[]     // Verified students
- pendingStudents[]      // Awaiting approval

Functions:
- registerStudent(data)       // Add to pending
- approveStudent(id)          // Move to approved
- rejectStudent(id)           // Remove from pending
- getStudentByEmail(email)    // Find student
- updateStudentResume(id, data) // Update resume
- applyForJob(studentId, jobId) // Track application
```

#### Recruiter Management
```javascript
- approvedRecruiters[]   // Verified recruiters
- pendingRecruiters[]    // Awaiting verification

Functions:
- registerRecruiter(data)     // Add to pending
- approveRecruiter(id)        // Move to approved
- rejectRecruiter(id)         // Remove from pending
- getRecruiterByEmail(email)  // Find recruiter
```

#### Job Management
```javascript
- jobs[]  // All active jobs

Functions:
- postJob(jobData, recruiterId)     // Create job
- updateJob(jobId, jobData)         // Modify job
- getJobsByRecruiter(recruiterId)   // Recruiter's jobs
- getActiveJobs()                   // All active jobs
```

## LocalStorage Persistence

Data automatically syncs to localStorage:
```javascript
approvedStudents     // persists across sessions
pendingStudents      // persists across sessions
approvedRecruiters   // persists across sessions
pendingRecruiters    // persists across sessions
jobs                 // persists across sessions
```

When app restarts → Data reloads from localStorage → No data loss

## Integration in Components

### Student Registration
```javascript
const { registerStudent } = useContext(DataContext);

handleSubmit = () => {
  registerStudent(formData);  // Data saved to context + localStorage
}
```

### Admin Approval
```javascript
const { pendingStudents, approveStudent, rejectStudent } = useContext(DataContext);

const approve = (id) => {
  approveStudent(id);  // Student moved to approved automatically
  // No manual localStorage update needed
}
```

### Recruiter Search
```javascript
const { approvedStudents } = useContext(DataContext);

useEffect(() => {
  // Filter runs on approvedStudents directly
  // Updates in real-time when admin approves a student
}, [approvedStudents])
```

### Job Listing
```javascript
const { jobs, applyForJob } = useContext(DataContext);

useEffect(() => {
  // Filter jobs automatically
  // Shows only active jobs
}, [jobs])
```

## Key Benefits

✅ **No Duplication** - Single source of truth  
✅ **Real-time Updates** - Changes visible immediately across all modules  
✅ **Automatic Sync** - localStorage keeps data persistent  
✅ **Centralized Control** - Easy to manage all registrations/approvals  
✅ **Simplified Logic** - Components just call functions, don't manage data  
✅ **Data Integrity** - Consistent state across app  

## Example: Complete Registration-to-Search Flow

1. **New Student Registers**
   ```
   StudentRegistration → registerStudent() → pendingStudents state + localStorage
   ```

2. **Admin Approves**
   ```
   StudentRequests → approveStudent() → approvedStudents state + localStorage
   ```

3. **Recruiter Searches**
   ```
   SkillSearch reads approvedStudents (real live data) → Approved student appears
   ```

4. **Student Applies for Job**
   ```
   Jobs component → applyForJob() → Student's appliedJobs updated + job's applicants updated
   ```

5. **Data Persists**
   ```
   All changes → localStorage → Survives page refresh/restart
   ```

## File Structure

```
src/
├── context/
│   ├── AuthContext.jsx         (Authentication)
│   └── DataContext.jsx         (Centralized Data Management) ⭐
├── pages/auth/
│   ├── StudentRegistration.jsx (uses DataContext)
│   └── RecruiterRegistration.jsx (uses DataContext)
├── modules/
│   ├── admin/
│   │   └── StudentRequests.jsx (uses DataContext for approvals)
│   ├── student/
│   │   ├── Jobs.jsx            (uses DataContext for jobs)
│   │   └── ApplicationTracker.jsx (uses DataContext)
│   └── recruiter/
│       └── SkillSearch.jsx     (uses DataContext for students)
└── App.js                      (wraps all with DataProvider)
```

## Testing the Data Flow

### Test 1: Registration Chain
1. Register a student with college email
2. Go to Admin → Approve Requests
3. Approve the student
4. Logout & login as recruiter
5. Go to Find Students
6. Student should appear in search!

### Test 2: Job Application
1. Login as student
2. Go to Jobs
3. Click Apply on a job
4. Logout & login as recruiter
5. Go to View Applications
6. Applicant should be visible!

### Test 3: Data Persistence
1. Perform any action (register, approve, apply)
2. Refresh page (Ctrl+R)
3. Data should still be there!

---

**This unified architecture ensures that the system works like a real shared database where all data is automatically connected and synchronized across all modules.**
