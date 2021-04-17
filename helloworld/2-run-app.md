

# การรันทดสอบแอพพลิเคชั่น บน Simulator และ อุปกรณ์จริง

## การเตรียมอุปกรณ์จริงสำหรับทดสอบแอพ

- ปลดล๊อค Developer Option ได้จาก[ขั้นตอนใน Blog ของ Nextflow](https://nextflow.in.th/2014/enable-android-developer-option/)
- หากมีปัญหาไม่พบ USB Driver สามารถ[ใช้ ADB Driver ค้นหาและติดตั้ง](https://adbdriver.com/downloads/)ให้ได้

## การสร้างและรัน Simulator 

เราสามารถเปิด Android Device Manager เพื่อจัดการ Emulator ได้ 

<img width="591" alt="2021-04-17_14-26-15" src="https://user-images.githubusercontent.com/85179/115105566-00a44180-9f8a-11eb-84b0-835b72082e5e.png">



### รายละเอียดของ Android Device Manager 

<img width="1009" alt="2021-04-17_14-26-53" src="https://user-images.githubusercontent.com/85179/115105569-0732b900-9f8a-11eb-9374-410b71b21c0d.png">


1. สามารถเลือกสร้าง Emulator ใหม่ได้จากปุ่ม **New**
2. หากต้องการปรับแต่ง Emulator ให้เลือกจากรายการด้านล่าง และกด **Edit**
3. สามารถรัน Emulator ที่ต้องการได้ จากการกดปุ่ม **Start**

### Note 

- การรัน Emulator จะมีการใช้ทรัพยากรของเครื่องคอมพิวเตอร์ที่ใช้งานอยู่ทั้ง CPU และ Ram แนะนำว่าหากทำได้ ให้รันทดสอบแอพบนอุปกรณ์จริงจะสะดวกกว่า
- **การรัน Emulator สำเร็จหรือไม่นั้น ขึ้นอยู่กับการตั้งค่าพื้นฐานของคอมพิวเตอร์เครื่องนั้นด้วย** ซึ่งการตั้งค่าบางอย่าง อาจจะมีผลให้ไม่สามารถรัน Emulator ได้สำเร็จ

## การรันทดสอบแอพ

หากมีการรัน Emulator หรือเชื่อมต่ออุปกรณ์เข้ากับคอมพิวเตอร์ได้เรียบร้อย จะปรากฎชื่อขึ้นมาในรายการ Target 

สามารถเลือกเป้าหมายในการทดสอบจากรายการ และกดปุ่มรันทดสอบได้เลย 

<img width="583" alt="2021-04-17_14-32-50" src="https://user-images.githubusercontent.com/85179/115105574-0dc13080-9f8a-11eb-9c19-bd95fc4d725e.png">


