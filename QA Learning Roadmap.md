

# 📚 QA Learning Roadmap

> บันทึกเส้นทางการเรียนรู้ของตัวเอง - เรียนตามลำดับจากบนลงล่าง

---

## 🎯 ตารางการเรียนรู้

| หัวข้อ | ไฟล์/ลิงก์ที่ต้องอ่าน | เรียนได้อะไร |
|--------|------------------------|--------------|
| **1. พื้นฐาน QA** 🌱 | 1. [QA Big Picture & Principles](03-knowledge-base/01-qa-fundamentals/01-core-principles/01.%20QA%20Big%20Picture%20&%20Principles.md)<br>2. [SDLC & STLC Framework](03-knowledge-base/01-qa-fundamentals/01-core-principles/02.%20SDLC%20&%20STLC%20Framework.md)<br>3. [Test Levels](03-knowledge-base/03-testing-strategy/01.%20Test%20Levels.md)<br>4. [Test Types](03-knowledge-base/03-testing-strategy/02.%20Test%20Types%20(Functional%20&%20Non-Functional).md) | ทำความเข้าใจภาพรวม QA ว่าคืออะไร ทำอะไร มีกระบวนการแบบไหน |
| **2. Requirement Analysis** 📋 | 1. [Requirement Analysis](01-real-world-operations/01-requirement-analysis/01.%20Requirement%20Analysis.md)<br>2. [Acceptance Criteria (AC)](01-real-world-operations/01-requirement-analysis/02.%20Acceptance%20Criteria%20(AC).md)<br>3. [Impact Analysis](01-real-world-operations/01-requirement-analysis/03.%20Impact%20Analysis.md) | ฝึกอ่าน requirement แล้วแยก AC ออกมาให้ได้, วิเคราะห์ว่าถ้ามีการเปลี่ยนแปลงจะกระทบอะไรบ้าง |
| **3. Test Design Techniques** 🎨 | 1. [Design Techniques Overview](03-knowledge-base/02-design-techniques/00.%20Design%20Techniques%20Overview.md)<br>2. [Equivalence Partitioning (EP)](03-knowledge-base/02-design-techniques/01-black-box/01.%20Equivalence%20Partitioning%20(EP).md)<br>3. [Boundary Value Analysis (BVA)](03-knowledge-base/02-design-techniques/01-black-box/02.%20Boundary%20Value%20Analysis%20(BVA).md)<br>4. [Decision Table](03-knowledge-base/02-design-techniques/01-black-box/03.%20Decision%20Table.md) | เรียนรู้เทคนิคต่างๆ เพื่อเลือกใช้ให้เหมาะกับแต่ละสถานการณ์ (เมื่อไหร่ใช้ EP, BVA, Decision Table) |
| **4. Test Case Design** ✍️ | 1. [Test Case Design](01-real-world-operations/02-test-design-data/01.%20Test%20Case%20Design.md)<br>2. [Test Case Template](01-real-world-operations/02-test-design-data/02.%20Test%20Case%20Template.md)<br>3. [Writing Test Steps](01-real-world-operations/02-test-design-data/03.%20Writing%20Test%20Steps.md)<br>4. [Test Data Strategy](01-real-world-operations/02-test-design-data/04.%20Test%20Data%20Strategy.md)<br>5. [Traceability Matrix (RTM)](01-real-world-operations/02-test-design-data/06.%20Traceability%20Matrix%20(RTM).md) | ฝึกเขียน test case ให้ชัดเจนจนคนอื่นอ่านแล้วทำตามได้, ออกแบบ test data, ทำ RTM เพื่อ map กับ requirement |
| **5. Test Execution** ▶️ | 1. [Test Execution Strategy](03-knowledge-base/03-testing-strategy/06.%20Test%20Execution%20Strategy.md)<br>2. [Build & Change-Related Testing](03-knowledge-base/03-testing-strategy/03.%20Build%20&%20Change-Related%20Testing%20(Smoke,%20Sanity,%20Regression,%20Re-testing).md)<br>3. [Test Execution Result](01-real-world-operations/04-test-reporting/01.%20Test%20Execution%20Result.md)<br>4. [Test Run & Summary Report](01-real-world-operations/04-test-reporting/03.%20Test%20Run%20&%20Summary%20Report.md) | รู้ว่าเมื่อไหร่ต้องทำ Smoke/Sanity/Regression, ฝึกรัน test แล้วบันทึกผลและสรุปรายงานให้ได้ |
| **6. Defect Management** 🐛 | 1. [Bug Management Overview](01-real-world-operations/03-defect-management/01.%20Bug%20Management%20Overview.md)<br>2. [Anatomy of Bug Report](01-real-world-operations/03-defect-management/02.%20Anatomy%20of%20Bug%20Report.md)<br>3. [Severity vs Priority](01-real-world-operations/03-defect-management/05.%20Severity%20vs%20Priority.md)<br>4. [Defect Life Cycle](01-real-world-operations/03-defect-management/06.%20Defect%20Life%20Cycle.md)<br>5. [Root Cause Analysis (RCA)](01-real-world-operations/03-defect-management/08.%20RCA%20(Root%20Cause%20Analysis).md) | ฝึกเขียน bug report ให้ชัดเจน, จำแยก Severity vs Priority ให้ได้, ลองทำ RCA หาสาเหตุของ bug |
| **7. API & SQL** 🛠️ | 1. [API Fundamentals](02-technical-stack/01-api-testing/01.%20API%20Fundamentals.md)<br>2. [Postman Guide](02-technical-stack/01-api-testing/02.%20Postman%20Guide.md)<br>3. [API & Postman (Hands-on)](02-technical-stack/01-api-testing/03.%20API%20&%20Postman.md)<br>4. [SQL Basics for QA](02-technical-stack/02-database-sql/01.%20SQL%20Basics%20for%20QA.md) | ฝึกยิง API ด้วย Postman, เขียน SQL query เพื่อดึงข้อมูลมาเช็คให้ได้ |
| **8. Automation** 🤖 | 1. [Automation Concept (Manual vs Automation)](02-technical-stack/03-automation/01.%20Automation%20Concept%20(Manual%20vs%20Automation).md)<br>2. [Automation Frameworks & Tools](02-technical-stack/03-automation/02.%20Automation%20Frameworks%20&%20Tools.md)<br>3. [Playwright Basics](02-technical-stack/03-automation/04.%20Playwright%20Basics.md)<br>4. [Best Practices & Page Object Model (POM)](02-technical-stack/03-automation/05.%20Best%20Practices%20&%20Page%20Object%20Model%20(POM).md) | ทำความเข้าใจว่าเมื่อไหร่ควร automate, เรียนรู้แนวคิด POM, ลองเขียน automation script ดู |
| **9. Real-World Practice** 💼 | - อ่าน bug report จริงๆ แล้วลองวิเคราะห์ดู<br>- หา case study หรือโปรเจกต์มาลองเขียน test case จริงๆ<br>- ลองทำ automation กับโปรเจกต์ง่ายๆ (Todo App, E-commerce) | ประยุกต์ใช้ทุกอย่างที่เรียนมา ทำจริง ลองจริง |

