

# 📚 QA Learning Roadmap

> บันทึกเส้นทางการเรียนรู้ของตัวเอง - เรียนตามลำดับจากบนลงล่าง

**Status:** ✅ All files organized with clear structure (33+ files updated)  
**Last Updated:** Feb 10, 2026

---

## 🎯 ตารางการเรียนรู้

| หัวข้อ                               | ไฟล์/ลิงก์ที่ต้องอ่าน                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | เรียนได้อะไร                                                                                             |
| ------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **1. พื้นฐาน QA** 🌱                 | 1. [QA Big Picture & Principles](01-qa-fundamentals/01-core-principles/01.%20QA%20Big%20Picture%20&%20Principles.md)<br>2. [SDLC & STLC Framework](01-qa-fundamentals/01-core-principles/02.%20SDLC%20&%20STLC%20Framework.md)<br>3. [Quality Assurance Overview](01-qa-fundamentals/01-core-principles/Quality%20Assurance.md)                                                                                                                                                                                             | ทำความเข้าใจภาพรวม QA ว่าคืออะไร ทำอะไร มีกระบวนการแบบไหน                                                |
| **2. Requirement Analysis** 📋       | 1. [Requirement Analysis](02-qa-process/01-requirement-analysis/01.%20Requirement%20Analysis.md)<br>2. [Acceptance Criteria (AC)](02-qa-process/01-requirement-analysis/02.%20Acceptance%20Criteria%20(AC).md)<br>3. [Impact Analysis](02-qa-process/01-requirement-analysis/03.%20Impact%20Analysis.md)                                                                                                                                                                                                                    | ฝึกอ่าน requirement แล้วแยก AC ออกมาให้ได้, วิเคราะห์ว่าถ้ามีการเปลี่ยนแปลงจะกระทบอะไรบ้าง               |
| **3. Test Design Techniques** 🎨     | 1. [Design Techniques Overview](03-design-techniques/00.%20Design%20Techniques%20Overview.md)<br>2. [Equivalence Partitioning (EP)](03-design-techniques/01-black-box/01.%20Equivalence%20Partitioning%20(EP).md)<br>3. [Boundary Value Analysis (BVA)](03-design-techniques/01-black-box/02.%20Boundary%20Value%20Analysis%20(BVA).md)<br>4. [Decision Table](03-design-techniques/01-black-box/03.%20Decision%20Table.md)                                                                                                 | เรียนรู้เทคนิคต่างๆ เพื่อเลือกใช้ให้เหมาะกับแต่ละสถานการณ์ (เมื่อไหร่ใช้ EP, BVA, Decision Table)        |
| **4. Test Case Design** ✍️           | 1. [Test Case Design](02-qa-process/02-test-design-data/01.%20Test%20Case%20Design.md)<br>2. [Test Case Template](02-qa-process/02-test-design-data/02.%20Test%20Case%20Template.md)<br>3. [Writing Test Steps](02-qa-process/02-test-design-data/03.%20Writing%20Test%20Steps.md)<br>4. [Test Data Strategy](02-qa-process/02-test-design-data/04.%20Test%20Data%20Strategy.md)<br>5. [Traceability Matrix (RTM)](02-qa-process/02-test-design-data/06.%20Traceability%20Matrix%20(RTM).md)                                | ฝึกเขียน test case ให้ชัดเจนจนคนอื่นอ่านแล้วทำตามได้, ออกแบบ test data, ทำ RTM เพื่อ map กับ requirement |
| **5. Test Execution & Reporting** ▶️ | 1. [Test Execution Result](02-qa-process/04-test-reporting/01.%20Test%20Execution%20Result.md)<br>2. [Test Run & Summary Report](02-qa-process/04-test-reporting/03.%20Test%20Run%20&%20Summary%20Report.md)<br>3. [Go & No-Go Criteria](02-qa-process/04-test-reporting/04.%20Go%20&%20No-Go%20Criteria.md)                                                                                                                                                                                                                | รู้ว่าเมื่อไหร่ต้องทำ Smoke/Sanity/Regression, ฝึกรัน test แล้วบันทึกผลและสรุปรายงานให้ได้               |
| **6. Defect Management** 🐛          | 1. [Bug Management Overview](02-qa-process/03-defect-management/01.%20Bug%20Management%20Overview.md)<br>2. [Anatomy of Bug Report](02-qa-process/03-defect-management/02.%20Anatomy%20of%20Bug%20Report.md)<br>3. [Severity vs Priority](02-qa-process/03-defect-management/05.%20Severity%20vs%20Priority.md)<br>4. [Defect Life Cycle](02-qa-process/03-defect-management/06.%20Defect%20Life%20Cycle.md)<br>5. [Root Cause Analysis (RCA)](02-qa-process/03-defect-management/08.%20RCA%20(Root%20Cause%20Analysis).md) | ฝึกเขียน bug report ให้ชัดเจน, จำแยก Severity vs Priority ให้ได้, ลองทำ RCA หาสาเหตุของ bug              |
| **7. Templates & Cheatsheets** 📝    | 1. [Test Case Template](05-templates-cheatsheets/test-case-template.md)<br>2. [Bug Report Template](05-templates-cheatsheets/bug-report-template.md)<br>3. [SQL Cheatsheet](05-templates-cheatsheets/sql-cheatsheet.md)<br>4. [API Testing Checklist](05-templates-cheatsheets/api-testing-checklist.md)                                                                                                                                                                                                                    | Template พร้อมใช้สำหรับการทำงานจริง                                                                      |
| **8. Technical Skills** 🛠️          | _Coming Soon_<br>- SQL for QA<br>- API Testing with Postman<br>- Automation with Playwright                                                                                                                                                                                                                                                                                                                                                                                                                                 | ทักษะเทคนิคสำหรับการทำงาน QA ในยุคปัจจุบัน                                                               |
| **9. Real-World Practice** 💼        | - อ่าน bug report จริงๆ แล้วลองวิเคราะห์ดู<br>- หา case study หรือโปรเจกต์มาลองเขียน test case จริงๆ<br>- ลองทำ automation กับโปรเจกต์ง่ายๆ (Todo App, E-commerce)                                                                                                                                                                                                                                                                                                                                                          | ประยุกต์ใช้ทุกอย่างที่เรียนมา ทำจริง ลองจริง                                                             |

