
# สร้าง User Interface จาก View

- ลาก Linear Layout, TextView (Large), และ Button มาวางใน Activity
- กำหนด Id ให้กับ View ที่ต้องการเรียกใช้ใน Activity

```xml
<!-- Resources/layout/activity_main.xml -->
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
		android:layout_width="wrap_content"
		android:layout_height="wrap_content"
		android:id="@+id/linearLayout1" >
		<TextView
			android:text="ตัวตั้ง"
			android:textAppearance="?android:attr/textAppearanceLarge"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/textView1" />
		<EditText
			android:inputType="number"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"


			android:id="@+id/inputFirst" /> />


		<TextView
			android:text="ตัวบวก"
			android:textAppearance="?android:attr/textAppearanceLarge"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/textView2" />
		<EditText
			android:inputType="number"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"


			android:id="@+id/inputSecond" />


		<Space
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:layout_weight="1"
			android:id="@+id/space1" />
		<Button
			android:text="คำนวน"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"


			android:id="@+id/button_calculate" />

			
	</LinearLayout>
</RelativeLayout>

```