---

## 📂 โครงสร้างเนื้อหารายละเอียด

### 🚀 1. Real-World Operations (งานจริง)
- **01. Requirement Analysis** - อ่าน Requirement, AC, Impact Analysis
- **02. Test Design & Data** - ออกแบบ Test Case, Test Data, RTM, Review
- **03. Defect Management** - Bug Report, Severity/Priority, Life Cycle, RCA
- **04. Test Reporting** - Test Execution Result, Defect Report, Go/No-Go

### 🛠️ 2. Technical Stack (Hard Skills)
- **01. API Testing** - API Fundamentals, Postman, Test Design, Defect Reporting
- **02. Database (SQL)** - SQL Basics, Intermediate Joins, Data Verification, Cheatsheet
- **03. Automation** - Concept, Frameworks, Locators, Playwright, POM

### 📚 3. Knowledge Base (ทฤษฎี)
#### QA Fundamentals
- **Core Principles** - QA Big Picture, SDLC & STLC, Quality & Risk, Coverage
- **Test Thinking & Mindset** - Test Case Design Intro, Positive & Negative Testing

#### Design Techniques
- **Black-box** - EP, BVA, Decision Table, State Transition
- **White-box** - Statement & Decision Coverage
- **Experience-based** - Error Guessing, Exploratory, EBT

#### Testing Strategy
- **Test Levels** - Unit, Integration, System, UAT
- **Test Types** - Functional, Non-Functional, Change-Related
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


