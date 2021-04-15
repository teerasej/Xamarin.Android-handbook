

# การสร้างไฟล์ APK 

- หากต้องการติดตั้งแอพโดยตรงบนเครื่องเป้าหมาย จากการรันไฟล์ติดตั้ง ควรเลือกวิธีนี้ 
- หากต้องการนำไฟล์ขึ้น Google Play Store ให้ดำเนินการ [archive โปรเจค](#1-การ-archive-โปรเจค)ให้เรียบร้อยก่อน จากนั้นค่อยเริ่ม[ขั้นตอนการสร้างไฟล์สำหรับ Google Play Store (AAB)](build-aab.md)

## กำหนดการตั้งค่าบนเครื่องเป้าหมาย

- ปกติระบบ Android จะปิดการติดตั้งไฟล์แอพพลิเคชั่น ที่ไม่ได้ติดตั้งผ่าน Google Play Store (ก็คือการติดตั้งผ่านไฟล์ APK โดยตรงนี่แหละ)
- เครื่องที่ต้องการติดตั้งผ่านไฟล์ APK ต้องเปิดตัวเลือกใน Setting (การตั้งค่า) ตามภาพ (อาจจะแตกต่างไปตามระบบปฏิบัติการ)

![settings](https://user-images.githubusercontent.com/85179/114735886-cf502980-9d6f-11eb-9b6d-5b4cf7cd9e5b.png)

## การไฟล์ APK (Ad hoc Distribution)

- [การเช็คค่าต่างๆ ก่อนการ distribute ตัวแอพ](before-build.md)

จะแบ่งเป็น 2 ขั้นตอน

1. การ archive โปรเจค
2. การสร้างไฟล์ Key Store
3. การ sign แอพ

### 1. การ archive โปรเจค

- ก่อนจะสร้างไฟล์ APK หรือ AAB เราจำเป็นต้องสั่ง Archive โปรเจคเสียก่อน เพื่อให้โปรเจคอยู่ในสภาพที่เตรียมการทุกอย่างพร้อมสำหรับการ distribution
- ลองนึกภาพเราทำกับข้าวเสร็จแล้ว จะส่งให้ลูกค้า ต้องจัดแจงเตรียมลงกล่อง เช็คความเรียบร้อย 

1. เริ่มจาก set configuration ของโปรเจค จาก debug เป็น release 
2. คลิกขวาที่โปรเจค และเลือก Archive 

![07-archive-for-publishing-sml](https://user-images.githubusercontent.com/85179/114748596-47bce780-9d7c-11eb-8436-a37b80af8bb6.png)

3. จะเป็นการเปิด Archive Manager ขึ้นมา และมีการ build โปรเจคเพื่อสร้าง Archive

![08-archive-manager-sml](https://user-images.githubusercontent.com/85179/114748611-4986ab00-9d7c-11eb-8825-010f7ff93a53.png)

สามารถเลือก **Archive All** ได้ ถ้าคลิกขวาที่ Solution

![09-archive-all-sml](https://user-images.githubusercontent.com/85179/114748626-4d1a3200-9d7c-11eb-96df-49e26fb971e1.png)

เราสามารถเปิด Archive Manager ได้โดยตรงจากเมนู **Tools > Archive Manager**

![10-launch-archive-manager-sml](https://user-images.githubusercontent.com/85179/114748646-50adb900-9d7c-11eb-8ee2-8f61c0d934de.png)

และสามารถดู Archives ที่สร้างไว้ก่อนหน้านี้ ได้จากการคลิกขวาที่ Solution และเลือก **View Archives**

![11-view-archives-sml](https://user-images.githubusercontent.com/85179/114748665-560b0380-9d7c-11eb-8f02-ffc3e9d76d94.png)

4. เนื้อที่ใน Archive Manager จะมี 3 ส่วน

   - ส่วนสีฟ้า คือ **Solution List** เพื่อจำแนก archive ที่แยกตาม solution ที่ใช้งาน
   - ส่วนสีแดง คือ **Archive List** แสดง archive ทั้งหมดจาก solution ที่เลือก
   - ส่วนสีเขียว คือ **Detail Panel** แสดงรายละเอียดของ archive ที่ถูกเลือก

![12-archive-manager-detail-sml](https://user-images.githubusercontent.com/85179/114748703-5e633e80-9d7c-11eb-8def-6ba06637ebb5.png)

5. สามารถเลือก archive ที่ต้องการ และกดปุ่ม distibute เพื่อเริ่มดำเนินการสร้างไฟล์

![13-distribute-sml](https://user-images.githubusercontent.com/85179/114748749-69b66a00-9d7c-11eb-8aaa-7f2966aa43da.png)

6. จะขึ้นหน้าจอให้เลือกประเภทการ distibute 

   - แบบ Ad hoc จะเป็นการสร้างไฟล์ APK
   - แบบ Google Play จะเป็นการสร้างไฟล์ AAB และอัพขึ้น Store [ดูต่อได้ที่นี่](build-aab.md)

![14-distribution-channel-sml](https://user-images.githubusercontent.com/85179/114748763-6c18c400-9d7c-11eb-8e5b-7da4fd4d93a6.png)

### 2. การสร้างไฟล์ Key Store

- แอพที่จะเอาไปใช้งานได้ ต้องมีการ sign แอพด้วย (ลองนึกถึงภาพการประทับตรา หรือเซ็นชื่อเราบนพัศดุที่จะส่งทางไปรษณีย์) 
- การ sign แอพ จะทำโดยใช้ไฟล์ Certificate หรืออีกชื่อคือ Key Store ซึ่งเราสามารถสร้างขึ้นเองได้

> หากต้องการสร้างไฟล์ สำหรับ Google Play Store ให้ทำตาม[ขั้นตอนการสร้างไฟล์สำหรับ Google Play Store (AAB)](build-aab.md)

ในที่นี้เราจะเลือกแบบ Ad Hoc

![01-distribution-channel-sml](https://user-images.githubusercontent.com/85179/114748919-94a0be00-9d7c-11eb-9880-7ae702270680.png)

จะปรากฎส่วน Signin Identity ขึ้นมา ถ้าเรามีไฟล์ Key Store Certificate เดิมสามารถกดปุ่ม import ได้ 

![02-ad-hoc-signing-identity-vs-sml](https://user-images.githubusercontent.com/85179/114748939-99657200-9d7c-11eb-966d-b19de6aa1ade.png)

ถ้ายังไม่มีกดปุ่ม + ได้เลย จะเข้าสู่ขั้นตอนการกรอกข้อมูลสำหรับการสร้าง Key store

![03-create-android-key-store-vs-sml](https://user-images.githubusercontent.com/85179/114748944-9c606280-9d7c-11eb-91bb-abc771f44be1.png)


เสร็จแล้ว Visual Studio จะสร้างไฟล์ Key store ขึ้นมาให้ และเก็บในโฟลเดอร์ด้านล่าง

```
# โดยปกติโฟลเดอร์ AppData จะถูกซ่อนไว้ อย่าลืมไปเปิดตัวเลือกแสดงไฟล์และโฟลเดอร์ที่ซ่อนไว้ใน File Explorer

C:\Users\USERNAME\AppData\Local\Xamarin\Mono for Android\Keystore\ALIAS\ALIAS.keystore
```

### 3. การ sign app

ส่วนไฟล์ Key Store ที่สร้างเสร็จแล้ว หรือที่สร้างไว้ใช้งานก่อนหน้านี้ จะอยู่ในรายการด้านล่าง

![05-save-as-vs-sml](https://user-images.githubusercontent.com/85179/114748962-a1251680-9d7c-11eb-9ca4-5cb9ed71ff15.png)


เราสามารถกดปุ่ม Save as เพื่อระบุชื่อและที่อยู่ของไฟล์ APK ที่ถูกสร้างขึ้นมา

![06-save-as-dialog-vs-sml](https://user-images.githubusercontent.com/85179/114748976-a5e9ca80-9d7c-11eb-931c-737e656f553b.png)

หลังจากกดปุ่ม Save แล้วจะมีการให้กรอกรหัสของไฟล์ Key Store

![07-signing-password-vs-sml](https://user-images.githubusercontent.com/85179/114748998-ab471500-9d7c-11eb-8655-19b0eaf76867.png)

ถ้าการทำงานเสร็จสมบูรณ์ จะสามารถเลือกเปิดไปที่ไฟล์ APK ที่ถูกสร้างไว้ได้

![08-open-distribution-sml](https://user-images.githubusercontent.com/85179/114749083-c0bc3f00-9d7c-11eb-962c-8fb07cf540e6.png)

