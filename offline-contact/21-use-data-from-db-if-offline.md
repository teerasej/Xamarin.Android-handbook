
# ใช้ข้อมูล User ล่าสุดจาก database ถ้าไม่ต่ออินเตอร์เน็ต

```cs
// Service/UserService.cs

// ...

namespace RandomUser.Service
{
    public class UserService
    {
        //...

        public async Task<Result[]> PrepareOfflineData()
        {
            var users = new Result[] { };

            var storePath = System.Environment.GetFolderPath(System.Environment.SpecialFolder.LocalApplicationData);

            var dbName = "data.db";
            var dbPath = Path.Combine(storePath, dbName);
            var db = new UserDatabase(dbPath);

            var currentNetwork = Connectivity.NetworkAccess;
            var IsConnected = currentNetwork != Xamarin.Essentials.NetworkAccess.None;
            
            if (IsConnected)
            {
                users = await GetUserProfiles();
                await db.ResetDatabase();
            }
            else
            {
                // ถ้าไม่ได้เชื่อมต่อ ให้โหลดข้อมูลจาก SQLite Database
                users = await db.GetUsersAsync();

                // และคืนข้อมูลกลับไปให้ Activity เลย
                return users;
            }

           //...

            return users;
        }
    }
}
```

## ไฟล์เต็ม

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
            var request = new RestRequest("", DataFormat.Json).AddParameter("results", 200);
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
            var IsConnected = currentNetwork != Xamarin.Essentials.NetworkAccess.None;
            
            if (IsConnected)
            {
                users = await GetUserProfiles();
                await db.ResetDatabase();
            }
            else
            {
                users = await db.GetUsersAsync();

                return users;
            }

            var imageStorePath = storePath;
            webClient = new WebClient();

            foreach (var user in users)
            {
                var imageUri = user.Picture.Large;

                var fileName = Path.GetFileName(imageUri.LocalPath);
                var localImagePath = Path.Combine(imageStorePath, fileName);

                if (localImagePath == null || File.Exists(localImagePath))
                {
                    user.Picture.Large = new Uri(localImagePath);
                    await db.SaveUserAsync(user);
                    continue;
                }


                var bytes = webClient.DownloadData(imageUri);
                File.WriteAllBytes(localImagePath, bytes);

                if (File.Exists(localImagePath))
                {
                    user.Picture.Large = new Uri(localImagePath);
                    await db.SaveUserAsync(user);
                }

            }

            return users;
        }
    }
}
```