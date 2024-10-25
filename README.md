# ตั้งค่า SSH ราย User ให้ใช้ Password กรณี Server ของเราเชื่อมต่อด้วย Public key

เปิดไฟล์ต่อไปนี้
```bash
sudo nano /etc/ssh/sshd_config
```
ค้นหาคำว่า `Match User` ปกติจะอยู่ล่างสุดของไฟล์ตั้งค่า จากนั้นแก้ไขตามด้านล่าง
```bash
Match User [Your Username]
    PasswordAuthentication yes
    PubkeyAuthentication no
```

อธิบาย
- `PasswordAuthentication yes` : กำหนดให้ User ดังกล่าวสามารถใช้ Password ในการ Login ได้
- `PubkeyAuthentication no` : ตั้งค่าให้ user ดังกล่าวไม่ต้องใช้ Public key ในการ Login

จากนั้นทำการ Restart service ด้วยคำสั่ง
```bash
sudo systemctl restart ssh
```
