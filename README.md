# Alyx Jailbreak — 0.181

[Русский](README.ru.md) · **English** · [Download APK](https://github.com/alferiko/alyx-jailbreak-releases/releases/latest)

Standalone Half-Life: Alyx launcher and ARM64 runtime. This repository contains release documentation and APK downloads.

## What's new

- Fixed startup on Quest 2.
- Added shader preparation from the launcher.
- Improved graphics settings and shader cache handling.

## Installation and updates

1. Download [Alyx-Jailbreak-0.181.apk](https://github.com/alferiko/alyx-jailbreak-releases/releases/download/v0.181/Alyx-Jailbreak-0.181.apk).
2. Install over the existing app using your headset's APK installer or `adb install -r Alyx-Jailbreak-0.181.apk`. The package and signing certificate are unchanged. Do not uninstall first if you want to preserve app preferences.
3. For a first installation, download game files through the launcher using your own Steam account with a Half-Life: Alyx license, or copy the **game** folder from your Windows installation to `/sdcard/AlyxJailbreak/game/`, including every VPK part and shader file. The Steam download option appears when no complete game installation is found.
4. Grant file access, check the game files and launch. The bundled ARM64 runtime is installed automatically.

Steam downloads can be paused and resumed; signing in again is required after restarting the app. The download includes resource compression. Steam Cloud import preserves existing local saves and does not upload files to Steam Cloud. Wait until all installation and compression steps finish before launching the game.

Saves are under `game/hlvr/save`; Workshop addons are under `game/hlvr_addons`. Launcher and game languages are selected separately. Graphics changes apply on the next game launch.

**Automatic update downloads are available on all supported headsets and enabled by default.** Checks run when opening the launcher, at most once every six hours; installation requires confirmation. The setting remains under your control. If you already installed the original 0.180 build 909, an older universal test or a separate PICO build, install the current APK manually once to enable future checks.

## Graphics and storage

Quality, Performance and Extreme modes are available alongside individual graphics controls. Use Restore my settings to return to your previous selection. Available controls depend on the headset. On PICO, use physical controllers; camera hand tracking is unavailable.

Resource compression can reduce detail. Stop safely restores only the unfinished file; completed files remain compressed. Restoring their original detail requires copying the original game files again. Saves, configuration, runtime and Workshop addons are outside the compression scan. Free space is required for temporary files and backups; follow the launcher's space checks and completion status.

## Compatibility and checks

Targets: **Quest 2, Quest Pro, Quest 3, PICO 4 and PICO 4 Ultra**. Version **0.181**, build **2012**; Android 10 or newer. Runtime is pinned to ARM64 depot `546564-20260921`; compatibility with arbitrary future game data is not guaranteed.

The Quest 2 startup fix was confirmed on the earlier v911 test build. This release APK, v2012, has passed package checks but has not been separately tested in headset gameplay. Full campaign coverage and stutter-free rendering are not established.

The release includes all 150 runtime files and all three rendering variants, with heavy diagnostics and frame profiling disabled. Signature, package contents and release configuration are checked before publication. See [SHA256SUMS](SHA256SUMS.txt) for the APK checksum and [CHANGELOG](CHANGELOG.md) for release history.

## Support

- [DonationAlerts](https://dalink.to/zer0k0)
- [Patreon](https://www.patreon.com/cw/zer0k0)
- Crypto wallet: `0x4aF6a047C0B66d72d00455aea235F8c5aC529E9f`

Report problems in [Issues](https://github.com/alferiko/alyx-jailbreak-releases/issues). Include app version, headset/OS, graphics mode, map/save location, compression status and reproduction steps. Avoid sharing game content or private information in logs.

Unofficial project, not affiliated with Valve, Meta or PICO. Product names and trademarks belong to their owners. Third-party notices are included in the APK. No new source-code license is granted by this repository.
