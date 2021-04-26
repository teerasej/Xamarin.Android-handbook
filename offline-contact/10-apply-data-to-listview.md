
# นำข้อมูล Array ที่ได้มาใช้กับ ListView

- ใช้ userService ขอข้อมูล Array จาก Web API
- โหลดข้อมูลที่ได้ลง Adapter เพื่อแสดงใน ListView
- สลับตัวแสดง Loading แทนที่ด้วย ListView

```cs
// 

using System.Threading.Tasks;
using Android.App;
using Android.OS;
using Android.Runtime;
using Android.Views;
using Android.Widget;
using AndroidX.AppCompat.App;
using RandomUser.Service;

namespace RandomUser
{
    [Activity(Label = "@string/app_name", Theme = "@style/AppTheme", MainLauncher = true)]
    public class MainActivity : AppCompatActivity
    {

        ListView listView;
        LinearLayout loading;

        protected override void OnCreate(Bundle savedInstanceState)
        {
            //...

            LoadUserProfiles();
        }
        public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Android.Content.PM.Permission[] grantResults)
        {
            Xamarin.Essentials.Platform.OnRequestPermissionsResult(requestCode, permissions, grantResults);

            base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
        }

        private async Task<bool> LoadUserProfiles()
        {
            var service = new UserService();

            // ใช้ userService ขอข้อมูล Array จาก Web API
            var users = await service.GetUserProfiles();

            // โหลดข้อมูลที่ได้ลง Adapter เพื่อแสดงใน ListView
            listView.Adapter = new UserProfileListAdapter(this, users);

            // สลับตัวแสดง Loading แทนที่ด้วย ListView
            listView.Visibility = ViewStates.Visible;
            loading.Visibility = ViewStates.Gone;

            return true;
        }
    }
}
```

## ไฟล์เต็ม 

```cs

// MainActivity.cs

using System.Threading.Tasks;
using Android.App;
using Android.OS;
using Android.Runtime;
using Android.Views;
using Android.Widget;
using AndroidX.AppCompat.App;
using RandomUser.Service;

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
            // Set our view from the "main" layout resource
            SetContentView(Resource.Layout.activity_main);

            listView = FindViewById<ListView>(Resource.Id.listViewUser);
            loading = FindViewById<LinearLayout>(Resource.Id.layoutLoading);

            listView.Visibility = ViewStates.Gone;
            loading.Visibility = ViewStates.Visible;

            LoadUserProfiles();
        }
        public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Android.Content.PM.Permission[] grantResults)
        {
            Xamarin.Essentials.Platform.OnRequestPermissionsResult(requestCode, permissions, grantResults);

            base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
        }

        private async Task<bool> LoadUserProfiles()
        {
            var service = new UserService();
            var users = await service.GetUserProfiles();

            listView.Adapter = new UserProfileListAdapter(this, users);


            listView.Visibility = ViewStates.Visible;
            loading.Visibility = ViewStates.Gone;

            return true;
        }
    }
}
```