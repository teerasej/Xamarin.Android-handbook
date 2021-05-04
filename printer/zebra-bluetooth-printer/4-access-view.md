
# เรียกใช้ View ผ่าน Activity

```cs
// MainActivity.cs

using Android.App;
using Android.OS;
using Android.Runtime;
using Android.Views;
using Android.Widget;
using AndroidX.AppCompat.App;

namespace BluetoothPrinter
{
    [Activity(Label = "@string/app_name", Theme = "@style/AppTheme", MainLauncher = true)]
    public class MainActivity : AppCompatActivity
    {
        // สร้าง View 
        Button buttonPrint;
        Button buttonDiscoverPrinter;
        ProgressBar loading;
        TextView textPrinterInfo;


        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(savedInstanceState);
            Xamarin.Essentials.Platform.Init(this, savedInstanceState);
           
            SetContentView(Resource.Layout.activity_main);

            // เข้าถึง View ที่ต้องใช้ทั้งหมด
            buttonPrint = FindViewById<Button>(Resource.Id.buttonPrint);
            buttonDiscoverPrinter = FindViewById<Button>(Resource.Id.buttonDiscoverPrinter);
            loading = FindViewById<ProgressBar>(Resource.Id.loading);
            textPrinterInfo = FindViewById<TextView>(Resource.Id.textPrinterInfo);

            // ซ่อนตัวโหลด และข้อความ
            loading.Visibility = ViewStates.Gone;
            textPrinterInfo.Visibility = ViewStates.Gone;

              
        }
        public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Android.Content.PM.Permission[] grantResults)
        {
            Xamarin.Essentials.Platform.OnRequestPermissionsResult(requestCode, permissions, grantResults);

            base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
        }
    }
}
```