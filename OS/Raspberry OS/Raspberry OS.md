# Catatan

## INSTALL OS

### RASPBERRY OS

Untuk menjalankan Raspberry Pi, diperlukan sebuah OS dan salah satu yang sering digunakan adalah OS dari Raspberry.

(Source: <https://www.raspberrypi.com/software/>)

(Document: <https://www.raspberrypi.com/documentation/computers/os.html>)

1. Install Raspberry Pi Imager

   Windows: <https://downloads.raspberrypi.org/imager/imager_latest.exe>

   macOS: <https://downloads.raspberrypi.org/imager/imager_latest.dmg>

   Ubuntu: <https://downloads.raspberrypi.org/imager/imager_latest_amd64.deb>

2. Setelah download dan install Raspberry Pi Imager, selanjutnya adalah menginstal Raspberry OS menggunakan Raspberry Pi Imager

   * Buka `Raspberry Pi Imager`, Pilih `Raspberry Pi Device` yang digunakan, tentukan `Operating System` yang ingin diinstall, dan Pilih Storage (SD Card) yang akan digunakan!
   ![alt text](<Image/Raspberry Pi Imager.png>)

   * Kemudian klik `NEXT`, akan muncul pop up seperti di bawah
   ![alt text](<Image/Klik Next.png>)

   Kalau tidak ingin melakukan pengaturan OS, klik `NO`, pengaturan bisa dilakukan nanti melalui desktop setelah OS terinstall

   * Jika ingin melakukan kustomasi, klik `EDIT SETTINGS` dan lakukan pengaturan yang diinginkan
   ![alt text](Image/general.png)

   ```text
   GENERAL
   ├── Set hostname: raspberrypi
   ├── Set username and password
   |   └── Username: pi3
   |   └── Password: 123456 
   ├── Configure wireless LAN
   |   └── SSID: DBE
   |   └── Password: dieselcimanggis
   |   └── Wireless LAN country: ID
   └── Set locale settings
       └── Time zone: Asia/Jakarta
       └── Keyboard layout: us
   ```

   Jika sudah selesai setting, maka klik `SAVE`

   * Selanjutnya, klik `YES` untuk memulai instalasi
   ![alt text](<Image/OS setting.png>)

   * Selanjutnya akan ada pop-up yang menyatakan data di SD Card akan dihapus, klik `YES`
   ![alt text](<Image/data erased.png>)

   * Proses instalasi berlangsung &pm; 20 menit
   ![alt text](Image/writing.png)
   ![alt text](Image/selesai.png)

   * Setelah selesai maka lepaskan SD Card dan masukkan SD Card ke Raspberry Pi. Hubungkan layar, keyboard, dan mouse pada raspberry pi. lalu hubungkan adapter dayanya untuk menyalakan Raspberry Pi
   ![alt text](<Image/Setup Raspberry Pi.jpg>)

   * Selanjutnya lakukan update

   ```bash
   sudo apt update
   sudo apt full-upgrade
   ```
