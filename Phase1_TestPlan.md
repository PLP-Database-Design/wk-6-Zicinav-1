CleanCity Waste Pickup Scheduler – Phase 1 Test Plan

Project Phase: 1 – Planning & Setup 

Due Date: Wednesday, November 5, 2025 

---

1. Project Overview

Project Name: CleanCity – Waste Pickup Scheduler
Description:
CleanCity is a React-based web application simulating a waste management system for African cities. The project includes multiple user flows, form validation, admin workflows, and intentional flaws to provide QA learners a realistic testing environment.

Purpose of Test Plan:

* To outline the testing strategy for Phase 1
* To define testing objectives, scope, resources, and schedule
* To identify risks, dependencies, and test coverage

---

2. Objectives

* Verify that the project repository runs locally without errors
* Ensure core functionality of the application (forms, navigation, and dashboard)
* Test manual and automated QA scenarios
* Identify intentional and unintentional bugs early in development
* Prepare documentation for team roles and communication

---

3. Scope

In Scope:

* Home Page: Waste pickup form validation, success messages
* Dashboard: Display of pickup requests, filtering, and responsive design
* Feedback Page: Form submission, request ID validation
* Awareness Page: Accessibility testing, missing alt-text, responsive grid
* Admin Panel: Request management, status updates, data persistence

Out of Scope:

* Backend API integration (localStorage is used instead)
* Advanced automated deployment tests
* Integration with third-party payment systems

---

4. Test Approach

4.1 Manual Testing

| Test Area            | Test Case                 | Steps                                       | Expected Result                           | Known Issue / Bug                        |
| -------------------- | ------------------------- | ------------------------------------------- | ----------------------------------------- | ---------------------------------------- |
| Form Validation      | Submit empty form         | Click submit without filling fields         | Error messages appear for required fields | Date field doesn’t show validation error |
| Filter Functionality | Filter by location        | Select “Eldoret” in dashboard filter        | Only Eldoret requests shown               | Shows Nairobi requests instead           |
| Accessibility        | Screen reader test        | Navigate Awareness page using screen reader | All images have alt-text                  | Missing alt-text on all images           |
| UI State             | Mark request as scheduled | Click “Mark as Scheduled” in Admin panel    | Status badge updates immediately          | UI doesn’t refresh (localStorage issue)  |
| Boundary Testing     | Long text input           | Enter very long text in form fields         | App handles gracefully                    | Layout may break for very long text      |

4.2 Automated Testing

* Framework: React Testing Library
* Command: `npm test`
* Focus:

  * Component rendering
  * Form validation logic
  * Status update functionality
  * Data persistence checks

4.3 Regression Testing

* Retest after fixing bugs to ensure existing functionality is unaffected
* Verify changes do not introduce new errors

---

5. Test Environment

| Environment      | Details                                                   |
| ---------------- | --------------------------------------------------------- |
| Operating System | Windows 10 / 11                                           |
| Browser          | Chrome, Edge, Firefox                                     |
| Node.js          | v14+ (local development)                                  |
| React Version    | 18.2.0                                                    |
| Data Storage     | localStorage                                              |
| Tools            | VS Code, Browser DevTools, React Testing Library, Netlify |

---

6. Roles & Responsibilities

| Role          | Name             | Responsibilities                                                |
| ------------- | ---------------- | --------------------------------------------------------------- |
| Test Manager  | Palesa Radebe    | Oversees testing process, approves deliverables                 |
| Risk Analyst  | Veliswa Zicina   | Analyzes risks, prioritizes test focus, reports critical issues |
| Test Executor | Josephine Mbugua | Executes test cases, records results, reports bugs              |

---

7. Communication Plan

* Daily Updates: WhatsApp 
* Weekly Meeting: Voice calls to see how far everyone is 
* Issue Reporting: GitHub Issues for bug tracking
* Documentation: Share test logs and reports in repository

---

8. Deliverables

* Test Plan document (this file)
* Manual test cases and logs
* Automated test scripts (React Testing Library)
* Deployment to Netlify
* Team roles and communication plan

9. Approval

| Role          | Name             | Signature | Date       |
| ------------- | ---------------- | --------- | ---------- |
| Test Manager  | Palesa Radebe    | P.Radebe  | 05/11/2025 |
| Risk Analyst  | Veliswa Zicina   | V.Zicina  | 05/11/2025 |
| Test Executor | Josephine Mbugua | J.Mbugua  | 05/11/2025 |
