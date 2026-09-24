# Alyx Jailbreak 0.173-r1 — runtime packaging hotfix

## Русский

Исправлена ошибка упаковки 0.173: в APK отсутствовали `assets/runtime/manifest.json` и `assets/runtime/payload.zip`. Поэтому на чистой копии Windows-данных лаунчер не устанавливал необходимые ARM64/Linux-библиотеки.

- Восстановлен полный комплект runtime из 0.172: **147 файлов, 430 012 064 байта после распаковки**. Архив и манифест побайтно сверены с предоставленным APK 0.172.
- Сохранены прежние пути внутри выбранной папки игры (по умолчанию `/sdcard/AlyxJailbreak`): `client-runtime`, `game/bin/linuxsteamrtarm64`, `game/hlvr/bin/linuxsteamrtarm64`, `pango-runtime`, `panorama-runtime`, `usr/lib/aarch64-linux-gnu`, `gnu-unique`, `loader-cycle` и `game/hlvr/gameinfo.gi`; создаётся папка `lib`.
- Сохранены резервирование заменяемых файлов и защита пользовательского `gameinfo.gi`. Сохранения и игровые VPK не входят в распаковываемый комплект.
- Сборщик теперь обязательно добавляет runtime и проверяет его состав, размеры, SHA256 и наличие обоих assets в готовом APK. Регрессионная проверка отклоняет ошибочный 0.173.
- Android versionName **0.173-r1**, versionCode **363**; сертификат подписи прежний. Возможности 0.173 сохранены, оптимизированный режим остаётся alpha.

Установите `Alyx-Jailbreak-0.173-r1.apk` поверх предыдущей версии. Откройте лаунчер и нажмите **Проверить кеш**: он проверит и установит недостающие библиотеки. Подготовка runtime также выполняется перед запуском. Удалять приложение или заново копировать игровые данные не нужно.

Проверена полная распаковка производственным Java-установщиком в пустую тестовую папку: все 147 путей, размеры и SHA256, создание `lib` и повторный быстрый запуск. Также пройдены тесты восстановления, резервирования и сохранения пользовательских настроек. На Quest установлен 0.173-r1 и вызван штатный установщик APK в выбранной папке `/storage/emulated/0/AlyxJailbreak`: обработаны 147 файлов, SHA256 всех 146 управляемых файлов совпали; пользовательский `game/hlvr/gameinfo.gi` сохранён. Полный игровой прогон не выполнялся.

## English

Fixes a 0.173 packaging regression: `assets/runtime/manifest.json` and `assets/runtime/payload.zip` were missing, preventing installation of the ARM64/Linux runtime with fresh Windows game data.

- Restores the complete 0.172 runtime: **147 files, 430,012,064 unpacked bytes**. Both assets match the supplied 0.172 APK byte for byte.
- Preserves all destination paths under the selected game folder (default `/sdcard/AlyxJailbreak`): `client-runtime`, `game/bin/linuxsteamrtarm64`, `game/hlvr/bin/linuxsteamrtarm64`, `pango-runtime`, `panorama-runtime`, `usr/lib/aarch64-linux-gnu`, `gnu-unique`, `loader-cycle` and `game/hlvr/gameinfo.gi`, plus the `lib` directory.
- Retains replacement backups and custom gameinfo protection. The payload does not manage saves or game VPK files.
- The build now requires the runtime, verifies every size and SHA256, and rejects APKs with missing or altered runtime assets. The regression test rejects the broken 0.173 APK.
- Android versionName **0.173-r1**, versionCode **363**, unchanged signing certificate. All 0.173 features are retained; optimized mode remains alpha.

Install over the previous version and select **Check files** in the launcher to verify and install missing libraries. Runtime preparation also runs before launch. No uninstall or game-data recopy is needed.

The production Java installer was tested with all 147 files in a fresh directory, verifying every destination and SHA256, the `lib` directory and the repeated quick path. Repair, backup and custom-settings tests also passed. On Quest, 0.173-r1 was installed and its production runtime installer processed all 147 files under the selected `/storage/emulated/0/AlyxJailbreak` folder. All 146 managed file hashes match; custom `game/hlvr/gameinfo.gi` was preserved. A full gameplay run was not performed.

Verify the APK using the attached `SHA256SUMS.txt`.

# Alyx Jailbreak 0.173

