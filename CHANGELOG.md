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

