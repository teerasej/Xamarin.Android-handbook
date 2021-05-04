
# สร้าง Layout 

## 1. กำหนดข้อความในไฟล์ 

```xml
<!-- Resources/values/strings.xml  -->

<resources>
    <string name="app_name">BluetoothPrinter</string>
    <string name="action_settings">Settings</string>

    <string name="button_text_print">print</string>
    <string name="button_text_scan">Discover printer</string>
</resources>
```

## 2. สร้าง View ใน Layout

```xml
<!--  Resources/layout/activity_main.xml  -->

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
	
    <!-- 
        Layout
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
		android:id="@+id/layoutControl" >

        <!-- 
            ตัวโหลดแสดงตอนค้นหาเครื่อง
            style="?android:attr/progressBarStyleSmall"
			android:layout_width="match_parent"
            android:id="@+id/loading"
         -->
		<ProgressBar
			style="?android:attr/progressBarStyleSmall"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/loading" />

        <!-- 
            ปุ่มแสกน
            android:text="@string/button_text_scan"
            android:id="@+id/buttonDiscoverPrinter"
         -->
		<Button
			android:text="@string/button_text_scan"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/buttonDiscoverPrinter" />
		
        <!-- 
            ข้อความแสดงชื่อเครื่อง และ address
         -->
        <TextView
			android:text="Medium Text"
			android:textAppearance="?android:attr/textAppearanceMedium"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/textPrinterInfo" />

        <!-- 
            ปุ่มปริ้นท์
            android:text="@string/button_text_print"
            android:id="@+id/buttonPrint"
         -->
		<Button
			android:text="@string/button_text_print"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/buttonPrint" />
	</LinearLayout>

    
</RelativeLayout>
```