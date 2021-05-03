
# สร้าง Activity สำหรับแสดงไฟล์ PDF

## สร้าง Layout 

สร้างไฟล์ **Resources/layout/activity_viewer.xml**

```xml
<!-- Resources/layout/activity_viewer.xml-->

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    >
    <Syncfusion.SfPdfViewer.Android.SfPdfViewer
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:id="@+id/pdfViewer" />
</LinearLayout>

```

## สร้าง Activity 

สร้างไฟล์ **PDFViewerActivity.cs**

```cs
// PDFViewerActivity.cs

using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;

using Android.App;
using Android.Content;
using Android.OS;
using Android.Runtime;
using Android.Views;
using Android.Widget;
using AndroidX.AppCompat.App;
using Syncfusion.SfPdfViewer.Android;

namespace PDFPrinter
{  
    // กำหนด label และ Activity ต้นทาง
    [Activity(Label = "Preview", ParentActivity = typeof(MainActivity))]
    public class PDFViewerActivity : AppCompatActivity
    {
        SfPdfViewer pdfViewer;
        Stream stream;

        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(savedInstanceState);


            // กำหนด Layout 
            SetContentView(Resource.Layout.activity_viewer);

            // เข้าถึง pdfViewer View
            pdfViewer = FindViewById<SfPdfViewer>(Resource.Id.pdfViewer);

            // เรียกใช้ที่อยู่ไฟล์ PDF ในเครื่องจาก Intent
            var pdfFilePath = Intent.GetStringExtra("path");

            // แสดงไฟล์ PDF จากไฟล์ stream
            stream = File.Open(pdfFilePath, FileMode.Open);
            pdfViewer.LoadDocument(stream);

        }

        public override bool OnOptionsItemSelected(IMenuItem item)
        {
            Finish();
            return true;
        }

        public override void OnBackPressed()
        {
            Finish();
        }

        protected override void OnDestroy()
        {
            base.OnDestroy();
            stream.Dispose();
        }

    } 
}

```