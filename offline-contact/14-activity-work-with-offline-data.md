

# สลับมาใช้การโหลดใช้ข้อมูลแบบ Offline แทน

การทำส่วนนี้ให้รันได้อย่างสมบูรณ์ อาจต้องกำหนด Permission ชื่อ **READ_EXTERNAL_STORAGE** และ **WRITE_EXTERNAL_STORAGE** ใน Android Options (AndroidManifest.xml) ด้วย ขึ้นอยู่กับที่อยู่ และระบบการทำงานของ OS นั้นๆ

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
       
       //..

        private async Task<bool> LoadUserProfiles()
        {
            var service = new UserService();

            // สลับมาใช้การโหลดใช้ข้อมูลแบบ Offline แทนการโหลดโดยตรง
            // ความต่างตรงนี้คือข้อมูลที่อยู่รูปภาพจะไม่เหมือนกัน แบบใหม่จะอ้างจากไฟล์ที่ดาวน์โหลดเก็บไว้ในแอพ
            var users = await service.PrepareOfflineData();

            listView.Adapter = new UserProfileListAdapter(this, users);

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
            var users = await service.PrepareOfflineData();

            listView.Adapter = new UserProfileListAdapter(this, users);


            listView.Visibility = ViewStates.Visible;
            loading.Visibility = ViewStates.Gone;

            return true;
        }
    }
}
```

