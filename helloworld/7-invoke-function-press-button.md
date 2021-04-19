
# เรียกใช้ function เมื่อปุ่มถูกกด

- สร้าง function event เมื่อปุ่มถูกกด
- จะทำค่าที่ได้จาก input มาใส่ใน `TextView`

```cs
// MainActivity.cs

protected override void OnCreate(Bundle savedInstanceState)
{
    base.OnCreate(savedInstanceState);
    Xamarin.Essentials.Platform.Init(this, savedInstanceState);
    SetContentView(Resource.Layout.activity_main);

    EditText textName = FindViewById<EditText>(Resource.Id.inputName);
    TextView textResult = FindViewById<TextView>(Resource.Id.txtResult);
    Button buttonHello = FindViewById<Button>(Resource.Id.buttonHello);

    // สร้าง function สำหรับ Click event 
    buttonHello.Click += (sender, e) =>
    {
        // ดึงค่าที่กรอกใน EditText View มาแสดงใน TextView
        textResult.Text = "Hello, " + textName.Text;
    };
}
```

## เคลียร์ข้อความใน EditText View เมื่อกรอกข้อความเสร็จแล้ว

```cs
// MainActivity.cs

buttonHello.Click += (sender, e) =>
{
    textResult.Text = "Hello, " + textName.Text;

    // เคลียร์ข้อความ
    textName.Text = "";
};
```