
# กำหนด id ให้ Control แต่ละตัว

ในการควบคุมการทำงานของ User Interface หรือ View แต่ละตัว สามารถทำได้ผ่านการตั้งชื่อ id ก่อน 

```xml
<!-- Resources/layout/activity_main.xml -->

<EditText
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:inputType="text" 
    
    android:id="@+id/inputName" />

<Button
    android:text="สวัสดีแอพ"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    
    android:id="@+id/buttonHello" />

<TextView
    android:text=""
    android:textAppearance="?android:attr/textAppearanceLarge"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"

    android:id="@+id/txtResult" />

</LinearLayout>
```