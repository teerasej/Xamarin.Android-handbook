
# การกำหนด font size กับขนาดหน้าจอที่แตกต่างกัน

- เราสามารถสร้าง `dimens.xml` ไว้ในโฟลเดอร์ `Resources/values` ได้ 
- โดยเราสามารถกำหนด dimension ของค่าต่างๆ ที่เอาไปกำหนดใน Layout ได้อีกที

```xml
<!-- dimens.xml -->
<?xml version="1.0" encoding="UTF-8" ?>
<resources>
    <dimen name="font_size">16sp</dimen>
</resources>
```

```xml
<!-- activity_main.xml -->
<Button
	...
    android:textSize="@dimen/font_size"
/>
```

## การสร้าง dimension สำหรับขนาดหน้าจอต่างๆ 

### A. แบบ preset ขนาดหน้าจอ ของ Android 

- เราสามารถตั้งชื่อโฟลเดอร์ของ resource ต่อท้ายด้วยขนาดหน้าจอต่างๆ ได้ 
  - ***-small** (ช่วงแคบกว่า 320dp)
  - ***-normal** (ช่วง 320dp)
  - ***-large** (ช่วง 480dp)
  - ***-xlarge** (ช่วง 720dp ขึ้นไป)

เช่น 

- Resources/values-small/dimens.xml
- Resources/values-normal/dimens.xml
- Resources/values-large/dimens.xml
- Resources/values-xlarge/dimens.xml

โดย Android จะเป็นตัวที่พิจารณาว่าจะเอา dimens.xml ไฟล์ไหนมาใช้ โดยการวัดจากขนาด

> ตัว Preview อาจไม่สามารถตอบรับการทำงานดังกล่าวได้


### B. แบบกำหนดขนาดเอง 

- เราสามารถตั้งชื่อโฟลเดอร์ของ resource ต่อท้ายด้วยขนาดความกว้างต่างๆ ได้ 
  - Smallest Width
    - ***-sw<N>dp**
    - ค่าความกว้างน้อยสุด ที่ resource นี้จะมีผลใช้งาน
    - การเปลี่ยนแนวการวางอุปกรณ์ จะไม่มีผลเทียบใช้กับค่า Smallest width
    - [ดูเพิ่มเติมได้ที่นี่](https://developer.android.com/guide/topics/resources/providing-resources.html#SmallestScreenWidthQualifier)
  - Available Width
    - ***-w<N>dp**
    - มักใช้กับการ relayout ขนาดใหญ่บน Tablet 
    - ค่าจะถูกเทียบใช้เมื่อมีการเปลี่ยนแนวการถือของอุปกรณ์ (ไม่เหมือน Smallest widget)

เช่น 

- Resources/values-sw600dp/dimens.xml
- Resources/values-sw480dp/dimens.xml

โดย Android จะเป็นตัวที่พิจารณาว่าจะเอา dimens.xml ไฟล์ไหนมาใช้ โดยการวัดจากขนาด

> ตัว Preview อาจไม่สามารถตอบรับการทำงานดังกล่าวได้