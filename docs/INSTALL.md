# Installation draft

**Do not use this as permission to install the private candidate.** A tested public ROM, its signing plan, and a release-specific wipe/recovery procedure are not available yet. This explains the planned process and the bootloader steps; final release notes must complete the installation decisions.

## Before you begin

- Confirm the device is the original **SHIELD Portable / `roth`**, not a Tablet or TV.
- Back up saves and personal files to a PC, and verify you can restore important files.
- Use a working USB data port, dependable power, and a charged battery. Wi-Fi ADB cannot replace USB fastboot for an unbootable device.
- Preserve adopted-SD encryption information before any reset. Do not format an adopted card, wipe its parent device, or assume another SHIELD can read it.
- Obtain the exact future release files from [Downloads](DOWNLOADS.md). A missing release download is a reason to stop.

## 1 Prepare the PC

Extract Google's [Platform Tools](https://developer.android.com/tools/releases/platform-tools). On Windows, open PowerShell in that folder. Use the [NVIDIA USB driver](https://developer.nvidia.com/shield-open-source#SHIELD_PORTABLE) if Windows cannot detect the device.

Enable USB debugging on the SHIELD, connect USB, accept its authorization prompt, then check:

```powershell
.\adb.exe devices
```

Continue only if the correct device is listed as `device`, not `offline` or `unauthorized`.

## 2 Unlock only if needed

**Unlocking erases user data. Stop if your backup is incomplete.** Skip unlocking if the bootloader is already unlocked.

Enter the bootloader with:

```powershell
.\adb.exe reboot bootloader
.\fastboot.exe devices
```

The Portable's hardware alternative is to power it on while holding **Back and Home**. In the bootloader, those buttons navigate and the NVIDIA button confirms. Do not use Tablet/TV button combinations.

Only when you have accepted the wipe and confirmed this is the correct Portable:

```powershell
.\fastboot.exe oem unlock
```

Read the device's warning and confirm **Unlock** on the device. Do not repeat this command as troubleshooting. Bootloader unlocking is separate from installing a root app; the old rooting images in historical guides are not part of this project. [Original SHIELD bootloader instructions](https://github.com/linux-shield/shield-root#unlocking)

## 3 Check the device and recovery

```powershell
.\fastboot.exe getvar product
.\fastboot.exe getvar version-bootloader
```

The product must be `roth`. The private candidate currently asserts bootloader `01.00.14422_318.3689`; future release notes must state their accepted version. Stop on a mismatch rather than removing the check or flashing a random bootloader.

For the reference recovery named in [Downloads](DOWNLOADS.md), check its size and hash:

```powershell
Get-Item .\twrp-3.2.2-0-roth.img | Select-Object Name,Length
Get-FileHash .\twrp-3.2.2-0-roth.img -Algorithm SHA256
```

The documented TWRP installation command, **only after a release approves this recovery**, is:

```powershell
.\fastboot.exe flash recovery .\twrp-3.2.2-0-roth.img
```

Boot into recovery as directed by the final release notes before allowing stock Android to replace it. Do not flash the private ROM's Lineage recovery as if it were TWRP. [Team Win SHIELD Portable instructions](https://twrp.me/nvidia/nvidiahshieldportable.html)

## 4 Install the future qualified release

The expected order is **verified backup → release-specific clean/upgrade preparation → ROM → accepted optional Google apps → first boot**.

The final release must specify the exact TWRP wipe choices and whether an in-place upgrade is supported. Until then, **do not guess**, wipe internal/shared storage, format the SD card, or clear the launcher to get around signing errors. The current candidate is not cleared for an in-place upgrade.

If the final notes support Google apps, install the named package after the ROM in the same recovery session, before the first Android boot. Stop if it reports insufficient system space. [Open GApps clean-install guidance](https://github.com/opengapps/opengapps/wiki/FAQ)

Do not flash `userdata`, `staging`, `DTB`, factory/calibration images, or another device's partitions as shortcuts. Do not relock the bootloader while using this custom ROM.

## 5 First setup and checks

Complete Android setup, check that SHIELD Console opens, and test touch, controller buttons, Wi-Fi, speakers, headphones, sleep/wake, and SD files before restoring everything. Enable Quick Panel Accessibility only if you want that feature.

Start with a known working native ES2 game. Enable RothGL only for a game that needs a compatibility test. Stop and report boot loops, missing storage, or repeated system crashes; do not keep wiping or forcing a flash.

For a return to stock, use the correct **Portable** package and its own instructions from [NVIDIA](https://developer.nvidia.com/shield-open-source#SHIELD_PORTABLE), not commands copied from a SHIELD TV guide.
