

# Zebra Bluetooth Printer 

ดาวน์โหลดไฟล์ตัวอย่าง: [Archive.zip](https://github.com/teerasej/Xamarin.Android-handbook/files/6425214/Archive.zip)

1. [ติดตั้งโปรแกรมที่จำเป็น](1-setup-sdk.md)
2. [สร้างโปรเจค, ติดตั้ง package และเปิด Permission](2-create-project.md)
3. [สร้าง Layout](3-create-layout.md)
4. [เรียกใช้ View ผ่าน Activity](4-access-view.md)
5. [สร้าง Print Service](5-create-print-service.md)
6. [แสกนและค้นหาเครื่องปริ้นท์](6-scan-printer.md)
7. [ส่งข้อมูลไปพิมพ์ที่เครื่องปริ้นท์](7-print.md)

## Note

- สำหรับการเชื่อมต่อกับอุปกรณ์ Android ให้**ตั้งค่าการเชื่อมต่อ Bluetooth เป็นแบบ Classic อย่าใช้ LE (Low Energy)** เพราะไม่เพียงพอต่อการเชื่อมต่อกับอุปกรณ์มือถือ
- เราสามารถกำหนดให้ เครื่องปริ้นท์ทำงานแบบ continous mode (ใช้กับกระดาษสลิป) และยาว 400 dot

```zpl
^XA^MNN^LL300^XZ^XA^JUS^XZ
```
- คำสั่งดูไฟล์ทั้งหมดบน drive E บน printer
```
! U1 do "file.dir" "E:"
```
- ศึกษาการเขียนภาษา ZPL ได้เพิ่มเติมได้จาก [Zpl Programming Guide](https://www.zebra.com/content/dam/zebra_new_ia/en-us/manuals/printers/common/programming/zpl-zbi2-pm-en.pdf)
