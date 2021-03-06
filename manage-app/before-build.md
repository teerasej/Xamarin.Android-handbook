
# การเช็คค่าต่างๆ ก่อนการ distribute ตัวแอพ

### 1. กำหนดไฟล์รูปไอคอน

1. เปิด **Project Properties **
2. จากเมนูด้านซ้ายเลือก **Android Manifest** > **Application Icon **

![01-application-icon-sml](https://user-images.githubusercontent.com/85179/114737002-cd3a9a80-9d70-11eb-86ab-0c44a7931304.png)

### 2. กำหนดเลขเวอร์ชั่น

1. เปิด **Project Properties **
2. จากเมนูด้านซ้ายเลือก **Android Manifest** 

- **Version number** (เรียกอีกชื่อคือ Version Code): เป็นเลขเวอร์ชั่นที่ระบบจะอ้างอิงว่าใหม่ หรือเก่ากว่าที่ติดตั้งในเครื่องก่อนหน้า
- **Version name** เป็นเลขเวอร์ชั่นที่จะแสดงให้ผู้ใช้เห็นในเครื่อง หรือบน Play Store 

![02-versioning-sml](https://user-images.githubusercontent.com/85179/114738229-fc054080-9d71-11eb-8a6c-73b1d2dbdaf3.png)

### การลดขนาดไฟล์ติดตั้งด้วย linker

ในบางกรณี เราสามารถกำหนดให้ไฟล์แอพ ใช้โหมด share runtime ได้ ทำให้ตัวแอพจะถูกเพิ่มเฉพาะไฟล์ที่ถูกใช้ตอนรันแอพใช้งานจริง (runtime) ซึ่งจะทำให้ลดขนาดไฟล์ APK ได้มาก

1. เปิด **Project Properties **
2. จากเมนูด้านซ้ายเลือก **Android Options** 
3. ปรับค่า Linker properties

> การเปิดใช้งาน Linker อาจทำให้เกิดผลข้างเคียง แนะนำให้ทดสอบแอพใน release mode ให้ถี่ถ้วนก่อนนำไปใช้งานจริง

![03-linking-sml](https://user-images.githubusercontent.com/85179/114739163-d6c50200-9d72-11eb-8db2-55ecbacfeddc.png)