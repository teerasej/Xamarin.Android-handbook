
# สร้าง UserService เพื่อแยกส่วนติดต่อกับ Web API

- สร้างไฟล์ `Service/UserService.cs`


```cs
// Service/UserService.cs

using System;
using System.Threading.Tasks;
using RestSharp;
using RandomUser.Model;

namespace RandomUser.Service
{
    public class UserService
    {
        // ใช้ RestClient ของ RestSharp
        private RestClient Client;

        // กำหนด BaseURL ของ Web API
        private string BaseUrl = "https://randomuser.me/api/";

        public UserService()
        {
            this.Client = new RestClient(this.BaseUrl);
        }

        // กำหนด method ให้ทำงานแบบ Async ด้วย Task
        public async Task<Result[]> GetUserProfiles()
        {
            // ส่ง request พร้อม parameter เพื่อกำหนดจำนวน user
            var request = new RestRequest("", DataFormat.Json).AddParameter("results", 50);
            var response = await Client.ExecuteAsync(request);

            // แปลง JSON ที่ได้จาก response เป็น class ที่เตรียมไว้
            var userModel = UserRemoteModel.FromJson(response.Content);

            // คืนค่าออกไปเฉพาะ Array ของข้อมูล User ดูโครงใน UserRemoteModel ได้
            return userModel.Results;
        }
    }
}
```