
# จัดขนาด Linear Layout

- กินพื้นที่ความกว้างของหน้าจอ
- padding เว้นระยะห่าง

```xml
<!-- Resources/layout/activity_main.xml -->

<LinearLayout
		android:orientation="vertical"
		android:minWidth="25px"
		android:minHeight="25px"


		android:padding="18px"
		android:layout_width="match_parent"
		android:layout_height="match_parent"


		android:id="@+id/linearLayout1" >

```