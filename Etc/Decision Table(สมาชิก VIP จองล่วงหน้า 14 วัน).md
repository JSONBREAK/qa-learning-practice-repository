📌 **Requirement**: TC-003: สมาชิก VIP จองล่วงหน้า 14 วัน (Decision Table)

---

-  เฉพาะ **VIP** เท่านั้น
- VIP จองได้ **ไม่เกิน 14 วัน**
- VIP ที่เกิน 14 วัน → ต้อง “ปฏิเสธ + แจ้งเตือน”
- สมาชิกทั่วไป → “ปฏิเสธ + แจ้งเตือน”
- ระบบตรวจ 2 อย่าง
	- VIP?
	- ≤ 14 วัน?

> VIP AND ≤14 วัน → อนุญาต
   อื่น ๆ → ปฏิเสธ + แจ้งเตือน

---

### Conditions

| ID  | Condition                    |
| --- | ---------------------------- |
| C1  | ผู้ใช้เป็น VIP หรือไม่       |
| C2  | จำนวนวันจองล่วงหน้า ≤ 14 วัน |
| C3  | จำนวนวันจองล่วงหน้า > 14 วัน |

💡 **C2 กับ C3 เป็น mutually exclusive** 
⭐=  **VIP? and ≤ 14 วัน?**

---

### Actions

> “ระบบต้องทำอะไรได้บ้าง?”

| ID  | Action                                                                      |
| --- | --------------------------------------------------------------------------- |
| A1  | อนุญาตให้จอง                                                                |
| A2  | ปฏิเสธการจอง                                                                |
| A3  | แสดงข้อความแจ้งเตือน “จองล่วงหน้าได้สูงสุด 14 วันสำหรับสมาชิก VIP เท่านั้น” |
💡 **A1 กับ A2 เป็น mutually exclusive** 

---

### 📊 Decision Table

ก็จะเหลือ 
- VIP or not?
- ≤14 day or not?

|Rule|R1|R2|R3|
|---|---|---|---|
|VIP|T|T|F|
|≤14|T|F|–|
|อนุญาตให้จอง|x|||
|ปฏิเสธการจอง||x|x|
|แสดงข้อความแจ้งเตือน||x|x|
> Note:
> - "Condition “≤14” covers boundary cases (0–14 days)"
> - "Rule R3 applies regardless of booking days for non-VIP users"


---

## Scenario to Test Case
- TC-003-01: VIP + 14 วัน → Success
- TC-003-02: VIP + 15 วัน → Reject + Warning
- TC-003-03: Non-VIP + any days → Reject + Warning

---

# 🧪 Test Case (Detailed)

**Feature:** VIP Advance Booking (TC-003)

🔹 TC-003-01

```
Test Case ID
TC-003-01

Test Description
ตรวจสอบว่า **สมาชิก VIP สามารถจองล่วงหน้าได้ไม่เกิน 14 วัน**

Pre-condition
- ผู้ใช้มีสถานะเป็น **VIP** 
- ผู้ใช้ login สำเร็จ 
- ระบบเปิดให้ใช้งานฟีเจอร์จองล่วงหน้า
- วันที่ปัจจุบันตั้งค่าถูกต้องในระบบ
    
Test Data

User Type: VIP
- จำนวนวันจองล่วงหน้า: **14 วัน**
    

Test Steps
1. Login ด้วยบัญชีผู้ใช้ที่เป็น VIP 
2. ไปที่หน้าจอ Booking
3. เลือกวันที่จองล่วงหน้าเป็น **14 วันจากวันปัจจุบัน**
4. กดปุ่ม “ยืนยันการจอง”
    
Expected Result
- ระบบอนุญาตให้จองสำเร็จ
- แสดงข้อความยืนยันการจอง
- ไม่มีข้อความแจ้งเตือนเรื่องจำนวนวันจอง
```

---

🔹 TC-003-02

```
Test Case ID
TC-003-02

Test Description
ตรวจสอบว่า สมาชิก VIP ไม่สามารถจองล่วงหน้าเกิน 14 วันได้

Pre-condition
- ผู้ใช้มีสถานะเป็น VIP
- ผู้ใช้ login สำเร็จ
- ระบบเปิดให้ใช้งานฟีเจอร์จองล่วงหน้า
    
Test Data
- User Type: VIP
- จำนวนวันจองล่วงหน้า: 15 วัน
    
Test Steps
1. Login ด้วยบัญชีผู้ใช้ที่เป็น VIP
2. ไปที่หน้าจอ Booking
3. เลือกวันที่จองล่วงหน้าเป็น 15 วันจากวันปัจจุบัน
4. กดปุ่ม “ยืนยันการจอง”
    
Expected Result
ระบบ ไม่อนุญาตให้จอง
การจองไม่ถูกบันทึก
แสดงข้อความแจ้งเตือน
    
“จองล่วงหน้าได้สูงสุด 14 วันสำหรับสมาชิก VIP เท่านั้น”
```

---

🔹 TC-003-03

