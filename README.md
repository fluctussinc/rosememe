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

## How to unlock bootloader 

- You will find many tutorials for unlocking the device with official xiaomi method on YouTube, It is recommended to unlock the device using official method. How ever you MAY have to wait 7 days or more for the device to unlock or if you are lucky you may not have to wait at all! 
- https://xdaforums.com/t/how-to-unlock-bootloader-in-redmi-note-10s-without-waiting.4659081/ (Advanced/**Risky**)

## How to flash custom ROM?

- This step is after unlocking the bootloader!
- To flash a custom rom you first need to flash a custom recovery. While flashing the custom recovery please take notice of the kernel versions. a16 or higher ROMs generally use 4.19 kernel, if the rom is flashed using a lower kernel version recovery the ROM will encounter issues like no sound, vibration etc.
  
### How to flash custom recovery?

- First obviously you have to download the custom recovery. For A16 or higher https://
- To actually flash the custom recovery you need to download platform tools from https://developer.android.com/tools/releases/platform-tools.

- After downloading the platform tools follow the following steps:
  1. Extract the zip
  2. Open the folder
  3. Open a cmd/terminal inside the folder using the following steps given below if you happen to not know.
 

<details>
<summary>Click here</summary>

<img width="840" height="122" alt="image" src="https://github.com/user-attachments/assets/869fe0f2-7fb4-4d8e-9c4c-aea3cd37b867" />

<img width="973" height="535" alt="image" src="https://github.com/user-attachments/assets/3882d940-13b2-4bbc-acc8-227617ed8b06" />

<img width="811" height="208" alt="image" src="https://github.com/user-attachments/assets/2236c0ec-b80e-4d91-96e1-776e2063ae45" />

After writing "cmd", press Enter. This will open a terminal.

</details>

  4. Put your phone in fastboot mode by holding power + vol down button and connect your phone to the laptop/desktop using cable
  5. Check if your laptop detects the phone using the following command inside the terminal of platform tools folder `Fastboot devices`. 
  Usually output looks like <br>
  `Your_device_id    fastboot`<br>
If your device successfully gets detected by fastboot your ready to goto the next step, however incase your device does not get detected by fastboot follow the steps given below
<details>
  <summary>Troubleshoot fastboot not detecting device</summary>

  If your device does not get detected by fastboot it is most likely a driver issue to solve follow these steps:
  1. Open device manager and make sure your device is connected to the laptop/pc via cable
  2. Find android (There will be a yellow triangle with ! mark inside it indicating a issue) and double click on it, incase android does not appear restart your laptop. 
  3. Goto driver option and click on update driver
  4. Click browse my computer for driver
  5. Click on android bootloader interface and install it
  6. Done!

     This should install the necessary drivers in your device for the fastboot to work smoothly try running the `fastboot devices` command again to check connection
</details>
6. To flash the recovery this is the command `fastboot flash boot recovery_file.img`
7.Done your recovery should be flashed successfully!

## Additional notes

- 33w fast charging is not supported by most custom ROMS.
- You can always go back to stock/factory ROM.

## Note

- This project is not affiliated with Xiaomi, Google, or the maintainers of any of the mentioned resources please utilise them at your own risk.
- We are not responsible for bricked devices, dead SD cards, thermonuclear war, or the current economic crisis. YOU are choosing to make these modifications to your device.
- Phone specifications above are based on Xiaomi's published product specifications. Actual configuration and included accessories can vary by region.
- Rooting and module installation can affect device security, warranty, and system stability. Keep a recovery path and backups appropriate to your setup.

# Integrity Fix for redmi note 10s
