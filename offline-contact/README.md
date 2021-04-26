
# Offline Contact 

## App & Loading

1. [สร้างโปรเจค และติดตั้ง Package เพิ่มเติม](1-create-project-add-nuget.md)
2. [สร้าง ListView สำหรับแสดงรายชื่อ User](2-create-listview.md)
3. [สร้างส่วนหน้าจอ loading](3-create-loading.md)
4. [ซ่อน ListView และแสดง Loading ตอนเปิดหน้า Main](4-hide-and-show.md)

## Calling Web API

5. [สร้าง Class สำหรับข้อมูล User](5-create-model-for-remote-data.md)
6. [สร้าง UserService เพื่อแยกส่วนติดต่อกับ Web API](6-create-user-service.md)
7. [สร้าง method ที่เรียกใช้ service](7-calling-service.md) 

## ListView & Custom List Item

8. [สร้าง Layout เป็นตัวแทนของข้อมูลผู้ใช้ใน ListView](8-create-list-item.md)
9. [สร้าง User Profile Adapter สำหรับ ListView](9-create-listview-adapter.md)
10. [นำข้อมูล Array ที่ได้มาใช้กับ ListView](10-apply-data-to-listview.md)
11. [โหลดรูปภาพจาก url มาแสดงใน image view](11-load-image-to-show-in-list-item.md)

## Local file

12. [สร้างส่วนการเตรียมข้อมูลรูปภาพ เก็บไว้ภายในแอพ](12-prepare-local-file.md)
13. [ดึงที่อยู่รูปภาพจากในแอพพลิเคชั่น แทนจาก server เพื่อใช้ใน List Item](13-switch-to-local-file-imageview.md)
14. [สลับมาใช้การโหลดใช้ข้อมูลแบบ Offline แทน](14-activity-work-with-offline-data.md)

## Connectivity

15. [ตรวจเช็คสถานะการเชื่อมต่อ](15-check-connection.md)

## SQLite Database

- การทำส่วนนี้ต้องกำหนด Permission ชื่อ **READ_EXTERNAL_STORAGE** และ **WRITE_EXTERNAL_STORAGE** ใน Android Options (AndroidManifest.xml) ด้วย

16. [สร้าง Class ตัวแทนของข้อมูล User ใน Database](16-create-user-db.md)
17. [สร้าง class สำหรับเชื่อมต่อและจัดการ database](17-create-user-db-connection.md)
18. [ทิ้งข้อมูลที่โหลดเก็บไว้ ถ้ามีการเรียกข้อมูลใหม่จาก Web API](18-reset-local-db.md)
19. [บันทึกข้อมูลผู้ใช้ไว้สำหรับทำงาน offline](19-save-data-for-offline.md) 
20.  [สร้างคำสั่งโหลดข้อมูล User](20-load-user-data.md)
21.  [ใช้ข้อมูล User ล่าสุดจาก database ถ้าไม่ต่ออินเตอร์เน็ต](21-use-data-from-db-if-offline.md)

 