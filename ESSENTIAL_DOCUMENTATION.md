# Campus Placement Management System - Essentials

## 1. Purpose
- Minimal non-code documentation for quick understanding.
- Contains file map, tech stack, and implementation steps.

## 2. Files (what they are and why used)
- public/index.html: HTML entrypoint.
- src/index.js: React app entry.
- src/App.js: application root component.
- src/routes/AppRoutes.jsx: all routes + role-based route handling.
- src/routes/ProtectedRoute.jsx: authentication and role guard.
- src/pages/auth/Login.jsx: login UI + demo credentials.
- src/context/AuthContext.jsx: authentication state + role logic.
- src/data/mockData.js: sample data used across dashboards.
- src/lib/api.js: API helper methods (swappable for real backend).
- src/components/layout/Navbar.jsx, Sidebar.jsx: common layout.
- src/components/ui/Button.jsx, Card.jsx, Modal.jsx: reusable controls.
- src/modules/admin/*, src/modules/student/*, src/modules/recruiter/*: feature-specific pages.
- src/utils/helpers.js: shared utility functions.
- src/App.css, src/index.css: styling and theming.
- package.json: dependencies and scripts.

## 3. Tech stack
- React 18 (functional components + hooks)
- React Router DOM 6 (routing)
- Context API (global state)
- Recharts (charts)
- Axios + fetch-ready hooks (API calls)
- CSS + responsive layout

## 4. Implementation steps
1. Clone repository.
2. `npm install`.
3. `npm start`.
4. Visit `http://localhost:3000`.
5. Login with role credentials; explore `/admin`, `/student`, `/recruiter`.
6. To swap mock data for backend: update `src/lib/api.js`, and replace uses of `src/data/mockData.js` with API calls.
7. Extend feature pages in `src/modules/{role}` and add routes in `AppRoutes.jsx`.

## 5. Notes
- This file is the required “matter documentation” with only necessary info.
- Keep existing full documentation as archive, but use this file for practical implementation guide.
