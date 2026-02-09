# Test Case Template

> **Copy this template whenever you need to write new test cases**

---

## Test Case Information

| Field | Value |
|-------|-------|
| **Test Case ID** | TC-[MODULE]-[NUMBER] |
| **Module/Feature** | [Feature Name] |
| **Priority** | High / Medium / Low |
| **Test Type** | Functional / UI / Integration / Regression |
| **Created By** | [Your Name] |
| **Date** | [DD/MM/YYYY] |

---

## Test Scenario

**Objective:** [What are we testing?]

---

## Pre-conditions

- [ ] [Condition 1]
- [ ] [Condition 2]
- [ ] [Condition 3]

---

## Test Data

| Field | Value | Type |
|-------|-------|------|
| [Data Field 1] | [Value] | [Valid/Invalid] |
| [Data Field 2] | [Value] | [Valid/Invalid] |

---

## Test Steps

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | [Action description] | [Expected outcome] |
| 2 | [Action description] | [Expected outcome] |
| 3 | [Action description] | [Expected outcome] |

---

## Expected Result

**Overall Expected Behavior:**
- [Expected outcome 1]
- [Expected outcome 2]
- [Expected outcome 3]

---

## Post-conditions

- [What should happen after test execution]
- [Data cleanup needed]

---

## Execution Result

| Field | Value |
|-------|-------|
| **Executed By** | [Name] |
| **Execution Date** | [DD/MM/YYYY] |
| **Environment** | [Dev / QA / UAT / Production] |
| **Build Version** | [Version Number] |
| **Status** | Pass / Fail / Blocked |
| **Remarks** | [Any notes or issues encountered] |

---

## Example Usage

### Example: Login with Valid Credentials

| Field | Value |
|-------|-------|
| **Test Case ID** | TC-AUTH-001 |
| **Module/Feature** | User Authentication |
| **Priority** | High |
| **Test Type** | Functional |

**Test Scenario:** Verify user can login with valid email and password

**Pre-conditions:**
- [ ] User account exists in system
- [ ] User is not already logged in

**Test Data:**

| Field | Value | Type |
|-------|-------|------|
| Email | test@example.com | Valid |
| Password | P@ssw0rd123 | Valid |

**Test Steps:**

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Navigate to login page | Login page displays correctly |
| 2 | Input email: test@example.com | Email field accepts input |
| 3 | Input password: P@ssw0rd123 | Password is masked |
| 4 | Click "Login" button | User redirected to dashboard |
| 5 | Verify user name displays | "Welcome, Test User" appears |

**Expected Result:**
- User successfully logged in
- Redirected to dashboard page
- User session created
- Welcome message displays with correct username

---

## Tips for Writing Good Test Cases

✅ **Be Specific:** Use exact button names, field names as they appear in UI  
✅ **One Action per Step:** Each step = one action  
✅ **Repeatable:** Anyone should be able to execute and get same result  
✅ **Include Test Data:** Specify exact values to use  
✅ **Clear Expected Results:** No ambiguity about what "pass" means
