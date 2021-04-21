
# สร้าง Layout สำหรับใช้แสดง List item ของชื่อผู้ติดต่อ

- สร้างไฟล์ Layout ใหม่ ตั้งชื่อว่า `list_item_contact.xml` 
- สร้าง TextView และกำหนด id เป็น `android:id="@+id/textName"`
- สร้าง TextView และกำหนด id เป็น `android:id="@+id/textPhoneNumber"`

```xml
<!-- Resources/layout/list_item_contact.xml -->
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
	android:padding="10sp"
	>
	<TextView
		android:text="Medium Text"
		android:textAppearance="?android:attr/textAppearanceMedium"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:minWidth="25px"
		android:minHeight="25px"
		android:textColor="@android:color/black"
		android:id="@+id/textName" />
	<TextView
		android:text="Medium Text"
		android:textAppearance="?android:attr/textAppearanceMedium"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:id="@+id/textPhoneNumber" />
    
</LinearLayout>

```