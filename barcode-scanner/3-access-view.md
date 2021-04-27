
# 


```cs
// MainActivity.cs

using Android.App;
using Android.OS;
using Android.Runtime;
using Android.Widget;
using AndroidX.AppCompat.App;
using ZXing.Mobile;

namespace BarcodeScanner
{
    [Activity(Label = "@string/app_name", Theme = "@style/AppTheme", MainLauncher = true)]
    public class MainActivity : AppCompatActivity
    {
        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(savedInstanceState);
            Xamarin.Essentials.Platform.Init(this, savedInstanceState);
            
            SetContentView(Resource.Layout.activity_main);

            // เรียกใช้งาน View ต่่างๆ 
            var buttonScan = FindViewById<Button>(Resource.Id.buttonScan);
            var textBarcodeResult = FindViewById<TextView>(Resource.Id.textViewBarcodeResult);
            var textBarcodeFormat = FindViewById<TextView>(Resource.Id.textViewBarcodeFormat);
        }
        public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Android.Content.PM.Permission[] grantResults)
        {
            Xamarin.Essentials.Platform.OnRequestPermissionsResult(requestCode, permissions, grantResults);

            base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
        }
    }
}
```