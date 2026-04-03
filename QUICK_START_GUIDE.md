# Campus Placement System - Quick Start Guide

## 🚀 Getting Started

### 1. Start the Application
```bash
npm start
```
The application will open at `http://localhost:3000`

### 2. Login with Demo Accounts

**Admin Account:**
- Email: `admin@college.com`
- Password: `admin`
- Access: System-wide administration

**Student Account:**
- Email: `student@college.com`
- Password: `student`
- Access: Job search, applications, profile

**Recruiter Account:**
- Email: `recruiter@company.com`
- Password: `recruiter`
- Access: Job posting, candidate management

---

## 📊 Admin Dashboard Tour

### Main Dashboard (`/admin`)
After logging in as admin:
1. **KPI Cards** - See key statistics:
   - Total students: 980
   - Placement rate: 77%
   - Average package: 10.5 LPA
   - Highest package: 30 LPA

2. **4 Charts** - Visualize data:
   - Placement by department (bar chart)
   - Top recruiting companies (horizontal bar)
   - Year-wise trend (line chart with dual Y-axis)
   - Department percentage (pie chart)

3. **Search & Export** - Find and download data
   - Search students by name/email/ID
   - Export as CSV

### Manage Students (`/admin/students`)
1. **Summary Cards** - Quick overview
   - Total students, placed count, placement %, departments
2. **Filters & Search** - Refine data
   - Search by name or email
   - Filter by department or placement status
3. **Student Table** - Complete view with columns:
   - ID, Name, Email, Department, CGPA, Status
   - Company, Salary, Actions (Edit/Delete)
4. **Bulk Actions** - Manage multiple records
   - Generate reports, export data, send notifications

### Companies (`/admin/companies`)
1. **Company Management** - Register new companies
   - Click "Add Company" button
   - Fill in company details (required: name, industry, location)
2. **Filter & Search** - Find companies
   - Search by name
   - Filter by industry type
3. **Company Table** - View all companies with:
   - Industry, location, recruiter info, average package
   - Number of offers made
4. **Actions** - Edit or delete company information

### Recruiters (`/admin/recruiters`)
1. **Recruiter Management** - Add new recruiters
   - Click "Add Recruiter" button
   - Enter name, company, email, phone
2. **Status Management** - Activate/deactivate accounts
   - Toggle recruiter status as needed
3. **Recruiter Table** - View statistics
   - Jobs posted, total applicants per recruiter
   - Contact information

### Analytics (`/admin/analytics`)
1. **System-wide Analytics** - Comprehensive overview
   - Year-wise trends with placement percentage
   - Monthly activity (students, companies, offers)
   - Salary distribution by range
   - Cumulative placement growth
2. **Department Analysis** - Per-department metrics
   - Placement percentage, placed/total count
3. **Key Insights** - Summary statistics
   - Best performing department
   - Top recruiter company
   - Growth rate trends

---

## 👤 Student Dashboard Tour

