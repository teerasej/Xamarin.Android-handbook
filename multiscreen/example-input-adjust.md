
# Example Input Adjust

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    >
	<LinearLayout
		android:orientation="horizontal"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:id="@+id/linearLayout1" >
		<TextView
			android:text="Small Text"
			android:textAppearance="?android:attr/textAppearanceSmall"
			android:layout_width="wrap_content"
			android:layout_height="match_parent"
			android:id="@+id/textView1" />
		<Space
			android:layout_weight="1"
			android:layout_width="match_parent"
			android:layout_height="match_parent"
			android:id="@+id/space1" />
		<TextView
			android:text="Small Text"
			android:textAppearance="?android:attr/textAppearanceSmall"
			android:layout_width="wrap_content"
			android:layout_height="match_parent"
			android:id="@+id/textView2" />
		<TextView
			android:text="Small Text"
			android:textColor="@android:color/holo_red_light"
			android:textAppearance="?android:attr/textAppearanceSmall"
			android:layout_width="wrap_content"
			android:layout_height="match_parent"
			android:id="@+id/textView3" />
	</LinearLayout>
	<LinearLayout
		android:orientation="horizontal"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:id="@+id/linearLayout2">
		<TextView
			android:text="Adjust Code:"
			android:textAppearance="?android:attr/textAppearanceMedium"
			android:layout_width="106.0dp"
			android:layout_height="match_parent"
			android:id="@+id/textView4" />
		<Spinner
			android:layout_width="match_parent"
			android:layout_height="match_parent"
			android:id="@+id/spinner1" />
	</LinearLayout>
	<LinearLayout
		android:orientation="horizontal"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:id="@+id/linearLayout2" >
		<TextView
			android:text="Barcode:"
			android:textAppearance="?android:attr/textAppearanceMedium"
			android:layout_width="106.0dp"
			android:layout_height="match_parent"
			android:id="@+id/textView4" />
		<EditText
			android:layout_weight="1"
			android:layout_width="wrap_content"
			android:layout_height="match_parent"
			android:id="@+id/editText1" />
		
	</LinearLayout>
	<LinearLayout
		android:orientation="horizontal"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:id="@+id/linearLayout2" >
		<TextView
			android:text="Rootcode:"
			android:textAppearance="?android:attr/textAppearanceMedium"
			android:layout_width="106.0dp"
			android:layout_height="match_parent"
			android:id="@+id/textView4" />
		<TextView
			android:text="000000"
			android:textAppearance="?android:attr/textAppearanceMedium"
			android:layout_width="120"
			android:layout_height="match_parent"
			android:id="@+id/textView4" />
		<TextView
			android:text="CRE"
			android:textAppearance="?android:attr/textAppearanceMedium"
			android:layout_width="wrap_content"
			android:layout_height="match_parent"
			android:id="@+id/textView4" />
		
	</LinearLayout>
	<LinearLayout
		android:orientation="horizontal"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:id="@+id/linearLayout2" >
		<TextView
			android:text="Description: "
			android:textAppearance="?android:attr/textAppearanceMedium"
			android:layout_width="104.5dp"
			android:layout_height="match_parent"
			android:id="@+id/textView4"
		/>
		
		<TextView
			android:text="000000"
			android:textAppearance="?android:attr/textAppearanceMedium"
			android:layout_width="wrap_content"
			android:layout_height="match_parent"
			android:id="@+id/textView4" />
		
	</LinearLayout>
	<LinearLayout
		android:orientation="horizontal"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:id="@+id/linearLayout2" >
		<TextView
			android:text="หน่วย:"
			android:textAppearance="?android:attr/textAppearanceMedium"
			android:layout_width="106.0dp"
			android:layout_height="match_parent"
			android:id="@+id/textView4" />
		
		<TextView
			android:text="000000"
			android:textAppearance="?android:attr/textAppearanceMedium"
			android:layout_width="wrap_content"
			android:layout_height="match_parent"
			android:id="@+id/textView4" />
		
	</LinearLayout>
	<LinearLayout
		android:orientation="horizontal"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:id="@+id/linearLayout2" >
		<TextView
			android:text="จำนวน:"
			android:textAppearance="?android:attr/textAppearanceMedium"
			android:layout_width="106.0dp"
			android:layout_height="match_parent"
			android:id="@+id/textView4" />
		
		<EditText
			android:layout_weight="1"
			android:layout_width="wrap_content"
			android:layout_height="match_parent"
			android:id="@+id/editText1" />
		
	</LinearLayout>
	<Space
		android:layout_weight="1"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:id="@+id/space2" />
	<Button
		android:text="Button"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:id="@+id/button1" />
	<LinearLayout
		android:orientation="horizontal"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:id="@+id/linearLayout3" >
		<Button
			android:layout_marginRight="5sp"
			android:text="Button"
			android:layout_weight="1"
			android:layout_width="wrap_content"
			android:layout_height="match_parent"
			android:id="@+id/button2" />
		<Button
			android:layout_marginRight="5sp"
			android:text="Button"
			android:layout_weight="1"
			android:layout_width="wrap_content"
			android:layout_height="match_parent"
			android:id="@+id/button3" />
		<Button
			android:layout_marginRight="5sp"
			android:text="Button"
			android:layout_weight="1"
			android:layout_width="wrap_content"
			android:layout_height="match_parent"
			android:id="@+id/button4" />
		<Button
			android:text="Button"
			android:layout_width="wrap_content"
			android:layout_height="match_parent"
			android:id="@+id/button5" />
	</LinearLayout>
	<LinearLayout
		android:orientation="horizontal"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:id="@+id/linearLayout4" >
		<Button
			android:layout_marginRight="5sp"
			android:layout_weight="1"
			android:text="Button"
			android:layout_width="wrap_content"
			android:layout_height="match_parent"
			android:id="@+id/button6" />
		<Button
			android:layout_marginRight="5sp"
			android:layout_weight="1"
			android:text="Button"
			android:layout_width="wrap_content"
			android:layout_height="match_parent"
			android:id="@+id/button7" />
		<Button
			android:layout_weight="2"
			android:text="Button"
			android:layout_width="wrap_content"
			android:layout_height="match_parent"
			android:id="@+id/button8" />
	</LinearLayout>
</LinearLayout>

```