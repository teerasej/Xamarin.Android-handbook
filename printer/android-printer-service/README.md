
# Print ผ่าน Android Printer Service

> Google ยกเลิก Google Cloud Print จากวันที่ 1 มกราคม 2021 เป็นต้นมา และให้มาใช้ Printer Service ใน Android 8.0 เป็นต้นมาแทน [ดูรายละเอียดที่นี่](https://9to5google.com/2017/08/22/android-8-0-oreos-default-print-service/ )


1. [สร้างโปรเจค, ติดตั้ง Package, และเปิด permission](1-create-project.md)
2. [สร้าง Layout](2-create-layout.md)
3. [เรียกใช้ View ใน MainActivity](3-access-view-in-activity.md)
4. [สร้าง Download Service สำหรับดาวน์โหลดไฟล์](4-create-download-service.md)
5. [ดาวน์โหลดไฟล์มาไว้ในเครื่อง และเปิดการทำงานของปุ่มที่เหลือ](5-download-and-enable-button.md)
6. [สร้าง Activity สำหรับแสดงไฟล์ PDF](6-create-pdf-viewer.md)
7. [ส่งที่อยู่ไฟล์ pdf ไปเปิดแสดงในอีก activity](7-send-pdf-filepath-to-viewer.md)

การใช้ Printer Service จะมี 2 แบบ

สามารถติดตั้ง print service ในเครื่องได้ โดยไปที่ Settings > Printing > ... > เลือก service

- [ใช้ระบบ Share Activity](8-use-share.md)
- [ใช้ Print Manager](9-access-native-printer.md)