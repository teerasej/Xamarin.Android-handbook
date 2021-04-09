
# ลากวาง สร้าง UI

- ลาก LinearLayout มาวางสร้างโครง
- ลาก Text View (Large), Plain Text, และ Button มาวางใน Linear Layout

```xml
<!-- Resources/layout/activity_main.xml -->
   <LinearLayout
		android:orientation="vertical"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="wrap_content"
		android:layout_height="wrap_content"
		android:id="@+id/linearLayout1" >
		<TextView
			android:text="Large Text"
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
			android:text="Button"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/button1" />
        <TextView
			android:text=""
			android:textAppearance="?android:attr/textAppearanceLarge"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/textView2" />
	</LinearLayout>
```