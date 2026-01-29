https://sampleco.notion.site/Automation-Tester-Exam-1-0-1af60eb8cf41801e9ff2ca3c7e561560

---
# **Automation Tester Exam 1.0**

**empeo** is an all-in-one HR management platform with complete **HRM** and **HRD** features. The app has been on the market for several years and is widely used by companies of all sizes, from small businesses to large public companies. The name e**mpeo** comes from the idea of empowering people. Our goal is to help organizations manage HR efficiently while developing employee potential.

Your task is to **design and implement automation tests** for the **empeo registration system**.

You may use **any programming language or testing framework** that you are comfortable with (e.g., Selenium, Cypress, Playwright, Puppeteer, etc.). The goal is to ensure test coverage, reliability, and clarity of your solution.

### **Test Scope**

The registration system can be accessed here:

👉 [https://uat.tks.co.th/ClientPortal/Register/empeo](https://uat.tks.co.th/ClientPortal/Register/empeo)

Please cover as many scenarios as possible, including but not limited to:

- Successful registration with valid data.
- OTP verification flow.
- Promo code validation.
- Validation of required fields and error handling.
- Edge cases (e.g., invalid phone numbers, expired OTP, reused promo code).

### **Test Data**

You may use the following fixed data for automation:

- **Phone:** 0967690708
- **OTP:** 123456
- **Promo Code:** FREE15DAY
- Other fields: Fill in with appropriate test data as needed.

### **Deliverables**

1. **Test Case Design**
    - Write clear test cases (in Gherkin, table format, or your preferred style) that demonstrate coverage.
2. **Automation Script**
    - Implement automation scripts that execute the test cases.
    - Ensure the scripts can be run locally or in CI/CD (if you choose).
3. **Submission Format**
    - You may submit your work as:
        - A **video recording** of your automation running.
        - The **code files/project** with instructions on how to run.

### **Evaluation Criteria**

- Test coverage and completeness.
- Code readability and maintainability.
- Correct handling of edge cases and validations.
- Ability to demonstrate the test execution clearly.

**Please submit your work within 7 days after receiving this test.**

---

# วิธีทำ

✅ Automation Tester Exam 1.0 – Solution Guide 


แนวคิด:
> - เน้น **Test Coverage**
> - โค้ดอ่านง่าย ดูเป็นงานจริง
> - รองรับการอธิบายตอนสัมภาษณ์

> "Test Coverage ไม่ได้บอกว่าซอฟต์แวร์ไม่มีบั๊ก แต่บอกว่าเราได้ตรวจสอบในส่วนที่สำคัญไปครบถ้วนหรือยัง"
>

---
### 1️⃣ Step 1: Requirement Analysis
### 🔹 เป้าหมาย

> สมัครใช้งานระบบด้วย **Phone + OTP + Promo Code**

🔹 Assumption จากโจทย์
- Registration is completed on a single page
- OTP must be requested before submission
- Promo Code is optional
- Validation and error handling are required

- Enter Phone
- → Validate Phone
- → Request OTP
- → Enter OTP
- → (Optional) Enter Promo Code
- → Submit
- → Success / Error
### 🔹 แตกเป็น “Function”

> “ระบบมี business function อะไรบ้าง?”

| ID  | Function              | Description                        |
| --- | --------------------- | ---------------------------------- |
| F1  | Phone Validation      | Validate phone number format       |
| F2  | Request OTP           | Request OTP after phone validation |
| F3  | OTP Validation        | Validate OTP input                 |
| F4  | Promo Code Validation | Validate promo code                |
| F5  | Registration Submit   | Submit registration                |

|**Field**|**Value**|
|---|---|
|**Phone**|0967690708|
|**OTP**|123456|
|**Promo Code**|FREE15DAY|

---

### 2️⃣ Step 2: Test Strategy
กำหนด 01. Test Levels (Functional, Integration, End-to-End)

- 1️⃣ Test coverage
- 2️⃣ Edge cases (พังยังไงได้บ้าง)
- 3️⃣ Automation clarity (Test ต้องแยกชัด ไม่ยัดมั่ว)

💡1 function = positive, negative, edge

**คิด Test Case คร่าวๆ**
Phone : Valid → Pass, Invalid → error
OTP: Valid → Pass, Invalid/Expired → error
Promo: Valid → Pass, Invalid/ซ้ำ → error

💡: Test coverage

ต้องมี End-to-End ไว้ confirm ว่าทั้ง flow ยังใช้งานได้


---

### 3️⃣ Step 3: Test Case Design (Functional Tests)

🔹 F1 – Phone Validation

|TestCase ID|Function|Test Data|Steps|Expected Result|
|---|---|---|---|---|
|TC-F1-01|Phone Validation|Phone: 0967690708|1. เข้าหน้าลงทะเบียน2. กรอกหมายเลขโทรศัพท์|หมายเลขถูกต้อง (Valid), ปุ่ม Request OTP สามารถกดใช้งานได้|
|TC-F1-02|Phone Validation|Phone: 12345|1. เข้าหน้าลงทะเบียน2. กรอกหมายเลขโทรศัพท์ไม่ครบ|ระบบแสดง Validation error, ปุ่ม Request OTP ไม่สามารถกดได้ (Disabled)|

🔹 Function **Request OTP**: Valid Phone, Invalid Phone

|TestCase ID|Function|Precondition|Steps|Expected Result|
|---|---|---|---|---|
|TC-01|F2|Phone validated|Click Request OTP|OTP sent, OTP input enabled|
|TC-02|F2|Phone not validate|Click Request OTP|OTP request blocked, error shown|

🔹 Function **OTP Validation**:  Valid OTP, Invalid OTP

|TestCase ID|Function|Steps|Expected Result|
|---|---|---|---|
|TC-01|F3|Enter OTP|OTP verified successfully|
|TC-02|F3|Enter OTP|OTP invalid message shown|


🔹 Function OTP Validation: Valid OTP, Invalid OTP

|TestCase ID|Function|Steps|Expected Result|
|---|---|---|---|
|TC-01|F3|Enter OTP|OTP verified successfully|
|TC-02|F3|Enter OTP|OTP invalid message shown|

---

🔹 Function Promo Code Validation: Valid Promo Code

|Function|Test Data|Steps|Expected Result|
|---|---|---|---|
|F4|Promo Code: FREE15DAY|Enter promo code|Promo applied successfully|

🔹 Function Promo Code Validation: Invalid / Reused Promo Code

|Function|Test Data|Steps|Expected Result|
|---|---|---|---|
|F4|Promo Code: FREE15DAY (reused)|Enter promo code|Promo error message shown|

---


🔹 Function Registration Submit: OTP Verified

|Function|Precondition|Steps|Expected Result|
|---|---|---|---|
|F5|OTP verified|Click Submit|Registration success|
🔹 Function Registration Submit: Submit Without OTP

|Function|Steps|Expected Result|
|---|---|---|
|F5|Click Submit|Submit blocked, error shown|

---

🔹 Validation Tests

|Case ID|Scenario|Expected Result|
|---|---|---|
|VAL-001|Phone empty|Required field error|
|VAL-002|Phone non-numeric|Validation error|
|VAL-003|OTP empty|Error shown|
|VAL-004|Promo format invalid|Error shown|

🔹 Edge Cases

|Case ID|Scenario|Expected Result|
|---|---|---|
|EDGE-001|OTP expired|OTP expired message|
|EDGE-002|Request OTP many times|Rate limit message|
|EDGE-003|Change phone after OTP|OTP reset|
|EDGE-004|Refresh page after OTP|OTP invalid|

🔹 Integration Test – Phone → OTP

| Steps                                 | Expected Result          |
| ------------------------------------- | ------------------------ |
| Enter phone → Request OTP → Enter OTP | OTP flow works correctly |

🔹 End-to-End Test – Successful Registration

| Item            | Detail                       |
| --------------- | ---------------------------- |
| Test Data       | Phone + OTP + Promo          |
| Steps           | Full registration flow       |
| Expected Result | User registered successfully |

🔹 Mapping กับ Evaluation Criteria

|Criteria|Covered By|
|---|---|
|Test Coverage|Functional + Validation + Edge|
|Readability|One function per test|
|Edge Cases|Dedicated edge tests|
|Execution Clarity|End-to-End test|

---

## 4️⃣ Step 4: Automation Test Design (Concept)

> 👉 **Automation Script + แนวคิดการออกแบบโค้ด**

```
tests/
	functional/
		validation.spec.ts
		otp-request.spec.ts
		otp-validation.spec.ts
		promo.spec.ts
		registration-submit.spec.ts
	e2e/
		full-registration.spec.ts
```

### 5️⃣ Functional Tests

🔹 F1 – Phone Validation

`tests/functional/phone-validation.spec.ts`

```
import { test, expect } from '@playwright/test';

test.describe('F1 – Phone Validation', () => {
  test('TC-F1-01: valid phone enables Request OTP', async ({ page }) => {
    await page.goto('/ClientPortal/Register/empeo');
    await page.fill('input[name="phone"]', '0967690708');
    const requestOtpBtn = page.getByRole('button', { name: 'Request OTP' });
    await expect(requestOtpBtn).toBeEnabled();
  });

  test('TC-F1-02: invalid phone shows error', async ({ page }) => {
    await page.goto('/ClientPortal/Register/empeo');
    await page.fill('input[name="phone"]', '12345');
    await expect(page.getByText(/invalid phone/i)).toBeVisible();
  });
});
```

🔹 F2 – Request OTP

`tests/functional/otp-request.spec.ts`

```
import { test, expect } from '@playwright/test';

test.describe('F2 – Request OTP', () => {
  test('Request OTP with valid phone', async ({ page }) => {
    await page.goto('/ClientPortal/Register/empeo');
    await page.fill('input[name="phone"]', '0967690708');
    await page.click('button:has-text("Request OTP")');
    await expect(page.locator('input[name="otp"]')).toBeVisible();
  });
});
```

🔹 F3 – OTP Validation

`tests/functional/otp-validation.spec.ts`

```
import { test, expect } from '@playwright/test';

test.describe('F3 – OTP Validation', () => {
  test('Valid OTP', async ({ page }) => {
    await page.goto('/ClientPortal/Register/empeo');
    await page.fill('input[name="phone"]', '0967690708');
    await page.click('button:has-text("Request OTP")');
    await page.fill('input[name="otp"]', '123456');
    await expect(page.getByText(/otp verified/i)).toBeVisible();
  });
});
```

🔹 F4 – Promo Code

```
import { test, expect } from '@playwright/test';

test.describe('F4 – Promo Code Validation', () => {
test('Valid promo code', async ({ page }) => {
await page.goto('/ClientPortal/Register/empeo');
await page.fill('input[name="promoCode"]', 'FREE15DAY');
await expect(page.getByText(/promo applied/i)).toBeVisible();
});

});
```

🔹 F5 – Registration Submit

`tests/functional/registration-submit.spec.ts`

```
import { test, expect } from '@playwright/test';

test.describe('F5 – Registration Submit', () => {
  test('Submit after OTP verified', async ({ page }) => {
    await page.goto('/ClientPortal/Register/empeo');
    await page.fill('input[name="phone"]', '0967690708');
    await page.click('button:has-text("Request OTP")');
    await page.fill('input[name="otp"]', '123456');
    await page.click('button:has-text("Submit")');
    await expect(page.getByText(/registration success/i)).toBeVisible();
  });
});
```

---
## 6️⃣ Step 7: End-to-End Test

`tests/e2e/full-registration.spec.ts`

```
import { test, expect } from '@playwright/test';

test('TC-E2E-001 – Successful Registration', async ({ page }) => {
await page.goto('/ClientPortal/Register/empeo');
await page.fill('input[name="phone"]', '0967690708');
await page.click('button:has-text("Request OTP")');
await page.fill('input[name="otp"]', '123456');
await page.fill('input[name="promoCode"]', 'FREE15DAY');
await page.click('button:has-text("Submit")');
await expect(page.getByText(/success/i)).toBeVisible();

});
```

