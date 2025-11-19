1. Project Overview

Project: CleanCity – Waste Pickup Scheduler
Description: React-based waste management simulation app for African cities, including forms, dashboards, admin tools, accessibility checks, and intentional bugs for QA training.

Testing Goal:

Validate core functionality

Identify bugs early

Ensure usability, accessibility, and data persistence

Support both manual + automated test coverage

2. Test Objectives

Verify the app runs locally without errors

Test form validation & navigation

Validate admin workflows

Run automated tests (React Testing Library)

Perform regression tests for fixed issues

3. Test Scope
   ✔ In Scope

Home Page: Form validation, submission

Dashboard: Filtering, display, responsiveness

Feedback Page

Awareness Page: Accessibility

Admin Panel: Status updates, localStorage persistence

✖ Out of Scope

Backend API

Payment systems

CI/CD automated deployment testing

4. Test Approach
   4.1 Manual Testing

Key focus areas:

Form validation

Filters

Accessibility (alt text, keyboard navigation)

UI state updates

Boundary inputs (long strings)

4.2 Automated Testing

Tool: React Testing Library
Command: npm test

Covers:

Component rendering

Validation logic

Status updates

LocalStorage behaviour

4.3 Regression Testing

Re-run all high-severity cases after fixes

Confirm no new bugs introduced

5. Test Environment
   Component Version / Details
   OS Windows 10 / 11
   Browsers Chrome, Firefox, Edge
   Node.js v14+
   React 18.2.0
   Storage localStorage
   Tools VS Code, DevTools, React Testing Library, Netlify

6. Roles & Responsibilities
   Role Person
   Test Manager Palesa Radebe
   Risk Analyst Veliswa Zicina
   Test Executor Veliswa Zicina

7. Communication Plan

Daily: WhatsApp

Weekly: Voice call check-ins

Bugs: GitHub Issues

Docs: Shared in project repo

8. Test Case Summary (Condensed)
   TC ID Title Expected Result Status
   TC01 App loads correctly Homepage loads w/o errors Not Run
   TC02 Required form validation All required errors show Not Run
   TC03 Min name length Reject <3 chars Not Run
   TC04 Phone number validation Reject non-digits Not Run
   TC05 Email validation Reject invalid email Not Run
   TC06 Past date selection Reject past dates Not Run
   TC07 Comments required Error when empty Not Run
   TC08 Valid pickup form Saves + success message Not Run
   TC09 View stored requests Displays saved entry Not Run
   TC10 Filter Eldoret Show Eldoret only Fail
   TC14 Admin edit Edit should load record Fail
   TC15 Alt text check All imgs have alt Fail
   TC19 UI refresh after update List refreshes Fail
   Others Various validation, boundary, security tests Pass/Not Run Mixed

9. Defect Log (Condensed)
   ID Summary Severity Status
   D01 Eldoret filter returns Nairobi results High Open
   D02 Date validation missing Medium Open
   D03 Weak name validation Medium Open
   D04 Comments accepted when empty Medium Open
   D05 Missing alt attributes Medium Open
   D06 Admin edit intermittent fail Medium Open
   D07 UI not refreshing after updates Medium Open
   D08 No authorization control Low Open
   D09 Long input breaks layout Medium

10. Recommendations
    Area Recommendation Priority
    Filter logic Fix conditional check for Eldoret High
    Validation Add date + strong name validation High
    Accessibility Add alt text + limit long input lengths Medium
    Admin functions Improve click handlers + refresh UI Medium
    Security Add authorization checks Low

11. Approval Sign-Off
    Role Name Signature Date
    Test Manager Palesa Radebe P.Radebe 05/11/2025
    Risk Analyst Veliswa Zicina V.Zicina 05/11/2025
    Test Executor Veliswa Zicina V Zicina 05/11/2025
