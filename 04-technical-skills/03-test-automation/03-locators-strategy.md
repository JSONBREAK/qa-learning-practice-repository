# 03 - Locator Strategy: Stability Over Convenience

## 🎯 Why Locator Strategy Matters

Locator คือหัวใจของ E2E automation  
Test จะ stable หรือ flaky ขึ้นอยู่กับการเลือก locator

Bad locator = brittle test  
Good locator = maintainable system

Automation Engineer ต้องคิดเรื่อง "stability first" ไม่ใช่ "เร็วสุด"

---

## 🧱 Locator Priority Strategy (Best → Worst)

### 1️⃣ getByRole (Recommended)
ใช้ role + accessible name  
ดีที่สุดเพราะอิง semantic และ accessibility

```ts
await page.getByRole('button', { name: 'Login' }).click();
```
✔ Stable
✔ Reflect real user behavior
✔ Accessible-driven

### 2️⃣ getByLabel / getByPlaceholder
```ts
await page.getByLabel('Email').fill('user@example.com');
```
✔ อ่านง่าย
✔ ผูกกับ UX โดยตรง
✔ เปลี่ยนยากกว่าการเปลี่ยน class

### 3️⃣ data-testid (Automation-specific)
```ts
await page.getByTestId('login-btn').click();
```
✔ Stable มาก
✔ ไม่ผูกกับ style
✔ ปลอดภัยจาก UI refactor

📌 Best practice: ทีม frontend ควรกำหนด data-testid สำหรับ automation

### 4️⃣ CSS Selector (Use Carefully)
```ts
await page.locator('.btn-primary').click();
```
⚠ UI เปลี่ยน class = test พัง
⚠ Coupled กับ styling

### 5️⃣ XPath (Avoid If Possible)
```ts
await page.locator('//div[2]/button[1]').click();
```
❌ อ่านยาก
❌ เปราะบาง
❌ Maintenance nightmare

🚨 Common Anti-Patterns
❌ Hard-coded nth-child
```ts
await page.locator('div:nth-child(3) > button').click();
```
UI ขยับ 1 element = test fail

❌ Using waitForTimeout
```ts
await page.waitForTimeout(3000);
```
Test ช้า
Flaky
ไม่ deterministic

🧠 Real-World Stability Mindset
Automation ไม่ควรผูกกับ:
- CSS class
- DOM structure
- Animation timing

Automation ควรผูกกับ:
- Business meaning
- User intent
- Accessibility role

🔄 Refactoring Example
Before (Brittle)
```ts
await page.click('.btn-primary');
```
After (Stable)
```ts
await page.getByRole('button', { name: 'Login' }).click();
```

🏗 Integration With Page Object
Example:
```ts
class LoginPage {
  constructor(private page: Page) {}

  emailInput = () => this.page.getByLabel('Email');
  passwordInput = () => this.page.getByLabel('Password');
  loginButton = () => this.page.getByRole('button', { name: 'Login' });

  async login(email: string, password: string) {
    await this.emailInput().fill(email);
    await this.passwordInput().fill(password);
    await this.loginButton().click();
  }
}
```
✔ Centralized locator
✔ Easy maintenance
✔ Cleaner test code

🧪 Dynamic Element Strategy
When dealing with loading states:
```ts
await expect(page.getByTestId('loading')).toBeHidden();
```
Avoid manual waits.

📌 Final Principles
- Prefer semantic locator over structural locator
- Avoid styling-based selector
- Keep locator close to business meaning
- Design automation with frontend collaboration
- Stable locator = reliable CI
- Automation quality starts from locator quality.

---

## 🏆 Advanced Locator Strategy

### 1️⃣ Shadow DOM Handling
Playwright auto-pierces shadow DOM: ไม่ต้องใช้ special API เหมือน Selenium
สามารถใช้ locator chaining ได้เลย

**หมายเหตุ:** Playwright supports open shadow DOM only — closed shadow DOM ยังเข้าถึงไม่ได้

ตัวอย่าง:
```ts
await page.locator('my-element button').click(); // Playwright auto-pierces open shadow DOM
```

### 2️⃣ iFrame Handling
การเข้าถึง element ใน iFrame แบบ modern ใช้ frameLocator ซึ่ง auto-wait และ cleaner

ตัวอย่าง:
```ts
await page.frameLocator('#login-frame').getByRole('button', { name: 'Login' }).click();
```
- frameLocator คือ Playwright modern style, auto-wait, cleaner code

### 3️⃣ Multi-language Locator Strategy
รองรับหลายภาษาใน UI ต้องออกแบบ locator ให้ flexible

ตัวอย่าง:
```ts
await page.getByRole('button', { name: /Login|เข้าสู่ระบบ/ }).click();
```
- ใช้ regex หรือ data-testid เพื่อรองรับ multi-language

### 4️⃣ Strict Mode vs Soft Assertion
- Strict mode: locator ต้อง resolve เป็น single element เมื่อ action ถูกเรียก (default)
- ถ้า locator match หลาย element จะ throw error ทันที
- Soft assertion: ใช้ expect.soft() เพื่อไม่หยุด test ทันทีเมื่อ fail

ตัวอย่าง strict mode:
```ts
await page.getByRole('button', { name: 'Login' }).click(); // ถ้ามีหลายปุ่ม Login จะ error
```
ตัวอย่าง soft assertion:
```ts
await expect.soft(page.getByRole('button', { name: 'Login' })).toBeVisible();
```

### 5️⃣ Locator Performance Consideration
- หลีกเลี่ยง locator ที่กว้างเกินไป เช่น `page.locator('div')` เพราะ lookup cost สูง
- ใช้ role, testId หรือ selector ที่เฉพาะเจาะจงเพื่อลด lookup cost และเพิ่ม speed
- Performance awareness สำคัญกับ CI scale และ reliability

### 6️⃣ Locator Contract Strategy
การตั้งชื่อ data-testid แบบมี contract ช่วยให้ locator stable และ maintainable ระดับทีม

**Naming convention:**
- feature-action-element
- auth-login-button
- cart-checkout-submit

ตัวอย่าง:
```html
<button data-testid="auth-login-button">Login</button>
<button data-testid="cart-checkout-submit">Checkout</button>
```
- ทุกทีมควรตกลง naming contract เพื่อให้ automation code สื่อความหมายและ scale ได้

---

## 🧠 Senior Mindset Principles
- ออกแบบ locator ให้รองรับ UI refactor, multi-language, accessibility
- คิดล่วงหน้าเรื่อง shadow DOM, iFrame, dynamic content
- ทำงานร่วมกับ frontend เพื่อเพิ่ม data-testid, semantic role
- ใช้ strict assertion สำหรับ critical flow, soft assertion สำหรับ exploratory
- ทุก locator ต้องสะท้อน business intent ไม่ใช่แค่ DOM structure

---

Stable locator = reliable automation = scalable QA
