
# สร้าง Layout เป็นตัวแทนของข้อมูลผู้ใช้ใน ListView

- สร้างไฟล์ `Resources/layout/list_item_user_profile.xml`

```xml
<!-- Resources/layout/list_item_user_profile.xml -->

<?xml version="1.0" encoding="utf-8"?>
<!-- ปรับแบบ Horizontal -->
<LinearLayout
	xmlns:android="http://schemas.android.com/apk/res/android"
	android:orientation="horizontal"
	android:layout_width="match_parent"
	android:layout_height="wrap_content"
    >
    
    <!--
        วางรูป 
        layout_marginRight="10sp" เพื่อกำหนดระยะห่างจากข้อความทางขวา
        layout_gravity="center" กำหนดให้อยู่ตรงกลางของพื้นที่
        id="@+id/imageUserProfile"
      -->
	<ImageView
		android:src="@android:drawable/ic_menu_gallery"
		android:layout_width="wrap_content"
		android:layout_height="match_parent"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_marginRight="10sp"
		android:layout_gravity="center"
		android:id="@+id/imageUserProfile" />

    <!-- padding="10sp" -->
	<LinearLayout
		android:orientation="vertical"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="wrap_content"
		android:layout_height="match_parent"
		android:padding="10sp"
		android:id="@+id/linearLayout1" >

        <!-- 
            แสดงชื่อ
            textColor="@android:color/black" กำหนดสีดำ
            id="@+id/textFullName"
         -->
		<TextView
			android:text="Medium Text"
			android:textAppearance="?android:attr/textAppearanceMedium"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:textColor="@android:color/black"
			android:id="@+id/textFullName" />

        <!-- 
            แสดงเบอร์โทร
            id="@+id/textPhoneNumber"
         -->
		<TextView
			android:text="Medium Text"
			android:textAppearance="?android:attr/textAppearanceMedium"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/textPhoneNumber" />
	</LinearLayout>

</LinearLayout>
```