

# การสร้างไฟล์ APK 

- หากต้องการติดตั้งแอพโดยตรงบนเครื่องเป้าหมาย จากการรันไฟล์ติดตั้ง ควรเลือกวิธีนี้ 

## กำหนดการตั้งค่าบนเครื่องเป้าหมาย

- ปกติระบบ Android จะปิดการติดตั้งไฟล์แอพพลิเคชั่น ที่ไม่ได้ติดตั้งผ่าน Play Store (ก็คือการติดตั้งผ่านไฟล์ APK โดยตรงนี่แหละ)
- เครื่องที่ต้องการติดตั้งผ่านไฟล์ APK ต้องเปิดตัวเลือกใน Setting (การตั้งค่า) ตามภาพ (อาจจะแตกต่างไปตามระบบปฏิบัติการ)

![settings](https://user-images.githubusercontent.com/85179/114735886-cf502980-9d6f-11eb-9b6d-5b4cf7cd9e5b.png)

## การ release โปรเจค (Distribution)

- [การเช็คค่าต่างๆ ก่อนการ distribute ตัวแอพ](before-build.md)

จะแบ่งเป็น 2 ขั้นตอน

1. การ archive โปรเจค
2. การ sign แอพ

### 1. การ archive โปรเจค

![07-archive-for-publishing-sml](https://user-images.githubusercontent.com/85179/114748596-47bce780-9d7c-11eb-8436-a37b80af8bb6.png)

![08-archive-manager-sml](https://user-images.githubusercontent.com/85179/114748611-4986ab00-9d7c-11eb-8825-010f7ff93a53.png)

![09-archive-all-sml](https://user-images.githubusercontent.com/85179/114748626-4d1a3200-9d7c-11eb-96df-49e26fb971e1.png)

![10-launch-archive-manager-sml](https://user-images.githubusercontent.com/85179/114748646-50adb900-9d7c-11eb-8ee2-8f61c0d934de.png)

![11-view-archives-sml](https://user-images.githubusercontent.com/85179/114748665-560b0380-9d7c-11eb-8f02-ffc3e9d76d94.png)

![12-archive-manager-detail-sml](https://user-images.githubusercontent.com/85179/114748703-5e633e80-9d7c-11eb-8def-6ba06637ebb5.png)

![13-distribute-sml](https://user-images.githubusercontent.com/85179/114748749-69b66a00-9d7c-11eb-8aaa-7f2966aa43da.png)

![14-distribution-channel-sml](https://user-images.githubusercontent.com/85179/114748763-6c18c400-9d7c-11eb-8e5b-7da4fd4d93a6.png)

### 2. การ sign แอพ

- แอพที่จะเอาไปใช้งานได้ ต้องมีการ sign แอพด้วย (ลองนึกถึงภาพการประทับตรา หรือเซ็นชื่อเราบนพัศดุที่จะส่งทางไปรษณีย์) 
- การ sign แอพ จะทำโดยใช้ไฟล์ Certificate ซึ่งเราสามารถสร้างขึ้นเองได้

![01-distribution-channel-sml](https://user-images.githubusercontent.com/85179/114748919-94a0be00-9d7c-11eb-9880-7ae702270680.png)

![02-ad-hoc-signing-identity-vs-sml](https://user-images.githubusercontent.com/85179/114748939-99657200-9d7c-11eb-966d-b19de6aa1ade.png)

![03-create-android-key-store-vs-sml](https://user-images.githubusercontent.com/85179/114748944-9c606280-9d7c-11eb-91bb-abc771f44be1.png)


![05-save-as-vs-sml](https://user-images.githubusercontent.com/85179/114748962-a1251680-9d7c-11eb-9ca4-5cb9ed71ff15.png)

![06-save-as-dialog-vs-sml](https://user-images.githubusercontent.com/85179/114748976-a5e9ca80-9d7c-11eb-931c-737e656f553b.png)

![07-signing-password-vs-sml](https://user-images.githubusercontent.com/85179/114748998-ab471500-9d7c-11eb-8655-19b0eaf76867.png)
![08-open-distribution-sml](https://user-images.githubusercontent.com/85179/114749083-c0bc3f00-9d7c-11eb-962c-8fb07cf540e6.png)

