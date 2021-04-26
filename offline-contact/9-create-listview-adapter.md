

# สร้าง User Profile Adapter สำหรับ ListView

- สร้างไฟล์ `Service/UserProfileListAdapter.cs`

```cs
// Service/UserProfileListAdapter.cs

using System;
using Android.App;
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
            // Reuse View ซ้ำ ถ้าเป็นไปได้
            var view = convertView;

            // ถ้ายังไม่มี View ให้ Re-use ก็สร้างใหม่จาก Layout list_item_user_profile.xml
            if (view == null)
            {
                view = context.LayoutInflater.Inflate(Resource.Layout.list_item_user_profile, null);
            }

            // ดึงข้อมูลผู้ใช้จาก Array โดยอิงกับตำแหน่งของ List item
            var user = this.users[position];

            // สร้างชื่อเต็ม และกำหนดให้กับ TextView
            var fullName = user.Name.First + " " + user.Name.Last;
            view.FindViewById<TextView>(Resource.Id.textFullName).Text = fullName;

            // กำหนดข้อมูลเบอร์โทรศัพท์ ให้กับ TextView
            view.FindViewById<TextView>(Resource.Id.textPhoneNumber).Text = user.Phone;

            return view;
        }
    }
}
```