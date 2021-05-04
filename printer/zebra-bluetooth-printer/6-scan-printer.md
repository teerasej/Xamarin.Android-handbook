

# สร้างกลไกการแสกนหาเครื่องปริ้นท์

## 1. สร้าง handler สำหรับตอบรับผลการค้นหาเครื่อง print 

สร้างไฟล์ **BluetoothDiscoveryHandler.cs**

```cs
// BluetoothDiscoveryHandler.cs
using System;
using System.Collections.Generic;
using Zebra.Sdk.Printer.Discovery;

namespace BluetoothPrinter
{
    public class BluetoothDiscoveryHandler : DiscoveryHandler
    {

        public void DiscoveryError(string message)
        {
            DiscoveryComplete = true;
        }

        public void DiscoveryFinished()
        {
            DiscoveryComplete = true;
        }

        public void FoundPrinter(DiscoveredPrinter printer)
        {
            DiscoveredPrinters.Add(printer);
        }

        public bool DiscoveryComplete { get; private set; } = false;

        public List<DiscoveredPrinter> DiscoveredPrinters { get; } = new List<DiscoveredPrinter>();
    }
}

```

## 2. สร้างกลไกการแสกนอุปกรณ์ Bluetooth ใน Printer Service

```cs
// PrintService.cs

using System;
namespace BluetoothPrinter
{
    public class PrinterService
    {
       
        Activity Context;

        List<DiscoveredPrinter> AvailablePrinters;

        public PrinterService(Activity context)
        {
            Context = context;
            AvailablePrinters = new List<DiscoveredPrinter>();
        }


        public async Task<List<DiscoveredPrinter>> FindAndConnect()
        {
            // สร้างการทำงานแยก Thread
            await Task.Run(() =>
            {
                // เช็คการขอ Permission Bluetooth ในแอพ
                if (ContextCompat.CheckSelfPermission(this.Context, Manifest.Permission.Bluetooth) == (int)Permission.Granted)
                {
                    // สร้าง Handler ที่เตรียมไว้
                    BluetoothDiscoveryHandler discoveryHandler = new BluetoothDiscoveryHandler();

                    // สั่งแสกน
                    BluetoothDiscoverer.FindPrinters(Application.Context, discoveryHandler);

                    // ทำการรัน thread ไว้จนกว่าการแสกนจะเสร็จสมบูรณ์
                    while (!discoveryHandler.DiscoveryComplete)
                    {
                        Thread.Sleep(10);
                    }

                    // เอา printer ที่พบเก็บไว้ใน property
                    this.AvailablePrinters = discoveryHandler.DiscoveredPrinters;

                }
                else
                {
                    ActivityCompat.RequestPermissions(this.Context, new string[] { Manifest.Permission.Bluetooth }, 1);
                }


            });

            return this.AvailablePrinters;
        }
    }
}

```

## 3. 

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
        Button buttonPrint;
        Button buttonDiscoverPrinter;

        // กำหนดใช้งาน printer service
        PrinterService printerService;

        ProgressBar loading;
        TextView textPrinterInfo;


        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(savedInstanceState);
            Xamarin.Essentials.Platform.Init(this, savedInstanceState);
            // Set our view from the "main" layout resource
            SetContentView(Resource.Layout.activity_main);

            buttonPrint = FindViewById<Button>(Resource.Id.buttonPrint);
            buttonDiscoverPrinter = FindViewById<Button>(Resource.Id.buttonDiscoverPrinter);

            loading = FindViewById<ProgressBar>(Resource.Id.loading);
            textPrinterInfo = FindViewById<TextView>(Resource.Id.textPrinterInfo);

            loading.Visibility = ViewStates.Gone;
            textPrinterInfo.Visibility = ViewStates.Gone;

            // สร้าง printer service
            printerService = new PrinterService(this);

            // เริ่มสแกนเมื่อกดปุ่ม
            buttonDiscoverPrinter.Click += async (sender, e) =>
            {
                // แสดงตัวโหลด
                loading.Visibility = ViewStates.Visible;

                // เรียกใช้การแสกน
                var printers = await printerService.FindAndConnect();

                // ซ่อนตัวโหลด
                loading.Visibility = ViewStates.Gone;

                // แสดง toast ถ้าไม่พบปริ้นทเตอร์
                if (printers.Count == 0)
                {
                    Toast.MakeText(
                        Application.Context,
                        "No Printer Found, try again",
                        ToastLength.Short
                        );
                }
                else
                {
                    // แสดงชื่อ และ bluetooth address
                    var printer = printers[0];
                    textPrinterInfo.Text = printer.DiscoveryDataMap["FRIENDLY_NAME"] + " " + printer.Address;
                    textPrinterInfo.Visibility = ViewStates.Visible;
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