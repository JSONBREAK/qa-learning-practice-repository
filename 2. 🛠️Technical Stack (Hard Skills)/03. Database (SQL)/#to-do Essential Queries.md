# Essential SQL Queries (สำหรับ QA)

## คำสั่งหลักที่ต้องใช้ได้
- **SELECT**: ดึงข้อมูล
- **WHERE**: กรองข้อมูล
- **COUNT**: นับจำนวน
- **JOIN**: เชื่อมหลายตาราง
- **ORDER BY**: เรียงข้อมูล
- **GROUP BY**: สรุปข้อมูลเป็นกลุ่ม

## ตัวอย่างสั้นๆ
```sql
-- ดู user ที่สมัครวันนี้
SELECT * FROM users WHERE created_at >= CURRENT_DATE;

-- นับจำนวน order ที่รอจ่าย
SELECT COUNT(*) FROM orders WHERE status = 'pending';

-- ดูรายการ order พร้อมชื่อ user
SELECT o.id, u.name
FROM orders o
JOIN users u ON u.id = o.user_id;
```

## ข้อควรระวัง
- ระวังลืม WHERE (ดึงข้อมูลทั้งตาราง)
- ตรวจค่า NULL ให้ถูก
