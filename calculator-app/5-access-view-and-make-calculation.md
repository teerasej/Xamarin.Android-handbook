
# รับค่า และทำการคำนวน

## 1. เข้าถึง Views ผ่าน Id และเก็บไว้ในตัวแปร

```cs
// MainActivity.cs

using Android.App;
using Android.OS;
using Android.Runtime;
using Android.Widget;
using AndroidX.AppCompat.App;

namespace CalculatorApp
{
    [Activity(Label = "@string/app_name", Theme = "@style/AppTheme", MainLauncher = true)]
    public class MainActivity : AppCompatActivity
    {
        protected override void OnCreate(Bundle savedInstanceState)
        {
            base.OnCreate(savedInstanceState);
            Xamarin.Essentials.Platform.Init(this, savedInstanceState);
            
            SetContentView(Resource.Layout.activity_main);


            // เข้าถึง View ต่างๆ ที่ตั้งชื่อ Id ไว้ 
            var inputFirst = FindViewById<EditText>(Resource.Id.inputFirst);
            var inputSecond = FindViewById<EditText>(Resource.Id.inputSecond);
            var buttonCalcualte = FindViewById<Button>(Resource.Id.button_calculate);

            // สร้าง event สำหรับตอนปุ่มถูกกด
            buttonCalcualte.Click += (sender, e) =>
            {
                var first = inputFirst.Text;
                var second = inputFirst.Text;
                Toast toast;

                // เช็คค่าว่าง 
                if (string.IsNullOrEmpty(first) || string.IsNullOrEmpty(second))
                {
                    // ถ้าไม่มีการกรอกค่า ให้แสดงคำเตือน
                    toast = Toast.MakeText(Application.Context, "ข้อมูลยังกรอกไม่ครบ", ToastLength.Short);
                    toast.Show();
                    return;
                }

                try
                {
                    // ทำการแปลงข้อความเป็นตัวเลข
                    var firstNum = int.Parse(first);
                    var secondNum = int.Parse(second);

                    var result = firstNum + secondNum;

                    toast = Toast.MakeText(Application.Context, "ผลลัพธ์: " + result.ToString(), ToastLength.Short);
                    toast.Show();

                }
                catch (System.Exception ex)
                {
                    // หากแปลงค่าไม่ได้ จะเป็น Exception เราจะแสดงเป็นคำเตือน
                    toast = Toast.MakeText(Application.Context, "ข้อมูลไม่สามารถนำมาคำนวนได้", ToastLength.Short);
                    toast.Show();
                    return;
                }
            };


        }
        public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Android.Content.PM.Permission[] grantResults)
        {
            Xamarin.Essentials.Platform.OnRequestPermissionsResult(requestCode, permissions, grantResults);

            base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
        }
    }
}
```

## 2. 