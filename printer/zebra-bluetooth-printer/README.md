
- Enable Bluetooth Classic อย่าใช้ LE เพราะไม่เพียงพอต่อการเชื่อมต่อกับอุปกรณ์มือถือ

กำหนดให้ เครื่องปริ้นท์ทำงานแบบ continous mode (ใช้กับกระดาษสลิป) และยาว 400 dot

```zpl
^XA^MNN^LL300^XZ^XA^JUS^XZ
```


^CI28 กำหนดให้เป็น UTF-8

ดูไฟล์ทั้งหมดบน drive E บน printer
```
! U1 do "file.dir" "E:"
```

กำหนด font size 
```
^CFA,20
```