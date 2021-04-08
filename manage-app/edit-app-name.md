
# การแก้ไขชื่อแอพ

1. เปิดไฟล์ `Resources/values/strings.xml`
2. แก้ไขข้อความที่อยู่ในส่วน `<string name="app_name">`

```xml
<string name="app_name">ชื่อแอพ</string>
```

3. บันทึกไฟล์ และรันทดสอบแอพใหม่

## Note

- สังเกตว่าส่วนหัวของ MainActivity จะเป็นส่วนที่ใช้กำหนดชื่อแอพ นั่นคือส่วนที่ชื่อ `Activity(Label)` ที่ดึงค่ามาจากไฟล์ `strings.xml`

```cs
[Activity(Label = "@string/app_name", ... )]
```