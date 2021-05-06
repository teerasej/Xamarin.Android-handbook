
# มีคียบอร์ดที่กดได้จริงๆ ไหม? 

เราสามารถเช็คว่า Context กำลังทำงานกับอุปกรณ์ที่มี keyboard หรือไม่ ด้วยโค้ดต่อไปนี้

```cs
private bool isHardwareKeyboardAvailable(Activity context) 
{
    return context.Resources.Configuration.Keyboard != KeyboardType.Nokeys;
}
```

นอกจาก Nokeys แล้ว ยังเทียบเช็คประเภทของ Keyboard ได้ด้วย

- `KeyboardType.Twelvekey`
- `KeyboardType.Qwerty`

