
# สร้างตัวแสดงข้อมูลใน List (List item)

เราจะสร้าง Layout ไฟล์ขึ้นมาอันหนึ่ง โดยกำหนดชื่อ `list_item.xml`

- ด้านในจะใช้ TextView
- กำหนดค่า
  - `android:padding="10dp"` สำหรับ padding พื้นที่ว่างระหว่างตัว View กับข้อความ
  - `android:textSize="16sp"` สำหรับขนาดข้อความ (**sp** คือหน่วย scaled pixel เพื่อรองรับความละเอียดหน้าจอที่หลากหลาย)

```xml
<!-- Resources/layout/list_item.xml -->
<?xml version="1.0" encoding="utf-8"?>
<TextView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    android:padding="10dp"
    android:textSize="16sp">
</TextView>
```