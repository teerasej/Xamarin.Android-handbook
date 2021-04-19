
# กำหนดผลลัพธ์ให้แสดงบนหน้าจอ

```cs
// ResultActivity.cs
using Android.App;
using Android.OS;
using Android.Widget;
using AndroidX.AppCompat.App;

namespace CalculatorApp
{
    [Activity(Label = "ResultActivity", ParentActivity = typeof(MainActivity))]
    public class ResultActivity : AppCompatActivity
    {
        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(savedInstanceState);
            SetContentView(Resource.Layout.activity_result);
           
             // Create เรียกใช้ค่าที่เก็บไว้ใน intent 
             // ในที่นี้ต้องมีการกำหนดค่าเริ่มต้น ในกรณีที่ไม่สามารถหาชื่อข้อมูลใน intent ได้
            var result = Intent.GetIntExtra("result", 0);

            // เรียกใช้ TextView ผ่าน Id
            var txtResult = FindViewById<TextView>(Resource.Id.txtResult);

            // กำหนดค่าแสดงใน TextView
            txtResult.Text = result.ToString();
        }
    }
}
```