
# สร้างคำสั่งโหลดข้อมูล User 

- เขียน sql query และโหลดข้อมูลมาแปลงเป็น Array 
- ข้อมูลจาก Database จะถูกแปลงเป็น object ของ Result class


```cs
// Model/UserDatabase.cs

using System;
using System.Collections.Generic;
using System.Threading.Tasks;
using SQLite;

namespace RandomUser.Model
{
    public class UserDatabase
    {
        //...

        public async Task<Result[]> GetUsersAsync()
        {
            var results = new List<Result>();
            
            // สำหรับต้องการดูจำนวน record ในฐานข้อมูล
            //var count = await database.Table<UserDBModel>().CountAsync();
            
            // เขียน sql query และโหลดข้อมูลมาแปลงเป็น Array 
            var usersFromDB = await database.QueryAsync<UserDBModel>("SELECT * FROM users");

            // ข้อมูลจาก Database จะถูกแปลงเป็น object ของ Result class
            UserDBModel user;
            for (int i = 0; i < usersFromDB.Count; i++)
            {
                user = usersFromDB[i];
                results.Add(user.GenerateUserResultIntance());
            }

            return results.ToArray();
        }
    }
}

```



## ไฟล์เต็ม

```cs
// Model/UserDatabase.cs

using System;
using System.Collections.Generic;
using System.Threading.Tasks;
using SQLite;

namespace RandomUser.Model
{
    public class UserDatabase
    {
        readonly SQLiteAsyncConnection database;

        public UserDatabase(string dbPath)
        {
            database = new SQLiteAsyncConnection(dbPath);
            database.CreateTableAsync<UserDBModel>().Wait();
        }

        public async Task<bool> ResetDatabase()
        {
            await database.DropTableAsync<UserDBModel>();
            await database.CreateTableAsync<UserDBModel>();
            return true;
        }

        public Task<int> SaveUserAsync(Result userRemoteData)
        {
            var userToDB = new UserDBModel();
            userToDB.ApplyDataFromRemoteModel(userRemoteData);

            if (userToDB.Id != 0)
            {
                return database.UpdateAsync(userToDB);
            }
            else
            {
                return database.InsertAsync(userToDB);
            }
        }

        public async Task<Result[]> GetUsersAsync()
        {
            var results = new List<Result>();
            //var count = await database.Table<UserDBModel>().CountAsync();
            var usersFromDB = await database.QueryAsync<UserDBModel>("SELECT * FROM users");

            UserDBModel user;
            for (int i = 0; i < usersFromDB.Count; i++)
            {
                user = usersFromDB[i];
                results.Add(user.GenerateUserResultIntance());
            }

            return results.ToArray();
        }
    }
}

```