
# แสดงชื่อจังหวัดขึ้นมาใน List 

- ใช้ ArrayAdapter โหลดรายชื่อจังหวัดใส่ List Item 
- กำหนด function ที่จะทำงานเมื่อกดปุ่ม 
- แสดงชื่อจังหวัดที่ถูกเลือก

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


            var listView = FindViewById<ListView>(Resource.Id.listViewProvince);
            
            // ใช้ ArrayAdapter โหลดรายชื่อจังหวัดใส่ List Item 
            // โดยการกำหนด context, ชื่อ Layout ที่จะนำมาใช้แสดงเป็น List item และข้อมูล Array
            listView.Adapter = new ArrayAdapter<string>(this, Resource.Layout.list_item, Province.datas);

            // กำหนด function ที่จะทำงานเมื่อกดปุ่ม 
            listView.ItemClick += (object sender, AdapterView.ItemClickEventArgs args) =>
            {
                // แสดงชื่อจังหวัดที่ถูกเลือก
                var toast = Toast.MakeText(Application, ((TextView)args.View).Text, ToastLength.Short);
                toast.Show();
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