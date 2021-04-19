
# สร้างหน้าแอพ สำหรับเลือกจังหวัดโดยเฉพาะ 

## 1. ย้าย ListView มาจาก Layout เดิม 

เริ่มจากสร้างไฟล์ `Resources/layout/activity_select_province.xml` 

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    >
	<ListView
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="match_parent"
		android:layout_height="match_parent"
		android:id="@+id/listViewProvince" />
</LinearLayout>

```

## 2. ย้ายการทำงานของ ListView มาจาก MainActivity

จากนั้นสร้างไฟล์ `SelectProvinceActivity.cs`

และย้ายโค้ดส่วนทำงานกับ ListView จาก `MainActivity.cs` มาไว้ใน `SelectProvinceActivity.cs`

```cs

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
using AndroidX.AppCompat.App;

namespace MyContacts
{
    [Activity(Label = "เลือกจังหวัด")]
    public class SelectProvinceActivity : AppCompatActivity
    {
        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(savedInstanceState);

            SetContentView(Resource.Layout.activity_select_province);

            var listView = FindViewById<ListView>(Resource.Id.listViewProvince);

            listView.Adapter = new ArrayAdapter<string>(this, Resource.Layout.list_item, Province.datas);

            listView.ItemClick += (object sender, AdapterView.ItemClickEventArgs args) =>
            {
                var toast = Toast.MakeText(Application, ((TextView)args.View).Text, ToastLength.Short);
                toast.Show();
            };
        }
    }
}

```