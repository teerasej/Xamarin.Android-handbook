
# เปลี่ยนข้อความด้วยตัวเองขณะรันแอพ

```cs

// MainActivity.cs

using Android.App;
using Android.Content.Res;
using Android.OS;
using Android.Runtime;
using Android.Widget;
using AndroidX.AppCompat.App;
using Java.Util;

namespace multilanguage
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

            // เรียกใช้งาน button
            var buttonSwitchLanguage = FindViewById<Button>(Resource.Id.buttonSwitchLanguage);

            // เรียกใช้งาน TextView
            var textHello = FindViewById<TextView>(Resource.Id.textHello);

            buttonSwitchLanguage.Click += (sender, e) =>
            {
                // กำหนดโค้ดภาษา
                var languageCode = "th";

                // เรียกใช้ configuration เดิมจาก context
                Configuration overrideConfiguration = this.Resources.Configuration;

                // สร้าง locale
                Locale locale = new Locale(languageCode);
                // กำหนด locale ให้กับ configuration
                overrideConfiguration.SetLocale(locale);

                // สร้าง context ใหม่ จาก configuration ที่เรากำหนดภาษา
                var context = CreateConfigurationContext(overrideConfiguration);

                // ดึง string ออกมาจาก context ที่สร้างขึ้น และกำหนดให้กับ View
                var stringHello = context.GetString(Resource.String.hello);
                textHello.Text = stringHello;

                var stringButton = context.GetString(Resource.String.button_text_change_langauge);
                buttonSwitchLanguage.Text = stringButton;
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