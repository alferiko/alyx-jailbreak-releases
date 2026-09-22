# Alyx Jailbreak — 0.171

[Русский](README.ru.md) · **English** · [Download APK](https://github.com/alferiko/alyx-jailbreak-releases/releases/latest)

Standalone Half-Life: Alyx runtime/launcher for Meta Quest 3, using an ARM64
game runtime and the Quest Turnip rendering path. This is the public **release
repository**: application source code, build tools, signing keys and research
files are not published here.

## Version 0.171

- Russian/English switch in the launcher header; the choice is saved and applies
  immediately. It changes **only the launcher**, not the game's language.
- Graphics, audio, saves, help and file-check messages are translated.
- Independent foveation and MSAA 1×/2× selectors, using the existing four modes.
- Lean rendering configuration without heavy statistics or GPU tracing.
- Bundled ARM64/Linux runtime: 146 files plus a stock-only gameinfo adjustment.
- Based on the updated ARM64 depot `546564-20260921`.

This release updates launcher localization and version metadata. It does not
claim to fix the reported weak MSAA effect or occasional gameplay stutters.

Revision **0.171-r2** fixes startup error **20** after a fresh installation: the APK now includes the mandatory GNU-unique loader self-test libraries and the loader-cycle test libraries. Android versionCode is 172; versionName remains 0.171. Install over the previous APK and launch normally; no manual runtime copying is needed.

## Installation

1. Download `Alyx-Jailbreak-0.171-r2.apk` from [Releases](https://github.com/alferiko/alyx-jailbreak-releases/releases/tag/v0.171-r2).
2. Sideload it to your Quest 3 with your usual APK installer, or run
   `adb install -r Alyx-Jailbreak-0.171-r2.apk`.
3. Copy the **game** folder from your Windows installation to
   `/sdcard/AlyxJailbreak/game/` (including all VPK parts and shader files).
   The APK includes the missing ARM64/Linux runtime and installs it automatically
   when you select Check files or Launch. No separate ARM depot copy is needed.
4. Open the launcher, allow file access, select **Check files**, then **Launch**.
5. Use **RU → EN / EN → RU** in the header to change launcher language.

Requires your own Windows game data. The included runtime is pinned to ARM64
depot546564-20260921; arbitrary future Windows data updates are not guaranteed.
Allow at least1GB free for installation/update in addition to the game data.
The installer checks SHA256, preserves saves/preferences and backs up replaced
runtime files. Custom gameinfo is preserved; stock memory settings are adapted. Package ID: `com.alf.alyxquest`.
Graphics options apply on the next game launch; save progress before restarting.
Game saves are under `game/hlvr/save` in the external game folder.

## Known limitations

- Volumetric fog is disabled as a workaround for previous long GPU freezes.
  This changes atmospheric effects; it is not a complete driver fix.
- Some users may see little visual improvement with MSAA. Investigation is open.
- Occasional gameplay stutters remain under investigation; stable 32 FPS is
  **not guaranteed**. Foveation can visibly reduce peripheral detail.
- Version 171's rendering baseline was tested in all four modes by the project
  owner. The new build passed compilation, signature and runtime-installer tests.
  RU/EN switching, persistence and runtime verification were checked on Quest.
  A complete fresh Windows-data playthrough has not yet been repeated.

## Reports

Use [Issues](https://github.com/alferiko/alyx-jailbreak-releases/issues) and include version, headset/OS, FDM/MSAA settings,
render scale, map/save location and reproduction steps. Avoid uploading game
content, personal files or unfiltered logs containing private information.

This is an unofficial project, not affiliated with Valve or Meta. Product names
and trademarks belong to their owners. See the notices included in the APK for
third-party components. No new source-code license is granted by this repository.
