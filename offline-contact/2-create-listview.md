

# สร้าง ListView สำหรับแสดงรายชื่อ User

## 1. จัดการ Layout 

```xml
<!-- Resources/layout/activity_main.xml -->
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <!-- 
        กำหนดค่า 
        - layout_width
        - layout_height
        - id
    -->
    <ListView
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="match_parent"
		android:layout_height="match_parent"
		android:id="@+id/listViewUser" />
</RelativeLayout>
```

## 2. เรียกใช้งานใน MainActivity

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

        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(savedInstanceState);
            Xamarin.Essentials.Platform.Init(this, savedInstanceState);
            
            SetContentView(Resource.Layout.activity_main);

            // อ้างอิงถึง ListView ใน Layout
            listView = FindViewById<ListView>(Resource.Id.listViewUser);
        }
        public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Android.Content.PM.Permission[] grantResults)
        {
            Xamarin.Essentials.Platform.OnRequestPermissionsResult(requestCode, permissions, grantResults);

            base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
        }
    }
}
```