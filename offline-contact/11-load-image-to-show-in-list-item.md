

# โหลดรูปภาพจาก url มาแสดงใน image view

- การแสดงรูปภาพใน ImageView จะใช้ instance ของ Class Bitmap ใน `Android.Graphic`
- เราจึงต้องดาวน์โหลดไฟล์มาเป็น byte array แล้วแปลงเป็น Bitmap 
- **ตอนทดสอบจะสังเกตได้ว่า** มีรูปภาพแสดงจริง แต่จะมีอาการหน่วงหรือกระตุกบ้าง เพราะกดไกการโหลดจะทำซ้ำทุกครั้งที่มีการ render list item

```cs

// Service/UserProfileListAdapter.cs

using System;
using System.Net;
using Android.App;
using Android.Graphics;
using Android.Views;
using Android.Widget;
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

            // โหลดข้อมูลเป็น Bitmap Image
            var bitmapImage = GetImageBitmapFromUrl(user.Picture.Large.AbsoluteUri);

            // นำ Bitmap มาแสดงใน ImageView
            view.FindViewById<ImageView>(Resource.Id.imageUserProfile).SetImageBitmap(bitmapImage);

            return view;
        }

        private Bitmap GetImageBitmapFromUrl(string url)
        {
            Bitmap imageBitmap = null;

            // ใช้ WebClient ในการโหลดข้อมูลเป็น bitmap
            using (var webClient = new WebClient())
            {
                // ดาวน์โหลดไฟล์รูปภาพแล้ว จะได้เป็น Byte Array
                var imageBytes = webClient.DownloadData(url);
                if (imageBytes != null && imageBytes.Length > 0)
                {
                    // แปลง Byte Array เป็น Bitmap
                    imageBitmap = BitmapFactory.DecodeByteArray(imageBytes, 0, imageBytes.Length);
                }
            }

            return imageBitmap;
        }
    }
}
```