

# สร้างโปรเจค, ติดตั้ง Package, และเปิด permission

## สร้างโปรเจค 

1. ให้สร้างโปรเจคใหม่
2. เลือกประเภท Android App > Blank App 
3. ตั้งชื่อ **PDFPrinter**

## ติดตั้ง package 

- [Syncfusion.Xamarin.SfPdfViewer.Android](https://www.nuget.org/packages/Syncfusion.Xamarin.SfPdfViewer.Android/)


## เปิด Permission 

1. READ_EXTERNAL_STORAGE
2. WRITE_EXTERNAL_STORAGE

```xml
<!-- Properties/AndroidManifest.xml -->
	<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
	<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```