
#### เทสระบบสมัครสมาชิก โดยที่ Requirement บอกว่า 
**_"ต้องกรอก Email และ Password เท่านั้น"_**

---

### 1. **ยิง API (ใช้ Postman เช็คหน้าด่าน)**

**Method:** `POST`
**URL:** `/api/v1/register`
Body (JSON):

`{` 
	`"email": "surachok@test.com",` 
	`"password": "123"` 
`}`

**ผลลัพธ์ที่เป็นไปได้** (สิ่งที่ต้องมองหา):
- **ถ้าพังที่ Logic:** ระบบตอบ `400 Bad Request` พร้อมบอกว่า `"Password must be at least 8 characters"` (คุณจะรู้ทันทีว่าพังเพราะ Validation)
- **ถ้าพังที่ Code:** ระบบตอบ `500 Internal Server Error` (คุณจะรู้ทันทีว่าหลังบ้านมีบั๊ก ต้องตาม Dev)


### 1. ตรวจ SQL (เช็คปลายทาง)

**จุดที่ QA ต้องจับผิด (SQL Verification):**
- **ข้อมูลหาย:** Query แล้วไม่เจออะไรเลย (แสดงว่า API หลอกเรา)
- **ข้อมูลเพี้ยน:** ในตาราง `users` มีอีเมลเราโผล่มาจริง แต่ `password` ดันถูกเก็บเป็นตัวหนังสือธรรมดา (Plain text) แทนที่จะเข้ารหัสไว้ (Security Bug!)