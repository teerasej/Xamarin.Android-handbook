
# Distribute แอพจากโปรเจคใน Visual Studio

เริ่มต้นหลังจาก[ขั้นตอนการ Archive](../build-apk.md#1-การ-archive-โปรเจค) ให้กดเลือก Google Play

![01-distribution-channel-sml](https://user-images.githubusercontent.com/85179/115046620-e030a480-9f01-11eb-9104-a2dc12790d6a.png)

ในขั้นตอน Signing Identity ให้เลือกไฟล์ key store ที่สร้างไว้[จากขั้นตอนนี้](../build-apk.md#2-การสร้างไฟล์-key-store)
จากนั้นกดปุ่ม continue

![02-select-identity-sml](https://user-images.githubusercontent.com/85179/115046643-e6268580-9f01-11eb-9ad7-0f83abc4bdfa.png)

ในขั้นตอน Google Play Account ให้กดปุ่มเพิ่มบัญชีใหม่

![03-google-play-accounts-sml](https://user-images.githubusercontent.com/85179/115046651-e888df80-9f01-11eb-8acf-e872e4642715.png)

จะปรากฎหน้าต่าง Register Google API Access

![04-register-google-api-access-sml](https://user-images.githubusercontent.com/85179/115046657-eaeb3980-9f01-11eb-8bd2-a39da68ce02b.png)

กรอกชื่อ และ Client ID และ Client Secret ที่เราได้จาก[การสร้าง Credentials](create-credential-on-google-play-console.md)

![05-enter-client-id-and-secret-sml](https://user-images.githubusercontent.com/85179/115046667-ec1c6680-9f01-11eb-9099-25ecd23e2be0.png)

จะเป็นการเปิดหน้าเว็บขึ้นมา ให้เรากดปุ่ม **Allow** เพื่ออนุญาตการเชื่อมต่อ

![06-authorize-app-sml](https://user-images.githubusercontent.com/85179/115046673-ede62a00-9f01-11eb-8c97-541a41bcf733.png)
