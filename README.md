# Alyx Jailbreak — 0.177

[Русский](README.ru.md) · **English** · [Download APK](https://github.com/alferiko/alyx-jailbreak-releases/releases/latest)

Standalone Half-Life: Alyx launcher and ARM64 runtime for Meta Quest 3 with Quest Turnip rendering. This public repository contains release documentation and APK downloads. Application sources, build tools, signing keys and research files are kept separately.

## What's new in 0.177

Version **0.177**, build **870**, is freshly compiled from source `main` commit `9e5b66d8f3851c244b64dd95a48aac9eaa5e7cd2`. All three native renderers were rebuilt. The supplied test APK v869 was used as a reference, not as the release payload.

- Redesigned native launcher with RU/EN support, clearer navigation and the existing application icon.
- MK2 rendering: updated PGO-optimized Turnip compiler, cached VRS maps, reduced duplicate pipeline compilation and a VR readback-lock fix. Bundled shader preparation contains **606 pipelines** with separate catalogs for Off, MSAA and SMAA and profiles for VRS/filtering combinations. Preparation can add startup time; the catalog does not cover every possible scene.
- Independent **VRS**, render acceleration, AA, MQSR and resolution controls. Five AA choices: Off, MSAA 2×, SMAA Medium, SMAA Ultra and SMAA Ultra with softening. VRS works with Off/SMAA; MSAA temporarily disables VRS while preserving your checkbox choice. Experimental TAA is unavailable; a saved TAA selection becomes SMAA with softening.
- Reversible **Quality / Performance** presets and **Restore my settings**. Quality uses **85%** render resolution; Performance uses **50%**. Both set a **1024-pixel texture limit**, automatic texture pool, VRS, basic reprojection, SMAA with softening, render acceleration and vegetation simplification/hiding; MQSR is off. Performance also enables model simplification. Manual adjustments remain available. The 1024 value is texture resolution, not a 1024 MB pool budget.
- Resumable Workshop downloads verify each chunk and the complete file before publication, retain verified partial data and bound parallel transfers.
- Cache compression now preserves authored detail for UI, fonts, first-person hands/weapons and readable signs/labels. Recovery and directory synchronization are strengthened, and updated caches can be detected for compression. Previously removed detail requires original files to restore.
- Strict public-release configuration: frame profiling, runtime telemetry, GPU/allocation traces, shader dumps, diagnostic markers and Android debug/profileable modes are disabled in every renderer.

**After updating:** the first migration to MK2 applies the **Performance preset at 50%**. Open Graphics to select Quality, change individual settings or restore the previous settings. If you already used the MK2 test build, existing migrated choices remain. The previous 67% Performance switch is retired; **67% is still available manually**. Optional dynamic resolution remains **67–92%**, targeting 36 new game frames/s. Reprojection choices are Basic / Off; AppSW is unavailable.

## Cache compression

Compression changes game resources and can reduce their detail. Files and VPK parts are processed one at a time. Each backup is deleted after that file is verified and its index updated. **Stop safely restores only the unfinished file; completed files remain compressed.** Restoring their original detail requires copying the original game files again. Saves, configuration, runtime and Workshop addons are outside the compression scan.

Free space is needed for the current file's backup and index; a large standalone VPK still requires room for its own backup. Finish compression or use Stop safely before launching the game. Opening the launcher resumes interrupted work unless it was explicitly paused. Directory durability depends on filesystem support; Windows fault-model tests do not establish Quest power-loss behavior.

## Installation and updates

1. Download [Alyx-Jailbreak-0.177.apk](https://github.com/alferiko/alyx-jailbreak-releases/releases/download/v0.177/Alyx-Jailbreak-0.177.apk).
2. Install over the existing app with your usual Quest APK installer or `adb install -r Alyx-Jailbreak-0.177.apk`. The signing certificate is unchanged; do not uninstall first if you want to preserve app preferences.
3. For a first installation, copy the **game** folder from your own Windows installation to `/sdcard/AlyxJailbreak/game/`, including every VPK part and shader file.
4. Open the launcher, allow file access, check the game files, then launch. The bundled ARM64/Linux runtime is installed automatically; a separate ARM depot copy is unnecessary.
5. Select RU/EN for the launcher language. Game interface/subtitle language is a separate setting.

Keep at least 1 GB free beyond the game data for installation/update. The runtime remains pinned to ARM64 depot `546564-20260921`; compatibility with arbitrary future Windows game data is not guaranteed. Runtime installation checks hashes and backs up replaced files. Saves are under `game/hlvr/save` in the external game folder. Workshop addons go under `game/hlvr_addons` in the selected game folder.

Graphics changes apply on the next game launch; save progress before restarting. Launcher-managed updates preserve game files and saves and block installation while the game or addon installation is running. Android requires permission to install updates from the launcher.

## Validation and limitations

- Fresh build 870 passed signature/certificate and alignment checks. All **19 native libraries**, **150 runtime files**, renderer catalogs and **6573 source-input hash records** were verified. The original 148 runtime entries are unchanged; all 150 files passed extraction to their declared paths using the production installer and a repeated-install check.
- Preset/restore/manual-choice, AA/VRS, Workshop, runtime recovery and release-policy tests passed, including 26 rejected diagnostic configurations, 3065 cache-compression assertions and 12 Android filesystem fault-model assertions.
- The supplied v869 test APK has documented Quest 3 validation: six cold launches of a heavy save, at least 150 seconds each, covering Off/MSAA/SMAA with the supported VRS combinations. This evidence belongs to **v869**. The freshly rebuilt **870 has not been separately tested in gameplay on the headset**.
- Full campaign coverage, every chapter transition and stutter-free rendering are not established. Dynamic resolution does not guarantee its target frame rate. Render acceleration reduces some shadows/effects while retaining the flashlight; no specific flashlight memory-leak cure or performance percentage is claimed. Experimental Xen controls are excluded from this public build.

See [CHANGELOG](CHANGELOG.md) for earlier releases and [SHA256SUMS](SHA256SUMS.txt) to verify the current APK.

## Support

You can support Alyx Jailbreak development:

- [DonationAlerts](https://dalink.to/zer0k0)
- [Patreon](https://www.patreon.com/cw/zer0k0)
- Crypto wallet: `0x4aF6a047C0B66d72d00455aea235F8c5aC529E9f`

## Reports

Use [Issues](https://github.com/alferiko/alyx-jailbreak-releases/issues) and include version, headset/OS, graphics preset, AA, VRS, reprojection, scale, cache-compression status, map/save location and reproduction steps. Avoid sharing game content or private information in logs.

Unofficial project, not affiliated with Valve or Meta. Product names and trademarks belong to their owners. Third-party notices are included in the APK. No new source-code license is granted by this repository.
