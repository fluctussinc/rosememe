# Redmi Note 10S / POCO M5s (rosemary) — Custom ROM Guide

A step-by-step guide to installing a custom ROM on the **Redmi Note 10S / POCO M5s** (codename: **rosemary**) — from unlocking the bootloader all the way to booting your new ROM.

> **Follow the steps in order** if you're starting from the very beginning:
> **Unlock bootloader → Flash custom recovery → Flash custom ROM**

## Table of contents

1. [Device overview](#device-overview)
2. [Requirements](#requirements)
3. [The order of operations](#the-order-of-operations)
4. [Step 1: Unlock the bootloader](#step-1-unlock-the-bootloader)
5. [Step 2: Flash a custom recovery](#step-2-flash-a-custom-recovery)
6. [Step 3: Flash a custom ROM](#step-3-flash-a-custom-rom)
7. [Additional notes](#additional-notes)
8. [Note (disclaimer)](#note-disclaimer)
9. [Play Integrity fix](#play-integrity-fix)
10. [If this guide helped](#if-this-guide-helped)

---

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
| Memory / storage options | 6 GB + 64 GB, 6 GB + 128 GB, or 8 GB + 128 GB (market dependent) |

## Requirements

- Laptop or desktop
- Internet connection
- Windows (optional, but recommended)
- **Unlocked bootloader**
- microSD card (optional, but recommended)

## The order of operations

Please follow the steps in order if you're doing this from the very beginning:

**Unlock bootloader → Flash custom recovery → Flash custom ROM**

## Step 1: Unlock the bootloader

- You'll find many tutorials for unlocking the device with the official Xiaomi method on YouTube — the official method is recommended. However, you **may** have to wait 7 days or more for the device to unlock, or, if you're lucky, you may not have to wait at all!
- [How to unlock bootloader in Redmi Note 10S without waiting (XDA)](https://xdaforums.com/t/how-to-unlock-bootloader-in-redmi-note-10s-without-waiting.4659081/) — **Advanced / risky**

> ⚠️ **Warning:** Unlocking the bootloader wipes all data on your phone. Back up anything important first.

## Step 2: Flash a custom recovery

### 2.1 Download what you need

1. **Custom recovery** — download the recovery image (`.img`) that matches your ROM's Android version:
   - For A16 (Android 16) or higher: `[TODO: add recovery link]`
2. **Platform tools** (adb & fastboot) — download from <https://developer.android.com/tools/releases/platform-tools>, then extract the zip to a folder you can easily find.

### 2.2 Open a terminal inside the platform-tools folder

1. Extract the zip.
2. Open the extracted folder.
3. Open a `cmd`/terminal inside that folder — here's how, in case you don't know:

<details>
<summary><b>Click here</b></summary>

<br>

In File Explorer, open your **platform-tools** folder, click the **address bar**, type `cmd`, and press **Enter**. A terminal window opens, already pointed at that folder.

<br>

<img width="840" height="122" alt="Typing cmd in the File Explorer address bar" src="https://github.com/user-attachments/assets/869fe0f2-7fb4-4d8e-9c4c-aea3cd37b867" />

<br><br>

<img width="973" height="535" alt="The platform-tools folder open in File Explorer" src="https://github.com/user-attachments/assets/3882d940-13b2-4bbc-acc8-227617ed8b06" />

<br><br>

<img width="811" height="208" alt="Pressing Enter opens a terminal in the folder" src="https://github.com/user-attachments/assets/2236c0ec-b80e-4d91-96e1-776e2063ae45" />

<br><br>

After writing `cmd`, press **Enter** — this will open a terminal.

</details>

### 2.3 Boot into fastboot mode and check the connection

4. Put your phone into **fastboot mode** by holding **Power + Volume Down**, then connect it to the laptop/desktop using a USB cable.
5. Check that your PC detects the phone — inside the platform-tools terminal, run:

```bash
fastboot devices
```

The output usually looks like this:

```
your_device_id    fastboot
```

If your device is detected, you're ready to go to the next step. If it **isn't**, follow the troubleshooting below.

<details>
<summary><b>Troubleshooting: fastboot doesn't detect the device</b></summary>

<br>

If your device doesn't get detected, it's most likely a **driver issue**. To fix it:

1. Open **Device Manager** and make sure your phone is connected to the laptop/PC via cable.
2. Find **Android** (there will be a yellow triangle with a `!` mark inside it, indicating an issue) and double-click it. If "Android" doesn't appear, restart your laptop.
3. Go to the **Driver** tab and click **Update driver**.
4. Click **Browse my computer for drivers**.
5. Select **Android Bootloader Interface** and install it.
6. Done!

This installs the necessary drivers for fastboot to work smoothly. Try running the `fastboot devices` command again to check the connection.

</details>

### 2.4 Flash the recovery

6. Flash the recovery with this command:

```bash
fastboot flash boot recovery_file.img
```

> Replace `recovery_file.img` with the actual filename of the recovery image you downloaded.

7. Done — your recovery should now be flashed successfully!

## Step 3: Flash a custom ROM

> **Prerequisite:** this step comes **after** unlocking the bootloader and **after** flashing the custom recovery.

- Keep the ROM `.zip` on your **SD card**. If you don't have an SD card, you can keep the file on your phone storage and flash it from there — just make sure to **not** format that storage before flashing.

### Method A: install from SD card or phone storage

1. Reboot to recovery using **Power + Volume Up**.
2. **Format / Factory reset** — skip this step if you're flashing from the device storage, since formatting would delete the ROM zip.
3. Tap **Apply update**, then select the ROM zip from your storage and install it.
4. If it asks about **signature verification**, press **Continue** so the ROM installs.
5. After the install finishes, **Format / Factory reset again** (required).
6. Done! You may reboot to the system now.

### Method B: adb sideload from a PC

1. Reboot to recovery using **Power + Volume Up**.
2. **Format / Factory reset**.
3. Tap **Apply update**, then choose **Sideload** (Apply update from ADB).
4. Make sure your **PC** is connected to the phone via USB cable and adb is available.
5. In the **platform-tools** folder, open a `cmd`/terminal (see [Step 2.2](#22-open-a-terminal-inside-the-platform-tools-folder)).
6. Flash the ROM with this command:

```bash
adb sideload rom_name.zip
```

   Tip: you can also drag & drop the zip from your PC into the terminal to automatically fill in the path.

7. After the install finishes, **Format / Factory reset again**.
8. Done! You may reboot to the system now.

## Additional notes

- **33 W fast charging** is not supported by most custom ROMs.
- You can always go back to the stock/factory ROM.
- Banking and security-sensitive apps like PayTM do not work on custom ROMs without Play Integrity and other security fixes — see the [Play Integrity fix](#play-integrity-fix) section below.

## Note (disclaimer)

- This project is not affiliated with Xiaomi, Google, or the maintainers of any of the mentioned resources — please utilise them at your own risk.
- We are not responsible for bricked devices, dead SD cards, thermonuclear war, or the current economic crisis. **YOU** are choosing to make these modifications to your device.
- Phone specifications above are based on Xiaomi's published product specifications. Actual configuration and included accessories can vary by region.
- Rooting and module installation can affect device security, warranty, and system stability. Keep a recovery path and backups appropriate to your setup.

## Play Integrity fix

> ⚠️ **READ THIS BEFORE COMPLAINING ABOUT PLAY INTEGRITY** ⚠️

On **October 14**, the custom ROM community noticed that every device **without Remote Key Provisioning** running a custom ROM only had **BASIC_INTEGRITY** when checking Play Integrity status.

- It is **not** a keybox issue, modules issue, or skill issue. Google actually did something on their side, and we are still trying to figure it out.
- It looks like they're checking more than just the device fingerprint or bootloader status — but don't worry, it already happened before, and the community found a way to fix it.
- So **please don't complain about Play Integrity** — it cannot be fixed right now.

**Important:** I highly suggest you do **not** wipe your data, or uninstall/clear WhatsApp or banking app data — they will probably not work anymore when you try to log in. Just wait until there's a fix for this.

### The latest known fix

For a Play Integrity fix with a **hardware-attested keybox**, you basically need to select devices with a `DEVICE_INITIAL_SDK_INT` value of **32–35**. A value of **36** only works if you use an **RKP-attested keybox**.

For custom ROMs, you have two options:

1. Turn off the built-in keybox and pif spoof, then:
   - Install **teesimulator** — use a hardware-attested keybox and additional extra configs.
   - Install **pif-inject** — enable the first three toggles and use `DEVICE_INITIAL_SDK_INT=32` (Pixel 6a).
2. Wait for your custom ROM devs to adapt the current methods and do it for you (like option 1) — meanwhile, you can try loading a **Pixel 6a fingerprint** config file and load the keybox as usual.

Basically, the **Pixel 6a fingerprint is your savior** for custom ROMs.

Reference: <https://t.me/ksunext/1180>

## If this guide helped

If you found this guide useful, maybe drop it a **⭐**! (no pressure)
