
# กระจาย View ให้เต็มหน้าจอ

- เราสามารถกำหนดให้ View แบ่งพื้นที่ใน Container เดียวกันได้โดยกำหนด `android:layout_weight="1"` (หมายถึง 1 ส่วน จากการคำนวนพื้นที่ทั้งหมดกับ View อื่น)

ทดสอบเพิ่มปุ่ม ที่มีค่า layout_weight ลงไปจนเต็ม LinearLayout และลองปรับค่า พรีวิวดู

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:padding="10sp"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    >
	<Button
		android:text="Button"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_weight="1"
		android:id="@+id/button1" />
	<Button
		android:text="Button"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_weight="1"
		android:id="@+id/button1" />
	<Button
		android:text="Button"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_weight="1"
		android:id="@+id/button1" />
	
</LinearLayout>

```