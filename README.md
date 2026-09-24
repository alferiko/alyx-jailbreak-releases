# Alyx Jailbreak — 0.174

[Русский](README.ru.md) · **English** · [Download APK](https://github.com/alferiko/alyx-jailbreak-releases/releases/latest)

Standalone Half-Life: Alyx launcher and ARM64 runtime for Meta Quest 3 with Quest Turnip rendering. This public repository contains release documentation and APK downloads. Application sources, build tools, signing keys and research files are kept separately.

## What's new in 0.174

Built from source `main` commit `b2302d504d22f6dfd12c5377d51d081ce3e21991`. Android versionName **0.174**, versionCode **485**, package `com.alf.alyxquest`.

- Workshop addons now keep their VPK archives intact instead of extracting game assets into loose files. Split archives and multiple archives are supported. Addon metadata is preserved or generated when missing; new folder names use up to 20 letters/digits, with collision handling. Existing managed addons keep their folder during updates. CRC checks and transactional replacement protect the previous installation on failure.
- Shared pipeline caching, larger persistent caches and parallel compilation for central MSAA reduce compilation stalls. The selective FlushAndWait bypass preserves completion callbacks.
- Enabling **Optimized mode (alpha)** sets **Maximum texture resolution to 1024**, central MSAA with foveation, 67% render scale and soft filtering. It leaves the texture-pool budget unchanged. Settings remain editable; selecting On again reapplies the preset. Turning it off retains the visible settings. In-game graphics quality is saved separately for normal and alpha modes.
- Four render modes: no foveation, foveation, foveation with central MSAA 2×, and Quest foveation without MSAA. Pixel or soft bilinear scaling is selected separately.
- The complete bundled ARM64/Linux runtime is retained: all 147 files, hashes and destination paths match 0.172. No separate ARM depot download is needed.

Steam Workshop browsing is available without login. Downloads require a Steam account that owns Alyx and Steam Guard authentication. Enable installed addons in Alyx's Addons menu; installation does not enable them automatically. Passwords and tokens are not saved.

The launcher checks this repository for updates and can download APKs automatically, verifying size, SHA256, package, signing certificate and version. Android confirms installation. Automatic downloads can be disabled in Help.

## Installation and updates

1. Download [Alyx-Jailbreak-0.174.apk](https://github.com/alferiko/alyx-jailbreak-releases/releases/download/v0.174/Alyx-Jailbreak-0.174.apk).
2. Install over the existing app with your usual Quest APK installer or `adb install -r Alyx-Jailbreak-0.174.apk`. The signing certificate is unchanged; do not uninstall first if you want to preserve app preferences.
3. For a first installation, copy the **game** folder from your own Windows installation to `/sdcard/AlyxJailbreak/game/`, including every VPK part and shader file.
4. Open the launcher, allow file access, choose **Check files**, then **Launch**. The bundled ARM64/Linux runtime is installed automatically; a separate ARM depot copy is unnecessary.
5. Use the header's RU/EN button for the launcher language. Game interface/subtitle language is a separate setting.

Keep at least 1 GB free beyond the game data for installation/update. The runtime remains pinned to ARM64 depot `546564-20260921`; compatibility with arbitrary future Windows game data is not guaranteed. Runtime installation checks hashes and backs up replaced files. Saves are under `game/hlvr/save` in the external game folder. Workshop addons go under `game/hlvr_addons` in the selected game folder.

Graphics changes apply on the next game launch; save progress before restarting. Launcher-managed updates preserve game files and saves and block installation while the game or addon installation is running. Android requires permission to install updates from the launcher.

## Validation and limitations

- All three native libraries serving the four render modes were rebuilt from the specified `main` commit. APK signature, unchanged signing certificate, package/version and alignment were verified. Packaged native libraries were checked against build outputs; the bundled runtime was compared with 0.172 by path, size and SHA256 and unpacked with the production extractor.
- Local tests passed for packed Workshop installation/recovery (74 checks), game menu/language, runtime packaging/extraction/repair, build presets, render-mode selection and the editable alpha preset.
- The packed-addon test build 483 was installed on Quest and its launcher started successfully. The final public APK has not had a new on-device gameplay run; packed-addon loading in the game remains unverified.
- Optimized mode is alpha. Sustained 72 FPS, stable frame pacing and a complete playthrough are not guaranteed. Foveation reduces peripheral detail.
- Volumetric fog remains disabled to avoid previously observed GPU freezes. Stutter and rendering investigations continue.

See [CHANGELOG](CHANGELOG.md) for earlier releases and [SHA256SUMS](SHA256SUMS.txt) to verify the current APK.

## Reports

Use [Issues](https://github.com/alferiko/alyx-jailbreak-releases/issues) and include version, headset/OS, rendering mode, alpha setting, scale, map/save location and reproduction steps. Avoid sharing game content or private information in logs.

Unofficial project, not affiliated with Valve or Meta. Product names and trademarks belong to their owners. Third-party notices are included in the APK. No new source-code license is granted by this repository.
