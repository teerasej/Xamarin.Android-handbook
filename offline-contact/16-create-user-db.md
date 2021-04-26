

# สร้าง Class ตัวแทนของข้อมูล User ใน Database

- กำหนด property ด้วย tag `[Table]` เพื่อกำหนดชื่อ Database โดยตรง
- กำหนด property ด้วย tag `[PrimaryKey]` และ `[AutoIncrement]`
- กำหนด column คู่กับ property ต่างๆ 
- สร้าง method สำหรับโหลดข้อมูลจาก Web API มาใส่

```cs

using System;
using SQLite;

namespace RandomUser.Model
{
    // กำหนด property ด้วย tag [Table] เพื่อกำหนดชื่อ Database โดยตรง
    [Table("users")]
    public class UserDBModel
    {
        // กำหนด property ด้วย tag [PrimaryKey] และ [AutoIncrement]
        [PrimaryKey, AutoIncrement]
        public int Id { get; set; }

        // กำหนด column คู่กับ property ต่างๆ 
        [Column("first_name")]
        public string FirstName { get; set; }

        [Column("last_name")]
        public string LastName { get; set; }

        [Column("phone_number")]
        public string PhoneNumber { get; set; }

        [Column("email")]
        public string Email { get; set; }

        [Column("image_path")]
        public string ImagePath { get; set; }

        public UserDBModel()
        {
        }

        // สร้าง method สำหรับโหลดข้อมูลจาก Web API มาใส่
        public void ApplyDataFromRemoteModel(Result result)
        {
            this.FirstName = result.Name.First;
            this.LastName = result.Name.Last;

            this.PhoneNumber = result.Phone;
            this.Email = result.Email;

            this.ImagePath = result.Picture.Large.AbsoluteUri;
        }
    }
}

```