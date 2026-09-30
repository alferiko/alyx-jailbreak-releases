# Alyx Jailbreak — 0.176

[Русский](README.ru.md) · **English** · [Download APK](https://github.com/alferiko/alyx-jailbreak-releases/releases/latest)

Standalone Half-Life: Alyx launcher and ARM64 runtime for Meta Quest 3 with Quest Turnip rendering. This public repository contains release documentation and APK downloads. Application sources, build tools, signing keys and research files are kept separately.

## What's new in 0.176

Based on 0.176-rc1 (806), confirmed in gameplay on Quest 3, from source `main` `32ff1d35ab21403a03ac107059f98b95a49bdf88`. Public version **0.176**, versionCode **807**, package `com.alf.alyxquest`. Only version metadata changed; code, libraries and assets are byte-identical to the tested APK. The signing certificate is unchanged.

- **Quality** and **Speed** buttons apply graphics settings once. Quality: **85%** render resolution, **SMAA Ultra + TAA (test)**, model simplification off. Speed: **67%**, **SMAA Ultra + softening**, model simplification on. Both set textures to 1024, mip 0, automatic texture pool, linear scaling, basic reprojection, memory savings and vegetation simplification/hiding; MQSR is off. Manual changes remain until the preset is selected again. In-game graphics quality remains independent.
- Independent **AA and MQSR** settings. AA options: Off, MSAA 2×, SMAA Medium, SMAA Ultra, SMAA Ultra with softening and experimental SMAA Ultra + TAA. Optional **67–92% dynamic resolution** targets 36 new game frames/s. Direct rendering without foveation; Basic / Off reprojection without AppSW.
- Bundled simplified vegetation: **149 models and 152 materials**, installed as a separate VPK without overwriting stock game archives. Disable Hide vegetation to see plants; both presets enable hiding. Xen plants are excluded and collision data is preserved.
- Updated Turnip driver with GMEM synchronization, descriptor lifetime, memory accounting, constant reuse and shader compiler fixes. Memory-saving and geometry-simplification options are included.
- Corrected hand alignment, pistol double-press binding and animated loading text. Optional camera finger tracking supports controller fallback. The flashlight remains available while flickering shadows are suppressed in Performance mode.
- Packed Workshop installation and cache compression are retained. Compression controls hide after successful completion, precompressed caches are recognized, and launcher translations are expanded.

The separate **Performance → On** switch still sets **67%** render resolution and **1024** textures without changing the pool budget. Quality/Speed additionally reset the pool to automatic.

## Cache compression

Compression changes game resources and can reduce their detail. Files and VPK parts are processed one at a time. Each backup is deleted after that file is verified and its index updated. **Stop safely restores only the unfinished file; completed files remain compressed.** Restoring their original detail requires copying the original game files again. Saves, configuration, runtime and Workshop addons are outside the compression scan.

Free space is needed for the current file's backup and index; a large standalone VPK still requires room for its own backup. Finish compression or use Stop safely before launching the game. Opening the launcher resumes interrupted work unless it was explicitly paused.

## Installation and updates

1. Download [Alyx-Jailbreak-0.176.apk](https://github.com/alferiko/alyx-jailbreak-releases/releases/download/v0.176/Alyx-Jailbreak-0.176.apk).
2. Install over the existing app with your usual Quest APK installer or `adb install -r Alyx-Jailbreak-0.176.apk`. The signing certificate is unchanged; do not uninstall first if you want to preserve app preferences.
3. For a first installation, copy the **game** folder from your own Windows installation to `/sdcard/AlyxJailbreak/game/`, including every VPK part and shader file.
4. Open the launcher, allow file access, choose **Check files**, then **Launch**. The bundled ARM64/Linux runtime is installed automatically; a separate ARM depot copy is unnecessary.
5. Use the header's RU/EN button for the launcher language. Game interface/subtitle language is a separate setting.

Keep at least 1 GB free beyond the game data for installation/update. The runtime remains pinned to ARM64 depot `546564-20260921`; compatibility with arbitrary future Windows game data is not guaranteed. Runtime installation checks hashes and backs up replaced files. Saves are under `game/hlvr/save` in the external game folder. Workshop addons go under `game/hlvr_addons` in the selected game folder.

Graphics changes apply on the next game launch; save progress before restarting. Launcher-managed updates preserve game files and saves and block installation while the game or addon installation is running. Android requires permission to install updates from the launcher.

## Validation and limitations

- The user confirmed gameplay testing of 0.176-rc1 (806) on Quest 3. Only AndroidManifest.xml version metadata changed for the final APK; all executable code, 19 native libraries and assets match the tested build.
- Verified signature, unchanged certificate, alignment, all three renderers, AA/MQSR settings and the pinned driver. All **148 runtime files** passed size/SHA256 checks and production extraction. The original 147 entries are preserved; only the vegetation VPK was added. All 301 VPK resources passed CRC/SHA256 checks.
- Preset/manual-override, localization, Workshop, vegetation mounting and runtime extraction/recovery tests passed.
- Heavy diagnostics are disabled in all three renderers: GPU/per-frame tracing, shader dumps, allocation tracing, Vulkan validation, diagnostic probes and Android debug/profileable modes. Bounded aggregate counters and lifecycle events from the tested build remain enabled.
- SMAA Ultra + TAA is experimental. Dynamic resolution does not guarantee the target frame rate. A full playthrough, every chapter transition and all plants/LODs have not been verified. Volumetric fog remains disabled.

See [CHANGELOG](CHANGELOG.md) for earlier releases and [SHA256SUMS](SHA256SUMS.txt) to verify the current APK.

## Reports

Use [Issues](https://github.com/alferiko/alyx-jailbreak-releases/issues) and include version, headset/OS, Performance setting, reprojection, scale, cache-compression status, map/save location and reproduction steps. Avoid sharing game content or private information in logs.

Unofficial project, not affiliated with Valve or Meta. Product names and trademarks belong to their owners. Third-party notices are included in the APK. No new source-code license is granted by this repository.
