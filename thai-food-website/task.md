# Task List — Thai Food Recommendation Site (index.html)

อ้างอิง glossary จาก [CONTEXT.md](./CONTEXT.md) และ requirement ที่ confirm กับผู้ใช้แล้ว

## 1. ข้อมูล Dish
- [x] คิวเรตข้อมูล 12 Dish (ชื่อ, Category, คำอธิบายสั้นๆ, emoji icon) ครอบคลุมหลาย Category (ผัด/แกง/ต้ม/ยำ/ของหวาน ฯลฯ)
- [x] เก็บเป็น array/object ในไฟล์ JS ฝังใน index.html

## 2. โครงหน้าเว็บ (HTML skeleton)
- [x] Header: ชื่อเว็บไซต์ + คำโปรย (ภาษาไทยล้วน)
- [x] Section ปุ่มสุ่ม "สุ่มอาหารไทยวันนี้" + การ์ดแสดงผล Random Pick
- [x] Section แถบปุ่มกรอง Category + grid แสดง Dish ทั้งหมด
- [x] Section "รายการโปรดของฉัน" (ซ่อนไว้เริ่มต้น)

## 3. ฟีเจอร์ Random Pick
- [x] ปุ่มสุ่ม: สุ่ม Dish จากทั้ง 12 รายการเสมอ ไม่ล็อกวันที่ ไม่สนใจ Category filter ที่เลือกอยู่
- [x] แสดงผลลัพธ์เป็นการ์ด (ชื่อ, Category, คำอธิบาย, icon)
- [x] การ์ดผลลัพธ์มีปุ่ม Favorite (heart) ของตัวเอง เชื่อมกับ Dish เดียวกับใน grid

## 4. Grid เมนูทั้งหมด + Filter
- [x] Render grid การ์ด Dish ทั้ง 12 รายการ (ชื่อ, Category, คำอธิบาย, icon, ปุ่ม heart)
- [x] ปุ่มกรอง Category (รวมปุ่ม "ทั้งหมด") กรองเฉพาะ grid นี้ ไม่กระทบ Random Pick

## 5. ฟีเจอร์ Favorite + localStorage
- [x] Toggle heart บน Dish card ใดๆ (ทั้ง grid และผล Random Pick) อัปเดต state ร่วมกันตาม Dish id
- [x] บันทึก/อ่านค่า Favorite จาก localStorage เมื่อโหลดหน้าและทุกครั้งที่ toggle
- [x] Section "รายการโปรดของฉัน": โผล่ขึ้นมาเมื่อมี Favorite แรก แล้วแสดงค้างไว้ตลอด (ไม่ซ่อนกลับแม้ Favorite จะเหลือ 0)
- [x] Empty state message ใน section รายการโปรด ("ยังไม่มีเมนูโปรด ลองกดหัวใจดูสิ!") สำหรับกรณีเคยโผล่มาแล้วแต่ Favorite เหลือ 0

## 6. ดีไซน์ / สไตล์
- [x] โทนสีอบอุ่นสไตล์ไทย (แดง-ทอง-เขียวใบตอง)
- [x] Responsive อย่างน้อยสำหรับมือถือ (จอแคบ)
- [x] ข้อความในหน้าทั้งหมดเป็นภาษาไทยล้วน

## 7. ทดสอบ
- [ ] เปิดไฟล์ index.html ในเบราว์เซอร์จริง ทดสอบปุ่มสุ่ม _(เปิดไฟล์ให้แล้วผ่านคำสั่ง `open`, แต่ claude-in-chrome extension ไม่ได้เชื่อมต่อ เลยยังไม่ได้เห็นผลด้วยตาตัวเองแบบอัตโนมัติ — รบกวนช่วยเช็กหน้าที่เปิดขึ้นมาด้วยครับ)_
- [ ] ทดสอบปุ่มกรอง Category
- [ ] ทดสอบกดหัวใจ เพิ่ม/ลบ Favorite และ section รายการโปรดโผล่/ค้างไว้ตามที่ออกแบบ
- [ ] Reload หน้าเพื่อยืนยันว่า Favorite ยังอยู่ (localStorage ทำงานถูกต้อง)
