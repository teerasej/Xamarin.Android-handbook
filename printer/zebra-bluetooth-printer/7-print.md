
# 

## 1. พิมพ์ข้อมูลตามคำสั่ง ZPL 

```cs
// PrintService.cs 

public async void Print()
{
    await Task.Run(async () => { 
        
        // ถ้า ไม่พบเครื่องปริ้นท์ ให้จบการทำงานของ method
        if (AvailablePrinters.Count == 0)
        {
           return false;
        }

        // ดึงเอา bluetooth address ของเครื่องปริ้นท์
        var availablePrinter = AvailablePrinters[0];
        var printerAddress = availablePrinter.Address;

        // สร้างการเชื่อมต่อ
        Connection connection = new BluetoothConnection(printerAddress);
        
        try
        {
            connection.Open();

            // สั่งส่งข้อมูล zpl ไปทาง connection
            var bytes = Encoding.UTF8.GetBytes("^PON^LH0,0^FWN^XA^FO150,200^FDHelloWorld^FS^XZ");
            connection.Write(bytes);

            // สร้าง thread delay เพื่อให้การส่งข้อมูลเสร็จ
            await Task.Delay(2000);

        }
        catch (ConnectionException e)
        {
            Console.WriteLine(e.ToString());
        }
        catch (ZebraPrinterLanguageUnknownException e)
        {
            Console.WriteLine(e.ToString());
        }
        catch (Exception e)
        {
            Console.WriteLine(e.ToString());
        }
        finally
        {
            connection.Close();
        }
    });
}
```

## 2. ทำงานกับ printer instance 

```cs
// PrintService.cs 

try
{
    connection.Open();

    // สร้าง printer instance จาก connection
    printer = ZebraPrinterFactory.GetInstance(connection);

    // พิมพ์ข้อความตัวอย่าง
    printer.PrintConfigurationLabel();
    //var files = printer.RetrieveFileNames();

    Dictionary<int, string> vars = new Dictionary<int, string>
    {
        //{ 11, "John" }
        //{ 11, "Smith" }
    };

    printer.PrintStoredFormat("E:HELLO2.ZPL", vars, "utf-8");

    await Task.Delay(2000);

}
catch (ConnectionException e)
{
    Console.WriteLine(e.ToString());
}
catch (ZebraPrinterLanguageUnknownException e)
{
    Console.WriteLine(e.ToString());
}
catch (Exception e)
{
    Console.WriteLine(e.ToString());
}
finally
{
    connection.Close();
}
```

## 3. พิมพ์ store format 

```cs
// PrintService.cs 

try
{
    connection.Open();

    // สร้าง printer instance จาก connection
    printer = ZebraPrinterFactory.GetInstance(connection);

    // สร้างตัวแปร โดยระบุตำแหน่ง
    Dictionary<int, string> vars = new Dictionary<int, string>
    {
        //{ 11, "John" }
        //{ 11, "Smith" }
    };

    // ระบุชื่อ template และส่งตัวแปร
    printer.PrintStoredFormat("E:HELLO2.ZPL", vars, "utf-8");

    await Task.Delay(2000);

}
catch (ConnectionException e)
{
    Console.WriteLine(e.ToString());
}
catch (ZebraPrinterLanguageUnknownException e)
{
    Console.WriteLine(e.ToString());
}
catch (Exception e)
{
    Console.WriteLine(e.ToString());
}
finally
{
    connection.Close();
}
```