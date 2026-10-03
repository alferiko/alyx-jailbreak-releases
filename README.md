# Alyx Jailbreak — PICO 4 Ultra 0.178.1

[Русский](README.ru.md) · **English** · [Download PICO 4 Ultra APK](https://github.com/alferiko/alyx-jailbreak-releases/releases/download/pico4-ultra-v0.178.1/Alyx-Jailbreak-PICO4-Ultra-0.178.1.apk)

Standalone Half-Life: Alyx launcher and ARM64 runtime for **PICO 4 Ultra**. This branch and releases tagged `pico4-ultra-*` are the PICO Ultra channel. The repository's `main` branch and global Latest release remain the Quest channel. Always use the explicit PICO download above.

## This release

First PICO 4 Ultra release, based on the accepted v885 support build and the 0.178 game/runtime baseline. Android versionCode **886**, versionName **0.178-pico4ultra.1**. Supports Android API 32 or newer; the external tester used Ultra A9210, Android 14, PICO OS 5.13.3.

- Correct shared-image layout eliminates the mosaic reported in the initial PICO build.
- The Android launcher and VR game activity are classified separately, resolving the initial loading-circle problem.
- Controller actions and bindings are recreated when the graphics session changes. A missing interaction-profile label no longer prevents querying real controller poses.
- Camera hand tracking is disabled, with its checkbox unchecked and unavailable. MQSR and Quest-specific dynamic resolution are also unavailable.
- Includes the Off, MSAA 2x and SMAA renderers and their matching shader catalogs.
- PICO updates are installed manually. Quest automatic updates are blocked in this build.

## Install or update

1. Download [Alyx-Jailbreak-PICO4-Ultra-0.178.1.apk](https://github.com/alferiko/alyx-jailbreak-releases/releases/download/pico4-ultra-v0.178.1/Alyx-Jailbreak-PICO4-Ultra-0.178.1.apk). This APK is for **Ultra**, not ordinary PICO 4 or Quest.
2. Install over the previous PICO test with your APK installer, or connect USB debugging and run `adb -s SERIAL_NUMBER install -r Alyx-Jailbreak-PICO4-Ultra-0.178.1.apk`. Replace SERIAL_NUMBER with the Ultra serial from `adb devices -l`. The package and signing certificate are unchanged. Do not uninstall first if you want to preserve app preferences.
3. For a new installation, copy the **game** folder from your own Windows game installation into `/sdcard/AlyxJailbreak/game/`, including every VPK part and shader file. The bundled ARM64 runtime is installed automatically.
4. Open **Alyx Jailbreak PICO 4 Ultra**, grant file access, check the game files and launch. Keep the graphics settings that worked in your previous PICO build.

If the PICO settings screen cannot grant all-files access, use:

```powershell
adb -s SERIAL_NUMBER shell appops set --uid com.alf.alyxquest MANAGE_EXTERNAL_STORAGE allow
adb -s SERIAL_NUMBER shell appops get --uid com.alf.alyxquest MANAGE_EXTERNAL_STORAGE
```

The UID result should show `allow`. Close and reopen the app afterwards. If the game already loads its files, no permission change is needed. Permission to install unknown apps is separate from file access.

Keep at least 1 GB free beyond game data for installation/update. Game saves live in `game/hlvr/save` under the chosen external game folder. Updates preserve the game files and saves. Do not interrupt cache compression: finish it or use Stop safely before launching. Completed compression cannot restore original detail without the original game files.

## Updates and channel separation

Use only [PICO Ultra releases](https://github.com/alferiko/alyx-jailbreak-releases/releases/tag/pico4-ultra-v0.178.1) and the [`pico4-ultra` branch](https://github.com/alferiko/alyx-jailbreak-releases/tree/pico4-ultra). The generic `/releases/latest` link is reserved for Quest. PICO releases are published with Latest disabled. Do not install a Quest APK onto PICO; both builds retain the same application package for compatibility with earlier installations.

## Validation and reports

The tester confirmed v885 restored the controllers/menu interaction and later reported gameplay without problems. This release retains those rendering/input fixes and changes release branding, version metadata and installation guidance. The exact release APK has not had a separate physical-headset test. Full campaign coverage and every graphics-mode combination have not been established.

Build validation covers three native hosts, catalogs, the 150-file runtime payload, API/manifest configuration, signing certificate and APK alignment. The working v883-v885 image import layer and pinned driver are retained. No new game content is included; use your own game files.

For problems, download `PICO-Ultra-log-tools.zip` from this release, start recording **before** opening the launcher, then reproduce the issue. Review logs for personal information before sharing. Report build number, PICO OS, graphics settings and the result through [Issues](https://github.com/alferiko/alyx-jailbreak-releases/issues). See [SHA256SUMS](SHA256SUMS.txt) for this release's checksums.

## Support

- [DonationAlerts](https://dalink.to/zer0k0)
- [Patreon](https://www.patreon.com/cw/zer0k0)

Unofficial project, not affiliated with Valve or PICO. Third-party notices are included in the APK. This repository contains release documentation and downloads; application sources, build tools and signing material are maintained separately.
