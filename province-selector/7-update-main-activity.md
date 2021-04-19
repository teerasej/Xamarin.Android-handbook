
# อัพเดตการทำงานของหน้าแรก

## 1. เริ่มจากปรับ Layout ของ `activity_main.xml`

```xml
<!-- Resources/layout/activity_main.xml -->
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <!-- ใช้ Linear Layout -->
    <!-- 
        กำหนด layout_width และ layout_height เป็น match_parent 
        กำหนด layout_margin="10px"
        -->
	<LinearLayout
		android:orientation="vertical"
		android:minWidth="25px"
		android:minHeight="25px"
		android:layout_width="match_parent"
		android:layout_height="match_parent"
		android:id="@+id/linearLayout1"
		android:layout_margin="10px"
		>

        <!-- สร้างปุ่มกดเลือกจังหวัด -->
        <!-- 
            กำหนด 
            android:text="เลือกจังหวัด" 
            id="@+id/buttonSelectProvince" 
            android:layout_width="match_parent"
        -->
		<Button
			android:text="เลือกจังหวัด"
			android:layout_width="match_parent"
			android:layout_height="wrap_content"
			android:id="@+id/buttonSelectProvince" />
	</LinearLayout>
	
</RelativeLayout>
```

## 2. การกดปุ่มจะเป็นการเปิดไปยังหน้าเลือกจังหวัด

ทำการเขียนกำหนดให้การกดปุ่มเป็นการเปิดไปยังหน้าแสดงรายชื่อจังหวัดเพื่อเลือก

```cs
// MainActivity.cs

using Android.App;
using Android.Content;
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
        Button buttonSelectProvince;

        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(savedInstanceState);
            Xamarin.Essentials.Platform.Init(this, savedInstanceState);
            
            SetContentView(Resource.Layout.activity_main);

            // ส่วนที่ทำงานกับ ListView ถูกย้ายไปใช้ใน Activity อื่นแล้ว

            //var listView = FindViewById<ListView>(Resource.Id.listViewProvince);

            //listView.Adapter = new ArrayAdapter<string>(this, Resource.Layout.list_item, Province.datas);

            //listView.ItemClick += (object sender, AdapterView.ItemClickEventArgs args) =>
            //{
            //    var toast = Toast.MakeText(Application, ((TextView)args.View).Text, ToastLength.Short);
            //    toast.Show();
            //};

            buttonSelectProvince = FindViewById<Button>(Resource.Id.buttonSelectProvince);

            buttonSelectProvince.Click += (sender, e) =>
            {
                // สร้าง Intent สำหรับเปิดไปยัง Activity สำหรับแสดงรายชื่อเลือกจังหวัด
                var intent = new Intent(this, typeof(SelectProvinceActivity));

                // เริ่มการทำงานของ Activity เป้าหมาย โดยคาดหวังการตอบกลับจาก Activity ด้วย ซึ่งจะไม่เหมือนกับ StartActivity() ทั่วไป
                // Request code เปรียบเหมือนป้ายชื่อของ Activity ที่เปิดใช้งาน ใช้จำแนก Activity ที่ส่งข้อมูลกลับมาหลายๆ แบบ
                StartActivityForResult(intent, 0);
            };

        }
        public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Android.Content.PM.Permission[] grantResults)
        {
            Xamarin.Essentials.Platform.OnRequestPermissionsResult(requestCode, permissions, grantResults);

            base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
        }
    }
}
```

- อ้างอิง[เรื่อง Request Code ได้ที่นี่](https://stackoverflow.com/a/14148838/95974)