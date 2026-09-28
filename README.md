# Alyx Jailbreak — 0.175

[Русский](README.ru.md) · **English** · [Download APK](https://github.com/alferiko/alyx-jailbreak-releases/releases/latest)

Standalone Half-Life: Alyx launcher and ARM64 runtime for Meta Quest 3 with Quest Turnip rendering. This public repository contains release documentation and APK downloads. Application sources, build tools, signing keys and research files are kept separately.

## What's new in 0.175

Built from source `main` commit `2aeef3616253f843718685930e9bb5332e2ce381`. Android versionName **0.175**, versionCode **682**, package `com.alf.alyxquest`. The signing certificate is unchanged.

- New release profile with direct rendering and a pinned XEMU driver containing 23 verified patches. These address memory cleanup, command-buffer reuse, visibility fences and submission recovery. No overall FPS gain is claimed from the memory fixes.
- This build uses **no foveation or MSAA**. The old four-mode selector is replaced by the current main release profile. Ordinary reprojection offers **Basic / Off**; Basic limits new game frames to 36 per second while headset rotation correction remains active. Depth reprojection and AppSW are unavailable.
- Selecting **Performance → On** applies **67% render resolution**, soft scaling and a **1024 px maximum texture resolution**. It disables shadows and reduces particles/effects. **The texture-pool budget is unchanged.** Manual changes remain available; selecting On again restores the preset, and Off retains visible settings. Autosaves and transparent objects are preserved.
- Asynchronous eye transfer, shared/persistent pipeline caching and the simulation-timing correction are included.
- Optional **Compress cache** in Main settings processes textures and eligible large static models directly on Quest. Ordinary textures use existing mip levels up to 1024 px; eligible models use an authored lower-detail level. Special textures and unsupported models are preserved. Pause/Resume and recovery after interruption are supported.
- Packed Workshop installation is retained, with short folder names, CRC verification and recovery after failed updates. The full 147-file ARM64/Linux runtime and its installation paths are retained.

## Cache compression

Compression changes game resources and can reduce their detail. Files and VPK parts are processed one at a time. Each backup is deleted after that file is verified and its index updated. **Stop safely restores only the unfinished file; completed files remain compressed.** Restoring their original detail requires copying the original game files again. Saves, configuration, runtime and Workshop addons are outside the compression scan.

Free space is needed for the current file's backup and index; a large standalone VPK still requires room for its own backup. Finish compression or use Stop safely before launching the game. Opening the launcher resumes interrupted work unless it was explicitly paused.

## Installation and updates

1. Download [Alyx-Jailbreak-0.175.apk](https://github.com/alferiko/alyx-jailbreak-releases/releases/download/v0.175/Alyx-Jailbreak-0.175.apk).
2. Install over the existing app with your usual Quest APK installer or `adb install -r Alyx-Jailbreak-0.175.apk`. The signing certificate is unchanged; do not uninstall first if you want to preserve app preferences.
3. For a first installation, copy the **game** folder from your own Windows installation to `/sdcard/AlyxJailbreak/game/`, including every VPK part and shader file.
4. Open the launcher, allow file access, choose **Check files**, then **Launch**. The bundled ARM64/Linux runtime is installed automatically; a separate ARM depot copy is unnecessary.
5. Use the header's RU/EN button for the launcher language. Game interface/subtitle language is a separate setting.

Keep at least 1 GB free beyond the game data for installation/update. The runtime remains pinned to ARM64 depot `546564-20260921`; compatibility with arbitrary future Windows game data is not guaranteed. Runtime installation checks hashes and backs up replaced files. Saves are under `game/hlvr/save` in the external game folder. Workshop addons go under `game/hlvr_addons` in the selected game folder.

Graphics changes apply on the next game launch; save progress before restarting. Launcher-managed updates preserve game files and saves and block installation while the game or addon installation is running. Android requires permission to install updates from the launcher.

## Validation and limitations

- Verified APK signature, unchanged signing certificate, package/version and alignment. All 17 packaged ARM64 libraries match the build output. The pinned driver and all 23 included patch hashes were checked; experimental marker overrides and diagnostic manifest flags are disabled.
- All 147 runtime files match 0.172 by path, size and SHA256. The complete archive was unpacked with the production installer and verified again.
- Passed Workshop checks (74), cache compression checks (2,443), runtime tests, launcher settings/localization, preset/manual-override tests, release build guards and native reprojection/frame-pacing/prediction tests.
- The earlier RC 673 reached the heavy `s0/quick` scene on Quest with the same pinned driver. The final 0.175 APK has not had a new on-device gameplay run or full visual acceptance test. Sustained 72 FPS, stable frame pacing and a complete playthrough are not guaranteed.
- No antialiasing is enabled; edges can look jagged. Volumetric fog remains disabled to avoid previously observed GPU freezes.

See [CHANGELOG](CHANGELOG.md) for earlier releases and [SHA256SUMS](SHA256SUMS.txt) to verify the current APK.

## Reports

Use [Issues](https://github.com/alferiko/alyx-jailbreak-releases/issues) and include version, headset/OS, Performance setting, reprojection, scale, cache-compression status, map/save location and reproduction steps. Avoid sharing game content or private information in logs.

Unofficial project, not affiliated with Valve or Meta. Product names and trademarks belong to their owners. Third-party notices are included in the APK. No new source-code license is granted by this repository.
