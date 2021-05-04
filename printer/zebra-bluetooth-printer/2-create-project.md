

# สร้างโปรเจค, ติดตั้ง Package, และเปิด permission

## สร้างโปรเจค 

1. ให้สร้างโปรเจคใหม่
2. เลือกประเภท Android App > Blank App 
3. ตั้งชื่อ **BluetoothPrinter**

## ติดตั้ง package 

- [Zebra.Printer.SDK](https://www.nuget.org/packages/Zebra.Printer.SDK/)


## เปิด Permission 

1. ACCESS_COARSE_LOCATION
2. ACCESS_FINE_LOCATION
3. BLUETOOTH
4. BLUETOOTH_ADMIN

```xml
<!-- Properties/AndroidManifest.xml -->
	<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
	<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
	<uses-permission android:name="android.permission.BLUETOOTH" />
	<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
```