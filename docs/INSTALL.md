# Install Android 8.1

[← Home & features](../README.md) · [SHIELD settings](SETTINGS.md)

**The ROM download is not available yet. Do not start flashing until it is available here.**

Use the original SHIELD Portable with a working USB data connection and reliable charging. Back up your files and saves to a PC before starting. Unlocking or resetting can erase data. An SD card used as internal storage also needs a backup; do not format it.

## 1 Get the PC tools

Download and extract [Android Platform Tools](https://developer.android.com/tools/releases/platform-tools). On Windows, install the [NVIDIA SHIELD USB driver](https://developer.nvidia.com/shield-open-source#SHIELD_PORTABLE) if the PC does not detect the device.

Open PowerShell inside the extracted Platform Tools folder.

## 2 Get the installation files

- **ROM ZIP:** not available yet.
- **Recovery:** [TWRP 3.2.2-0 for SHIELD Portable](https://dl.twrp.me/roth/twrp-3.2.2-0-roth.img.html).
- **Google apps, optional:** [Open GApps ARM 8.1 pico](https://sourceforge.net/projects/opengapps/files/arm/20220215/open_gapps-arm-8.1-pico-20220215.zip/). Choose `open_gapps-arm-8.1-pico-20220215.zip`, not ARM64.
- **Small Google-apps setup:** [gapps-config.txt](../resources/gapps-config.txt). Save it beside the Google-apps ZIP using that exact name.
- **Our Google-apps support ZIP:** [download the Google Services fix](https://github.com/hakami55/shield-portable-android81/raw/refs/heads/main/resources/roth-google-services-repair-candidate.zip). Required with the exact Google-apps package above. This is a helper, **not a ROM**.
- **File checks:** [SHA256SUMS.txt](../resources/SHA256SUMS.txt).

Do not substitute a newer recovery image: it may be too large for the device. These downloads come from their own projects; no Google apps are included in the ROM.

The support ZIP contains only repair scripts. It prepares the native libraries from your installed Google Services APK; it does not include or replace Google's APK. Do not use it with another Google-apps version, another device or stock Android. If its checks reject your installation, stop—do not force it.

To check a downloaded file in PowerShell, run `Get-FileHash .\filename -Algorithm SHA256` and compare it with the checksum list. A matching checksum checks the file, not whether installation has been tested on your device.

## 3 Enable USB debugging

On the SHIELD, open **Settings → About**, tap **Build number** seven times, then enable **USB debugging** in Developer options. Connect USB and accept the authorization prompt.

Run:

```powershell
.\adb.exe devices
```

Continue only if the correct SHIELD appears as `device`.

Check the device and bootloader:

```powershell
.\adb.exe shell getprop ro.product.device
.\adb.exe shell getprop ro.bootloader
```

The device must be `roth`. The bootloader must match one of these supported versions:

- `01.00.14422_318.3689`
- `01.00.32208_722.2550`

If it does not match, stop and follow [NVIDIA's official SHIELD Portable update instructions](https://developer.nvidia.com/shield-open-source#SHIELD_PORTABLE) first. An official recovery installation can erase data; back up before using it. Do not substitute another model's bootloader files.

## 4 Enter the bootloader

Enter the bootloader and check the connected device:

```powershell
.\adb.exe reboot bootloader
.\fastboot.exe devices
.\fastboot.exe getvar product
```

The product must be `Roth` (case does not matter). If it is different, stop.

**Unlocking erases data. Skip this command if your SHIELD is already unlocked.** Only if the bootloader is locked and your backup is complete:

```powershell
.\fastboot.exe oem unlock
```

Read the warning on the SHIELD. Use **Back/Home** to select and the **NVIDIA button** to confirm.

You can also enter the bootloader by powering on while holding **Back + Home**. [Bootloader visual guide](https://www.youtube.com/watch?v=7Am5WYRojMs). Use the video for the button/menu view only; use the files linked above, not its rooting downloads.

## 5 Install recovery

Place the downloaded recovery image in your Platform Tools folder. Check it before flashing:

```powershell
Get-Item .\twrp-3.2.2-0-roth.img | Select-Object Name,Length
Get-FileHash .\twrp-3.2.2-0-roth.img -Algorithm SHA256
```

Its size must be **8,384,512 bytes**, and its hash must match [the checksum list](../resources/SHA256SUMS.txt).

When the ROM and its final installation instructions are available:

```powershell
.\fastboot.exe flash recovery .\twrp-3.2.2-0-roth.img
```

Enter **Recovery** from the SHIELD bootloader menu before returning to Android. [Official recovery instructions](https://twrp.me/nvidia/nvidiahshieldportable.html).

## 6 Install the ROM

Use the reset/install directions supplied with the ROM download. Do not guess which storage to wipe. Never select the SD card or internal shared storage just to clear an installation error.

Without Google apps, the installation order is **ROM ZIP → first Android boot**.

With Google apps, the order is:

1. Install the **ROM ZIP**.
2. Install [Open GApps ARM 8.1 pico](https://sourceforge.net/projects/opengapps/files/arm/20220215/open_gapps-arm-8.1-pico-20220215.zip/), keeping [gapps-config.txt](../resources/gapps-config.txt) beside it.
3. Install [our Google Services fix](https://github.com/hakami55/shield-portable-android81/raw/refs/heads/main/resources/roth-google-services-repair-candidate.zip).
4. Reboot to Android and complete setup.

Install all three ZIPs in the **same TWRP session, before the first Android boot**. If there is a storage or compatibility error, stop rather than forcing installation. The helper being available does not mean the ROM is ready to download.

Do not flash another SHIELD model's files or relock the bootloader while using this ROM.

## 7 Set up your SHIELD

Complete Android setup, then open [SHIELD settings](SETTINGS.md). Check the controls, Wi-Fi, sound, sleep/wake, and SD files before restoring everything.

Enable the Quick Panel accessibility service if you want the sidebar **or Auto cooling**. Its sidebar master switch can stay off when you only use Auto cooling. Leave optional graphics settings off unless you need them.

After setup, turn USB debugging off unless you need it. Root access and GPU boost should stay off for normal use.

To return to the original software, use [NVIDIA's SHIELD Portable recovery package and instructions](https://developer.nvidia.com/shield-open-source#SHIELD_PORTABLE).
