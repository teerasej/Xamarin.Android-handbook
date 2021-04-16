
# การสร้างไฟล์ AAB สำหรับการอัพขึ้น Google Play Store

- การเอาขึ้น Play Store ได้ ต้องสมัคร Developer Account ด้วย Google Account มีค่าใช้จ่าย 25 ดอลลาร์ [สมัครตามขั้นตอนและชำระเงินที่นี่](https://play.google.com/console/)
- ใน Play Store ปัจจุบัน การอัพโหลดแอพจำเป็นต้องรองรับทั้งระบบ 32-bits และ 64-bits 
- ระบบไฟล์ประเภท AAB (Android App Bundle) จะทำให้การอัพโหลดไฟล์แอพขึ้น Store ทำได้โดยง่าย

## ไฟล์รูปที่ต้องเตรียมให้ Play Store

เหมือนขายของออนไลน์ เราจำเป็นต้องเตรียมรูปภาพที่เกี่ยวข้องกับแอพของเรา[ทั้งหมดตามนี้](image-for-play-store.md)


## ขั้นตอนการอัพแอพขึ้น Play Store 

1. สร้าง Application Project บน Google Play Console
2. Distribute แอพแบบ Google Play
3. เชื่อม Application Project เข้ากับ Visual Studio 
4. Distribute แอพ
