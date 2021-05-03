
# สร้าง Download Service สำหรับดาวน์โหลดไฟล์

- สร้างไฟล์ `DownloadService.cs`

```cs
// DownloadService.cs

using System;
using System.IO;
using System.Net;
using System.Threading.Tasks;


namespace PDFPrinter
{
    public class DownloadService
    {
        public string DestinationPath;
        public WebClient webClient;

        public DownloadService(string destinationPath)
        {
            // กำหนดที่อยู่โฟลเดอร์ภายในแอพสำหรับเก็บไฟล์ที่ดาวน์โหลด
            DestinationPath = destinationPath;
            webClient = new WebClient();
        }

        public async Task<Uri> Download(string targetFileUrl)
        {
            // ดึงชือไฟล์จาก url เป้าหมาย
            var targetFileName = Path.GetFileName(targetFileUrl);

            // สร้างที่อยู่ไฟล์ในแอพ จากการประกอบที่อยู่โฟลเดอร์ เข้ากับชื่อไฟล์
            var localFilePath = Path.Combine(DestinationPath, targetFileName);

            // ดาวน์โหลดไฟล์
            await webClient.DownloadFileTaskAsync(targetFileUrl, localFilePath);

            // เช็คว่ามีไฟล์อยู่จริง และส่งออกเป็น Uri
            if(!File.Exists(localFilePath))
            {
                return new Uri("");
            }
            
            return new Uri(localFilePath);
        }
    }
}

```