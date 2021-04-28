

# สร้าง Class ตัวแทนของไฟล์เสียงสำหรับใช้แสดงบนแอพ

## 1. สร้างไฟล์ `SoundFileModel.cs`

```cs
// SoundFileModel.cs

using System;
namespace AudioPlayer
{
    public class SoundFileModel
    {
        public string Name { get; set; }
        public int MediaID { get; set; }
        

        public SoundFileModel()
        {
        }
    }
}
```

## 2. กำหนดข้อมูลไฟล์เสียงไว้ใน MainActivity ด้วย Resource Id

```cs
// MainActivity.cs

using Android.App;
using Android.OS;
using Android.Runtime;
using Android.Widget;
using AndroidX.AppCompat.App;

namespace AudioPlayer
{
    [Activity(Label = "@string/app_name", Theme = "@style/AppTheme", MainLauncher = true)]
    public class MainActivity : AppCompatActivity
    {
        Spinner spinnerSoundFile;
        Button buttonPlay;
        Button buttonPause;
        Button buttonStop;

        // สร้าง Array ของไฟล์เสียง โดยกำหนดค่าของ Resource Id ที่เรานำไฟล์เสียงไปใส่ไว้ใน folder raw
        private SoundFileModel[] soundFiles = new SoundFileModel[]
        {
            new SoundFileModel
            {
                Name = "Spring Field",
                MediaID = Resource.Raw.spring_field
            },
            new SoundFileModel
            {
                Name = "Sunset Dream",
                MediaID = Resource.Raw.sunset_dream
            }
        };

        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(savedInstanceState);
            Xamarin.Essentials.Platform.Init(this, savedInstanceState);

            SetContentView(Resource.Layout.activity_main);

            spinnerSoundFile = FindViewById<Spinner>(Resource.Id.spinnerSoundFile);
            buttonPlay = FindViewById<Button>(Resource.Id.buttonPlay);
            buttonPause = FindViewById<Button>(Resource.Id.buttonPause);
            buttonStop = FindViewById<Button>(Resource.Id.buttonStop);

        }
        //..
    }
}
```

## ไฟล์เต็ม

```cs
using Android.App;
using Android.OS;
using Android.Runtime;
using Android.Widget;
using AndroidX.AppCompat.App;

namespace AudioPlayer
{
    [Activity(Label = "@string/app_name", Theme = "@style/AppTheme", MainLauncher = true)]
    public class MainActivity : AppCompatActivity
    {
        Spinner spinnerSoundFile;
        Button buttonPlay;
        Button buttonPause;
        Button buttonStop;

        private SoundFileModel[] soundFiles = new SoundFileModel[]
        {
            new SoundFileModel
            {
                Name = "Spring Field",
                MediaID = Resource.Raw.spring_field
            },
            new SoundFileModel
            {
                Name = "Sunset Dream",
                MediaID = Resource.Raw.sunset_dream
            }
        };

        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(savedInstanceState);
            Xamarin.Essentials.Platform.Init(this, savedInstanceState);

            SetContentView(Resource.Layout.activity_main);

            spinnerSoundFile = FindViewById<Spinner>(Resource.Id.spinnerSoundFile);
            buttonPlay = FindViewById<Button>(Resource.Id.buttonPlay);
            buttonPause = FindViewById<Button>(Resource.Id.buttonPause);
            buttonStop = FindViewById<Button>(Resource.Id.buttonStop);

        }
        public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Android.Content.PM.Permission[] grantResults)
        {
            Xamarin.Essentials.Platform.OnRequestPermissionsResult(requestCode, permissions, grantResults);

            base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
        }
    }
}
```