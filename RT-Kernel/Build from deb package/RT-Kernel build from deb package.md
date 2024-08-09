### INSTALLING THE KERNEL FROM A DEBIAN PACKAGE (RASPBERRY OS)

(Source: <https://github.com/kdoren/linux/releases/tag/rpi_6.1.54-rt15>)

The following steps will guide you through installing the rt-kernel:

1. Create a folder to download the kernel:

    ```bash
    mkdir ~/kernel-download
    ```

2. Navigate to the created folder:

    ```bash
    cd ~/kernel-download
    ```

3. Download the rt-kernel image and headers. The rt-kernel is required to run LinuxCNC, and the headers are necessary for installing EtherCAT

   Kernel:

   ```bash
   wget https://github.com/kdoren/linux/releases/download/rpi_6.1.54-rt15/linux-image-6.1.54-rt15-v7l+_6.1.54-1_armhf.deb
   ```

   Header:

   ```bash
   wget https://github.com/kdoren/linux/releases/download/rpi_6.1.54-rt15/linux-headers-6.1.54-rt15-v7l+_6.1.54-1_armhf.deb
   ```

4. Install the package

   ```bash
   sudo su
   apt install ./linux-image-6.1.54-rt15-v7l+_6.1.54-1_armhf.deb
   ```

5. Set the bash variable `KERN`

   ```bash
   KERN=6.1.54-rt15-v7l+
   ```

6. Next, execute the following command by copying and pasting it into the terminal

   ```bash
   KERNDIR=/boot/$KERN
   CONFDIR=/boot
   [[ -d /boot/firmware ]] && KERNDIR=/boot/firmware/$KERN && CONFDIR=/boot/firmware
   mkdir -p /$KERNDIR/
   cp -dr /usr/lib/linux-image-$KERN/* /$KERNDIR/
   mv $KERNDIR/overlays $KERNDIR/o
   [[ -d /usr/lib/linux-image-$KERN/broadcom ]] && cp -d /usr/lib/linux-image-$KERN/broadcom/* /$KERNDIR/
   touch /$KERNDIR/o/README
   cp /boot/vmlinuz-$KERN /$KERNDIR/
   cp /boot/initrd.img-$KERN /$KERNDIR/
   cp /boot/System.map-$KERN /$KERNDIR/
   cp /boot/config-$KERN /$KERNDIR/
   cp /$CONFDIR/cmdline.txt /$KERNDIR/
   cat >> /$CONFDIR/config.txt << EOF
   
   [all]
   kernel=vmlinuz-$KERN
   initramfs initrd.img-$KERN
   os_prefix=$KERN/
   overlay_prefix=o/$(if [[ "$KERN" =~ (v8|2712) ]]; then echo -e "\narm_64bit=1"; fi)
   [all]
   EOF
   ```

7. Next, reboot the Raspberry Pi

   ```bash
   reboot
   ```

8. After rebooting, check the kernel. It should now be switched to PREEMPT_RT

   ```bash
   uname -a
   ```

    output:

    ```text
    Linux raspberrypi 6.1.54-rt15-v7l+ #1 SMP PREEMPT_RT Thu Sep 28 23:13:21 BST 2023 armv7l GNU/Linux
    ```

9. Next, install the kernel headers

    ```bash
    cd ~/kernel-download
    ```

    ```bash
    sudo apt install ./linux-headers-6.1.54-rt15-v7l+_6.1.54-1_armhf.deb
    ```
