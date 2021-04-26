
# ซ่อน ListView และแสดง Loading ตอนเปิดหน้า Main

- ในที่นี้เราสามารถใช้เทคนิคการแสดง และซ่อน View ที่ต้องการได้ ผ่าน Property ชื่อ `Visibility`

```cs 
// MainActivity.cs

using Android.App;
using Android.OS;
using Android.Runtime;
using Android.Views;
using Android.Widget;
using AndroidX.AppCompat.App;

namespace RandomUser
{
    [Activity(Label = "@string/app_name", Theme = "@style/AppTheme", MainLauncher = true)]
    public class MainActivity : AppCompatActivity
    {
        ListView listView;
        LinearLayout loading;

        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(savedInstanceState);
            Xamarin.Essentials.Platform.Init(this, savedInstanceState);
            
            SetContentView(Resource.Layout.activity_main);

            listView = FindViewById<ListView>(Resource.Id.listViewUser);
            loading = FindViewById<LinearLayout>(Resource.Id.layoutLoading);

            // ซ่อน ListView และแสดงตัว Loading จนกว่าข้อมูลจะพร้อม
            listView.Visibility = ViewStates.Gone;
            loading.Visibility = ViewStates.Visible;
        }
        public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Android.Content.PM.Permission[] grantResults)
        {
            Xamarin.Essentials.Platform.OnRequestPermissionsResult(requestCode, permissions, grantResults);

            base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
        }
    }
}
```