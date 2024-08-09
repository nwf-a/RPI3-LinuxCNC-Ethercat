## INSTALL OS

### RASPBERRY OS

To run a Raspberry Pi, an operating system (OS) is required, and one of the commonly used OSes is the Raspberry Pi OS.

(Source: <https://www.raspberrypi.com/software/>)

(Document: <https://www.raspberrypi.com/documentation/computers/os.html>)

1. Install Raspberry Pi Imager

   Windows: <https://downloads.raspberrypi.org/imager/imager_latest.exe>

   macOS: <https://downloads.raspberrypi.org/imager/imager_latest.dmg>

   Ubuntu: <https://downloads.raspberrypi.org/imager/imager_latest_amd64.deb>

2. After downloading and installing the Raspberry Pi Imager, proceed to install the Raspberry Pi OS using the Raspberry Pi Imager

   * Open `Raspberry Pi Imager`, select the `Raspberry Pi Device` you are using, choose the `Operating System` you want to install, and select the `Storage` device (SD Card) you will use.
   ![alt text](<Image/Raspberry Pi Imager.png>)

   * Then click NEXT, and a pop-up window will appear as shown below:
   ![alt text](<Image/Klik Next.png>)

   If you don't want to customize the OS immediately, click `NO`. You can make these customizations later via the desktop after the OS is installed.

   * If you want to customize the settings, click `EDIT SETTINGS` and configure the desired options.
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

   Once you have completed the settings, click `SAVE`.

   * Next, click `YES` to start the installation.
   ![alt text](<Image/OS setting.png>)

   * A pop-up will then appear indicating that all data on the SD card will be erased. Click `YES`.
   ![alt text](<Image/data erased.png>)

   * The installation process takes approximately 20 minutes
   ![alt text](Image/writing.png)
   ![alt text](Image/selesai.png)

   * Once the process is complete, remove the SD card and insert it into your Raspberry Pi. Connect the monitor, keyboard, and mouse to the Raspberry Pi. Then, plug in the power adapter to turn on the Raspberry Pi.
   ![alt text](<Image/Setup Raspberry Pi.jpg>)

   * Next, proceed with updating the system.

   ```bash
   sudo apt update
   sudo apt full-upgrade
   ```
