# Release checklist

**Documentation publication is approved; ROM publication is not.** This repository is a documentation preview with screenshots, configuration text and official download links. No installable ROM or third-party recovery/Google-app bundle is supplied.

## Completed PC checks

- Nine readiness audit groups passed on 4 November 2026.
- The historical private OTA matches its recorded hash and passes image/archive checks.
- Latest RothGL home XML/source and UI-policy tests pass.
- Core packaged APK signatures validate against their configured development keys.
- Launcher/Quick Panel staging matches the project copies.
- Speaker policy, GPU safety policy/mock I/O, launcher navigation, Quick Panel policy, and both product configurations pass local tests.
- A local launcher key matching the installed development launcher is available.
- Original installation logs confirm TWRP 3.2.2-0 and Open GApps ARM 8.1 pico dated 15 February 2022; their local reference checksums are recorded.

These are PC checks, not a new full-image hardware qualification.

## Before a private release candidate

- [ ] Finish and verify the device backup; validate a recovery/restore route.
- [ ] Choose the signing/upgrade policy without deleting launcher data.
- [ ] Build the full ROM with the latest RothGL settings and the selected signing policy.
- [ ] Re-audit that exact ZIP, images, partition sizes, default Home, services, and file hashes.
- [ ] Confirm the accepted bootloader and exact size-checked recovery.
- [ ] Retest the original optional Google-apps package with the core-only configuration and check the final image's system-space budget.

## On a powered test Portable

- [ ] Clean setup completes and opens Console without an unwanted chooser.
- [ ] Test touch pacing, physical controls, mapping, accessories, fan modes, sleep/wake, audio, video, HDMI, Wi-Fi and Bluetooth.
- [ ] Test SD mount, app movement and save/load; never assume adopted-card transplantation works.
- [ ] Check native games stay native and a known unchanged game works with RothGL on/off.
- [ ] Rehearse a documented rollback while preserving the test device's own calibration/identity.

Do not flash the unchargeable development device with a broken USB port for acceptance testing.

## Before publishing

- [ ] Decide public release signing and hardening; do not ship the current test-key build as production-ready.
- [ ] Publish corresponding source/patches and component licences as required; this documentation folder is not the complete ROM source.
- [ ] Review proprietary NVIDIA files, fixes, intro artwork/video and redistribution permissions.
- [ ] Add final version, changes, exact downloads, checksums, supported hardware, installation and rollback instructions.
- [ ] Finish a fresh review of known issues and the install walkthrough.
- [ ] Remove private backups, keys, accounts, hardware identifiers and personal screenshots.
- [x] Owner approved publishing the documentation preview and official file references.
- [ ] Obtain separate ROM-release approval after the acceptance checks are complete.

## Third party files

Link to official recovery and Google-apps pages; their projects do not permit casual public mirroring. Only redistribute a file after confirming the applicable permission and source/licence requirements. No game APKs, OBB data, emulator game images, or personal saves belong in the public ROM package.
