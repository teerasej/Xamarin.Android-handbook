
# ทิ้งข้อมูลที่โหลดเก็บไว้ ถ้ามีการเรียกข้อมูลใหม่ 


## 1. สร้าง method ที่ drop table ทิ้ง 

```cs
// Model/UserDatabase.cs

using System;
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
        
        // ทำการ drop และสร้าง table ขึ้นใหม่
        public async Task<bool> ResetDatabase()
        {
            await database.DropTableAsync<UserDBModel>();
            await database.CreateTableAsync<UserDBModel>();
            return true;
        }
    }
}

```

## 2. ปรับ UserService ให้ทำงานกับกลไกใน Database

- แก้ให้ใช้ path เดียวกันกับการเก็บรูปภาพ และไฟล์ database    
- ถ้ามีการโหลดข้อมูลใหม่ จะเคลียร์ของเก่าทิ้ง

```cs
// Service/UserService.cs

//...
namespace RandomUser.Service
{
    public class UserService
    {

       //...

        public async Task<Result[]> PrepareOfflineData()
        {
            var users = new Result[] { };

            // ประกาศตัวแปรสำหรับใช้เป็นที่อยู่อ้างอิงสำหรับไฟล์รูปภาพ และไฟล์ SQLite
            var storePath = System.Environment.GetFolderPath(System.Environment.SpecialFolder.LocalApplicationData);

            // กำหนดชื่อไฟล์ database
            var dbName = "data.db";
            // สร้าง path ที่อยู่ไฟล์ database
            var dbPath = Path.Combine(storePath, dbName);

            // สร้าง instance สำหรับทำงานกับ database
            var db = new UserDatabase(dbPath);

            var currentNetwork = Connectivity.NetworkAccess;
            var IsConnected = currentNetwork != Xamarin.Essentials.NetworkAccess.None;

            if(IsConnected)
            {
                users = await GetUserProfiles();

                // Reset ฐานข้อมูล User ถ้ามีการโหลดข้อมูลมาใหม่
                await db.ResetDatabase();
            }
            else
            {
                // ถ้าไม่ได้เชื่อมต่อ ให้โหลดข้อมูลจาก SQLite Database

                // และคืนข้อมูลกลับไปให้ Activity เลย
            }

            // var imageStorePath = System.Environment.GetFolderPath(System.Environment.SpecialFolder.LocalApplicationData);
            // เปลี่ยนมาใช้ที่อยู่โฟลเดอร์เดียวกับไฟล์ SQLite 
            var imageStorePath = storePath;
            webClient = new WebClient();

            foreach (var user in users)
            {
                var imageUri = user.Picture.Large;

                //...

            }

          
            return users;
        }
    }
}
```

### ไฟล์เต็ม

```cs
// Service/UserService.cs

using System;
using System.Threading.Tasks;
using RestSharp;
using RandomUser.Model;
using System.Net;
using Android.App;
using System.IO;
using Result = RandomUser.Model.Result;
using Xamarin.Essentials;

namespace RandomUser.Service
{
    public class UserService
    {

        private RestClient Client;
        private string BaseUrl = "https://randomuser.me/api/";
        WebClient webClient;

        public UserService()
        {
            this.Client = new RestClient(this.BaseUrl);
        }

        public async Task<Result[]> GetUserProfiles()
        {
            var request = new RestRequest("", DataFormat.Json).AddParameter("results", 100);
            var response = await Client.ExecuteAsync(request);
            var userModel = UserRemoteModel.FromJson(response.Content);
            return userModel.Results;
        }

        public async Task<Result[]> PrepareOfflineData()
        {
            var users = new Result[] { };

            var storePath = System.Environment.GetFolderPath(System.Environment.SpecialFolder.LocalApplicationData);

            var dbName = "data.db";
            var dbPath = Path.Combine(storePath, dbName);
            var db = new UserDatabase(dbPath);

            var currentNetwork = Connectivity.NetworkAccess;

            if(currentNetwork != Xamarin.Essentials.NetworkAccess.None)
            {
                users = await GetUserProfiles();
                await db.ResetDatabase();
            }
            else
            {
               // ถ้าไม่ได้เชื่อมต่อ ให้โหลดข้อมูลจาก SQLite Database

                // และคืนข้อมูลกลับไปให้ Activity เลย
            }

            var imageStorePath = storePath;
            webClient = new WebClient();

            // loop through users list to download their's profile
            foreach (var user in users)
            {
                var imageUri = user.Picture.Large;

                var fileName = Path.GetFileName(imageUri.LocalPath);
                var localImagePath = Path.Combine(imageStorePath, fileName);

                if (localImagePath == null || File.Exists(localImagePath))
                {
                    user.Picture.Large = new Uri(localImagePath);
                    continue;
                }


                var bytes = webClient.DownloadData(imageUri);
                File.WriteAllBytes(localImagePath, bytes);

                if (File.Exists(localImagePath))
                {
                    user.Picture.Large = new Uri(localImagePath);
                }

            }

            // after finish download image file, save its paths, and user's info to db

            // show user's info and image profile from database in listview

            return users;
        }
    }
}
```