# STEP 1 : Requirement Analysis (ระบบทำอะไร)

ก่อนเขียน Test Case หรือ Automation
ต้องแตก Requirement ออกมาก่อนว่า **ระบบทำอะไรบ้าง**

❓ ผู้ใช้เข้ามาเพื่อ “ทำอะไร” 
เช่น 
- สมัครสมาชิก
- Login
- ชำระเงิน,
- กรอกฟอร์ม 
- อัปโหลดไฟล์

> 1 ระบบ = 1 เป้าหมายหลัก (Feature)

---

# STEP 2 : แตกเป็น Feature (ไม่ใช่ Test Case!)

สมมติระบบ “สมัครสมาชิก”

⚠️ ให้แตกเป็น **Feature / Function** ก่อน

เช่น: 
- กรอก Email
- กรอกรหัสผ่าน
- ยืนยันรหัสผ่าน
- กด Submit

📌 ตรงนี้คือ **Business Function**  $!=$  test

---

# STEP 3 : แตก Feature → Scenario

### กฎเหล็ก:

> **ทุก Feature ต้องมี**

- Positive
- Negative
- Edge (ถ้ามี)

#### 📝ตัวอย่าง
#### Feature: Email Input
**Positive**
- Email ถูก format
**Negative**
- Email ผิด format
- Email ว่าง
**Edge**
- Email ยาวมาก
- Email ตัวอักษรพิเศษ

📌 ยังไม่เขียน steps  
📌 ยังไม่เขียน expected แบบละเอียด

---

# STEP 4 : Scenario → Test Case

### Test Case คืออะไร?

> Scenario + Steps + Expected Result

|Test Case ID|Scenario|Steps|Expected Result|
|---|---|---|---|
|TC-01|Valid email|Enter valid email|Email accepted|
|TC-02|Invalid email|Enter invalid email|Error shown|

---

# STEP 5 : จัด Test Level (จุดที่ Automation เข้ามา)

เนื่องจากเรามีจำนวน Test Case เยอะมาก 

> ❓ อันไหนควร automate

```
Unit (Dev)
↑
Functional (Automation)
↑
End-to-End (Automation)
```

**สำหรับ Automation Tester**
- สำหรับ Automation Tester
- **Functional** → automate เยอะ

---
# STEP 6 : Mapping Test Case → Automation

💡 ไม่ Automate ทุก test case

วิธีเลือกคือ

**Functional Automation**
- 1 Feature = 1 test file
- Test สั้น ชัด

**E2E Automation**
- 1-2 Case
- เพื่อนพิสูจน์ว่า flow ยังใช้งานได้

---

# STEP 7 : โครงสร้าง Automation (Generic)

ต้องวางแผนในหัวให้ชัด เช่น

```
tests/
functional/
	feature-a.spec
	feature-b.spec
e2e/
	main-flow.spec
```

---

## 🟢 สรุปแบบสั้น

>Requirement → Feature → Scenario → Test Case → Automation
>
  Automation =  เอา Test Case ไปเขียนโค้ด

---

### ⚠️บางอย่างไม่คุ้ม automate

ตัวอย่าง:
- Text error message เปลี่ยนบ่อย
- UI layout / wording
- One-time test

👉 Manual เร็วกว่า

### 🟢 แล้วอะไร “ควร automate”

> High value × High repeat × High risk = Automate

----

## ✅ กลุ่มที่ควร automate (สำคัญมาก)

### 1️⃣ Business Critical Flow

สิ่งที่พังไม่ได้เด็ดขาด

- Register
- Login
- Payment
- Create order
    
👉 ต้อง automate

---

### 2️⃣ Happy Path

Flow ปกติที่ user ใช้จริง

> เพราะถ้าอันนี้พัง = ระบบตาย

---

### 3️⃣ Regression

เคสเดิมที่ต้อง test ซ้ำทุก release

- เคยพังมาแล้ว
- มี history

👉 automate เพื่อกันพลาด

---

## ⚠️ กลุ่มที่ “ไม่ควร” automate (หรือ automate น้อย)

### ❌ Validation จุกจิก

- Field required ทุกช่อง
- Message wording

👉 Manual พอ

|ประเภท|จำนวน|
|---|---|
|Happy Path|1|
|Core validation|3–5|
|Negative สำคัญ|2–3|
|Edge|Manual|

👉 รวม automate แค่ ~30–40%

**แต่ cover 80% risk**

---

## 🧱 Mapping ชัด ๆ

### Feature: Phone + OTP + Promo

#### Automate ✅

- Valid phone → request OTP
- Valid OTP → submit success
- Invalid OTP → error
- Promo valid → applied
    

#### Manual ❌

- OTP expired
- Promo reused
- UI message detail

---

## 🧠 ประโยคทอง 

> “We don’t automate everything.  
> We automate **high-risk** and **high-value scenarios** to ensure stability and fast regression feedback.”