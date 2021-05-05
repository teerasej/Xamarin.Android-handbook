
# สร้าง strings.xml สำหรับภาษาไทย

1. สร้างโฟลเดอร์ **values-th** ขึ้นมาในโฟลเดอร์ **Resources**
2. สร้างไฟล์ **strings.xml** ไว้ด้านในโฟลเดอร์ **values-th**
3. หลังจากสร้างไฟล์แล้ว ให้ทดสอบเปลี่ยนภาษาจาก Setting ในเครื่องดู

```xml
<!-- Resources/values-th/strings.xml -->

<resources>
    <string name="app_name">หลายภาษา</string>
    <string name="action_settings">การตั้งค่า</string>

    <string name="text_hello">สวัสดีจ้า</string>
    <string name="button_text_change_langauge">เปลี่ยนภาษา</string>
</resources>

```