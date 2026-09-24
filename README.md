# Alyx Jailbreak — 0.173

[Русский](README.ru.md) · **English** · [Download APK](https://github.com/alferiko/alyx-jailbreak-releases/releases/latest)

Standalone Half-Life: Alyx launcher and ARM64 runtime for Meta Quest 3 with Quest Turnip rendering. This public repository contains release documentation and APK downloads. Application sources, build tools, signing keys and research files are kept separately.

## What's new in 0.173

Built from source `main` commit `04548e3913934a4e2e25495cfd374f49043c2b36`. Android versionName **0.173**, versionCode **362**, package `com.alf.alyxquest`.

- Steam Workshop tab with browsing and direct downloads on Quest, including replacement addons without embedded addon metadata. Browsing needs no login; downloads require a Steam account that owns Alyx and Steam Guard authentication. Enable installed addons in Alyx's Addons menu. Passwords and tokens are not saved.
- Game interface/subtitle language selection, separate from the RU/EN launcher switch.
- Three rendering modes: no foveation, foveation, and foveation with central MSAA 2×. The MSAA path targets the central area of each eye.
- Independent pixel or soft bilinear image scaling, and a WebM video file-lock fix for Quest shared storage.
- Optional **Optimized mode (alpha)**, disabled by default. Enabling it applies an editable preset: central MSAA with foveation, 67% scale and soft filtering, plus alpha rendering policies. You can then adjust the visible controls. Selecting On again reapplies the preset. Turning it off retains those visible settings. In-game graphics quality is saved separately for normal and alpha modes.
- Fix for the depth-resource registry exhaustion identified in the in-game settings crash.
- Launcher update checks and automatic APK downloads from this repository, with size, SHA256, package, signing-certificate and version checks. Installation requires Android confirmation. Automatic downloads can be disabled in Help.

## Installation and updates

1. Download [Alyx-Jailbreak-0.173.apk](https://github.com/alferiko/alyx-jailbreak-releases/releases/download/v0.173/Alyx-Jailbreak-0.173.apk).
2. Install over the existing app with your usual Quest APK installer or `adb install -r Alyx-Jailbreak-0.173.apk`. The signing certificate is unchanged; do not uninstall first if you want to preserve app preferences.
3. For a first installation, copy the **game** folder from your own Windows installation to `/sdcard/AlyxJailbreak/game/`, including every VPK part and shader file.
4. Open the launcher, allow file access, choose **Check files**, then **Launch**. The bundled ARM64/Linux runtime is installed automatically; a separate ARM depot copy is unnecessary.
5. Use the header's RU/EN button for the launcher language. Game interface/subtitle language is a separate setting.

Keep at least 1 GB free beyond the game data for installation/update. The runtime remains pinned to ARM64 depot `546564-20260921`; compatibility with arbitrary future Windows game data is not guaranteed. Runtime installation checks hashes and backs up replaced files. Saves are under `game/hlvr/save` in the external game folder. Workshop addons go under `game/hlvr_addons` in the selected game folder.

Graphics changes apply on the next game launch; save progress before restarting. Launcher-managed updates preserve game files and saves and block installation while the game or addon installation is running. Android requires permission to install updates from the launcher.

## Validation and limitations

- All three native variants were rebuilt from the specified `main` commit. APK signature, unchanged signing certificate, package/version, alignment and payload parity after public version metadata packaging were verified.
- Local tests passed for Workshop installation/recovery, game menu/language, runtime extraction/repair, Vulkan boot configuration, localization, render modes, scaling, graphics-quality persistence and the editable alpha preset.
- This release APK has **not** undergone a new on-device installation or full gameplay pass. Earlier builds have Quest checks documented during development; the latest settings-crash fix still needs live reproduction testing.
- Optimized mode is alpha. Sustained 72 FPS, stable frame pacing and a complete playthrough are not guaranteed. Foveation reduces peripheral detail.
- Volumetric fog remains disabled to avoid previously observed GPU freezes. Stutter and rendering investigations continue.

See [CHANGELOG](CHANGELOG.md) for earlier releases and [SHA256SUMS](SHA256SUMS.txt) to verify the current APK.

## Reports

Use [Issues](https://github.com/alferiko/alyx-jailbreak-releases/issues) and include version, headset/OS, rendering mode, alpha setting, scale, map/save location and reproduction steps. Avoid sharing game content or private information in logs.

Unofficial project, not affiliated with Valve or Meta. Product names and trademarks belong to their owners. Third-party notices are included in the APK. No new source-code license is granted by this repository.
