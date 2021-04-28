
# สร้าง layout และ adapter สำหรับ spinner

ส่วนนี้จะมี 3 ขั้นตอน

## 1. สร้างไฟล์ Layout สำหรับ spinner item

สร้างไฟล์ `Resources/layout/spinner_item_sound.xml` 

```xml
<!-- Resources/layout/spinner_item_sound.xml -->
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    >

    <!-- 
        ข้อความสำหรับแสดงชื่อไฟล์เสียง 
        android:padding="10sp"
		android:id="@+id/textSoundFileName"
    -->
	<TextView
		android:text="Large Text"
		android:textAppearance="?android:attr/textAppearanceLarge"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:minWidth="25px"
		android:minHeight="25px"
		android:padding="10sp"
		android:id="@+id/textSoundFileName" />

</LinearLayout>

```

## 2. สร้าง Adapter 

สร้างไฟล์​ `SoundFileAdapter.cs`

```cs
// SoundFileAdapter.cs
using System;
using Android.App;
using Android.Views;
using Android.Widget;

namespace AudioPlayer
{
    public class SoundFileAdapter : BaseAdapter<SoundFileModel>
    {
        Activity context;
        SoundFileModel[] soundFiles;

        public SoundFileAdapter(Activity context, SoundFileModel[] soundFiles)
        {
            this.context = context;
            this.soundFiles = soundFiles;
        }

        public override SoundFileModel this[int position] => this.soundFiles[position];

        public override int Count => this.soundFiles.Length;

        public override long GetItemId(int position)
        {
            return position;
        }

        public override View GetView(int position, View convertView, ViewGroup parent)
        {
            var view = convertView;

            // สร้าง View จากไฟล์ Layout 
            if(view == null)
            {
                view = context.LayoutInflater.Inflate(Resource.Layout.spinner_item_sound, null);
            }

            // ดึงข้อมูลไฟล์เสียงตามลำดับ position ที่จะแสดงขึ้นใน spinner
            var soundFile = this.soundFiles[position];

            // แสดงชื่อไฟล์เสียง
            view.FindViewById<TextView>(Resource.Id.textSoundFileName).Text = soundFile.Name;

            return view;
        }
    }
}

```

## 3. กำหนด Adapter ให้กับ Spinner 


```cs
// MainActivity.cs

// ...

namespace AudioPlayer
{
    [Activity(Label = "@string/app_name", Theme = "@style/AppTheme", MainLauncher = true)]
    public class MainActivity : AppCompatActivity
    {
        //...

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
            
            // กำหนด adapter ให้กับ spinner เพื่อแสดงรายการชื่อไฟล์เสียง
            spinnerSoundFile.Adapter = new SoundFileAdapter(this, soundFiles);

        }
        //....
    }
}
```


### ไฟล์เต็ม

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

            spinnerSoundFile.Adapter = new SoundFileAdapter(this, soundFiles);

        }
        public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Android.Content.PM.Permission[] grantResults)
        {
            Xamarin.Essentials.Platform.OnRequestPermissionsResult(requestCode, permissions, grantResults);

            base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
        }
    }
}
```