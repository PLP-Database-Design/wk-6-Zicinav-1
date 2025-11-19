# 🧪 Phase 2 Deliverables — CleanCity: Waste Pickup Scheduler

## 1️⃣ Test Case Table — Draft

| TC ID | Test Title | Precondition | Test Steps | Expected Result | Severity | Status |
|-------|-------------|---------------|-------------|------------------|-----------|--------|
| TC01 | Verify application loads correctly | Browser open | Open `index.html` | Homepage displays without console errors | Low | Pass |
| TC02 | Validate required form fields | Pickup form displayed | Leave all fields blank → Submit | Validation messages appear for all required fields | High | Partial(sequential validation instead of aggregate) |
| TC03 | Validate name minimum length | Pickup form displayed | Enter 2-character name → Submit | “Name must be at least 3 characters” shown | Medium | Fail(Form submits for single and double character names) |
| TC04 | Validate full name input | Pickup form displayed | Enter digits instead of letters | Validation error: “Enter a valid name” | Medium | Fail(Form submits withy digits in the name field)|
| TC05 | Validate email format | Pickup form displayed | Enter invalid email (e.g. `abc@`) | “Invalid email format” shown | Medium | Pass |
| TC06 | Validate preferred date in the past | Pickup form displayed | Enter yesterday’s date | Error: “Date must be today or later” | Medium | Fail(Form submits with past dates) |
| TC07 | Validate comments field | Feedback form displayed | Leave comments empty → Submit | Validation message appears | Medium | Pass |
| TC08 | Submit valid pickup form | All fields filled correctly | Fill valid data → Submit | Success message, record stored in localStorage | High | Fail(Records not found under profile) |
| TC09 | View stored requests | After submitting pickup | Navigate to Admin or Dashboard | Recently added record displays | Medium | Fail(dashboard shows zero requests) |
| TC10 | Admin edit button functionality | Admin list displayed | Click Edit on a record | Record populates editable form| Medium | Fail(depends on click target) |
| TC11 | Accessibility: Keyboard navigation | Use Tab key | All form fields focusable in order | Pass | Low | Pass |
| TC12 | Boundary test – long comments | Feedback form | Enter 500+ chars in comments | App should truncate / wrap properly | Medium | Pass |
| TC13 | LocalStorage persistence | Submit & reload browser | Request remains visible after reload | Pass | Medium | Fail (Requests are not stored) |


## 2️⃣ Exploratory Testing Checklist

| Area | Objective | Checks / Notes | Status |
|------|------------|----------------|--------|
| Homepage Load | Ensure UI renders properly | Check layout, console errors | [X] |
| Pickup Form | Validate fields, boundary inputs | Required, invalid formats, long strings | [X] |
| Date Field | Verify cannot select past dates | Edge case for timezone differences | [X] |
| Feedback Form | Validate comment and rating | Empty vs valid data | [X] |
| Data Storage | Verify localStorage data | Inspect saved objects | [X] |
| Accessibility | Tab order, alt text | Missing alt tags flagged |[X]  |
| Responsive UI | Resize window or use mobile view | Elements adapt correctly | [X] |
| Error Handling | Submit with blank or invalid data | Meaningful messages appear | [X] |


## 3️⃣ Initial Defect Log

| Defect ID | Summary | Steps to Reproduce | Actual Result | Expected Result | Severity | Status |
|------------|----------|-------------------|----------------|-----------------|-----------|--------|
| D01 | Date validation missing | Enter past date → submit | Accepted | Should reject past dates | Medium | Open |
| D02 | Weak name validation (2 chars accepted) | Enter 2-char name | Accepted | Should require ≥3 characters | Medium | Open |
| D03 | Feedback comments not validated | Submit empty comments | Accepted | Should show error | Medium | Open |
| D04 | Images missing alt attributes | Inspect HTML images | No `alt` text found | All `<img>` need alt text | Medium | Open |
| D05 | UI not refreshing after update | Change status → view list | UI doesn’t refresh | List should reload immediately | Medium | Open |
| D06 | No authorization control on updates | Modify localStorage directly | Changes accepted | Should restrict unauthorized access | Low | Open |


## 4️⃣ Recommendations

| Area | Action | Priority |
|------|---------|----------|
| Validation | Add future-date check & stronger name validation | High |
| UI / Accessibility | Add missing `alt` text, input length limits | Medium |
| Data integrity | Add authorization / user role handling | Low |
