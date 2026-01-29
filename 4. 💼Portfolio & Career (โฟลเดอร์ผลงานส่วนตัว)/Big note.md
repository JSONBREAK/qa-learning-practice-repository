
## สูตรเด็ด Playwright (Assertion & Actions)
จดคีย์เวิร์ดที่ต้องใช้ปิดท้าย Test Case เพื่อให้ได้คะแนนเต็ม:

- **ตรวจสอบ URL:** `await expect(page).toHaveURL(/.*success/);`
- **ตรวจสอบการแสดงผล:** `await expect(locator).toBeVisible();`
- **ตรวจสอบข้อความ:** `await expect(locator).toContainText('บันทึกสำเร็จ');`
- **การพิมพ์/คลิก:** `await page.fill('#id', 'value');` และ `await page.click('.btn-class');`
	


## SQL Cheat Sheet (Data Verification)
จดโครงสร้างที่ต้องใช้คิวรีข้อมูลขึ้นมาเช็คหลังทำ Automate เสร็จ:

- **เช็คข้อมูลล่าสุด:** `SELECT * FROM table ORDER BY created_at DESC LIMIT 1;`
- **ช็คเงื่อนไข:** `SELECT count(*) FROM employees WHERE email = 'test@mail.com';` (ถ้าผลเป็น 1 คือผ่าน)
- **การเชื่อมตาราง (JOIN):** ```sql SELECT a.name, b.department FROM employees a JOIN departments b ON a.dept_id = b.id;


## SQL Cheat Sheet (Data Verification)

- **ช็ค Status 200:** `pm.test("Status 200", () => { pm.response.to.have.status(200); });`
- **เช็คค่าใน JSON:** `pm.expect(pm.response.json().message).to.eql("Success");`
