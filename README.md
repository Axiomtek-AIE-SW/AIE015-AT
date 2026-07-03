# Introduction

This is sample code for Axiomtek AIE015-AT

# Image Flash

### **Before flashing image, you MUST prepare a Linux host system running x86_64 Ubuntu 22.04 or later.**
- **Step 1. Set up the AIE015-AT connection as follows:**
    * Take off the Maintenance cover.
    * Connect a USB cable from the Linux host system to the USB Type A port at AIE015-AT, and press the recovery button.
    * onnect an HDMI monitor to AIE015-AT.

- **Step 2. Open the terminal at host system, and change the path to the image file directory for example  "~/Downloads" with following commands to check image tarball data integrity first.**

    > ```
    > $ cd ~/Downloads
    > $ md5sum -c <image_tarball_file_name>.tbz2.md5sum
    > ```

    #### \[Command example\]:
    > ```
    > $ md5sum -c JetPack_7.1_Linux_JETSON_AGX_THOR_TARGETS.tbz2.md5sum
    > ```

- **Step 3. If above command returns OK, Untar the image file with the command below:**

    > ```
    > $ sudo tar jxvf <image_tarball_file_name>.tbz2
    > ```

    #### \[Command example\]:
    > ```
    > $ sudo tar jxvf JetPack_7.1_Linux_JETSON_AGX_THOR_TARGETS.tbz2
    > ```

- **Step 4. Change the directory to the image package folder with the command below:**

    > ```
    > $ cd <image_file_name>
    > ```

    #### \[Command example\]:
    > ```
    > $ cd JetPack_7.1_Linux_JETSON_AGX_THOR_TARGETS/Linux_for_Tegra/
    > ```

- **Step 5. Run the command lsusb, then the command line "0955:7026 NVidia Corp." should be listed.**

    > ```
    > $ lsusb
    > <Note>:
    >   - "0955:7026 NVidia Corp." for Jetson T5000
    >   - "0955:7226 NVidia Corp." for Jetson T4000
    > ```

- **Step 6. Running the following command to flash the image.**

    > ```
    > [T5000]:
    > $ sudo SKIP_EEPROM_CHECK=1 BOARDID=3834 BOARDSKU=0008 ./tools/kernel_flash/l4t_initrd_flash.sh --flash-only --massflash 1 --network usb0 --showlogs  jetson-agx-thor-devkit internal
    > [T4000]:
    > $ sudo SKIP_EEPROM_CHECK=1 BOARDID=3834 BOARDSKU=0000 ./tools/kernel_flash/l4t_initrd_flash.sh --flash-only --massflash 1 --network usb0 --showlogs  jetson-agx-thor-devkit internal
    > ```

- **Step 7. The flashing procedure takes approximately 20 minutes or more. Once finished, you should see "Flashing finished Successfullly!!" shown on the screen. Then reboot AIE015-AT manually.**

    > ```
    > <Note>:
    >   THE DEFAULT LOGIN CREDENTIALS:
    >     - Username: nvidia
    >     - Password: nvidia
    > ```

