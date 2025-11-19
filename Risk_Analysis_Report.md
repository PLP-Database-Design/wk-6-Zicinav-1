# 🧪 Phase 2 Deliverables — CleanCity: Waste Pickup Scheduler

## 1️⃣ Test Case Table

| TC ID | Test Title | Precondition | Test Steps | Expected Result | Severity | Status |
|-------|-------------|---------------|-------------|------------------|-----------|--------|
| TC01 | Verify application loads correctly | Browser open | Open `index.html` | Homepage displays without console errors | Low | Not Run |
| TC02 | Validate required form fields | Pickup form displayed | Leave all fields blank → Submit | Validation messages appear for all required fields | High | Not Run |
| TC03 | Validate name minimum length | Pickup form displayed | Enter 2-character name → Submit | “Name must be at least 3 characters” shown | Medium | Not Run |
| TC04 | Validate phone number input | Pickup form displayed | Enter letters instead of digits | Validation error: “Enter a valid phone number” | Medium | Not Run |
| TC05 | Validate email format | Pickup form displayed | Enter invalid email (e.g. `abc@`) | “Invalid email format” shown | Medium | Not Run |
| TC06 | Validate preferred date in the past | Pickup form displayed | Enter yesterday’s date | Error: “Date must be today or later” | Medium | Not Run |
| TC07 | Validate comments field | Feedback form displayed | Leave comments empty → Submit | Validation message appears | Medium | Not Run |
| TC08 | Submit valid pickup form | All fields filled correctly | Fill valid data → Submit | Success message, record stored in localStorage | High | Not Run |
| TC09 | View stored requests | After submitting pickup | Navigate to Admin or Dashboard | Recently added record displays | Medium | Not Run |
| TC10 | Filter requests by location = “Eldoret” | At least 2 requests exist | Select location “Eldoret” from filter | Displays only Eldoret requests | **Fails due to bug** | High | Fail |
| TC11 | Filter requests by location = “Nairobi” | As above | Select “Nairobi” | Displays only Nairobi requests | Pass | Not Run |
| TC12 | Admin mark as “Scheduled” | Admin page | Click “Mark as Scheduled” | Status updates in localStorage | Medium | Not Run |
| TC13 | Admin mark as “Completed” | Admin page | Click “Completed” button | Request status updates | Medium | Not Run |
| TC14 | Admin edit button functionality | Admin list displayed | Click Edit on a record | Record populates editable form | Intermittent (depends on click target) | Medium | Fail |
| TC15 | Accessibility: Image alt text | Awareness section loaded | Inspect `<img>` elements | Each image has alt text | **Fails (missing)** | Medium | Fail |
| TC16 | Accessibility: Keyboard navigation | Use Tab key | All form fields focusable in order | Pass | Low | Not Run |
| TC17 | Boundary test – long comments | Feedback form | Enter 500+ chars in comments | App should truncate / wrap properly | Medium | Not Run |
| TC18 | Security check (no authorization) | Open DevTools → edit status manually | Verify if admin actions require auth | Action still executes (vulnerability) | Low | Not Run |
| TC19 | UI refresh after status update | Admin updates request | Observe list reload | List refreshes immediately | **Fails (intermittent)** | Medium | Fail |
| TC20 | LocalStorage persistence | Submit & reload browser | Request remains visible after reload | Pass | Medium | Not Run |


## 2️⃣ Testing Checklist

| Area | Objective | Checks / Notes | Status |
|------|------------|----------------|--------|
| Homepage Load | Ensure UI renders properly | Check layout, console errors | ☐ |
| Pickup Form | Validate fields, boundary inputs | Required, invalid formats, long strings | ☐ |
| Date Field | Verify cannot select past dates | Edge case for timezone differences | ☐ |
| Feedback Form | Validate comment and rating | Empty vs valid data | ☐ |
| Filter Function | Test all location filters | Eldoret bug expected | ☐ |
| Admin Panel | Test edit, mark as scheduled | Observe UI refresh delay | ☐ |
| Data Storage | Verify localStorage data | Inspect saved objects | ☐ |
| Accessibility | Tab order, alt text | Missing alt tags flagged | ☐ |
| Responsive UI | Resize window or use mobile view | Elements adapt correctly | ☐ |
| Error Handling | Submit with blank or invalid data | Meaningful messages appear | ☐ |


## 3️⃣ Initial Defect Log

| Defect ID | Summary | Steps to Reproduce | Actual Result | Expected Result | Severity | Status |
|------------|----------|-------------------|----------------|-----------------|-----------|--------|
| D01 | Eldoret filter returns Nairobi results | Open dashboard → filter by *Eldoret* | Shows *Nairobi* requests | Should show *Eldoret* requests | High | Open |
| D02 | Date validation missing | Enter past date → submit | Accepted | Should reject past dates | Medium | Open |
| D03 | Weak name validation (2 chars accepted) | Enter 2-char name | Accepted | Should require ≥3 characters | Medium | Open |
| D04 | Feedback comments not validated | Submit empty comments | Accepted | Should show error | Medium | Open |
| D05 | Images missing alt attributes | Inspect HTML images | No `alt` text found | All `<img>` need alt text | Medium | Open |
| D06 | Admin edit button intermittent failure | Click edit icon | No data loads if click on icon span | Should load record consistently | Medium | Open |
| D07 | UI not refreshing after update | Change status → view list | UI doesn’t refresh | List should reload immediately | Medium | Open |
| D08 | No authorization control on updates | Modify localStorage directly | Changes accepted | Should restrict unauthorized access | Low | Open |
| D09 | Long input breaks layout | Enter 500-char comments | Layout overflows | Text wraps or truncates | Medium | Open |


## 4️⃣ Recommendations

| Area | Action | Priority |
|------|---------|----------|
| Filter logic | Fix Eldoret condition | High |
| Validation | Add future-date check & stronger name validation | High |
| UI / Accessibility | Add missing `alt` text, input length limits | Medium |
| Admin functions | Refactor button handlers to use `e.currentTarget` | Medium |
| Data integrity | Add authorization / user role handling | Low |
