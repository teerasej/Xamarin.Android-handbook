
# Main Menu Example 

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="10sp"
    >
	<LinearLayout
		android:orientation="horizontal"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="match_parent"
		android:layout_height="157.5dp"
		android:id="@+id/linearLayout1">
		<LinearLayout
			android:orientation="vertical"
			android:layout_weight="2"
			android:minWidth="25px"
			android:minHeight="25px"
			android:layout_width="match_parent"
			android:layout_height="match_parent"
			android:id="@+id/linearLayout2" >
			<ImageView
				android:layout_weight="1"
				android:src="@android:drawable/ic_menu_gallery"
				android:layout_width="match_parent"
				android:layout_height="wrap_content"
				android:id="@+id/imageView1" />
			<TextView
				android:text="Small Text"
				android:textAppearance="?android:attr/textAppearanceSmall"
				android:layout_width="match_parent"
				android:layout_height="wrap_content"
				android:id="@+id/textView1" />
		</LinearLayout>
		<LinearLayout
			android:padding="20sp"
			android:layout_weight="1"
			android:orientation="vertical"
			android:minWidth="25px"
			android:minHeight="25px"
			android:layout_width="match_parent"
			android:layout_height="match_parent"
			android:id="@+id/linearLayout3" >
			<TextView
				android:layout_weight="1"
				android:text="Small Text"
				android:textAppearance="?android:attr/textAppearanceSmall"
				android:layout_width="match_parent"
				android:layout_height="wrap_content"
				android:id="@+id/textView2" />
			<TextView
				android:layout_weight="1"
				android:text="Small Text"
				android:textAppearance="?android:attr/textAppearanceSmall"
				android:layout_width="match_parent"
				android:layout_height="wrap_content"
				android:id="@+id/textView3" />
			<TextView
				android:layout_weight="1"
				android:text="Small Text"
				android:textAppearance="?android:attr/textAppearanceSmall"
				android:layout_width="match_parent"
				android:layout_height="wrap_content"
				android:id="@+id/textView4" />
			<TextView
				android:layout_weight="1"
				android:text="Small Text"
				android:textAppearance="?android:attr/textAppearanceSmall"
				android:layout_width="match_parent"
				android:layout_height="wrap_content"
				android:id="@+id/textView5" />
		</LinearLayout>
	</LinearLayout>
	<LinearLayout
		android:padding="10sp"
		android:orientation="vertical"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="match_parent"
		android:layout_height="match_parent"
		android:id="@+id/linearLayout4">
		<LinearLayout
			android:layout_weight="1"
			android:orientation="horizontal"
			android:minWidth="25px"
			android:minHeight="25px"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/linearLayout5"
			android:layout_marginBottom="0.0dp">
			<Button
				android:layout_weight="1"
				android:layout_marginRight="10sp"
				android:text="Button"
				android:layout_width="wrap_content"
				android:layout_height="match_parent"
				android:id="@+id/button1" />
			<Button
				android:layout_weight="1"
				android:text="Button"
				android:layout_width="wrap_content"
				android:layout_height="match_parent"
				android:id="@+id/button2" />
		</LinearLayout>
		<LinearLayout
			android:layout_weight="1"
			android:orientation="horizontal"
			android:minWidth="25px"
			android:minHeight="25px"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/linearLayout5"
			android:layout_marginBottom="0.0dp">
			<Button
				android:layout_weight="1"
				android:layout_marginRight="10sp"
				android:text="Button"
				android:layout_width="wrap_content"
				android:layout_height="match_parent"
				android:id="@+id/button1" />
			<Button
				android:layout_weight="1"
				android:text="Button"
				android:layout_width="wrap_content"
				android:layout_height="match_parent"
				android:id="@+id/button2" />
		</LinearLayout>
		<LinearLayout
			android:layout_weight="1"
			android:orientation="horizontal"
			android:minWidth="25px"
			android:minHeight="25px"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/linearLayout5"
			android:layout_marginBottom="0.0dp">
			<Button
				android:layout_weight="1"
				android:layout_marginRight="10sp"
				android:text="Button"
				android:layout_width="wrap_content"
				android:layout_height="match_parent"
				android:id="@+id/button1" />
			<Button
				android:layout_weight="1"
				android:text="Button"
				android:layout_width="wrap_content"
				android:layout_height="match_parent"
				android:id="@+id/button2" />
		</LinearLayout>
		<LinearLayout
			android:layout_weight="1"
			android:orientation="horizontal"
			android:minWidth="25px"
			android:minHeight="25px"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/linearLayout5"
			android:layout_marginBottom="0.0dp">
			<Button
				android:layout_weight="1"
				android:layout_marginRight="10sp"
				android:text="Button"
				android:layout_width="wrap_content"
				android:layout_height="match_parent"
				android:id="@+id/button1" />
			<Button
				android:layout_weight="1"
				android:text="Button"
				android:layout_width="wrap_content"
				android:layout_height="match_parent"
				android:id="@+id/button2" />
		</LinearLayout>
		<LinearLayout
			android:layout_weight="1"
			android:orientation="horizontal"
			android:minWidth="25px"
			android:minHeight="25px"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/linearLayout5"
			android:layout_marginBottom="0.0dp">
			<Button
				android:layout_weight="1"
				android:layout_marginRight="10sp"
				android:text="Button"
				android:layout_width="wrap_content"
				android:layout_height="match_parent"
				android:id="@+id/button1" />
			<Button
				android:layout_weight="1"
				android:text="Button"
				android:layout_width="wrap_content"
				android:layout_height="match_parent"
				android:id="@+id/button2" />
		</LinearLayout>
	</LinearLayout>



</LinearLayout>

```