# Playwright Basics: Operational Foundation

## 1️⃣ Playwright คืออะไร
Playwright คือเครื่องมือสำหรับการทดสอบ End-to-End (E2E) ที่รองรับ Chromium, Firefox, WebKit สามารถรันแบบ parallel, headless และเหมาะกับการทดสอบอัตโนมัติในระดับ production


## 2️⃣ Installation & Project Setup
```bash
npm init -y
npm install -D @playwright/test
npx playwright install
```
**Test runner** คือระบบที่จัดการการรัน test, assertion, report
**playwright.config.js** ใช้กำหนด config เช่น baseURL, testDir, reporter, retries, trace

ตัวอย่าง config ที่ production-aware:
```js
// playwright.config.js
module.exports = {
  use: {
    baseURL: 'https://example.com',
  },
  retries: 2,
  trace: 'on-first-retry',
};
```
**baseURL** ทำให้ test เขียนแบบ relative path ได้ เช่น `page.goto('/login')`
**retries** เพิ่ม reliability ให้ test suite
 test('login page should load', async ({ page }) => {
 **trace** เปิด trace viewer อัตโนมัติเมื่อ retry


## 3️⃣ Basic Test Structure
ตัวอย่างโครงสร้าง test suite:
```js
import { test, expect } from '@playwright/test';

test.describe('Login Feature', () => {
  test.beforeEach(async ({ page }) => {
    await page.goto('/login'); // ใช้ baseURL จาก config
  });

  test('should login successfully', async ({ page }) => {
    await page.fill('#email', 'user@example.com');
    await page.fill('#password', 'password123');
    await page.click('button[type="submit"]');
    await expect(page).toHaveURL(/dashboard/);
  });

  test('should show error on fail', async ({ page }) => {
    await page.fill('#email', 'wrong@example.com');
    await page.fill('#password', 'wrongpass');
    await page.click('button[type="submit"]');
    await expect(page.locator('.error')).toBeVisible();
  });
});
```
- `test.describe()` คือการจัดกลุ่ม test suite
- `test.beforeEach()` เตรียม environment ก่อนแต่ละ test
- `page.goto('/login')` ใช้ baseURL จาก config
- `test()` คือฟังก์ชันสร้าง test case
- `page` fixture คือ browser context
- ใช้ `async/await` เพื่อจัดการ async operation
- `expect()` ใช้ assertion ตรวจสอบผลลัพธ์

## 4️⃣ Core Actions ที่ต้องรู้
- `page.goto(url)` เปิดหน้าเว็บ
- `page.click(selector)` คลิก element
- `page.fill(selector, value)` กรอกข้อมูล
- `page.locator(selector)` หา element
- `page.waitForSelector(selector)` รอ element
- `expect()` ใช้ตรวจสอบผลลัพธ์

**Playwright auto-wait**: ทุก action จะรอ element พร้อมโดยอัตโนมัติ ไม่ควรใช้ hard wait (`waitForTimeout`) เพราะทำให้ test ช้าและ brittle

## 5️⃣ Assertions Strategy
- `toHaveText`
- `toBeVisible`
- `toHaveURL`
- `toHaveValue`

**Assertion** คือหัวใจของ automation test ไม่ใช่แค่คลิกแล้วจบ ต้องตรวจสอบผลลัพธ์ทุกครั้ง

## 6️⃣ Test Execution
```bash
npx playwright test
npx playwright test tests/login.spec.ts
npx playwright test --headed
npx playwright test --debug
```
- **Trace viewer**: ดูรายละเอียดการรัน test
- **HTML report**: สรุปผล test แบบมืออาชีพ

## 7️⃣ Best Practice ระดับพื้นฐาน
- แยก test ตาม feature
- ตั้งชื่อ test ให้สื่อ business
- หลีกเลี่ยง brittle selector (เช่นใช้ data-testid)
- อย่าเขียนทุกอย่างใน test file เดียว

## 8️⃣ Mini Practical Example
### Example: Login Flow
ตัวอย่างโค้ด:
```js
import { test, expect } from '@playwright/test';

test('login success', async ({ page }) => {
  await page.goto('/login');
  await page.fill('#email', 'user@example.com');
  await page.fill('#password', 'password123');
  await page.click('button[type="submit"]');
  await expect(page).toHaveURL(/dashboard/);
});

test('login fail', async ({ page }) => {
  await page.goto('/login');
  await page.fill('#email', 'wrong@example.com');
  await page.fill('#password', 'wrongpass');
  await page.click('button[type="submit"]');
  await expect(page.locator('.error')).toBeVisible();
});
```

## Screenshot & Report
Playwright สามารถ capture screenshot และสร้าง HTML report อัตโนมัติ
```js
await page.screenshot({ path: 'login.png' });
```

## Debugging Test Failures
- ใช้ `--debug` mode
- เปิด trace viewer
- ดู log และ screenshot

---

## 🧠 Deep Dive: Playwright Behavior

### 1. Auto-wait & Timing
Playwright จะ auto-wait ทุก action เช่น click, fill, assertion โดยรอจนกว่า element จะพร้อม (visible, enabled, attached, stable) ไม่ต้องใช้ sleep/hard wait

**ตัวอย่าง:**
```js
await page.click('#submit'); // จะรอจนปุ่มพร้อม ไม่ต้อง wait เอง
```
หาก element ไม่พร้อมจริง จะ timeout และแจ้ง error

### 2. Flaky Test & Dynamic Element
ปัญหาที่เจอจริง เช่น element เปลี่ยน state, network delay, animation ทำให้ test fail แบบ intermittent

**วิธีแก้:**
- ใช้ locator ที่ robust เช่น data-testid
- ใช้ expect assertion ที่ flexible เช่น toBeVisible, toHaveText
- ใช้ waitForSelector เฉพาะกรณีจำเป็น

**ตัวอย่าง:**
```js
await expect(page.locator('.loading')).toBeHidden(); // รอ loading หาย
```

### 3. Test Isolation & Parallelism
Playwright สร้าง browser context ใหม่ทุก test เพื่อ isolation ไม่เกิด side effect ระหว่าง test
สามารถรัน parallel ได้จริง (config workers)

**ตัวอย่าง:**
```js
// playwright.config.js
module.exports = {
  workers: 4, // รัน parallel 4 workers
};
```

### 4. Debugging Failures ในงานจริง
เมื่อ test fail ใน production:
- เปิด trace viewer ดู step-by-step
- ดู screenshot, video, log
- ใช้ headed mode, slowMo เพื่อสังเกต behavior

**ตัวอย่าง:**
```bash
npx playwright test --trace
npx playwright show-trace trace.zip
```

### 5. Mindset ของ Automation Engineer
- คิดล่วงหน้าเรื่อง reliability: test ต้องไม่ flaky
- maintainability: selector ต้อง robust, code ต้อง reusable
- performance: test ต้องเร็ว ไม่ใช้ hard wait
- reporting: ทุก test ต้องมี assertion และ report

---

## Example: ปัญหาจริง & วิธีแก้

**Case:** Login flow fail เพราะ animation delay
```js
await page.click('#login');
await expect(page.locator('.dashboard')).toBeVisible(); // บางครั้ง fail เพราะ dashboard ยังไม่โหลด
```
**Solution:**
```js
await page.waitForSelector('.dashboard', { state: 'visible' });
await expect(page.locator('.dashboard')).toBeVisible();
```

**Case:** Selector brittle เพราะ UI เปลี่ยน
```js
await page.click('.btn-primary'); // UI เปลี่ยน class ทำให้ test fail
```
**Solution:**
```js
await page.click('[data-testid="login-btn"]'); // ใช้ data-testid
```

---



