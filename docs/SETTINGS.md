# SHIELD settings guide

Open **Android Settings → Shield settings**. These features are implemented in the development project; the final combined ROM still needs its own acceptance test.

## Controller settings

Choose the built-in controller, enable remapping, then choose a global profile or a particular app. Change only the buttons you need; other controller inputs keep their normal behaviour.

Examples:

- Map **NVIDIA single-press → Guide** for a streaming app that accepts a controller Guide button.
- Map **Back → Select** when an app needs a Select button.
- Use the **Sound button** as an alternative remappable button.

The Portable does not have a separate physical Guide button. The setting creates a Guide input from a chosen button; it does not add a new physical button. **Long-press NVIDIA remains the power menu.** Whether a remote app forwards Guide to a host depends on that app too.

Controller testing and profile reset are available. Touchscreen-mapper controls expose the existing NVIDIA mapping path for games without native controls; support depends on the game and mapper. It is not a promise that every touch game becomes fully playable.

## SHIELD accessories

Pair or manage a supported controller, open its details, inspect available battery/device information, or forget it. Battery information depends on what the accessory reports. The 2015 P2570 controller has been exercised during development; other controllers and old remotes need their own checks.

## Launcher settings

SHIELD Console is the intended initial Home after setup. Fresh-install setup behaviour is still a release test, not a completed claim.

Use the D-pad or left stick to move. **A** selects, **B** returns, **X** quick-launches, and **Y** changes favourite status where offered. **L1/R1** change tabs, **L2/R2** change Games/Apps filters, and **Start** opens or closes the launcher menu.

The launcher settings provide:

- **Startup intro:** enable or disable the intro on a fresh launcher start.
- **Video intro:** video or the lighter logo animation.
- **Intro sound:** video audio at the current media volume; off by default.
- **Preview startup intro:** try it; **A or touch skips**.
- **Quick Panel settings**, Android settings, and the controls guide.

The intro belongs to the launcher. It does not replace the ROM boot animation. Intro artwork/video distribution remains a release review item.

Use an app's **Cover / icon** option to choose artwork or restore its original app icon. Restoring the icon removes the custom cover, not the app or its saves. Recents in the launcher track launches from that launcher.

## Quick Panel

Open **Launcher settings → Quick Panel settings**. Turn on the master switch and explicitly enable **SHIELD Quick Panel** in Android Accessibility.

Open the panel with a left-edge swipe or by holding ordinary Back for about **0.6 seconds**. It offers shortcuts such as Home, recent apps, media volume, and **Quit with confirmation**. Opening it does not necessarily pause a game. Quit can lose unsaved progress.

For each app choose **Use global settings**, **Disabled in this app**, or **Custom shortcuts**. Moonlight is excluded by default to avoid stealing streaming input. A master-off setting overrides every app profile.

If Back has been remapped to Select or Guide, use edge swipe instead: the Back-hold shortcut cannot intercept the replacement controller input. The service does not read screen contents or use a network connection. It does observe foreground-app/window information for its shortcuts.

## Fan control

| Mode | What it does |
|---|---|
| Quiet | Original quieter fan behaviour |
| Performance | Stronger cooling for all apps |
| Maximum cooling | Strongest cooling, with more fan noise |
| Auto | Performance cooling for selected foreground apps, Quiet elsewhere |

Auto uses the companion Quick Panel service to follow foreground apps. Select **Apps with extra cooling** to change the list. Stronger cooling is not a guaranteed FPS increase.

**Overclock settings are not available.** The experimental GPU boost entry is also safety-gated off in the ROM configuration. Do not interpret its “up to 828 MHz” label as an available, validated overclock or guaranteed frequency. No CPU/RAM overclock is provided as a finished feature.

## RothGL

Leave it off when a game already works normally. RothGL is a partial, experimental compatibility layer, not a complete ES3 driver or a universal speed boost.

The home page has four choices:

1. **About RothGL:** what it does and a short guide.
2. **Google Play ES3 games:** an experimental catalogue-visibility switch.
3. **Games:** choose a game, turn RothGL on/off, and open it.
4. **FPS counter:** optional counter settings with limited support.

To try a game: save your progress, open **Games**, choose it, enable **Use RothGL**, accept the close-game warning, then open it again. To return to normal graphics, turn the same switch off and reopen the game. The game may be closed when applying a change.

![Per-game RothGL switch and Advanced settings](../images/rothgl-game.png)

**Advanced settings** contains library choices, older compatibility workarounds, and per-game FPS options. Keep the suggested defaults unless troubleshooting a specific game. Older “Hybrid” names may still exist internally; they are not a separate promise of full ES3 support.

The **Show more ES3 games** switch may make additional games eligible to appear in Google Play. It does **not** make them run, add missing GPU features, change your purchases, bypass payment, or guarantee certification. RothGL still needs to be selected separately for a game.

![Google Play ES3 games with one visibility switch](../images/rothgl-play.png)

The FPS counter is not supported by every game or graphics path. A missing counter alone does not mean a game has crashed.

## Other development fixes

The project includes speaker-initialization and audio-latency work, controller/accessory fixes, and HDMI console-mode work so the built-in screen can turn off during external-display use. These must be rechecked on the final combined image. Wi-Fi reconnect reliability remains a test item.

An App Fixes component is included in the private candidate. Treat available fixes as game/version-specific, not as permission to modify every installed APK. It does not supply paid game files.
