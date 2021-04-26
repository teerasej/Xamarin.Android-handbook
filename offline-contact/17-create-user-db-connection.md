

# สร้าง class สำหรับเชื่อมต่อและจัดการ database

สร้างไฟล์ `Model/UserDatabase.cs`

```cs
// Model/UserDatabase.cs

using System;
using SQLite;

namespace RandomUser.Model
{
    public class UserDatabase
    {
        // ใช้ในการเชื่อมต่อ และรัน SQL ต่างๆ 
        readonly SQLiteAsyncConnection database;

        public UserDatabase(string dbPath)
        {
            // ต้องการที่อยู่สำหรับสร้างและเชื่อมต่อไฟล์ database
            database = new SQLiteAsyncConnection(dbPath);

            // สร้าง Table จาก Class UserDBModel โดยจะทำการอ่านค่า property มากำหนดเป็น table 
            // .wait() คือให้โค้ดรอกระบวนการนี้จนเสร็จถึงทำงานต่อ ใช้ในกรณีที่ต้องการให้ Async ทำงานแบบ Sync
            database.CreateTableAsync<UserDBModel>().Wait();
        }
    }
}

```