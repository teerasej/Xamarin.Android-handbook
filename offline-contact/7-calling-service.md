
# สร้าง method ที่เรียกใช้ service 

- เพื่อดึงข้อมูลจาก Web API 
- ทำงานแบบ Async

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
            
            // เริ่มการโหลดรายการของข้อมูล User
            LoadUserProfiles();
        }
        public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Android.Content.PM.Permission[] grantResults)
        {
            Xamarin.Essentials.Platform.OnRequestPermissionsResult(requestCode, permissions, grantResults);

            base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
        }

        // สร้าง Method ที่ทำงานแบบ Async
        private async Task<bool> LoadUserProfiles()
        {
            // เรียกใช้งาน User service
            var service = new UserService();
            // ขอข้อมูลผู้ใช้จาก Web API
            var users = await service.GetUserProfiles();
            return true;
        }
    }
}
```