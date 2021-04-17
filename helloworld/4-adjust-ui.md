
# ปรับแต่ง User Interface

## ปรับ Layout

- ปรับให้พื้นที่ Linear Layout ด้วย `android:layout_width="match_parent"`
- ใส่ระยะห่างจากขอบ Layout กับ Control ด้านในด้วย `android:layout_margin`

```xml
<!-- Resources/layout/activity_main.xml -->
<LinearLayout
		android:orientation="vertical"
		android:minWidth="25px"
		android:minHeight="25px"

		android:layout_width="match_parent"
		android:layout_margin="12px"
		
        android:layout_height="wrap_content"
		android:id="@+id/linearLayout1" >
```

## แก้ไขข้อความ

- แก้ข้อความบน TextView และ Button

```xml
<!-- Resources/layout/activity_main.xml -->
    <TextView
        
        android:text="ชื่อ"

        android:textAppearance="?android:attr/textAppearanceLarge"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/textView1" />
    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:inputType="text" 
        android:id="@+id/editText1" />
    <Button

        android:text="สวัสดีแอพ"
        
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/button1" />
    <TextView

            android:text=""
            
            android:textAppearance="?android:attr/textAppearanceLarge"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/textView3" />
```