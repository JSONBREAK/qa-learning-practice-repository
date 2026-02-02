
# Playwright (พื้นฐานสำหรับ QA)

## Playwright คืออะไร
- เครื่องมือทำ **Web Automation** ที่เลียนแบบการคลิก/พิมพ์ของคน
- ใช้รันทดสอบตาม Test Case แบบอัตโนมัติ

## Flow การทำงานแบบย่อ
1) เปิดหน้าเว็บ (navigate)
2) หา element (locator)
3) ทำ action (click/type)
4) ตรวจผล (assert)

## คอนเซ็ปต์ที่ควรรู้
- **Locator**: วิธีหา element
- **Wait**: รอให้หน้าพร้อมก่อนตรวจ
- **Assertion**: ตรวจว่าผลลัพธ์ตรงที่คาด

## Best Practice (สั้นๆ)
- ใช้ locator ที่เสถียร (data-testid)
- แยก Test Data ออกจาก Test Steps
- เขียนเคสตาม requirement ที่ชัดเจน
