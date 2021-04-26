
# ตรวจเช็คสถานะการเชื่อมต่อ

- ดูเพิ่มเติมเรื่องการเช็คสถานะการเชื่อมต่อของแอพได้ที่ [Xamarin.Essentials](https://docs.microsoft.com/en-us/xamarin/essentials/connectivity?tabs=android)
- ต้องไปเปิด Permission ชื่อ **Access Network State** ใน Project Options ด้วย (AndroidManifest.xml) ด้วย

# ไฟล์เต็ม

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

            // ดึงสถานะการเชื่อมต่อปัจจุบัน
            var currentNetwork = Connectivity.NetworkAccess;

            // เทียบว่าถ้าค่าไม่เท่ากับ None แปลว่ามีการเชื่อมต่ออยู่ 
            // จริงๆ มีสถานะอื่นอีก ดูเพิ่มเติมได้ที่ https://docs.microsoft.com/en-us/xamarin/essentials/connectivity?tabs=android
            var IsConnected = currentNetwork != Xamarin.Essentials.NetworkAccess.None;

            // ถ้าเชื่อมต่ออินเตอร์เน็ต ให้ดึงข้อมูลใหม่จาก Server ทุกครั้ง
            if(IsConnected)
            {
                users = await GetUserProfiles();
            }
            else
            {
                // ถ้าไม่ได้เชื่อมต่อ ให้โหลดข้อมูลจาก SQLite Database

                // และคืนข้อมูลกลับไปให้ Activity เลย
            }

            

            var imageStorePath = System.Environment.GetFolderPath(System.Environment.SpecialFolder.LocalApplicationData);

            webClient = new WebClient();

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

            return users;
        }
    }
}
```