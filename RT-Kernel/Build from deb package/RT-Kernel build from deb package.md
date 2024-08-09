### INSTALL KERNEL FROM DEB PACKAGE (RASPBERRY OS)

(Source: <https://github.com/kdoren/linux/releases/tag/rpi_6.1.54-rt15>)

Berikut ini adalah langkah-langkah untuk install kernel

1. Buat folder untuk download kernel

    ```bash
    mkdir ~/kernel-download
    ```

2. Masuk ke folder yang dibuat

    ```bash
    cd ~/kernel-download
    ```

3. Download image kernel dan header. Kernel untuk menjalankan linuxcnc dan Header digunakan untuk install ethercat

   Kernel:

   ```bash
   wget https://github.com/kdoren/linux/releases/download/rpi_6.1.54-rt15/linux-image-6.1.54-rt15-v7l+_6.1.54-1_armhf.deb
   ```

   Header:

   ```bash
   wget https://github.com/kdoren/linux/releases/download/rpi_6.1.54-rt15/linux-headers-6.1.54-rt15-v7l+_6.1.54-1_armhf.deb
   ```

4. Install package

   ```bash
   sudo su
   apt install ./linux-image-6.1.54-rt15-v7l+_6.1.54-1_armhf.deb
   ```

5. Set bash variabel KERN

   ```bash
   KERN=6.1.54-rt15-v7l+
   ```

6. Kemudian jalankan perintah berikut (copy and paste seluruhnya ke terminal)

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

7. Lakukan reboot

   ```bash
   reboot
   ```

8. Setelah reboot, coba cek kernel. Seharusnya kernel sudah berganti menjadi PREEMPT_RT

   ```bash
   uname -a
   ```

    output:

    ```text
    Linux raspberrypi 6.1.54-rt15-v7l+ #1 SMP PREEMPT_RT Thu Sep 28 23:13:21 BST 2023 armv7l GNU/Linux
    ```

9. Install header kernel

    ```bash
    cd ~/kernel-download
    ```

    ```bash
    sudo apt install ./linux-headers-6.1.54-rt15-v7l+_6.1.54-1_armhf.deb
    ```
