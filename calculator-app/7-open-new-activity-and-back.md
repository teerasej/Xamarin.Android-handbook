
# การเปิด Activity ใหม่ และการใช้งานปุ่ม Back


## 1. สร้าง Intent เพื่อเริ่มการทำงานของ Activity ใหม่

```cs
// MainActivity.cs

namespace CalculatorApp
{
    [Activity(Label = "@string/app_name", Theme = "@style/AppTheme", MainLauncher = true)]
    public class MainActivity : AppCompatActivity
    {
        protected override void OnCreate(Bundle savedInstanceState)
        {
            //...    

            buttonCalcualte.Click += (sender, e) =>
            {
                var first = inputFirst.Text;
                var second = inputSecond.Text;
                Toast toast;

                if (string.IsNullOrEmpty(first) || string.IsNullOrEmpty(second))
                {
                    toast = Toast.MakeText(Application.Context, "ข้อมูลยังกรอกไม่ครบ", ToastLength.Short);
                    toast.Show();
                    return;
                }

                try
                {
                    var firstNum = int.Parse(first);
                    var secondNum = int.Parse(second);

                    var result = firstNum + secondNum;

                    // ไม่ใช้การแสดงผลลัพท์ใน toast แล้ว
                    //toast = Toast.MakeText(Application.Context, "ผลลัพธ์: " + result.ToString(), ToastLength.Short);
                    //toast.Show();

                    // สร้าง intent ใหม่ และกำหนด activity ที่ต้องการเป็นเป้าหมาย
                    Intent intent = new Intent(this, typeof(ResultActivity));

                    // ใช้ extra เป็น string ลงไปใน intent
                    intent.PutExtra("result", result);

                    // สั่งเริ่ม Activity จาก Intent ที่กำหนด
                    StartActivity(intent);

                }
                catch (System.Exception ex)
                {
                    toast = Toast.MakeText(Application.Context, "ข้อมูลไม่สามารถนำมาคำนวนได้", ToastLength.Short);
                    toast.Show();
                    return;
                }

              

            };
        }

        //..
    
    }
}
```

## 2. กำหนด parent activity เพื่อสร้างกลไกปุ่ม Back


```cs
// ResultActivity.cs

    // ใส่ Parent เพื่อแสดง และกำหนดเป้าหมายของปุ่ม Back
    [Activity(Label = "ResultActivity", ParentActivity = typeof(MainActivity))]
    public class ResultActivity : AppCompatActivity
    {
        protected override void OnCreate(Bundle savedInstanceState)
```