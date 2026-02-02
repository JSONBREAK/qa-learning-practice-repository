# Postman Guide (แบบย่อ)

## เริ่มต้นเร็วที่สุด
1) เลือก **Method** (GET/POST/PUT/PATCH/DELETE)
2) ใส่ **URL**
3) ใส่ **Headers** ถ้าจำเป็น (เช่น Authorization)
4) ใส่ **Body** (ถ้ามี)
5) กด **Send**

## สิ่งที่ต้องดูหลังส่ง
- **Status Code**
- **Response Body (JSON)**
- **Response Time**

## การจัดระเบียบงาน
- สร้าง **Collection** แยกตาม Feature
- ใช้ **Environment Variables** เช่น `{{base_url}}`, `{{token}}`

## Test เบื้องต้นใน Postman
- เช็ค Status Code
- เช็ค Key สำคัญใน JSON

ตัวอย่าง (แนวคิด):
- Expect 200
- Expect `data.id` ไม่ว่าง
