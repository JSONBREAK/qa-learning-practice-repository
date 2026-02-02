# API Fundamentals (สำหรับ QA)

## API คืออะไร
- API คือช่องทางให้ระบบ 2 ระบบคุยกันผ่าน HTTP
- เราเทสเพื่อยืนยันว่า **Request ถูก** และ **Response ถูก**

## HTTP Methods ที่ต้องรู้
- **GET**: ดึงข้อมูล
- **POST**: สร้างข้อมูล
- **PUT**: แก้ไขทั้งก้อน
- **PATCH**: แก้ไขบางส่วน
- **DELETE**: ลบข้อมูล

## Status Code ที่เจอบ่อย
- **200 OK**
- **201 Created**
- **400 Bad Request**
- **401 Unauthorized**
- **403 Forbidden**
- **404 Not Found**
- **500 Internal Server Error**

## Request/Response พื้นฐาน
- **Request**: URL, Method, Headers, Body
- **Response**: Status Code, Body, Time

## JSON เบื้องต้น
- Object `{}` / Array `[]`
- Data types: string, number, boolean, null

## Checklist เทส API (แบบสั้น)
- [ ] Status Code ตรงที่คาด
- [ ] Response Schema ถูก
- [ ] Error Message ถูกในเคสผิด
- [ ] Response Time ไม่ช้าเกิน
- [ ] Data ถูกต้องตามเงื่อนไข
