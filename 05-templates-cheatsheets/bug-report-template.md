# Bug Report Template

> **Use this template to report defects clearly and completely**

---

## Bug Information

| Field | Value |
|-------|-------|
| **Bug ID** | BUG-[NUMBER] |
| **Summary** | [Short description of the bug] |
| **Reporter** | [Your Name] |
| **Date Reported** | [DD/MM/YYYY] |
| **Module/Feature** | [Feature Name] |

---

## Classification

| Field | Value |
|-------|-------|
| **Severity** | Critical / High / Medium / Low |
| **Priority** | High / Medium / Low |
| **Status** | New / Open / In Progress / Fixed / Closed / Rejected |
| **Bug Type** | Functional / UI / Performance / Security / Data |

---

## Environment

| Field | Value |
|-------|-------|
| **Environment** | Dev / QA / UAT / Production |
| **Build/Version** | [Version Number] |
| **Browser** | [Chrome/Firefox/Safari + Version] |
| **OS** | [Windows/Mac/Linux + Version] |
| **Device** | [Desktop/Mobile/Tablet] |

---

## Test Data

| Field | Value |
|-------|-------|
| **User Account** | [Test account used] |
| **Test Data** | [Specific data values] |

---

## Frequency

- [ ] Always (100% reproducible)
- [ ] Sometimes (Intermittent)
- [ ] Once (Cannot reproduce)

---

## Pre-conditions

[Describe the state before bug occurs]

Example:
- User is logged in
- Has active subscription
- Shopping cart has 3 items

---

## Steps to Reproduce

1. [Step 1]
2. [Step 2]
3. [Step 3]
4. [Step 4]

---

## Actual Result

**What actually happened:**

[Describe the incorrect behavior]

---

## Expected Result

**What should happen:**

[Describe the correct behavior based on requirements]

---

## Evidence

**Screenshots/Videos:**
- [Attach screenshot 1]
- [Attach screenshot 2]
- [Attach video if applicable]

**Logs/Error Messages:**
```
[Paste error messages, console logs, or API responses here]
```

---

## Additional Information

**Impact:**
- [Describe business impact]
- [Number of users affected]

**Workaround:**
- [If any workaround exists, describe it]

**Related Bugs:**
- [BUG-XXX] [Description]

---

## Example Bug Report

### Example: Transfer Amount Exceeds Limit

| Field | Value |
|-------|-------|
| **Bug ID** | BUG-001 |
| **Summary** | System allows money transfer exceeding daily limit of 50,000 THB |
| **Severity** | Critical |
| **Priority** | High |
| **Environment** | UAT |
| **Build/Version** | v1.2.3 |
| **Browser** | Chrome v120 |

**Pre-conditions:**
- User logged in with account ID: TEST_001
- Account balance: 100,000 THB
- Daily transfer limit: 50,000 THB
- No transfers made today

**Steps to Reproduce:**

1. Navigate to "Transfer Money" page
2. Input amount: 50,001 THB
3. Select recipient account: 123-456-789
4. Click "Confirm Transfer" button
5. Click "Confirm" on confirmation popup

**Actual Result:**
- System processes transfer successfully
- Amount 50,001 THB deducted from account
- Success message: "Transfer completed successfully"
- New balance: 49,999 THB

**Expected Result:**
- System should reject transfer
- Error message should display: "Transfer amount exceeds daily limit of 50,000 THB"
- No amount deducted from account

**Evidence:**
- [Screenshot: success_message.png]
- [Screenshot: account_balance.png]
- API Response:
```json
{
  "status": "success",
  "amount": 50001,
  "message": "Transfer completed"
}
```

**Impact:**
- Business rule violation
- Financial risk
- Affects all users

**Frequency:** Always (100% reproducible)

---

## Severity vs Priority Guide

### Severity (Technical Impact)

| Level | Definition | Example |
|-------|------------|---------|
| **Critical** | System crash, data loss, security breach | Cannot login, payment fails, data corruption |
| **High** | Major function broken | Cannot checkout, search not working |
| **Medium** | Function works but with issues | Slow performance, incorrect calculation |
| **Low** | Minor issues, cosmetic | Typo, misaligned button |

### Priority (Business Urgency)

| Level | Definition | When to Use |
|-------|------------|-------------|
| **High** | Must fix before release | Blocking critical feature, business impact |
| **Medium** | Should fix in current sprint | Important but has workaround |
| **Low** | Can fix later | Nice to have, minimal impact |

---

## Tips for Writing Good Bug Reports

✅ **Clear Summary:** Read it and know what's broken  
✅ **Reproducible Steps:** Dev can follow and see the bug  
✅ **Exact Values:** Use actual data, not "some value"  
✅ **Evidence:** Screenshots with highlights  
✅ **One Bug per Report:** Don't mix multiple issues  
✅ **No Assumptions:** State facts, not opinions