```
Test Case ID
TC-003-03

Test Description
ตรวจสอบว่า สมาชิกทั่วไปไม่สามารถจองล่วงหน้าได้ ไม่ว่ากี่วัน

Pre-condition
- ผู้ใช้มีสถานะเป็น สมาชิกทั่วไป (Non-VIP)
- ผู้ใช้ login สำเร็จ
- ระบบเปิดให้ใช้งานฟีเจอร์จองล่วงหน้า
    
Test Data
- User Type: Non-VIP
- จำนวนวันจองล่วงหน้า: 7 วัน (หรือค่าใดก็ได้)
    
Test Steps
1. Login ด้วยบัญชีผู้ใช้ที่เป็นสมาชิกทั่วไป
2. ไปที่หน้าจอ Booking
3. เลือกวันที่จองล่วงหน้า (เช่น 7 วันจากวันปัจจุบัน)
4. กดปุ่ม “ยืนยันการจอง”
    
Expected Result
- ระบบ ไม่อนุญาตให้จอง
- การจองไม่ถูกบันทึก
- แสดงข้อความแจ้งเตือน
    
    “จองล่วงหน้าได้สูงสุด 14 วันสำหรับสมาชิก VIP เท่านั้น”
```

---

📄 **Test Case Specification**

```
Document Name: Test Case - VIP Advance Booking
Feature: TC-003 VIP Advance Booking
Version: 1.0
Prepared by: QA
Date: YYYY-MM-DD
Environment: SIT
```

|Test Case ID|Description|Pre-condition|Test Data|Steps|Expected Result|Actual Result|Status|
|---|---|---|---|---|---|---|---|
|TC-003-01|VIP booking ≤14 days|User is VIP|14 days|See detail|Booking success|||
|TC-003-02|VIP booking >14 days|User is VIP|15 days|See detail|Reject + warning|||
|TC-003-03|Non-VIP booking|User non-VIP|Any|See detail|Reject + warning|||

---

📄 **Test Execution Log**

```
Feature: TC-003
Tester: <Name>
Environment: SIT
Execution Date: YYYY-MM-DD
```

|TC ID|Result|Evidence|Comment|
|---|---|---|---|
|TC-003-01|PASS|screenshot_003_01.png|–|
|TC-003-02|FAIL|screenshot_003_02.png|Booking created unexpectedly|
|TC-003-03|PASS|screenshot_003_03.png|–|

---

📄 **Bug Report Template**

```
Bug ID: BUG-003
Title: VIP user can book more than 14 days in advance
Module: Booking
Environment: SIT
Severity: High
Priority: High
Status: Open
```

```
Description
VIP user is able to create booking beyond 14 days which violates TC-003 requirement.

Steps to Reproduce
1. Login as VIP user
2. Go to Booking page
3. Select booking date = Today + 15 days
4. Click Confirm
    
Actual Result
- Booking is created successfully
    
Expected Result
- Booking should be rejected
- Warning message displayed:  
    “จองล่วงหน้าได้สูงสุด 14 วันสำหรับสมาชิก VIP เท่านั้น”
    
Reference
- Test Case: TC-003-02
- Decision Rule: R2
    
Evidence
- screenshot_003_02.png
```

---

📄 **Test Summary Report**

```
Feature: VIP Advance Booking (TC-003)
Environment: SIT
Test Period: YYYY-MM-DD – YYYY-MM-DD
```

```
**Test Coverage**
- Total Test Cases: 3
- Executed: 3
- Passed: 2
- Failed: 1
    
**Defect Summary**
- Open Bugs: 1 (High)
- Closed Bugs: 0
    
**Risk & Notes**
- Booking rule for VIP users still violated
- Release is NOT recommended until BUG-003 is fixed
    
**QA Recommendation**  
❌ Hold release
```

---

📄 RTM – Booking Rule : **“Requirement นี้ ถูก test ครบหรือยัง?”**

|**Req ID**|**Business Requirement**|**Test Scenario**|**Test Case ID**|**Test Result**|**Defect ID**|
|---|---|---|---|---|---|
|**REQ-003**|เฉพาะ VIP จองล่วงหน้าได้ไม่เกิน 14 วัน|VIP จองภายในเงื่อนไข|TC-BK-001|**PASS**|-|
|**REQ-003**|VIP จองเกิน 14 วันต้องแจ้งเตือน|VIP จองเกิน 14 วัน|TC-BK-002|**FAILED**|BUG-003|
|**REQ-003**|สมาชิกทั่วไปจองไม่ได้ทุกกรณี|Non-VIP จองล่วงหน้า|TC-BK-003|**PASS**|-|

---

📄 Automation Candidate List

|Test Case ID|Scenario|Automation Feasibility|Reason|
|---|---|---|---|
|TC-BK-001|VIP ≤14 days|✅ High|Stable, no UI complex|
|TC-BK-002|VIP >14 days|✅ High|Clear assertion|
|TC-BK-003|Non-VIP ≤14|⚠️ Medium|Depends on user setup|
|TC-BK-004|Non-VIP >14|⚠️ Medium|Needs data control|
|TC-BK-005|Notification message|❌ Low|External service|

---

📄 UAT Test Scenario – Booking

**UAT-01: VIP Advance Booking (Within Limit)**

```
Scenario
VIP user books within 14 days

Pre-condition
- User is VIP
- User logged in

Steps
1. User selects booking date within 14 days
2. User confirms booking

Expected Result
- Booking is successful
- Confirmation message displayed
```

---

**UAT-02: VIP Advance Booking (Exceed Limit)**

```
Scenario
VIP user books beyond allowed days

Pre-condition
- User is VIP
- User logged in

Steps
1. User selects booking date more than 14 days
2. User confirms booking

Expected Result
- Booking is rejected
- Warning message is displayed
```

---

**UAT-03: Non-VIP Attempt Booking**

```
Scenario
Non-VIP user attempts advance booking

Expected Result
- Booking is rejected
- Warning message is displayed
```

---

💡 **UAT = Confirm “สิ่งที่ควรเกิด” ไม่ใช่ “สิ่งที่ไม่ควรเกิดทุกกรณี”**
