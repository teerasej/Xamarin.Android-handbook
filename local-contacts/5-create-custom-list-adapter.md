
# สร้าง ListAdapter สำหรับข้อมูล ContactModel

- เราจะสร้าง class ที่ทำหน้าที่จัดการข้อมูลให้กับ ListView เรียกว่า **List Adapter**
- สามารถทำได้โดยการ extend abstract class ชื่อ `BaseAdapter` และ implement method ที่จำเป็น 
- สามารถกำหนด generic type ได้ด้วย

## 1. สร้าง List Adapter สำหรับ ContactModel

```cs
// ContactModelListAdapter.cs

using System;
using Android.Views;
using Android.Widget;

namespace LocalContact
{
    // สร้าง class, กำหนด generic type และ implement abstract method
    public class ContactModelListAdapter : BaseAdapter<ContactModel>
    {

        public ContactModelListAdapter()
        {
        }

        public override ContactModel this[int position] => throw new NotImplementedException();

        public override int Count => throw new NotImplementedException();

        public override long GetItemId(int position)
        {
            throw new NotImplementedException();
        }

        public override View GetView(int position, View convertView, ViewGroup parent)
        {
            throw new NotImplementedException();
        }
    }
}

```

## 2. Implement การทำงานของ ListAdapter 

- รับ Activity และข้อมูลมาเก็บใช้งาน 
- implement การทำงานต่างๆ

```cs
// ContactModelListAdapter.cs
using System;
using System.Collections.Generic;
using Android.App;
using Android.Views;
using Android.Widget;

namespace LocalContact
{
    public class ContactModelListAdapter : BaseAdapter<ContactModel>
    {
        // สร้าง property สำหรับเก็บข้อมูลใช้งานใน adapter
        ContactModel[] contacts;

        // เก็บใช้งาน Activity เพื่อเข้าถึง view
        Activity context;

        // กำหนด constructor เพื่อรับข้อมูลมาใช้งานใน Adapter
        public ContactModelListAdapter(Activity context, ContactModel[] contacts)
        {
            this.context = context;
            this.contacts = contacts;
        }

        // implement การคืนค่าเป็น ContactModel ถ้าได้รับเลข position
        public override ContactModel this[int position] => this.contacts[position];

        // implement การคืนค่าเป็นจำนวนของข้อมูล
        public override int Count => this.contacts.Length;

        // implement การคืนค่าเลข unique id
        // ในที่นี้เราคืนเป็นเลข position แต่กรณีอื่นก็สามารถคืนค่าเป็นค่าเลขอื่นได้ เช่น id ของสินค้า หรือของข้อมูล
        public override long GetItemId(int position)
        {
            return position;
        }

        public override View GetView(int position, View convertView, ViewGroup parent)
        {
            // ใช้ View ที่สร้างอยู่แล้ว (ถ้ามี) จะเกิดขึ้นในกรณีที่ข้อมูลของ ListView กินพื้นที่เกินหน้าจอ
            View view = convertView; 

            // ถ้าไม่มีให้สร้าง View ขึ้นมาจาก Layout ไฟล์ที่เตรียมไว้
            if (view == null) 
                view = context.LayoutInflater.Inflate(Resource.Layout.list_item_contact, null);
            
            // กำหนดค่าลงไปใน View ที่เตรียมไว้ ผ่าน id ที่ตั้ง
            view.FindViewById<TextView>(Resource.Id.textName).Text = contacts[position].Name;
            view.FindViewById<TextView>(Resource.Id.textPhoneNumber).Text = contacts[position].PhoneNumber;
            
            return view;
        }
    }
}

```