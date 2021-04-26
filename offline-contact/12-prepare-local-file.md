
# สร้างส่วนการเตรียมข้อมูลรูปภาพ เก็บไว้ภายในแอพ

- ในที่นี้จะเตรียมรูปภาพที่ต้องแสดงในแอพ โดยใช้วิธีโหลดมาเก็บไว้ในเครื่องก่อน 

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

        // สร้าง method ที่โหลดข้อมูลผู้ใช้ และดาวน์โหลดรูปภาพมาเก็บในแอพก่อนแสดงผล
        public async Task<Result[]> PrepareOfflineData()
        {
            // เริ่มจากโหลดข้อมูล User ก่อน
            var users = await GetUserProfiles();

            // กำหนดที่อยู่สำหรับเก็บรูปภาพไว้ใน LocalApplicationData 
            var imageStorePath = System.Environment.GetFolderPath(System.Environment.SpecialFolder.LocalApplicationData);

            webClient = new WebClient();

            // หลังจากได้ข้อมูลผู้ใช้ทั้งหมดแล้ว ก็เริ่มวนโหลดรูปมาเก็บไว้ในแอพ 
            foreach (var user in users)
            {
                // ใช้ข้อมูลของรูปภาพใหญ่ที่ได้จาก Web API
                var imageUri = user.Picture.Large;

                // ดึงชื่อ และนามสกุลไฟล์ออกมาจาก Url 
                var fileName = Path.GetFileName(imageUri.LocalPath);

                // สร้างที่อยู่ของไฟล์รูปภาพที่จะดาวน์โหลดไว้ในแอพ
                var localImagePath = Path.Combine(imageStorePath, fileName);

                // ถ้ามีไฟล์รูปดังกล่าวอยู่แล้ว ไม่ต้องโหลด ให้กำหนดที่อยู่ไฟล์ในแอพ ใส่ลงไปใน User object แทน
                if (localImagePath == null || File.Exists(localImagePath))
                {
                    user.Picture.Large = new Uri(localImagePath);
                    continue;
                }

                // ดาวน์โหลดไฟล์ด้วย web client 
                var bytes = webClient.DownloadData(imageUri);
                // บันทึกไฟล์
                File.WriteAllBytes(localImagePath, bytes);

                // ถ้าการดาวน์โหลดสมบูรณ์ กำหนดที่อยู่ local ให้กับ user object
                if (File.Exists(localImagePath))
                {
                    user.Picture.Large = new Uri(localImagePath);
                }

            }

            // หลังเสร็จสิ้นการดาวน์โหลดไฟล์รูปภาพ ให้คืนรายการข้อมูลผู้ใช้ออกไปตามปกติ
            return users;
        }
    }
}
```