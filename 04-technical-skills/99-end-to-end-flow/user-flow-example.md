---

---

---

Flow Name: User Registration

Business Goal: ให้ผู้ใช้สมัครสมาชิกใหม่ได้ และระบบต้องป้องกัน email ซ้ำ

User Actions: 
1. เปิดหน้า Register 
2. กรอก email 
3. กรอก password 
4. กดปุ่ม Register

System Flow: 
1. UI ตรวจ required field 
2. UI ส่ง request ไป API /register 
3. API ตรวจสอบ email ซ้ำ 
4. API บันทึกข้อมูลลง database (users table) 
5. API ส่ง response success 
6. UI แสดงข้อความสมัครสำเร็จ

Possible Fail Points: 
- email format ไม่ถูกต้อง, email ซ้ำ แต่ระบบยังสมัครได้
- API error แต่ UI ยังขึ้น success
- ข้อมูลไม่ถูกบันทึกใน database

QA Validation Ideas: 
- ตรวจ UI validation
- ยิง API ตรงโดยไม่ผ่าน UI
- ตรวจ database ว่ามี record จริงหรือไม่

---


ถ้าเราได้ Flow มา User Registration
เป้าหมายคืออะไร: การสมัครสมาชิกเสร็จสิ้น
เงื่อนไขคืออะไร: ระบบต้องป้องกัน email ซ้ำ

| Scenario ID        | Scenario Description                   |
| ------------------ | -------------------------------------- |
| TS-Registration-01 | User Registration ด้วยข้อมูลถูกต้อง    |
| TS-Registration-02 | User Registration ด้วยข้อมูล email ซ้ำ |
| TS-Registration-03 | User Registration โดยไม่กรอกข้อมูล     |

