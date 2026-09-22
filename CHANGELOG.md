# 0.171-r3

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

