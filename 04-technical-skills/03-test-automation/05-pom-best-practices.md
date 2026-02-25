# 05 – POM Best Practices: Architecture Layer

## 🎯 Purpose
Page Object Model (POM) คือ architectural pattern สำหรับ automation ที่เน้น maintainability, scalability, readability

ไฟล์นี้เน้น:
- Page class separation
- Single responsibility
- Avoid logic in test file
- Reusability
- Anti-pattern (God Page Object)

ไม่ลงรายละเอียด:
- พื้นฐาน Playwright
- Locator strategy
- Test runner config

---

## 🧱 1️⃣ Page Class Separation
- 1 page = 1 class (หรือ 1 component = 1 class)
- แต่ละ class แทน business page จริง เช่น LoginPage, CartPage, CheckoutPage
- ไม่ควรรวมหลาย page ใน class เดียว

---

## ✅ 2️⃣ Single Responsibility Principle
- แต่ละ page class ควรมี responsibility เดียว เช่น LoginPage = login flow เท่านั้น
- Method ใน class ควรสื่อ business action เช่น login(), fillEmail(), fillPassword()
- ไม่ควรมี logic ที่ไม่เกี่ยวกับ page นั้น

---

## 🚫 3️⃣ Avoid Logic in Test File
- Test file ควรเรียก method จาก page object เท่านั้น
- ไม่ควรมี locator, business logic, data setup ใน test file
- Test file = scenario, Page Object = implementation

---

## ♻️ 4️⃣ Reusability
- Page object ควร reusable ข้าม test scenario
- Method ควร generic เช่น fillForm(), submit(), selectItem()
- ไม่ hardcode data ใน page object

---

## ❌ 5️⃣ Anti-pattern: God Page Object
- God Page Object = class ที่รวมทุก flow ทุก locator ทุก method
- Debug ยาก, maintain ยาก, test พังง่าย
- ควรแยก page object ตาม business domain

---


## 🔁 Dependency Direction
- Test layer ต้องไม่รู้ implementation detail
- Page object ต้องไม่ import test logic
- หลีกเลี่ยง circular dependency ระหว่าง page classes

---

## 🧩 Component Object Pattern
UI ที่ reusable (navbar, modal, table, card) ควรถูกแยกเป็น component object
Page class สามารถ compose component เหล่านี้ได้
หลีกเลี่ยงการ duplicate locator/method ในหลาย page

---

## 🏗 Composition over Inheritance
หลีกเลี่ยง deep inheritance chain
ควรใช้ composition แทน เช่น inject helper/service แทนการ extends ซ้อนหลายชั้น

---

## 🔄 Page Lifecycle Awareness
Page object ควรรู้ขอบเขตของตัวเอง เช่น:
- หน้านี้ถือว่า loaded เมื่อไร
- Method ใดควรรอ navigation
- หลีกเลี่ยง cross-page action ใน class เดียว

---

## 🧠 Senior Mindset
- POM ที่ดี = scalable, readable, maintainable
- ทุก class/method ต้องสื่อ business intent
- Test file = business scenario, Page Object = technical implementation
- ยิ่งแยก page object ได้ granular ยิ่ง maintain ง่าย
- หลีกเลี่ยงการรวม logic/data/locator ไว้ใน test file

---

Stable POM = Reliable Automation = Scalable QA
