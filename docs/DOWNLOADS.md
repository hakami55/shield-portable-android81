# Downloads

**No public ROM is available yet.** Use the [release checklist](RELEASE_CHECKLIST.md) to see why. Do not use an old private ZIP in place of a tested release.

| Item | Where to get it | Status |
|---|---|---|
| This project's ROM ZIP and SHA256SUMS | Not published | Waiting for final build and device tests |
| Android Platform Tools | [Google download page](https://developer.android.com/tools/releases/platform-tools) | Official ADB and fastboot |
| Windows SHIELD USB driver | [NVIDIA resources page](https://developer.nvidia.com/shield-open-source#SHIELD_PORTABLE) | Use its Windows USB driver link |
| TWRP 3.2.2-0 for `roth` | [Team Win download page](https://dl.twrp.me/roth/twrp-3.2.2-0-roth.img.html) | Used during development; final-ROM acceptance pending |
| Optional Open GApps ARM 8.1 pico, 15 February 2022 | [Open GApps](https://opengapps.org/) and [official archive](https://sourceforge.net/projects/opengapps/files/arm/20220215/) | Used with a minimal configuration during development; final-image fit still needs validation |
| Original NVIDIA software and restoration information | [NVIDIA SHIELD Portable resources](https://developer.nvidia.com/shield-open-source#SHIELD_PORTABLE) | Different from TWRP or this custom ROM |

## Recovery warning

Do not automatically choose the newest TWRP image. This project uses an **8,388,608-byte recovery partition**. Some newer `roth` downloads are larger. Do not force an oversized image or repartition the device to follow this draft.

The original development installation logs identify TWRP 3.2.2-0. The checked reference file is:

```text
File: twrp-3.2.2-0-roth.img
Size: 8384512 bytes
SHA-256: bb4ac27eecb0eba4ac991a6658a499e0c8ab442c137bbb8c7d3b460de72dd020
```

Its bytes match Team Win's published checksum. That establishes file identity, not compatibility with a future final release or adopted-SD decryption. Use the exact recovery named by that release's notes.

Team Win asks users to link to its HTML download pages, not mirror images or link straight to the binary. Recovery is therefore **not re-uploaded here**. [Team Win download policy](https://dl.twrp.me/roth/)

## Google apps warning

The original installation logs identify this package, which is still available in the local project:

```text
File: open_gapps-arm-8.1-pico-20220215.zip
Size: 191618543 bytes
SHA-256: 034c91278ab3c7f9af15fb8a77633dabaf490105cc42ad7d5be616220202f2d4
```

This is a **32-bit ARM** device: choose ARM, Android 8.1, pico, not ARM64 or a TV package. The development setup used a [core-only gapps-config.txt](../resources/gapps-config.txt), not the entire default Pico selection. The configuration includes essential Google services while omitting optional Pico apps to preserve system space. It is a reference recipe, not an approved installer for the final ROM. [Open GApps selector](https://opengapps.org/)

[Reference checksums](../resources/REFERENCE_SHA256SUMS.txt) identify the original files; the files themselves are not included. Google apps are optional, and a working Play Store does not guarantee a game will install or run.

The final release must retest this exact package/configuration and confirm system space. Do not assume it fits merely because it worked with an older ROM. A large SD card does not enlarge `/system`. If Google apps are part of a clean setup, install the accepted package after the ROM and before the first Android boot. Do not add an arbitrary package to an already configured device to fix login errors. [Open GApps FAQ](https://github.com/opengapps/opengapps/wiki/FAQ)

Open GApps' prebuilt-package terms prohibit public mirroring outside its project. Use its official downloads; do not upload a bundle to this repository. [Open GApps package terms](https://github.com/opengapps/opengapps#license)

Games, game data, ROMs, account files, and signing keys are not downloads supplied by this project.