---

## 📂 โครงสร้างเนื้อหารายละเอียด

### 🧠 1. QA Fundamentals (พื้นฐาน)
- **Core Principles** - QA Big Picture, SDLC & STLC, Quality & Risk, Coverage
- **Test Thinking & Mindset** - Test Case Design Intro, Positive & Negative Testing

### ⚙️ 2. QA Process (กระบวนการทำงาน)
- **Requirement Analysis** - อ่าน Requirement, AC, Impact Analysis
- **Test Design & Data** - ออกแบบ Test Case, Test Data, RTM, Review
- **Defect Management** - Bug Report, Severity/Priority, Life Cycle, RCA
- **Test Reporting** - Test Execution Result, Defect Report, Go/No-Go

### 🎨 3. Design Techniques (เทคนิคออกแบบ)
- **Black-box** - EP, BVA, Decision Table, State Transition
- **White-box** - Statement & Decision Coverage
- **Experience-based** - Error Guessing, Exploratory, EBT

### 🛠️ 4. Technical Skills (Coming Soon)
- **SQL for QA** - Data verification, queries, joins
- **API Testing** - Postman, REST APIs, test automation
- **Automation** - Playwright, Selenium, POM

### 📝 5. Templates & Cheatsheets
- **Templates** - Test Case, Bug Report, Test Summary Report
- **Cheatsheets** - SQL, API Testing Checklist

### 📦 6. Resources
- **Examples** - Decision Tables, Test Cases
- **Reference Materials**
- **Build & Change** - Smoke, Sanity, Regression, Re-testing
- **Execution Strategy** - Risk-based, Manual vs Automation

---
## 🎯 QA Tips

- 🤔 กล้าถามเมื่อ requirement ไม่ชัด ตั้งแต่เริ่มต้น
- ✍️ เขียน test case ให้คนอื่นอ่านแล้วทำตามได้ (Reproducible)
- 🔧 ฝึกจากของจริง (Postman, SQL, Playwright)
- 🐛 อ่าน bug report เยอะ ๆ และวิเคราะห์ root cause
- 🤖 เข้าใจแนวคิด automation ก่อน ไม่ต้องรีบเก่ง
- 📊 ใช้ Design Techniques (BVA, EP, Decision Table) เลือก Test Case ที่มีประสิทธิภาพ
- 🎯 รู้ Severity vs Priority ให้ชัด ตรวจสอบความเสี่ยงก่อน Release

---


