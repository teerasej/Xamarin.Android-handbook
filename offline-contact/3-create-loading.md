
# สร้างส่วนหน้าจอ loading

- การทำงานของแอพพลิเคชั่นที่มีการโหลดข้อมูลมาจาก Web API ควรแสดงสถานะการทำงานให้ผู้ใช้เห็น
- ในที่นี้เราเลยจะสร้างส่วนการแสดงผลสถานะการทำงาน (Loading) ขึ้นมา

## 1. เพิ่ม Layout 

```xml
<!-- Resources/layout/activity_main.xml -->
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:gravity="center"
        android:orientation="vertical"
        android:id="@+id/layoutLoading"
        >

        <ProgressBar
            style="?android:attr/progressBarStyle"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="center_vertical|center_horizontal" />

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="center_vertical|center_horizontal"
            android:text="@string/text_loading" />
    </LinearLayout>
    <ListView
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="match_parent"
		android:layout_height="match_parent"
		android:id="@+id/listViewUser" />
</RelativeLayout>
```

## 2. กำหนดข้อความใน strings.xml

```xml
<!-- Resources/values/strings.xml -->
<resources>
    <string name="app_name">RandomUser</string>
    <string name="action_settings">Settings</string>

    <!-- ข้อความสำหรับหน้า Loading -->
    <string name="text_loading">Loading...</string>
</resources>

```


## 3. เรียกใช้งานใน MainActivity


```cs
// MainActivity.cs

using Android.App;
using Android.OS;
using Android.Runtime;
using Android.Widget;
using AndroidX.AppCompat.App;

namespace RandomUser
{
    [Activity(Label = "@string/app_name", Theme = "@style/AppTheme", MainLauncher = true)]
    public class MainActivity : AppCompatActivity
    {
        ListView listView;

        // สร้าง property อ้างถึงส่วน loading
        LinearLayout loading;


        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(savedInstanceState);
            Xamarin.Essentials.Platform.Init(this, savedInstanceState);
            SetContentView(Resource.Layout.activity_main);

            listView = FindViewById<ListView>(Resource.Id.listViewUser);
            
            // อ้างอิงถึง LinearLayout ที่เป็นตัว Loading
            loading = FindViewById<LinearLayout>(Resource.Id.layoutLoading);
        }
        public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Android.Content.PM.Permission[] grantResults)
        {
            Xamarin.Essentials.Platform.OnRequestPermissionsResult(requestCode, permissions, grantResults);

            base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
        }
    }
}
```