### Main Dashboard (`/student`)
1. **Profile Section** - Your information
   - Avatar, name, department, CGPA, phone
   - Profile completion: 85% (shows what's missing)

2. **Quick Statistics** - Your metrics
   - Jobs applied (12)
   - Interviews scheduled (3)
   - Offers received (1)
   - Placement status

3. **Skills Section** - Your technical skills
   - Shows: React, JavaScript, Node.js, MongoDB
   - Click "+ Add Skills" to add/remove skills

4. **Resume Section** - Upload area
   - Drag and drop file
   - Or click to browse

5. **Quick Actions** - Shortcuts to main features
   - Browse Jobs, View Applications, Interview Schedule, Resources

### Jobs (`/student/jobs`)
1. **Filter Options** - Narrow down search
   - Search by title or company name
   - Select location from dropdown
   - Choose specific company
   - Filter by salary range

2. **Clear Filters** - Reset search

3. **Job Cards** - View each opportunity
   - Job title, company, location
   - Required skills as badges
   - Salary, job type, min CGPA
   - Days remaining before deadline

4. **Job Actions**
   - "Apply Now" → Changes to "✓ Applied" (disabled)
   - "Save Job" → Changes to "❤️ Saved"

### Resume Upload (`/student/resume`)
1. **Upload Area** - Add your resume
   - Drag and drop PDF file
   - File type validation (PDF only)
   - File size display after upload

2. **Resume Tips** - Best practices
   - Keep it concise and achievable
   - Highlight accomplishments
   - Professional formatting
   - Keywords for ATS

3. **Resume Management** - Track uploads
   - Table shows: Filename, upload date, size
   - Status: Active or Inactive
   - Actions: Activate, Download, Delete
   - Only one resume can be active

### Applications (`/student/applications`)
1. **Summary Cards** - Application stats
   - Total applications
   - Applied count (25%)
   - Interviews (50%)
   - Offers (100%)

2. **Application Cards** - Track each application
   - Job title, company, status, applied date
   - 4-step progress bar showing where you are
   - Next step information
   - Status-specific action buttons

3. **Progress Stages**
   - Applied → Screening → Interview → Offer
   - Current stage highlighted with circle number
   - Completed stages show ✓

### Profile (`/student/profile`)
1. **Edit Profile** - Toggle between view/edit
   - Click "✏️ Edit Profile" button to edit
   - Update personal information
   - Can edit: name, phone, CGPA, LinkedIn, GitHub, bio

2. **Profile Completion** - See what you've filled
   - Percentage shows completion level
   - Missing fields are easily identifiable

3. **Skills Management**
   - View current skills as badges
   - In edit mode: Type skill name and press Enter or click "Add"
   - Remove skills by clicking ✕

4. **Bio** - Write about yourself
   - Personal statement visible in view mode
   - Editable in edit mode

---

## 💼 Recruiter Dashboard Tour

### Main Dashboard (`/recruiter`)
1. **KPI Cards** - Recruitment metrics
   - Jobs posted
   - Applications received
   - Interviews scheduled
   - Offers made

2. **Quick Actions** - Main functions
   - Post New Job
   - View My Jobs
   - Export Applicants
   - View Analytics

3. **Recent Applicants Table** - Latest applications
   - Student name with avatar
   - Position applied for, department, CGPA
   - Applied date, current status, actions
   - Status-colored badges
   - Download resume button

### Post Job (`/recruiter/post-job`)
1. **Post New Job** - Create job listing
   - Click "➕ Post New Job" button
   - Form opens with 10 fields:

2. **Job Form Fields**
   - Job Title (required)
   - Company Name (required)
   - Job Location (required)
   - Salary Package (required, e.g., "20-25 LPA")
   - Job Type (dropdown: Full-Time, Internship, Contract)
   - Minimum CGPA required
   - Application Deadline
   - Required Skills (comma-separated)
   - Detailed Job Description (textarea)

3. **Posted Jobs Display** - View all jobs you posted
   - Job cards with: title, company, location
   - Posted date and deadline
   - Applications count, shortlisted count
   - Interview count, offers count
   - Required skills as badges
   - Actions: View Applicants, Edit, Delete

### Applications (`/recruiter/applications`)
1. **KPI Overview** - Application statistics
   - Total applications
   - By status: Pending, Shortlisted, Interview, Offered

2. **Filter & Search** - Find specific applications
   - Search by student name
   - Filter by status (All, Pending, Shortlisted, Interview, Offered, Rejected)

3. **Applications Table** - Manage candidates
   - Student name with avatar
   - Email, department, CGPA
   - Application status, applied date
   - Action buttons change based on status:

4. **Status Progression**
   - **Pending:** "Shortlist" or "Reject" buttons
   - **Shortlisted:** "Interview" button
   - **Interview:** "Offer" button
   - **All statuses:** "Resume" button to view PDF

### My Jobs (`/recruiter/my-jobs`)
1. **Summary Cards** - Your job posting stats
   - Total jobs posted
   - Total applications across all jobs
   - Total interviews scheduled
   - Total offers made

2. **Status Filter** - Quick navigation
   - All, Active, Closing Soon, Closed
   - Click to filter job postings

3. **Job Cards** - Track each posting
   - Job title, company, location, status
   - 4 mini statistics: Applications, Shortlisted, Interviews, Offers
   - Posted date, deadline, view count
   - Status-specific actions:
     - **Active:** Edit, Close buttons
     - **Closed:** Reopen button
     - Always: Delete button

4. **Job Status Indicators**
   - **Active** (green) - Currently receiving applications
   - **Closing Soon** (amber) - Deadline approaching
   - **Closed** (red) - No longer accepting applications

### Analytics (`/recruiter/analytics`)
1. **KPI Cards** - Performance metrics
   - Total applications received
   - Conversion rate (%)
   - Average time to hire (days)
   - Cost per hire

2. **Charts** - Visualize recruitment data
   - Application Trend (area chart showing weekly growth)
   - Top Jobs Performance (bar chart comparing job popularity)
   - Conversion Funnel (horizontal bar showing stages)
   - Department Distribution (pie chart)

3. **Conversion Rates** - Analysis by stage
   - Applied to Shortlisted percentage
   - Shortlisted to Interview percentage
   - Interview to Offer percentage
   - Overall conversion rate

4. **Key Insights** - Summary cards
   - Best performing job
   - Average response time
   - Most recruited department
   - Top conversion source

5. **Export** - Download reports
   - PDF Report button
   - Export CSV button

---

## 🎯 Common Tasks

### As Admin:
1. **View placement statistics** → Go to `/admin`
2. **Find a specific student** → `/admin/students`, use search
3. **Add a new company** → `/admin/companies`, click "Add Company"
4. **Manage recruiter account** → `/admin/recruiters`, toggle status
5. **Analyze placement trends** → `/admin/analytics`, view charts

### As Student:
1. **Find job opportunities** → `/student/jobs`, use filters
2. **Upload resume** → `/student/resume`, drag & drop file
3. **Track applications** → `/student/applications`, view progress
4. **Update profile** → `/student/profile`, click "Edit Profile"
5. **Apply for job** → `/student/jobs`, click "Apply Now"

### As Recruiter:
1. **Post a new job** → `/recruiter`, click "Post New Job"
2. **Review applications** → `/recruiter/applications`, filter by status
3. **Update job status** → `/recruiter/my-jobs`, click status action
4. **Advance candidate** → `/recruiter/applications`, use status buttons
5. **View recruitment metrics** → `/recruiter/analytics`, analyze charts

---

## 💡 Tips & Tricks

1. **Filtering is Smart** - Use filters to quickly narrow down information
2. **Toast Notifications** - Watch for green success messages confirming actions
3. **Status Badges** - Color-coded badges help quickly identify statuses
4. **Progress Bars** - Visual indicators show completion percentages
5. **Search Works Anywhere** - Most tables have search functionality
6. **Export Data** - Admin can export student data and reports as CSV
7. **Profile Completion** - Students should aim for 100% profile completion
8. **Status Buttons** - Action buttons change based on application/job status
9. **Real-time Updates** - Changes are reflected immediately (using state)
10. **Responsive Design** - Works on desktop, tablet, and mobile

---

## 🔒 Security Notes

- Always logout when finished (email icon → Logout)
- Don't share demo account credentials
- Each role has restricted access to relevant features
- Protected routes prevent unauthorized access

---

## 📞 Need Help?

- Check the sidebar for all available options
- Use search and filter features to find information
- Look for the "?" help icons (future enhancement)
- Hover over fields for tooltips (future enhancement)
- Review this guide for step-by-step instructions

---

**Enjoy using the Campus Placement Management System!**

For detailed technical documentation, see `COMPLETE_DOCUMENTATION.md`
For new pages summary, see `NEW_PAGES_SUMMARY.md`