## Русский

Сборка из последней `main`: `04548e3913934a4e2e25495cfd374f49043c2b36`. Android versionName **0.173**, versionCode **362**.

- Steam Workshop прямо на Quest: каталог, скачивание через Steam Guard и установка, включая дополнения-замены без addoninfo. Для скачивания нужен аккаунт с Alyx.
- Отдельный выбор языка интерфейса/субтитров игры.
- Три режима рендера: без фовеации, с фовеацией, с фовеацией и центральным MSAA 2×; независимое мягкое масштабирование.
- Исправлены файловые блокировки WebM-видео и переполнение реестра ресурсов глубины, выявленное при вылете в настройках.
- Оптимизированный режим **alpha**, по умолчанию выключен: редактируемый пресет 67% / мягкая фильтрация / фовеация с центральным MSAA. Качество графики сохраняется отдельно для обычного и alpha-режимов.
- Проверка обновлений и автоскачивание APK из GitHub с проверкой SHA256, подписи, пакета и версии. Установку подтверждает Android.

Установите `Alyx-Jailbreak-0.173.apk` поверх предыдущей версии без удаления приложения. Подпись прежняя, сохранения остаются. Инструкции: [README.ru.md](https://github.com/alferiko/alyx-jailbreak-releases/blob/main/README.ru.md).

Все три нативных варианта пересобраны. Пройдены локальные тесты Workshop, runtime, конфигурации запуска, локализации, рендера и настроек. Проверены подпись, сертификат, метаданные, выравнивание APK и неизменность полезного содержимого при присвоении номера версии. Этот APK не проходил новую установку и игровой прогон на Quest; последнее исправление вылета в настройках требует проверки на устройстве. Alpha не гарантирует 72 FPS или отсутствие подлагиваний. Объёмный туман остаётся выключенным.

## English

Built from latest source `main`: `04548e3913934a4e2e25495cfd374f49043c2b36`. Android versionName **0.173**, versionCode **362**.

- Steam Workshop on Quest: browsing, Steam Guard downloads and installation, including replacement addons without addoninfo. Downloads require an account that owns Alyx.
- Separate game interface/subtitle language selection.
- Three render modes: no foveation, foveation, and foveation with central MSAA 2×; independent soft image scaling.
- Fixes for WebM file locks and depth-resource registry exhaustion identified in the settings crash.
- Optional **alpha** optimized mode, off by default: editable 67% / soft filtering / foveation with central MSAA preset. Graphics quality is saved separately for normal and alpha modes.
- GitHub update checks and automatic APK downloads with SHA256, certificate, package and version verification. Android confirms installation.

Install `Alyx-Jailbreak-0.173.apk` over the previous version without uninstalling. The signing certificate is unchanged and saves are retained. Instructions: [README.md](https://github.com/alferiko/alyx-jailbreak-releases/blob/main/README.md).

All three native variants were rebuilt. Local Workshop, runtime, startup configuration, localization, rendering and settings tests passed. APK signature, certificate, metadata, alignment and unchanged payload after version packaging were verified. This APK has not had a new Quest installation/gameplay run; the latest settings-crash fix still needs on-device reproduction testing. Alpha does not guarantee 72 FPS or stutter-free gameplay. Volumetric fog remains disabled.

Verify the download against the attached `SHA256SUMS.txt`.

## 0.172 — asymmetric stereo projection

- Apply `vr_symmetric_fov 0` automatically on every launch in all four FDM/MSAA modes.
- Addresses stretched geometry and inconsistent eye images observed on affected headsets. Correct output was confirmed by the project owner in the Turnip diagnostic build.
- Retain Turnip, memory optimizations, pipeline caching, RU/EN launcher and bundled runtime from 0.171-r3. No heavy tracing or diagnostic UI.
- APK versionName 0.172, versionCode 174. Install over 0.171-r3 or diagnostic builds; preserve game data and saves.
- This is not a general MSAA or stutter fix. Full visual validation of all four modes is still pending.

## 0.172 — асимметричная стереопроекция

- `vr_symmetric_fov 0` автоматически применяется при каждом запуске во всех четырёх режимах фовеации/MSAA.
- Исправление направлено на растянутую геометрию и несовпадающие изображения глаз. Владелец проекта подтвердил целостную картинку в диагностике с Turnip.
- Сохранены Turnip, оптимизации памяти, кэш конвейеров, лаунчер RU/EN и runtime 0.171-r3. Тяжёлой трассировки и диагностического интерфейса нет.
- Версия APK 0.172, versionCode 174. Установка поверх 0.171-r3 или диагностики, без удаления данных и сохранений.
- Это не общее исправление MSAA или подлагиваний. Полная визуальная проверка всех четырёх режимов ещё не завершена.


# 0.171-r3

## Русский
- Исправлен вылет при запуске с чистой копией Windows-данных, содержащей выбор DirectX в game/hlvr/cfg/boot.vcfg. Перед каждым запуском лаунчер автоматически выбирает Vulkan.
- Исходный boot.vcfg сохраняется в .runtime-backups/0.171-r3; остальные параметры файла сохраняются. Отсутствующий файл создаётся автоматически.
- Включены все библиотеки runtime из r2, в том числе исправление ошибки 20. Ручные патчи и повторное копирование игры не нужны: установите APK поверх прежнего и нажмите «Запустить».
- Версия 0.171-r3, Android versionCode 173. Библиотеки рендера и assets побайтно совпадают с r2; тяжёлая статистика не добавлялась.
- Проверены подпись APK, тесты миграции/резервирования/повторного запуска. На Quest намеренно возвращён проблемный -dx11: APK самостоятельно заменил его на -vulkan и прошёл прежнее место вылета. Полное прохождение не проверено.

## English
- Fixed startup crashes with fresh Windows game data selecting DirectX in game/hlvr/cfg/boot.vcfg. The launcher now selects Vulkan before every launch.
- Original boot.vcfg is backed up under .runtime-backups/0.171-r3; unrelated settings are preserved. Missing boot configuration is created automatically.
- Includes the complete r2 runtime and error-20 fix. Install over the previous APK and Launch; manual patches or recopying game data are unnecessary.
- Version 0.171-r3, Android versionCode 173. Native rendering libraries and assets are byte-identical to r2; no heavy statistics added.
- APK signature and migration/backup/idempotence tests passed. On Quest, the failing -dx11 configuration was deliberately restored: the APK automatically changed it to -vulkan and passed the previous crash point. Full playthrough not tested.

# 0.171-r2

## Русский
- Исправлена ошибка запуска 20 после чистой установки Windows-данных: добавлены две обязательные библиотеки GNU-unique, пропущенные в APK 0.171, и две библиотеки loader-cycle.
- Полный комплект: 147 файлов. Android versionCode 172, versionName 0.171.
- Рендер и Java-код побайтно совпадают с 0.171. Тяжёлая трассировка не добавлялась.
- Проверены подпись APK, распаковка и SHA256 всех 147 файлов. На Quest установщик автоматически добавил четыре библиотеки; запуск прошёл самопроверку, вызвавшую ошибку 20, и дошёл до инициализации рендера. Полное прохождение не проверено.
- Установите APK поверх предыдущего; повторная распаковка Windows-данных не нужна.

## English
- Fixed startup error 20 after a fresh Windows-data installation: bundled the two mandatory GNU-unique libraries omitted in 0.171 and two loader-cycle libraries.
- Complete payload: 147 files. Android versionCode 172, versionName 0.171.
- Renderer and Java bytecode are byte-identical to 0.171. No heavy tracing added.
- APK signature and fresh extraction/SHA256 of all 147 files verified. On Quest, the installer supplied the four libraries automatically; startup passed the failing self-test and reached renderer initialization. A full playthrough has not been tested.
- Install over the previous APK; no need to extract Windows game data again.

# 0.171

## English
- Added persistent RU/EN launcher-only language switch and translated UI messages.
- Application version: 0.171 (Android versionCode 171).
- Preserved the four lean171 rendering modes and volumetric-fog workaround.
- MSAA quality and gameplay stutter investigations remain open.

## Русский
- Добавлен сохраняемый переключатель RU/EN только для лаунчера, переведены сообщения.
- Версия приложения: 0.171 (Android versionCode 171).
- Сохранены четыре режима рендера lean171 и обход зависаний с выключенным туманом.
- Качество MSAA и подлагивания остаются предметом дальнейшей работы.

Quest startup and display were additionally confirmed by the owner after installation. / Запуск и изображение на Quest дополнительно подтверждены владельцем после установки.
