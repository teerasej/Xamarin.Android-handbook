
# ทำการแสกนและนำค่ากลับมาใช้งานใน Activity


```cs
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

            var buttonScan = FindViewById<Button>(Resource.Id.buttonScan);
            var textBarcodeResult = FindViewById<TextView>(Resource.Id.textViewBarcodeResult);
            var textBarcodeFormat = FindViewById<TextView>(Resource.Id.textViewBarcodeFormat);

            // สร้าง Event Handler
            buttonScan.Click += async (sender, e) =>
            {
                // สร้าง instance ของ MobileBarcodeScanner จาก package ZXing
                var scanner = new MobileBarcodeScanner();

                // สั่งแสกน
                var result = await scanner.Scan();

                // ถ้าการแสกนสมบูรณ์ 
                if(result != null)
                {
                    // นำค่าที่แสกนได้ มาแสดงบนแอพ
                    textBarcodeResult.Text = result.Text;

                    // นำประเภทบาร์โค้ดที่แสกนได้ มาแสดงบนแอพ
                    textBarcodeFormat.Text = result.BarcodeFormat.ToString();
                }
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