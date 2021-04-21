
# สร้างข้อมูลผู้ติดต่อ

## 1. สร้าง class เป็นตัวแทนของข้อมูลผู้ติดต่อ

```cs
// ContactModel.cs
using System;
namespace LocalContact
{
    public class ContactModel
    {
        public string Name { get; set; }
        public string PhoneNumber { get; set; }

        public ContactModel(string name, string phoneNumber)
        {
            this.Name = name;
            this.PhoneNumber = phoneNumber;
        }
    }
}

```

## 2. สร้าง Array ของชุดรายการข้อมูลผู้ติดต่อ

```cs
// MainActivity.cs

using Android.App;
using Android.OS;
using Android.Runtime;
using Android.Widget;
using AndroidX.AppCompat.App;

namespace LocalContact
{
    [Activity(Label = "@string/app_name", Theme = "@style/AppTheme", MainLauncher = true)]
    public class MainActivity : AppCompatActivity
    {
        // สร้าง Array ของชุดรายการข้อมูลผู้ติดต่อ
        private ContactModel[] contacts = new ContactModel[]
        {
            new ContactModel("Nextflow", "083-071-3373"),
            new ContactModel("Steve", "083-071-3373"),
            new ContactModel("Tony", "083-071-3373"),
            new ContactModel("Peter", "083-071-3373")
        };


        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(savedInstanceState);
            Xamarin.Essentials.Platform.Init(this, savedInstanceState);
            
            SetContentView(Resource.Layout.activity_main);

            var listView = FindViewById<ListView>(Resource.Id.listViewContact);
        }
        public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Android.Content.PM.Permission[] grantResults)
        {
            Xamarin.Essentials.Platform.OnRequestPermissionsResult(requestCode, permissions, grantResults);

            base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
        }
    }
}
```