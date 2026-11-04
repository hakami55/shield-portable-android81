# Help and known limitations

## Will this make every new game work

No. Apps still need a compatible Android version, 32-bit ARM code, sufficient memory, and a graphics path the device can actually execute. A game appearing in Google Play is not proof of playability. Current Roblox gameplay and 3DMark Sling Shot are not qualified successes for a public release.

## Is RothGL full ES3

No. It is an experimental per-game translation/compatibility path. It may help a specific game and may be slower or render incorrectly in another. There is no meaningful fixed percentage of “all ES3 support” or a universal performance promise. Leave working native games on normal graphics.

## Is overclock enabled

No finished CPU/RAM overclock is offered. The experimental GPU boost code is safety-gated off. Fan choices are available independently; more fan noise does not automatically mean a higher or safer clock.

## Will my SD card open in another SHIELD

A portable-storage card can be read by other compatible systems. An **adopted/internal** card is encrypted for its original parent Android installation and is not plug-and-play on another SHIELD. Preserve its data and keys before a reset; copying keys alone is not a tested migration procedure. [Android adoptable-storage explanation](https://source.android.com/docs/core/storage/adoptable)

## Quick Panel interferes with streaming

Open Quick Panel settings, choose **Per-app settings**, select the streaming app, and choose **Disabled in this app**. Moonlight starts excluded. If you remapped Back, use edge swipe or a different shortcut instead of expecting Back-hold to see Select/Guide events.

## There is no sound

Check media volume, the app's own audio setting, and whether sound is routed to HDMI, Bluetooth, or headphones. The project has development-tested speaker startup and BADLAND latency fixes, but a missing-sound report on the final image still needs investigation. Do not flash random audio libraries or clear game saves as the first step.

## Wi Fi will not reconnect

Wi-Fi association/reconnect, streaming, and controller coexistence remain final-image test items. Record whether it happens after sleep, boot, or accessory pairing. Do not describe the public ROM as having solved every Wi-Fi problem. If USB is broken, do not reboot into recovery merely to restore Wi-Fi debugging.

## Is this a modern secure Android release

No. The project is based on Android 8.1 and old NVIDIA components. The private source reports security patch date **2021-10-05**; that is not a claim that every vendor/kernel component has that coverage. A private userdebug/test-key build is not public-release hardening. Avoid sensitive accounts, and leave USB/network debugging off when not needed.

## Can I update without losing my setup

Not yet guaranteed. The current candidate's launcher certificate differs from the installed development launcher. The matching local development key exists, but the combined build/signing transition and public release keys still need a deliberate plan. Do not uninstall Console or clear its covers/preferences to force an upgrade.

## How are updates delivered

No automatic ROM update server or online profile-update service is promised. Future releases should state their own supported installation and rollback path.

## Report a problem

Include the ROM version, app version, graphics mode, exact steps, and whether it happens after sleep or reboot. Remove account information, serials, network names, debugging addresses, and tokens from logs or screenshots. Never attach an entire private backup or encryption-key archive.
