# SHIELD Portable Android 8.1

An unofficial Android 8.1 project for the original NVIDIA SHIELD Portable, with a controller-friendly home screen, practical SHIELD settings, and optional graphics compatibility tools.

**Status: documentation preview. No public ROM download is available yet.** The current private ROM ZIP still needs rebuilding with the latest settings, signing continuity, and fresh-install testing. Do not install an old development ZIP as a final release.

This is a community project, not an official NVIDIA update. It is for **SHIELD Portable with Tegra 4, device name `roth`**. SHIELD Tablet, SHIELD TV, and prototype hardware are not supported by this package.

## What you get

- **SHIELD Console:** a handheld-style launcher you can operate with the built-in controller or touch, with favourites, cover artwork, and startup options.
- **Controller settings:** global or per-app mappings for NVIDIA, Back, and Sound buttons. NVIDIA single-press can become Guide; long-press power behaviour stays unchanged.
- **SHIELD accessories:** connection and device-management screens for supported accessories.
- **Quick Panel:** an optional in-game sidebar for Home, recent apps, volume, and confirmed Quit, with per-app exclusions.
- **Fan control:** Quiet, Performance, Maximum cooling, or automatic cooling for selected apps.
- **RothGL:** optional, experimental per-game graphics compatibility. Normal ES2 games do not need it.
- **Audio improvements:** speaker startup and BADLAND sound-effect latency fixes tested on the development device.

Android 8.1 can help with apps that require a newer Android version than the original software. It does not add 64-bit app support or make every modern game compatible. This remains an old Android platform, not a modern security upgrade.

## Start here

| I want to | Open |
|---|---|
| Understand the new settings | [SHIELD settings guide](docs/SETTINGS.md) |
| Find ROM, recovery, tools, and optional Google apps | [Downloads](docs/DOWNLOADS.md) |
| Learn the installation process | [Installation draft](docs/INSTALL.md) |
| See pictures and a bootloader video | [Pictures and video](docs/MEDIA.md) |
| Check limitations or solve common problems | [Help and known limitations](docs/HELP.md) |
| See what remains before release | [Release checklist](docs/RELEASE_CHECKLIST.md) |

## A look at RothGL settings

Development screenshot of the current Settings component, not proof of a finished full-ROM release:

![RothGL home with About, Google Play ES3 games, Games, and FPS counter](images/rothgl-home.png)

## Before installing anything

Back up your data outside the device. Unlocking the bootloader erases user data. Use a working USB data port and reliable power; do not attempt first-time installation on a device that cannot charge or enter USB fastboot.

Google apps, games, and emulators are not bundled. Download third-party tools from their official pages in [Downloads](docs/DOWNLOADS.md).

## Files used during development

The original installation used **TWRP 3.2.2-0 for roth** and **Open GApps ARM 8.1 pico dated 15 February 2022**, with a small core-only configuration. See [exact filenames, checksums and official download links](docs/DOWNLOADS.md). These historical results do not qualify the final rebuilt ROM; no recovery or Google-app bundle is mirrored here.

See [credits and distribution notes](NOTICE.md). Do not upload private backups, encryption keys, or account information to this repository.
