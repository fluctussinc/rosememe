# Redmi note 10s/Poco M5s/Rosemary

Custom ROM guide for redmi note 10s/Poco M5s codename rosemary.


## Device overview

The Redmi Note 10S is built around a MediaTek Helio G95 processor and a 6.43-inch FHD+ Super AMOLED display. Published Xiaomi specifications include a 5,000 mAh (typical) battery, 33 W charging, and a 64 MP + 8 MP + 2 MP + 2 MP rear camera array. Memory and storage configurations vary by market.

| Specification | Details |
| --- | --- |
| Processor | MediaTek Helio G95; ARM Mali-G76 MC4 GPU |
| Display | 6.43-inch Super AMOLED, 2400 × 1080 |
| Rear cameras | 64 MP main, 8 MP ultra-wide, 2 MP macro, 2 MP depth |
| Front camera | 13 MP |
| Battery | 5,000 mAh typical |
| Charging | 33 W wired fast charging |
| Memory/storage options | 6 GB + 64 GB, 6 GB + 128 GB, or 8 GB + 128 GB (market dependent) |

## Requirements

- Laptop/Desktop
- Internet
- windows (optional but recommended)
- Unlocked bootloader
- SD card (optional but recommended)

## Please follow the steps in order if your doing it from the very beggining

 Unlock bootloader -> Flash custom recovery -> Flash custom ROM

## How to unlock bootloader 

- You will find many tutorials for unlocking the device with official xiaomi method on YouTube, It is recommended to unlock the device using official method. How ever you MAY have to wait 7 days or more for the device to unlock or if you are lucky you may not have to wait at all! 
- https://xdaforums.com/t/how-to-unlock-bootloader-in-redmi-note-10s-without-waiting.4659081/ (Advanced/**Risky**)
  
## How to flash custom recovery?

- First obviously you have to download the custom recovery. For A16 or higher https://
- To actually flash the custom recovery you need to download platform tools from https://developer.android.com/tools/releases/platform-tools.

- After downloading the platform tools follow the following steps:
  1. Extract the zip
  2. Open the folder
  3. Open a cmd/terminal inside the folder using the following steps given below if you happen to not know.
 

<details>
<summary><B>Click here</B></summary>

<img width="840" height="122" alt="image" src="https://github.com/user-attachments/assets/869fe0f2-7fb4-4d8e-9c4c-aea3cd37b867" />
<br><br>
<img width="973" height="535" alt="image" src="https://github.com/user-attachments/assets/3882d940-13b2-4bbc-acc8-227617ed8b06" />
<br><br>
<img width="811" height="208" alt="image" src="https://github.com/user-attachments/assets/2236c0ec-b80e-4d91-96e1-776e2063ae45" />
<br><br>
After writing "cmd", press Enter. This will open a terminal.

</details>

  4. Put your phone in fastboot mode by holding power + vol down button and connect your phone to the laptop/desktop using cable
  5. Check if your laptop detects the phone using the following command inside the terminal of platform tools folder `Fastboot devices`. 
  Usually output looks like <br>
  `Your_device_id    fastboot`<br>
If your device successfully gets detected by fastboot your ready to goto the next step, however incase your device does not get detected by fastboot follow the steps given below
<details>
  <summary><b>Troubleshoot fastboot not detecting device</b></summary>
  <br><br>
  If your device does not get detected by fastboot it is most likely a driver issue to solve follow these steps:<br>
  i. Open device manager and make sure your device is connected to the laptop/pc via cable<br>
  ii. Find android (There will be a yellow triangle with ! mark inside it indicating a issue) and double click on it, incase android does not appear restart your laptop. <br>
  iii. Goto driver option and click on update driver<br>
  iv. Click browse my computer for driver<br>
  v. Click on android bootloader interface and install it<br>
  vi. Done!<br>

     This should install the necessary drivers in your device for the fastboot to work smoothly try running the `fastboot devices` command again to check connection
</details>
<br>
6. To flash the recovery this is the command `fastboot flash boot recovery_file.img`
7.Done your recovery should be flashed successfully!

## How to flash custom ROM?

- *This step is after unlocking the bootloader and **AFTER** flashing custom recovery.*
- Keep the ROM file inside your sd card if you do not have a sd card you can keep the file in your phone storage and flash it, make sure to **not** format
 1. Reboot to recovery using power + volume up button
 2. Format/Factory reset (skip this step if you want to sideload from the device storage)
 3. Apply update
 4. Sideload
 5. Select the ROM zip and install
 6. It may ask for signature verification, press continue for the ROM to install
 7. After the install format/factory reset again (Required)
 8. Done! You may reboot to the system now

 #### How to sideload using laptop/pc
 <details>
 <summary><B>Click here</B></summary>
 
 - *This step is after unlocking the bootloader and **AFTER** flashing custom recovery.*
 1. Reboot to recovery using power + volume up button
 2. Format/Factory reset 
 3. Apply update
 4. Enable adb and make sure your device is connected to the phone through a cable
 5. In the platform tools folder open a CMD/Terminal
 6. To flash the rom type `adb sideload rom_name.zip` and press enter. You can also drag and drop the zip from your pc to the terminal to automatically fill in the path to your file/zip.
 7. After the install format/factory reset again
 8. Done! You may reboot to the system now
</details>

## Additional notes

- 33w fast charging is not supported by most custom ROMS.
- You can always go back to stock/factory ROM
- Banking and security sensitive apps like PayTM do not work on custom roms without PlayIntegrity and other security fixes.

## Note

- This project is not affiliated with Xiaomi, Google, or the maintainers of any of the mentioned resources please utilise them at your own risk.
- We are not responsible for bricked devices, dead SD cards, thermonuclear war, or the current economic crisis. YOU are choosing to make these modifications to your device.
- Phone specifications above are based on Xiaomi's published product specifications. Actual configuration and included accessories can vary by region.
- Rooting and module installation can affect device security, warranty, and system stability. Keep a recovery path and backups appropriate to your setup.

# Integrity Fix for redmi note 10s

⚠️ READ THIS BEFORE COMPLAINING ABOUT PLAY INTEGRITY ⚠️

On October 14, custom ROM community noticed that every device without Remote Key Provisioning running a custom ROM only have BASIC_INTEGRITY when checking Play Integrity status.

It is NOT a keybox issue, modules issue or skill issue. Google actually did something on their side, and we are still trying to figure out.

It looks like they're checking more than just device fingerprint or bootloader status, but don't worry, it already happened before, and the community found a way to fix it, so PLEASE. Don't complain about Play Integrity, it cannot be fixed now.

I highly suggest you guys to not wipe your data, uninstall or clear WhatsApp or banking apps data because it will probably not work anymore when you try to login. Just wait until a fix for this.

**Here is the latest fix currently known**

For play integrity fix with hardware attested keybox you basically need to select devices with DEVICE_INITIAL_SDK_INT value 32 - 35, value 36 only requires you use RKP attested keybox.

And for custom roms you got two options.

1. Turn off in-built keybox and pif spoof, install teesimulator (use hardware attested keybox and additional extra configs) + pif-inject (enable first three toggles and use DEVICE_INITIAL_SDK_INT=32, which is pixel 6a) 

2. Wait for you custom rom devs to either adapt the current methods and do it for you like method 1, but you can try loading a pixel 6a fingerprint config file and load the keybox as usual

Basically pixel 6a fingerprint is your savior for custom roms

(https://t.me/ksunext/1180)

### If you found this guide useful maybe **⭐** the guide! (no pressure)
