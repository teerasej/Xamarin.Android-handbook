
# สร้าง Layout สำหรับเลือกไฟล์เสียง

## 1. กำหนดข้อความใน Strings.xml

```xml

<!-- Resources/values/strings.xml -->

<resources>
    <string name="app_name">AudioPlayer</string>
    <string name="action_settings">Settings</string>

    <string name="button_play_text">เล่น</string>
    <string name="button_pause_text">หยุดชั่วคราว</string>
    <string name="button_stop_text">หยุดเล่น</string>

</resources>

```

## 2. สร้าง Layout ในไฟล์


```xml
<!-- Resources/layout/activity_main.xml -->

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    
    <!-- 
        สร้าง Layout เรียงแถวแนวดิ่ง

        android:layout_width="match_parent"
		android:layout_height="match_parent"
        android:padding="10sp"
     -->
	<LinearLayout
		android:orientation="vertical"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="match_parent"
		android:layout_height="match_parent"
		android:padding="10sp"
		android:id="@+id/linearLayout1" >

        <!-- 
            สร้าง Spinner เป็นตัวเลือก

            android:id="@+id/spinnerSoundFile"
        -->
		<Spinner
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/spinnerSoundFile" />


        <!-- 
            ปุ่มเล่นเสียง
            android:text="@string/button_play_text"
            android:id="@+id/buttonPlay"
        -->
		<Button
			android:text="@string/button_play_text"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/buttonPlay" />

        <!-- 
            ปุ่มหยุดเสียงชั่วคราว
            android:text="@string/button_pause_text"
            android:id="@+id/buttonPause"
        -->
		<Button
			android:text="@string/button_pause_text"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/buttonPause" />

        <!-- 
            ปุ่มหยุดเสียง
            android:text="@string/button_stop_text"
            android:id="@+id/buttonStop"
        -->    
		<Button
			android:text="@string/button_stop_text"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/buttonStop" />

    </LinearLayout>
</RelativeLayout>
```