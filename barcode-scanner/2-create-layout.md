
# สร้าง Layout สำหรับเริ่มการแสกน และแสดงผล


## 1. จัดวาง View สำหรับหน้า Main

```xml

<!-- Resources/layout/activity_main.xml -->

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <!-- 
        สร้าง Layout แนวตั้ง 
        layout_width="match_parent"
        layout_height="match_parent"
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
            ปุ่มสำหรับเริ่มการแสกน
            id="@+id/buttonScan"
        -->
		<Button
			android:text="@string/button_barcode_text"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/buttonScan" />

        <!-- 
            แสดงข้อมูลที่แสกนได้ 
            android:id="@+id/textViewBarcodeResult"
         -->
		<TextView
			android:text="Large Text"
			android:textAppearance="?android:attr/textAppearanceLarge"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/textViewBarcodeResult" />

        <!-- 
            แสดงประเภทของบาร์โค้ดที่แสกนได้
            id="@+id/textViewBarcodeFormat"
         -->
         <TextView
			android:text=""
			android:textAppearance="?android:attr/textAppearanceLarge"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/textViewBarcodeFormat" />
	</LinearLayout>

</RelativeLayout>
```

## 2. กำหนดข้อความแสดงบนปุ่ม 

```xml
<!-- 
Resources/values/strings.xml -->

<resources>
    <string name="app_name">BarcodeScanner</string>
    <string name="action_settings">Settings</string>
    <string name="button_barcode_text">แสกน</string>
</resources>
```