
# เข้าถึง View ด้วย id ที่กำหนด จากภายในโค้ดโปรแกรม

จากการกำหนด id ในไฟล์ layout เราสามารถเขียนอ้างอิงถึง View ดังกล่าว เพื่อใช้ในการทำงานของเราได้

```cs
// MainActivity.cs
using Android.App;
using Android.OS;
using Android.Runtime;

// อ้างอิง Class View จาก namespace 
using Android.View;

using AndroidX.AppCompat.App;

namespace HelloAndroid
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

            // เข้าถึง View แต่ละประเภทด้วย Resource.Id.<ชื่อ View>
            EditText textName = FindViewById<EditText>(Resource.Id.inputName);
            TextView textResult = FindViewById<TextView>(Resource.Id.txtResult);
            Button buttonHello = FindViewById<Button>(Resource.Id.buttonHello);

           
        }


        public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Android.Content.PM.Permission[] grantResults)
        {
            Xamarin.Essentials.Platform.OnRequestPermissionsResult(requestCode, permissions, grantResults);

            base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
        }
    }
}

```