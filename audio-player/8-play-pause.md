
# เพิ่ม event handler สำหรับการเล่น และหยุดเพลง

```cs
// MainActivity.cs

//...

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
            
            //....


            spinnerSoundFile.ItemSelected += (sender, e) =>
            {
                var soundFile = this.soundFiles[e.Position];

                player = MediaPlayer.Create(this, soundFile.MediaID);
            };
            
            // สร้าง event handler ให้กับปุ่มเล่นเสียง
            buttonPlay.Click += (sender, e) =>
            {
                player.Start();
            };

            // สร้าง event handler ให้กับปุ่มหยุดเล่นเสียงชั่วคราว
            buttonPause.Click += (sender, e) =>
            {
                player.Pause();
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
            };

            buttonPlay.Click += (sender, e) =>
            {
                player.Start();
            };

            buttonPause.Click += (sender, e) =>
            {
                player.Pause();
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