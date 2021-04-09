
# การกำหนด Icon ให้กับแอพใหม่

โดยปกติแล้ว จะมีไฟล์รูปภาพที่ใช้เป็น Icon ให้แอพเราอยู่ในโฟลเดอร์ต่อไปนี้ 

- Resources/mipmap-hdpi/ic_launcher.png
- Resources/mipmap-mdpi/ic_launcher.png
- Resources/mipmap-xhdpi/ic_launcher.png
- Resources/mipmap-xxhdpi/ic_launcher.png
- Resources/mipmap-xxxhdpi/ic_launcher.png

ซึ่งไฟล์รูปภาพในโฟลเดอร์เหล่านี้ จะถูกโหลดขึ้นมาใช้งานตามความเหมาะสมของความละเอียดหน้าจอ

## ลบไฟล์เก่า

คลิกขวาที่ไฟล์ไอคอนแต่ละอัน และเลือกคำสั่ง Remove


## เพิ่มไฟล์ไอคอนใหม่

เราสามารถ [ดาวน์โหลด Xamarin App Icon set](https://github.com/xamarin/monodroid-samples/blob/master/Phoneword/Resources/XamarinAndroidIcons.zip?raw=true) มาใช้เป็นต้นแบบในการสร้างไฟล์รูปภาพไอคอนขนาดต่างๆ ได้ 

### การเพิ่มไฟล์

1. คลิกขวาที่โฟลเดอร์ที่ต้องการเพิ่มไฟล์ 
2. เลือกคำสั่ง **Add** > **Add Files...**
3. เลือกไฟล์ขนาดที่เหมาะสมกับโฟลเดอร์
4. เลือก **Copy the file to the directory**

### การกำหนดชื่อไฟล์ไอคอนให้ให้แอพ

ถ้ามีการเปลี่ยนชื่อไฟล์รูปภาพจาก `ic_launcher` เป็นชื่ออื่น สามารถกำหนดใหม่ได้

1. คลิกขวาที่โปรเจค ใน Solution Pad
2. เลือกแสดง Options
3. จากเมนูเลือก Android Application > Application icon แล้วกำหนดชื่อใหม่

<img width="610" alt="2021-04-09_21-07-17" src="https://user-images.githubusercontent.com/85179/114193445-bb27b900-9978-11eb-8c07-f640ed513db6.png">
