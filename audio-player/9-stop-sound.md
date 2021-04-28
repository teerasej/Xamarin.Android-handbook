
# สร้าง event handler สำหรับหยุดไฟล์เสียงและเล่นใหม่ 
- การ stop() ไม่ทำให้ไฟล์เสียงเล่นใหม่ได้ จำเป็นต้อง สร้าง mediaplayer ใหม่ 
- ใช้การจำไฟล์เสียงที่เลือกล่าสุด เพื่อสร้าง mediaplayer ใหม่เมื่อหยุดไฟล์เสียง

```cs
// MainActivity.cs

using Android.App;
using Android.Media;
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

        MediaPlayer player;

        // สร้าง property ไว้ใน activity เพื่อจำไฟล์เสียงที่ถูกเลือก
        int selectedSoundFilePosition;

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
            //...


            spinnerSoundFile.ItemSelected += (sender, e) =>
            {
                var soundFile = this.soundFiles[e.Position];

                player = MediaPlayer.Create(this, soundFile.MediaID);

                // จำไฟล์เสียงเมื่อถูกเลือก
                selectedSoundFilePosition = e.Position;
            };

            buttonPlay.Click += (sender, e) =>
            {
                player.Start();
            };

            buttonPause.Click += (sender, e) =>
            {
                player.Pause();
            };

            buttonStop.Click += (sender, e) =>
            {
                // หลังจากหยุดเล่นเสียงแล้ว เราจะสั่ง reset และ release ไฟล์ออกจาก memory
                player.Stop();
                player.Reset();
                player.Release();

                // ใช้การจำไฟล์เสียงที่เลือกล่าสุด เพื่อสร้าง mediaplayer ใหม่เมื่อหยุดไฟล์เสียง
                player = MediaPlayer.Create(this, this.soundFiles[selectedSoundFilePosition].MediaID);
            };

            spinnerSoundFile.SetSelection(0);
        }
        public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Android.Content.PM.Permission[] grantResults)
        {
            Xamarin.Essentials.Platform.OnRequestPermissionsResult(requestCode, permissions, grantResults);

            base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
        }
    }
}
```

## ไฟล์เต็ม

```cs
// MainActivity.cs

using Android.App;
using Android.Media;
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

        MediaPlayer player;
        int selectedSoundFilePosition;

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


            spinnerSoundFile.ItemSelected += (sender, e) =>
            {
                var soundFile = this.soundFiles[e.Position];

                player = MediaPlayer.Create(this, soundFile.MediaID);
                selectedSoundFilePosition = e.Position;
            };

            buttonPlay.Click += (sender, e) =>
            {
                player.Start();
            };

            buttonPause.Click += (sender, e) =>
            {
                player.Pause();
            };

            buttonStop.Click += (sender, e) =>
            {
                player.Stop();
                player.Reset();
                player.Release();

                player = MediaPlayer.Create(this, this.soundFiles[selectedSoundFilePosition].MediaID);
            };

            spinnerSoundFile.SetSelection(0);
        }
        public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Android.Content.PM.Permission[] grantResults)
        {
            Xamarin.Essentials.Platform.OnRequestPermissionsResult(requestCode, permissions, grantResults);

            base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
        }
    }
}
```