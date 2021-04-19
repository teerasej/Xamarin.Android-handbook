

# ส่งชื่อจังหวัดที่ถูกเลือกกลับไปให้หน้าแรก

```cs
// SelectProvinceActivity.cs


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
                // ดึงข้อความจากชื่อจังหวัดเอามาเก็บไว้ในตัวแปร 
                var selectedProvinceName = ((TextView)args.View).Text;

                // สร้าง intent สำหรับ MainActivity
                var myIntent = new Intent(this, typeof(MainActivity));

                // ใส่ข้อความลงไปใน intent
                myIntent.PutExtra("name", selectedProvinceName);

                // กำหนด Result object สำหรับส่งกลับไปให้ MainActivity
                SetResult(Result.Ok, myIntent);

                // ปิดการทำงานของ Activity
                Finish();
            };
        }
    }
}

```