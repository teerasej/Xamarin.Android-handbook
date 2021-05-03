

# สร้าง Layout

## กำหนด strings.xml

```xml
<!-- Resources/values/strings.xml -->

<resources>
    <string name="app_name">PDFPrinter</string>
    <string name="action_settings">Settings</string>
    
    <string name="button_download_pdf">ดาวน์โหลดไฟล์ PDF</string>
    <string name="button_view_pdf">ดูไฟล์ PDF</string>
    <string name="button_print_pdf">print</string>
</resources>

```

## สร้าง Layout 

```xml
<!-- Resources/layout/activity_main.xml -->

<?xml version="1.0" encoding="utf-8"?>
<!-- 
    แก้จาก RelativeLayout เป็น LinearLayout
    android:padding="10sp"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
 -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:orientation="vertical"
    android:padding="10sp"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <!-- 
        ปุ่มสำหรับ download pdf ไฟล์
        android:text="@string/button_download_pdf"
        android:id="@+id/buttonDownloadPDF"
     -->
	<Button
		android:text="@string/button_download_pdf"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:minWidth="25px"
		android:minHeight="25px"
		android:id="@+id/buttonDownloadPDF" />

    <!-- 
        ปุ่มสำหรับพรีวิว pdf ไฟล์
        android:text="@string/button_view_pdf"
        android:id="@+id/buttonViewPDF"
     -->
	<Button
		android:text="@string/button_view_pdf"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:minWidth="25px"
		android:minHeight="25px"
		android:id="@+id/buttonViewPDF" />

    <!-- 
        ปุ่มสำหรับปร้ินท์ pdf ไฟล์
        android:text="@string/button_print_pdf"
        android:id="@+id/buttonPrintPDF"
     -->
	<Button
		android:text="@string/button_print_pdf"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:minWidth="25px"
		android:minHeight="25px"
		android:id="@+id/buttonPrintPDF" />

</LinearLayout>
```