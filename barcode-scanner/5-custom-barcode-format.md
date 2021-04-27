
# กำหนดประเภท barcode ที่ต้องการแสกน



```cs
// MainActivity.cs

using System.Collections.Generic;
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
            //...

            buttonScan.Click += async (sender, e) =>
            {
                var scanner = new MobileBarcodeScanner();

                // สร้าง Barcode options 
                var options = new MobileBarcodeScanningOptions();

                // กำหนด format ที่ต้องการให้ตัวบาร์โค้ดอ่าน
                options.PossibleFormats = new List<ZXing.BarcodeFormat> { ZXing.BarcodeFormat.QR_CODE };

                // สั่งเปิดตัวแสกนด้วย options
                var result = await scanner.Scan(options);

                if(result != null)
                {
                    textBarcodeResult.Text = result.Text;
                    textBarcodeFormat.Text = result.BarcodeFormat.ToString();
                }
            };

        }
        
        //...

    }
}
```

## ไฟล์เต็ม 

```cs
// MainActivity.cs

using System.Collections.Generic;
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
            // Set our view from the "main" layout resource
            SetContentView(Resource.Layout.activity_main);

            var buttonScan = FindViewById<Button>(Resource.Id.buttonScan);
            var textBarcodeResult = FindViewById<TextView>(Resource.Id.textViewBarcodeResult);
            var textBarcodeFormat = FindViewById<TextView>(Resource.Id.textViewBarcodeFormat);

            buttonScan.Click += async (sender, e) =>
            {
                var scanner = new MobileBarcodeScanner();

                var options = new MobileBarcodeScanningOptions();
                options.PossibleFormats = new List<ZXing.BarcodeFormat> { ZXing.BarcodeFormat.QR_CODE };

                var result = await scanner.Scan(options);

                if(result != null)
                {
                    textBarcodeResult.Text = result.Text;
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