
# แสดงข้อความเตือนแบบเล็กๆ ถ้าไม่มีการกรอกข้อมูล

- ในที่นี้ เราจะแสดง toast ถ้าไม่ได้กรอกข้อความลงไปในช่อง

```cs
// MainActivity.cs 

buttonHello.Click += (sender, e) =>
{
    // เช็คว่าค่าใน EditText widget เป็นข้อความว่างหรือไม่
    if(textName.Text == string.Empty)
    {
        // สร้างตัวแปร toast และแสดง
        var toast = Toast.MakeText(Application.Context, "กรอกชื่อก่อน", ToastLength.Short);
        toast.Show();

        // จบการทำงานของ function ด้วยคำสั่ง return
        return;
    }

    textResult.Text = "Hello, " + textName.Text;
    textName.Text = "";
};
```