
# สร้าง List ใช้งานใน Main Activity

## 1. สร้าง Listview ใน Layout ของหน้า Main

```xml
<!-- Resources/layout/activity_main.xml -->

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <!-- กำหนด layout_width และ layout_height เป็น match_parent เพื่อกางเต็มพื้นที่ -->
    <!-- กำหนด id เป็น @+id/listViewProvince -->
	<ListView
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="match_parent"
		android:layout_height="match_parent"
		android:id="@+id/listViewProvince" />
</RelativeLayout>
```

## 2. เรียกใช้ใน MainActivity

```cs
// MainActivity.cs

using Android.App;
using Android.OS;
using Android.Runtime;
using Android.Widget;
using AndroidX.AppCompat.App;
using AndroidX.RecyclerView.Widget;

namespace MyContacts
{
    [Activity(Label = "@string/app_name", Theme = "@style/AppTheme", MainLauncher = true)]
    public class MainActivity : AppCompatActivity
    {
        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(savedInstanceState);
            Xamarin.Essentials.Platform.Init(this, savedInstanceState);

            SetContentView(Resource.Layout.activity_main);

            // เข้าถึง ListView ผ่าน Id ที่ตั้งไว้
            var listView = FindViewById<ListView>(Resource.Id.listViewProvince);

        }
        public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Android.Content.PM.Permission[] grantResults)
        {
            Xamarin.Essentials.Platform.OnRequestPermissionsResult(requestCode, permissions, grantResults);

            base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
        }
    }
}
```