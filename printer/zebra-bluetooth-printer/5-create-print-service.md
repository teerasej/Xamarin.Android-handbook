
# สร้าง Printer Service

```cs
// PrintService.cs

using System;
namespace BluetoothPrinter
{
    public class PrinterService
    {
        // อ้างอิงถึง Activity ในการขอ Permission
        Activity Context;

        // รายชื่ออุปกรณ์ที่แสกนพบ
        List<DiscoveredPrinter> AvailablePrinters;

        public PrinterService(Activity context)
        {
            Context = context;
            AvailablePrinters = new List<DiscoveredPrinter>();
        }
    }
}

```