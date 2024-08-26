### RIP-INSTALLATION

After installing the preempt-rt kernel, the next step is to install LinuxCNC. For the Raspberry Pi 3, there is no ISO image file available for installing LinuxCNC. Therefore, you need to build LinuxCNC from source.

1. Install Build Packages

   ```bash
   sudo apt install git build-essential
   ```

2. Clone the LinuxCNC Source Code

   ```bash
   git clone https://github.com/LinuxCNC/linuxcnc.git linuxcnc-dev
   ```

3. Switch to the Desired Version

   For version `2.8`, there are dependency issues with the current source code, as some dependencies are missing. Therefore, build version `2.9`.

   ```bash
   cd linuxcnc-dev
   git checkout f24ea9b19ea794ceb8ff614f3f184f5af0d25144
   ```

4. Change to the Debian Folder

   ```bash
   cd debian
   ```

5. Configure the Build

   ```bash
   ./configure uspace
   ```

6. Return to the LinuxCNC-Dev Folder

   ```bash
   cd ..
   ```

7. Check for Missing Build Dependencies

   ```bash
   dpkg-checkbuilddeps
   ```

8. Install Required Build Dependencies

   ```bash
   sudo apt-get install <dependendencies-1> <dependendencies-2> <dependendencies-3> ...
   ```

   Replace `<dependencies-1>`, `<dependencies-2>`, `<dependencies-3>`, etc., with the actual names of the packages you need to install. Ensure all necessary dependencies for building LinuxCNC are listed.

9. Verify Dependencies Again

    ```bash
    dpkg-checkbuilddeps
    ```

10. Once All Dependencies Are Installed, Move to the Source Folder

    ```bash
    cd src
    ```

11. Run Autogen

    ```bash
    ./autogen.sh
    ```

12. Configure the Build

    ```bash
    ./configure --with-realtime=uspace
    ```

13. Build LinuxCNC

    ```bash
    make
    ```

14. Set Permissions for Hardware Access

    ```bash
    sudo make setuid
    ```

15. Set Up the RIP Environment

    ```bash
    . ../scripts/rip-environment
    ```

16. Start LinuxCNC

    ```bash
    linuxcnc
    ```

    When the LinuxCNC configuration window appears, the “axis” simulation will already be highlighted. Select this highlighted “axis” configuration and check the box labeled “Created Desktop Shortcut.” Click “OK” to attempt to start LinuxCNC.
