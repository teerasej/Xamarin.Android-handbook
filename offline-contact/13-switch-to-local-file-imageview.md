
# ดึงที่อยู่รูปภาพจากในแอพพลิเคชั่น แทนจาก server เพื่อใช้ใน List Item

- จากการเปลี่ยนแปลงใน UserService ทำให้ที่อยู่ของไฟล์รูปภาพของผู้ใช้ เป็นที่อยู่อ้างอิงจากภายในแอพแทน
- เราจึงจะสลับการทำงานจากแบบโหลดไฟล์จาก Server มาใช้ไฟล์รูปภาพที่ดาวน์โหลดไว้แทน


```cs
// Service/UserProfileListAdapter.cs

using System;
using System.Net;
using Android.App;
using Android.Graphics;
using Android.Views;
using Android.Widget;
using Java.IO;
using Result = RandomUser.Model.Result;

namespace RandomUser
{
    public class UserProfileListAdapter : BaseAdapter<Result>
    {
        //...

        public override View GetView(int position, View convertView, ViewGroup parent)
        {
            var view = convertView;

            if (view == null)
            {
                view = context.LayoutInflater.Inflate(Resource.Layout.list_item_user_profile, null);
            }

            var user = this.users[position];

            var fullName = user.Name.First + " " + user.Name.Last;
            view.FindViewById<TextView>(Resource.Id.textFullName).Text = fullName;

            view.FindViewById<TextView>(Resource.Id.textPhoneNumber).Text = user.Phone;

            // ไม่ใช้ที่อยู่ไฟล์จาก server เนื่องจากมีความช้า
            //var bitmapImage = GetImageBitmapFromUrl(user.Picture.Large.AbsoluteUri);

            // ใช้ bitmap ที่สร้างจากที่อยู่ไฟล์ในแอพแทน
            var bitmapImage = GetImageBitmapFromFilePath(user.Picture.Large);
            view.FindViewById<ImageView>(Resource.Id.imageUserProfile).SetImageBitmap(bitmapImage);

            return view;
        }

        private Bitmap GetImageBitmapFromUrl(string url)
        {
           //...
        }


        // ใช้ที่อยู่ไฟล์รูปภาพในแอพ สร้าง Bitmap instance
        private Bitmap GetImageBitmapFromFilePath(Uri pathUri)
        {
            File imgFile = new File(pathUri.AbsolutePath);

            if (imgFile.Exists())
            {

                Bitmap bitmap = BitmapFactory.DecodeFile(imgFile.AbsolutePath);
                return bitmap;
            }

            return null;
        }
    }
}
```


## ไฟล์เต็ม 

```cs
// Service/UserProfileListAdapter.cs

using System;
using System.Net;
using Android.App;
using Android.Graphics;
using Android.Views;
using Android.Widget;
using Java.IO;
using Result = RandomUser.Model.Result;

namespace RandomUser
{
    public class UserProfileListAdapter : BaseAdapter<Result>
    {
        private Result[] users;
        private Activity context;

        public UserProfileListAdapter(Activity context, Result[] users)
        {
            this.users = users;
            this.context = context;
        }

        public override Result this[int position] => this.users[position];

        public override int Count => this.users.Length;

        public override long GetItemId(int position)
        {
            return position;
        }

        public override View GetView(int position, View convertView, ViewGroup parent)
        {
            var view = convertView;

            if (view == null)
            {
                view = context.LayoutInflater.Inflate(Resource.Layout.list_item_user_profile, null);
            }

            var user = this.users[position];

            var fullName = user.Name.First + " " + user.Name.Last;
            view.FindViewById<TextView>(Resource.Id.textFullName).Text = fullName;

            view.FindViewById<TextView>(Resource.Id.textPhoneNumber).Text = user.Phone;

            //var bitmapImage = GetImageBitmapFromUrl(user.Picture.Large.AbsoluteUri);
            var bitmapImage = GetImageBitmapFromFilePath(user.Picture.Large);
            view.FindViewById<ImageView>(Resource.Id.imageUserProfile).SetImageBitmap(bitmapImage);

            return view;
        }

        private Bitmap GetImageBitmapFromUrl(string url)
        {
            Bitmap imageBitmap = null;

            using (var webClient = new WebClient())
            {
                var imageBytes = webClient.DownloadData(url);
                if (imageBytes != null && imageBytes.Length > 0)
                {
                    imageBitmap = BitmapFactory.DecodeByteArray(imageBytes, 0, imageBytes.Length);
                }
            }

            return imageBitmap;
        }

        private Bitmap GetImageBitmapFromFilePath(Uri pathUri)
        {
            File imgFile = new File(pathUri.AbsolutePath);

            if (imgFile.Exists())
            {

                Bitmap bitmap = BitmapFactory.DecodeFile(imgFile.AbsolutePath);
                return bitmap;
            }

            return null;
        }
    }
}
```

