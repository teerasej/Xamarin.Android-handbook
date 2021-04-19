
# สร้างหน้าแสดงผลลัพธ์ 

## 1. สร้าง Layout 

สร้างไฟล์ `Resources/layout/activity_result.xml`

```xml
<!-- Resources/layout/activity_result.xml -->
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    >
    <!-- วางผลลัพธ์ไว้กลางหน้าจอ และกำหนด Id -->
    <TextView
        android:text="Large Text"
        android:textAppearance="?android:attr/textAppearanceLarge"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:minWidth="25px"
        android:minHeight="25px"
        android:gravity="center"
        android:id="@+id/txtResult" />
</LinearLayout>
```

## 2. สร้าง ResultActivity

- สร้างไฟล์ `ResultActivity.cs`
- เปลี่ยนมาใช้ `AppCompatActivity` แทน `Activity` ธรรมดา เพื่อแสดง App Bar (ให้สังเกตว่า MainActivity จะใช้ในรูปแบบเดียวกัน)
- กำหนดให้ใช้ Layout ที่ต้องการผ่าน method `SetContentView()`

```cs
// ResultActivity.cs


using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

using Android.App;
using Android.Content;
using Android.OS;
using Android.Runtime;
using Android.Views;
using Android.Widget;

namespace CalculatorApp
{
    // เปลี่ยนมาใช้ `AppCompatActivity` แทน `Activity` ธรรมดา เพื่อแสดง App Bar (ให้สังเกตว่า MainActivity จะใช้ในรูปแบบเดียวกัน)
    [Activity(Label = "ResultActivity")]
    public class ResultActivity : AppCompatActivity
    {
        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(savedInstanceState);

            // กำหนดให้ใช้ Layout ที่ต้องการผ่าน method `SetContentView()`
            SetContentView(Resource.Layout.activity_result);

            
            // Create your application here
        }
    }
}
```