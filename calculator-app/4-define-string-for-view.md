
# กำหนดข้อความด้วยไฟล์ strings.xml

## 1. กำหนดข้อความที่จะใช้ในแอพ

- การเขียนกำหนดข้อความลงไปในไฟล์ layout โดยตรง จะทำให้การแก้ไขมีความลำบากเมื่อแอพมีขนาดใหญ่ขึ้น
- การกำหนดส่วนนี้จะทำให้ใช้เป็นพื้นฐานแอพหลายภาษา (Multi-language) ได้ในอนาคต

เราสามารถกำหนดข้อความไว้ในไฟล์ `Resources/values/strings.xml` โดยใช้ tag `<string name="">Text</string>` ได้

```xml
<!-- Resources/values/strings.xml -->
<resources>
    <string name="app_name">CalculatorApp</string>
    <string name="action_settings">Settings</string>
    <string name="text_first_input">ตัวตั้ง</string>
    <string name="text_second_input">ตัวบวก</string>
    <string name="text_button_calculate">คำนวน</string>
</resources>
```

## 2. เรียกใช้ string ใน View

หลังจากกำหนดค่าใน strings.xml แล้ว เราสามารถเรียกค่าต่างๆ มาใช้ใน Layout ได้

```xml
<!-- Resources/layout/activity_main.xml -->

<TextView
	android:text="@string/text_first_input"
    ...
    />

<TextView
	android:text="@string/text_second_input"
    ...
    />

<Button
	android:text="@string/text_button_calculate"
    ...
    />
```



## ไฟล์เต็ม

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
	<LinearLayout
		android:orientation="vertical"
		android:minWidth="25px"
		android:minHeight="25px"
		android:padding="18px"
		android:layout_width="match_parent"
		android:layout_height="match_parent"
		android:id="@+id/linearLayout1" >
		<TextView
			android:text="@string/text_first_input"
			android:textAppearance="?android:attr/textAppearanceLarge"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/textView1" />
		<EditText
			android:inputType="number"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/editText2" />
		<TextView
			android:text="@string/text_second_input"
			android:textAppearance="?android:attr/textAppearanceLarge"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/textView2" />
		<EditText
			android:inputType="number"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/editText1" />
		<Space
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:layout_weight="1"
			android:id="@+id/space1" />
		<Button
			android:text="@string/text_button_calculate"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/button1" />
	</LinearLayout>
</RelativeLayout>

```