
# กำหนด strings.xml และ Layout 

## 1. กำหนดข้อความใน strings.xml

```xml
<!-- Resources/values/strings.xml -->
<resources>
    <string name="app_name">multilanguage</string>
    <string name="action_settings">Settings</string>

    <string name="text_hello">Hello World</string>
    <string name="button_text_change_langauge">Change Language</string>
</resources>
```

## 2. สร้าง Layout ที่ใช้ข้อความจาก strings.xml

```xml
<!-- Resources/layout/activity_main.xml -->
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
	xmlns:android="http://schemas.android.com/apk/res/android"
	xmlns:app="http://schemas.android.com/apk/res-auto"
	xmlns:tools="http://schemas.android.com/tools"
	android:layout_width="match_parent"
	android:layout_height="match_parent">

    <!-- 
        android:padding="10sp"
		android:layout_width="match_parent"
		android:layout_height="match_parent"
     -->
	<LinearLayout
		android:orientation="vertical"
		android:minWidth="25px"
		android:minHeight="25px"
		android:padding="10sp"
		android:layout_width="match_parent"
		android:layout_height="match_parent"
		android:id="@+id/linearLayout1">

        <!-- 
            ข้อความตัวอย่าง
            android:text="@string/text_hello"
            android:id="@+id/textHello"
         -->
		<TextView
			android:text="@string/text_hello"
			android:textAppearance="?android:attr/textAppearanceLarge"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/textHello" />

        <!-- 
            ปุ่มเปลี่ยนภาษา
            android:text="@string/button_text_change_langauge"
            android:id="@+id/buttonSwitchLanguage"
         -->
		<Button
			android:text="@string/button_text_change_langauge"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/buttonSwitchLanguage"/>

	</LinearLayout>
</RelativeLayout>
```