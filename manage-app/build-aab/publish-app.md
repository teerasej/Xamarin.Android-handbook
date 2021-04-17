

# Publish แอพ ขึ้น Play Store

จะเริ่มขั้นตอนนี้ได้นั้น ต้องผ่าน:

1. [ขั้นตอนการ Archive โปรเจค](../build-apk.md#1-การ-archive-โปรเจค)
2. [ขั้นตอนการสร้างไฟล​์ Key Store](../build-apk.md#2-การสร้างไฟล์-key-store) และโหลดเข้ามาใช้งานเรียบร้อยแล้ว
3. ขั้นตอนการ[สร้าง Google Play Account](create-credential-on-google-play-console.md) และ[เพิ่มเข้ามาใช้งานใน Visual Studio](add-google-play-account-to-visual-studio.md) เรียบร้อยแล้ว

เริ่มขั้นตอนโดยการกดปุ่ม Continue หลังจากเลือก Google Play Account แล้ว

![07-account-added-sml](https://user-images.githubusercontent.com/85179/115102558-cdf04e00-9f75-11eb-9610-afeb9040e63f.png)

จะมีให้เลือก Google Play Track ซึ่งจะเหมาะสำหรับการควบคุมการทดสอบแอพพลิเคชั่น ก่อนปล่อยเป็นเวอร์ชั่นที่คนทั่วไปโหลดใช้ได้จริง เช่น

- **Internal** ใช้ในการเอาไปทดสอบภายในทีม หรือส่งให้ QA 
- **Alpha** ใช้อัพโหลดแอพ สำหรับทดสอบกับคนกลุ่มเล็ก
- **Beta** ใช้อัพโหลดแอพ สำหรับทดสอบกับคนกลุ่มที่ใหญ่ขึ้น
- **Production** เปิดให้คนโหลดทั่วไปบน Play Store
- **Custom** ส่งให้กลุ่มคนที่มีรายชื่อ email ทดสอบ

> แอพที่ส่งขึ้นในขั้นตอนนี้อยู่ในรูปแบบ Draft ให้เปิดเข้าไปดำเนินการต่อใน Google Play Console ให้เสร็จสมบูรณ์

**คำเตือน** อย่าทำ Key Store หาย เพราะแอพที่ผ่านเข้า Store แล้วต้องใช้ Key Store อันเดิมในการส่งเวอร์ชั่นอัพเดตทุกครั้ง 

![08-google-play-track-sml](https://user-images.githubusercontent.com/85179/115102556-cd57b780-9f75-11eb-8592-4a015b0a622e.png)

หลังจากกดปุ่ม Upload จะมีให้ใส่รหัสของ Key Store 

![09-certificate-password-sml](https://user-images.githubusercontent.com/85179/115102553-ccbf2100-9f75-11eb-9868-9e3046665896.png)

จะขึ้นส่วนแสดงสถานะการอัพโหลด

![10-uploading-apk-sml](https://user-images.githubusercontent.com/85179/115102551-ca5cc700-9f75-11eb-9b79-ff5684d138a1.png)

เสร็จแล้วจะมีข้อความด้านล่างโปรแกรม Visual Studio แสดงขึ้นมา ถือว่าเสร็จสมบูรณ์

![11-published-sml](https://user-images.githubusercontent.com/85179/115102716-d4cb9080-9f76-11eb-8707-ebd2879697dc.png)
