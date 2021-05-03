
# ดาวน์โหลดไฟล์มาไว้ในเครื่อง และเปิดการทำงานของปุ่มที่เหลือ

```cs
// MainActivity.cs

using System;
using System.IO;
using Android.App;
using Android.OS;
using Android.Runtime;
using Android.Widget;
using AndroidX.AppCompat.App;

namespace PDFPrinter
{
    [Activity(Label = "@string/app_name", Theme = "@style/AppTheme", MainLauncher = true)]
    public class MainActivity : AppCompatActivity
    {
        Button buttonDownloadPDF;
        Button buttonViewPDF;
        Button buttonPrintPDF;

        // สร้าง property สำหรับอ้างอิงไฟล์ pdf ในเครื่อง
        Uri localPDFFile;

        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(savedInstanceState);
            Xamarin.Essentials.Platform.Init(this, savedInstanceState);
            SetContentView(Resource.Layout.activity_main);

            buttonDownloadPDF = FindViewById<Button>(Resource.Id.buttonDownloadPDF);
            buttonViewPDF = FindViewById<Button>(Resource.Id.buttonViewPDF);
            buttonPrintPDF = FindViewById<Button>(Resource.Id.buttonPrintPDF);

            buttonViewPDF.Enabled = false;
            buttonPrintPDF.Enabled = false;

            // สร้าง event handler สำหรับรันคำสั่งดาวน์โหลดไฟล์
            buttonDownloadPDF.Click += async (sender, e) =>
            {
                var targetFileUrl = "https://www.nextflow.in.th/demo/xamarin-android/files/flutter.pdf";

                // เรียกใช้ที่อยู่ของโฟลเดอร์ ภายในแอพพลิเคชั่น
                var localAppDataFolderPath = System.Environment.GetFolderPath(System.Environment.SpecialFolder.LocalApplicationData);

                // กำหนดที่อยู่โฟลเดอร์สำหรับไฟล์ที่ดาวน์โหลด และเริ่มดาวน์โหลด
                var downloader = new DownloadService(localAppDataFolderPath);
                localPDFFile = await downloader.Download(targetFileUrl);

                // เปิดการใช้งานของปุ่มที่เหลือ 
                buttonViewPDF.Enabled = true;
                buttonPrintPDF.Enabled = true;
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