# Test Summary Report Template

> **Use this template to summarize test execution results**

---

## Report Information

| Field | Value |
|-------|-------|
| **Project/Feature** | [Project Name] |
| **Test Cycle** | [Sprint X / Release X] |
| **Report Date** | [DD/MM/YYYY] |
| **Prepared By** | [Your Name] |
| **Test Period** | [Start Date] - [End Date] |

---

## Executive Summary

**Overall Status:** 🟢 Ready / 🟡 At Risk / 🔴 Not Ready

**Brief Summary:**
[2-3 sentences describing overall test results and readiness]

---

## Test Environment

| Component | Details |
|-----------|---------|
| **Environment** | Dev / QA / UAT / Production |
| **Build Version** | [Version Number] |
| **Test Data** | [Test dataset used] |
| **Browser/Platform** | [Chrome v120, iOS 17, etc.] |

---

## Test Scope

### In Scope
- [Feature/Module 1]
- [Feature/Module 2]
- [Feature/Module 3]

### Out of Scope
- [Items not tested in this cycle]

### Test Types Performed
- [ ] Functional Testing
- [ ] Regression Testing
- [ ] Integration Testing
- [ ] Performance Testing
- [ ] Security Testing
- [ ] API Testing
- [ ] UI/UX Testing

---

## Test Execution Summary

### Overall Statistics

| Metric | Count | Percentage |
|--------|-------|------------|
| **Total Test Cases** | [X] | 100% |
| **Executed** | [X] | [X%] |
| **Passed** | [X] | [X%] |
| **Failed** | [X] | [X%] |
| **Blocked** | [X] | [X%] |
| **Not Executed** | [X] | [X%] |

### Test Results by Priority

| Priority | Total | Passed | Failed | Blocked | Pass Rate |
|----------|-------|--------|--------|---------|-----------|
| **High** | [X] | [X] | [X] | [X] | [X%] |
| **Medium** | [X] | [X] | [X] | [X] | [X%] |
| **Low** | [X] | [X] | [X] | [X] | [X%] |

### Test Results by Module

| Module | Total | Passed | Failed | Blocked | Pass Rate |
|--------|-------|--------|--------|---------|-----------|
| [Module 1] | [X] | [X] | [X] | [X] | [X%] |
| [Module 2] | [X] | [X] | [X] | [X] | [X%] |
| [Module 3] | [X] | [X] | [X] | [X] | [X%] |

---

## Defect Summary

### Defects by Severity

| Severity | Open | In Progress | Fixed | Closed | Total |
|----------|------|-------------|-------|--------|-------|
| **Critical** | [X] | [X] | [X] | [X] | [X] |
| **High** | [X] | [X] | [X] | [X] | [X] |
| **Medium** | [X] | [X] | [X] | [X] | [X] |
| **Low** | [X] | [X] | [X] | [X] | [X] |
| **Total** | [X] | [X] | [X] | [X] | [X] |

### Critical/High Defects

| Bug ID | Summary | Severity | Status | Owner |
|--------|---------|----------|--------|-------|
| [BUG-001] | [Description] | Critical | Open | [Name] |
| [BUG-002] | [Description] | High | Fixed | [Name] |

---

## Key Findings

### ✅ Achievements
- [Achievement 1]
- [Achievement 2]
- [Achievement 3]

### ⚠️ Risks & Issues
- [Risk/Issue 1]
- [Risk/Issue 2]
- [Risk/Issue 3]

### 🚫 Blockers
- [Blocker 1]
- [Blocker 2]

---

## Test Coverage

### Requirements Coverage

| Requirement | Total Test Cases | Executed | Status |
|-------------|------------------|----------|--------|
| [REQ-001] | [X] | [X] | ✅ / ⚠️ / ❌ |
| [REQ-002] | [X] | [X] | ✅ / ⚠️ / ❌ |

**Coverage Rate:** [X%] of requirements tested

### Code Coverage (if applicable)
- **Line Coverage:** [X%]
- **Branch Coverage:** [X%]
- **Function Coverage:** [X%]

---

## Test Metrics

### Execution Progress

```
Week 1: [X%] completed
Week 2: [X%] completed  
Week 3: [X%] completed
Current: [X%] completed
```

### Defect Trend

```
Week 1: [X] defects found
Week 2: [X] defects found
Week 3: [X] defects found
Total: [X] defects found, [X] fixed
```

---

## Recommendations

### Immediate Actions Required
1. [Action 1]
2. [Action 2]
3. [Action 3]

### For Next Cycle
1. [Improvement 1]
2. [Improvement 2]
3. [Improvement 3]

---

## Go / No-Go Assessment

### Go Criteria

- [ ] All critical defects resolved
- [ ] Pass rate > 95%
- [ ] No open blocker issues
- [ ] Performance meets requirements
- [ ] Security scan passed

### Decision

**Recommendation:** ✅ GO / ❌ NO-GO

**Justification:**
[Explain the decision based on criteria above]

---

## Attachments

- [Link to detailed test results]
- [Link to defect tracking system]
- [Link to test cases]
- [Link to test data]

---

## Approvals

| Role | Name | Signature | Date |
|------|------|-----------|------|
| **QA Lead** | [Name] | | [Date] |
| **Project Manager** | [Name] | | [Date] |
| **Product Owner** | [Name] | | [Date] |

---

## Example Report

### Example: E-commerce Checkout Feature

| Field | Value |
|-------|-------|
| **Project** | E-commerce Platform |
| **Feature** | Shopping Cart & Checkout |
| **Test Cycle** | Sprint 15 |
| **Report Date** | 10 Feb 2026 |
| **Test Period** | 3 Feb - 9 Feb 2026 |

**Overall Status:** 🟡 At Risk

**Summary:** Testing completed for checkout flow. 85% pass rate achieved. 2 critical defects remain open affecting payment processing.

### Test Execution Summary

| Metric | Count | Percentage |
|--------|-------|------------|
| **Total Test Cases** | 120 | 100% |
| **Executed** | 115 | 96% |
| **Passed** | 98 | 85% |
| **Failed** | 12 | 10% |
| **Blocked** | 5 | 4% |
| **Not Executed** | 5 | 4% |

### Critical Defects

| Bug ID | Summary | Status |
|--------|---------|--------|
| BUG-045 | Payment fails for credit cards | Open |
| BUG-047 | Order total calculation incorrect | In Progress |

### Recommendation: ❌ NO-GO

**Justification:** 2 critical defects affecting core payment functionality must be fixed before release. Recommend fixing these bugs and re-testing before go-live decision.

---

**Tips for Good Test Summary:**

✅ **Be Honest:** Report actual status, not what stakeholders want to hear  
✅ **Use Visuals:** Charts and graphs help communicate quickly  
✅ **Highlight Critical:** Make critical issues stand out  
✅ **Be Specific:** Use numbers and percentages, not vague terms  
✅ **Actionable:** Include clear recommendations
