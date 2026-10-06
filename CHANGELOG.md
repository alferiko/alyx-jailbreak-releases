# Alyx Jailbreak 0.180

## Русский

- Единая сборка для Quest 2, Quest Pro, Quest 3, PICO 4 и PICO 4 Ultra.
- Добавлен режим Extreme.
- Добавлены загрузка игры через Steam и импорт сохранений из Steam Cloud.
- Улучшены стабильность, управление и работа графических режимов.

Устанавливайте APK поверх текущей версии, без удаления приложения.

## English

- One build for Quest 2, Quest Pro, Quest 3, PICO 4 and PICO 4 Ultra.
- Added Extreme mode.
- Added game downloads through Steam and save imports from Steam Cloud.
- Improved stability, controls and graphics modes.

Install the APK over your current version without uninstalling the app.

---

# Alyx Jailbreak 0.179 — build 889

## Русский

Исправлен вылет у лестницы в главе 9: разбор строк на рабочих потоках клиента и рендера мира переведён на системный обработчик Android. Это устраняет обращение к некорректному состоянию локали гостевой C-библиотеки на нативном потоке.

Сборка **889**, версия **0.179**, заново собрана из `main` `1a5d785647f4ef32b540194af1f29548367af1bd`. Сохранены исправления 0.178: выборочная подготовка шейдеров при несовпадении игровых файлов, обработка ошибок на нативном потоке, исключение модов из зависимостей каталога и однократная очистка четырёх кешей после обновления сборки. Настройки, сохранения и игровые архивы сохраняются.

Проверены подпись и прежний сертификат, выравнивание, **19 библиотек**, **150 файлов runtime** и все три каталога рендера. Тяжёлая диагностика, покадровое профилирование и runtime-телеметрия отключены. Runtime и 16 библиотек вне host не изменились относительно v877.

Исправление проверено на Android: 16 форматов строк, 8 рабочих потоков, по 10 000 итераций. На тестовой **v888** пользователь прошёл проблемную лестницу без вылета. **Новая релизная v889 отдельно в игре на гарнитуре не проверялась.** Это исправление конкретного вылета, а не подтверждение полного прохождения кампании. Ранее отмеченный сигнал 11 при выходе пользователя из игры этим выпуском не исправлен.

Установите [APK](https://github.com/alferiko/alyx-jailbreak-releases/releases/download/v0.179/Alyx-Jailbreak-0.179.apk) поверх приложения, без удаления. [Инструкция](https://github.com/alferiko/alyx-jailbreak-releases/blob/main/README.ru.md). Контрольная сумма — в `SHA256SUMS.txt`.

## English

Fixes the crash near the stairs in chapter 9. String parsing on client and world-renderer worker threads now uses the Android system parser, avoiding invalid access to the guest C library's thread-local locale state.

Build **889**, version **0.179**, freshly built from `main` `1a5d785647f4ef32b540194af1f29548367af1bd`. Retains the 0.178 fixes: selective shader preparation on game-file mismatches, native-worker failure handling, exclusion of mods from catalog dependencies and one-time clearing of four caches after a build-number change. Settings, saves and game archives are preserved.

Verified signature and unchanged certificate, alignment, **19 libraries**, **150 runtime files** and all three renderer catalogs. Heavy diagnostics, frame profiling and runtime telemetry are disabled. Runtime and 16 non-host libraries are unchanged from v877.

The fix passed an Android regression with 16 string formats, 8 workers and 10,000 iterations per worker. On test build **v888**, the user passed the previously crashing staircase. **The fresh release build v889 has not been separately tested in headset gameplay.** This addresses the specific crash, without claiming full campaign coverage. The previously observed signal 11 during a user-initiated exit is not fixed by this release.

Install the [APK](https://github.com/alferiko/alyx-jailbreak-releases/releases/download/v0.179/Alyx-Jailbreak-0.179.apk) over the existing app, without uninstalling. [Instructions](https://github.com/alferiko/alyx-jailbreak-releases/blob/main/README.md). Check `SHA256SUMS.txt`.

---

# Alyx Jailbreak 0.178 — build 877

## Русский

Исправлен вылет при подготовке шейдеров на старте, когда игровые файлы отличаются от эталона каталога, в том числе после сжатия игровых ресурсов.

- Ошибки проверки обрабатываются на отдельном нативном потоке, без прежнего аварийного разворачивания стека игры.
- При несовпадении файлов предварительно компилируются только пайплайны, все шейдерные стадии которых точно совпали с уже загруженными игрой. Остальные пропускаются и остаются на обычной компиляции. Если совпадений нет, игра продолжает запуск без импорта подготовленного кеша.
- Пользовательские моды исключены из перечня зависимостей встроенного каталога.
- При первом запуске после изменения номера сборки однократно очищаются четыре кеша шейдеров/pipeline. Сохранения, настройки и игровые архивы сохраняются.
- Во всех трёх вариантах рендера сохранён релизный режим без тяжёлой диагностики и покадрового профилирования.

Версия **0.178**, сборка **877**, исходный `main`: `d1e5ae59da94f3ce4900bbb4936ee97158f3df59`. Публикуется тот же подписанный APK, который прошёл беглую проверку на Quest 3. Проверены **19 библиотек**, **150 файлов runtime**, три каталога и прежний сертификат подписи. Нативные тесты выборочной подготовки и обработки ошибок прошли под ASan/UBSan.

На проверенном Quest при отличающемся индексе VPK успешно подготовлены и импортированы 44 графических и 3 вычислительных пайплайна. Это подтверждает работу выборочного режима, но не полное покрытие шейдеров или кампании. Ещё не загруженные шейдеры при несовпадении файлов остаются на обычной компиляции. Известное ограничение: Android зарегистрировал сигнал 11 при выходе пользователя из игры; исправление завершения процесса в этот выпуск не входит.

Установите APK поверх приложения. Владельцам тестовой **0.178 / v877** повторная установка не нужна: файл идентичен. [Инструкция](https://github.com/alferiko/alyx-jailbreak-releases/blob/main/README.ru.md). SHA256 — в `SHA256SUMS.txt`.

## English

Fixes the startup crash during shader preparation when installed game assets differ from the catalog reference, including after game-resource compression.

- Validation failures are handled on a native worker, avoiding the previous exception unwind through the game's stack.
- On an asset mismatch, only pipelines whose complete shader stages exactly match modules already loaded by the game are prepared. Other pipelines use normal compilation. With no matches, startup continues without importing a prepared cache.
- User mods are excluded from bundled catalog dependencies.
- Four shader/pipeline caches are cleared once on the first launch after a build-number change. Saves, settings and game archives are preserved.
- All three renderers retain the release configuration with heavy diagnostics and frame profiling disabled.

Version **0.178**, build **877**, source `main`: `d1e5ae59da94f3ce4900bbb4936ee97158f3df59`. This is the same signed APK checked on Quest 3. Verified **19 libraries**, **150 runtime files**, three catalogs and the unchanged signing certificate. Selective preparation and failure-handling tests passed under ASan/UBSan.

On the tested Quest, 44 graphics and 3 compute pipelines were successfully prepared and imported despite a VPK index mismatch. This verifies selective recovery, not full shader or campaign coverage. With mismatched assets, shaders not yet loaded use normal compilation. Known limitation: Android recorded signal 11 during a user-initiated game exit; shutdown handling is not fixed in this release.

Install over the existing app. Users already on test **0.178 / v877** do not need to reinstall: the APK is identical. [Instructions](https://github.com/alferiko/alyx-jailbreak-releases/blob/main/README.md). Check `SHA256SUMS.txt`.

---

# Alyx Jailbreak 0.177 — build 870

## Русский

Новая сборка из `main` **9e5b66d8f3851c244b64dd95a48aac9eaa5e7cd2**: Java, ресурсы и все три нативных варианта рендера собраны заново. Тестовый APK v869 использован для сверки. Версия **0.177**, versionCode **870**, пакет `com.alf.alyxquest`, сертификат подписи прежний.

- Новый интерфейс лаунчера RU/EN с прежней иконкой.
- Рендер MK2: обновлённый PGO-компилятор Turnip, кеш VRS, исправление блокировки readback, подготовка 606 pipeline с отдельными каталогами для всех трёх вариантов рендера.
- Пять режимов AA: выключено, MSAA 2×, SMAA Medium, Ultra и Ultra со смягчением. VRS доступен без AA и с SMAA; MSAA временно отключает его, сохраняя выбор галочки. TAA из публичного меню убран.
- Обратимые пресеты: **«Качество» — 85%, «Производительность» — 50%**, текстуры **1024 пикселя**, автоматический пул. **При первом переходе на MK2 применяется «Производительность» с 50% рендера.** Параметры можно изменить или вернуть кнопкой «Вернуть мои настройки». Ранее перенесённые настройки тестовой MK2-сборки сохраняются; 67% остаётся ручным выбором.
- Возобновление загрузок Workshop с проверкой блоков; улучшенное сжатие кеша с сохранением детализации интерфейса, оружия/рук и читаемых надписей, усиленное восстановление после сбоев. Уже потерянная детализация требует оригинальных файлов.
- Во всех рендерах отключены тяжёлая диагностика, покадровые профилировщики и runtime-телеметрия. Диагностические маркеры не включают их обратно.

Проверены подпись, выравнивание, **19 библиотек**, **150 файлов runtime** и их штатная распаковка, **6573 записи хешей сборочных входов**, каталоги, пресеты, Workshop и восстановление кеша. Все прежние 148 файлов runtime сохранены.

Для v869 документированы шесть холодных запусков тяжёлого сохранения на Quest 3 минимум по 150 секунд. **Новая сборка 870 отдельно на гарнитуре в игре не проверялась.** Каталог не гарантирует отсутствие рывков или полное покрытие кампании; конкретное устранение утечки памяти фонарика не заявляется.

Установите APK поверх приложения. [Полная инструкция](https://github.com/alferiko/alyx-jailbreak-releases/blob/main/README.ru.md). SHA256 — в приложенном `SHA256SUMS.txt`.

## English

Fresh build from source `main` **9e5b66d8f3851c244b64dd95a48aac9eaa5e7cd2**: Java, resources and all three native renderers were rebuilt. Test APK v869 was used as a reference. Version **0.177**, versionCode **870**, package `com.alf.alyxquest`; signing certificate unchanged.

- Redesigned RU/EN launcher, retaining its existing icon.
- MK2 rendering: updated PGO Turnip compiler, cached VRS, a readback-lock fix and preparation of 606 pipelines with separate catalogs for all three renderers.
- Five AA modes: Off, MSAA 2×, SMAA Medium, Ultra and Ultra with softening. VRS supports Off/SMAA; MSAA temporarily disables it while retaining the checkbox choice. Experimental TAA is removed from the public menu.
- Reversible presets: **Quality — 85%, Performance — 50%**, **1024-pixel textures**, automatic pool. **The first migration to MK2 applies Performance at 50% render resolution.** Adjust settings or use Restore my settings. Previously migrated MK2 test-build preferences remain; 67% is still a manual choice.
- Resumable, chunk-verified Workshop downloads; cache compression preserves UI, hands/weapons and readable text detail, with stronger recovery. Previously removed detail requires original files.
- Heavy diagnostics, frame profiling and runtime telemetry are disabled in every renderer. Diagnostic markers cannot re-enable them.

Verified signature, alignment, **19 libraries**, **150 runtime files** and their production extraction, **6573 source-input hash records**, catalogs, presets, Workshop and cache recovery. All previous 148 runtime entries are preserved.

Six cold Quest 3 heavy-save launches of at least 150 seconds each are documented for v869. **The new build 870 has not been separately tested in headset gameplay.** The catalog does not guarantee stutter-free rendering or full campaign coverage; no specific flashlight memory-leak cure is claimed.

Install over the existing app. [Full instructions](https://github.com/alferiko/alyx-jailbreak-releases/blob/main/README.md). Check the attached `SHA256SUMS.txt`.

# Alyx Jailbreak 0.176 — hotfix, build 823

## Русский

Версия остаётся **0.176**, versionCode повышен до **823** для обновления поверх прежней сборки 807 и тестовой 822. Основа — проверенная на Quest 3 сборка `0.176-hotfix.822-rc1` из `main` `53ef8506a0c81509e37352532366c31a9404789d`. От неё отличаются только метаданные версии; код, библиотеки и ресурсы совпадают побайтно.

- По умолчанию возвращены исходные теневые сравнения в шейдерах и генерация карт теней. Оптимизированный режим больше не подменяет этот путь; служебные файлы для включения хотфикса не нужны.
- На проблемном сохранении пользователь подтвердил отсутствие зависания при появлении/скрытии рук и работу фонарика. В контрольном журнале GPU fault не зарегистрирован.
- Остальные оптимизации, пресеты, сглаживание, растительность и runtime сохранены. Тяжёлая диагностика отключена во всех трёх вариантах рендера.
- Это проверенный обход зависания на пути теневых шейдеров. Устранение конкретной утечки памяти не подтверждено. Возможно возвращение прежнего мерцания теней и затрат на их отрисовку; отдельная проверка главы 8 не выполнялась.

Установите обновлённый `Alyx-Jailbreak-0.176.apk` поверх приложения. Версия в интерфейсе остаётся 0.176; в информации о пакете проверьте **versionCode 823**. Подпись прежняя, настройки и сохранения сохраняются. Автообновление различает сборки по контрольной сумме и коду версии.

Проверены подпись, выравнивание, 19 нативных библиотек, 148 файлов runtime и отключение тяжёлой диагностики. [Инструкция](https://github.com/alferiko/alyx-jailbreak-releases/blob/main/README.ru.md).

## English

The version remains **0.176**, with versionCode raised to **823** for installation over build 807 and test build 822. Based on Quest-tested `0.176-hotfix.822-rc1` from source `main` `53ef8506a0c81509e37352532366c31a9404789d`. Only version metadata differs from that APK; code, libraries and assets are byte-identical.

- Restores original shader shadow comparisons and shadow-map generation by default. Performance mode no longer rewrites this path; no marker files are needed to enable the hotfix.
- On the problematic save, the user confirmed no freeze when hands appear/disappear and a working flashlight. The observation log recorded no GPU fault.
- Other optimizations, presets, antialiasing, vegetation and runtime are retained. Heavy diagnostics are disabled in all three renderers.
- This is a verified workaround for a shadow-shader-path freeze. A specific memory-leak fix has not been established. Earlier shadow flicker and rendering costs may return; chapter 8 was not separately tested.

Install the updated `Alyx-Jailbreak-0.176.apk` over the existing app. The displayed version stays 0.176; package information should show **versionCode 823**. Signing certificate, settings and saves are preserved. The updater distinguishes builds by checksum and version code.

Verified signature, alignment, 19 native libraries, 148 runtime files and disabled heavy diagnostics. [Instructions](https://github.com/alferiko/alyx-jailbreak-releases/blob/main/README.md).

Verify the current APK with the updated `SHA256SUMS.txt`. This asset replaces the original build 807 under the same release tag and download URL.

# Alyx Jailbreak 0.176

## Русский

Основа — проверенная в игре на Quest 3 сборка 0.176-rc1 (806), исходный `main` `32ff1d35ab21403a03ac107059f98b95a49bdf88`. Публичная версия **0.176**, versionCode **807**, пакет `com.alf.alyxquest`. Изменены только метаданные версии; код, библиотеки и ресурсы побайтно совпадают с проверенным APK. Сертификат подписи прежний.

- Кнопки **«Качество»** и **«Скорость»** однократно заполняют настройки графики. «Качество»: **85%** рендера, **SMAA Ultra + TAA (тест)**, упрощение моделей выключено. «Скорость»: **67%**, **SMAA Ultra + смягчение**, упрощение моделей включено. Оба пресета ставят текстуры 1024, mip 0, автоматический пул, линейное масштабирование, обычную репроекцию, экономию памяти и упрощение/скрытие растительности; MQSR выключен. Ручные изменения сохраняются до повторного нажатия пресета. Качество из меню самой игры остаётся отдельной настройкой.
- Независимые настройки **AA и MQSR**. Сглаживание: выключено, MSAA 2×, SMAA Medium, SMAA Ultra, SMAA Ultra со смягчением и экспериментальный SMAA Ultra + TAA. Доступно динамическое разрешение **67–92%** с целью 36 новых игровых кадров/с. Прямой рендер без фовеации; Basic / Off для обычной репроекции, без AppSW.
- Новый пакет упрощённой растительности: **149 моделей и 152 материала**. Он устанавливается отдельным VPK и не перезаписывает исходные игровые архивы. Чтобы увидеть растения, отключите «Скрывать растительность»; оба готовых пресета включают скрытие. Xen-растения в пакет не входят, коллизии сохранены.
- Обновлён драйвер Turnip: исправления синхронизации GMEM, времени жизни дескрипторов, учёта памяти, повторного использования констант и проходов компилятора шейдеров. Включены настройки экономии памяти и упрощения геометрии.
- Исправлены ориентация рук, двойное нажатие для режима стрельбы пистолета и анимированный текст загрузки. Доступен опциональный трекинг пальцев камерами с возвратом к контроллерам. Фонарик сохранён при отключении мерцающих теней в режиме производительности.
- Сохранены Workshop с установкой целых VPK и сжатие кеша. После успешного сжатия его элементы управления скрываются; предварительно сжатый кеш распознаётся. Переводы лаунчера дополнены.

Отдельный переключатель **«Производительность → Вкл»** по-прежнему задаёт **67%** и текстуры **1024**, не меняя бюджет пула. Кнопки «Качество»/«Скорость» дополнительно переводят пул в автоматический режим.

- Пользователь подтвердил проверку 0.176-rc1 (806) в игре на Quest 3. У финального APK изменён только AndroidManifest.xml с номером версии; весь исполняемый код, 19 нативных библиотек и ресурсы совпадают с проверенной сборкой.
- Проверены подпись, прежний сертификат, выравнивание, все три варианта рендера, настройки AA/MQSR и закреплённый драйвер. Все **148 файлов runtime** проверены по размеру и SHA256 и распакованы штатным установщиком. Прежние 147 записей сохранены; добавлен только VPK растительности. Все 301 ресурса VPK прошли CRC/SHA256-проверку.
- Пройдены тесты пресетов, ручных изменений, локализации, Workshop, подключения растительности и распаковки/восстановления runtime.
- Тяжёлая диагностика отключена во всех трёх вариантах: GPU/покадровые трассировки, дампы шейдеров, учёт аллокаций, Vulkan validation, диагностические пробы и режимы Android debug/profileable. Сохранены ограниченные сводные счётчики и события жизненного цикла проверенной сборки.
- SMAA Ultra + TAA остаётся экспериментальным. Динамическое разрешение не гарантирует целевую частоту кадров. Полное прохождение, все переходы глав и все растения/LOD не проверены. Объёмный туман остаётся выключенным.

Установите `Alyx-Jailbreak-0.176.apk` поверх предыдущей версии и нажмите **Проверить кеш**. Настройки и сохранения сохраняются. [Инструкция](https://github.com/alferiko/alyx-jailbreak-releases/blob/main/README.ru.md).

## English

Based on 0.176-rc1 (806), confirmed in gameplay on Quest 3, from source `main` `32ff1d35ab21403a03ac107059f98b95a49bdf88`. Public version **0.176**, versionCode **807**, package `com.alf.alyxquest`. Only version metadata changed; code, libraries and assets are byte-identical to the tested APK. The signing certificate is unchanged.

- **Quality** and **Speed** buttons apply graphics settings once. Quality: **85%** render resolution, **SMAA Ultra + TAA (test)**, model simplification off. Speed: **67%**, **SMAA Ultra + softening**, model simplification on. Both set textures to 1024, mip 0, automatic texture pool, linear scaling, basic reprojection, memory savings and vegetation simplification/hiding; MQSR is off. Manual changes remain until the preset is selected again. In-game graphics quality remains independent.
- Independent **AA and MQSR** settings. AA options: Off, MSAA 2×, SMAA Medium, SMAA Ultra, SMAA Ultra with softening and experimental SMAA Ultra + TAA. Optional **67–92% dynamic resolution** targets 36 new game frames/s. Direct rendering without foveation; Basic / Off reprojection without AppSW.
- Bundled simplified vegetation: **149 models and 152 materials**, installed as a separate VPK without overwriting stock game archives. Disable Hide vegetation to see plants; both presets enable hiding. Xen plants are excluded and collision data is preserved.
- Updated Turnip driver with GMEM synchronization, descriptor lifetime, memory accounting, constant reuse and shader compiler fixes. Memory-saving and geometry-simplification options are included.
- Corrected hand alignment, pistol double-press binding and animated loading text. Optional camera finger tracking supports controller fallback. The flashlight remains available while flickering shadows are suppressed in Performance mode.
- Packed Workshop installation and cache compression are retained. Compression controls hide after successful completion, precompressed caches are recognized, and launcher translations are expanded.

The separate **Performance → On** switch still sets **67%** render resolution and **1024** textures without changing the pool budget. Quality/Speed additionally reset the pool to automatic.

- The user confirmed gameplay testing of 0.176-rc1 (806) on Quest 3. Only AndroidManifest.xml version metadata changed for the final APK; all executable code, 19 native libraries and assets match the tested build.
- Verified signature, unchanged certificate, alignment, all three renderers, AA/MQSR settings and the pinned driver. All **148 runtime files** passed size/SHA256 checks and production extraction. The original 147 entries are preserved; only the vegetation VPK was added. All 301 VPK resources passed CRC/SHA256 checks.
- Preset/manual-override, localization, Workshop, vegetation mounting and runtime extraction/recovery tests passed.
- Heavy diagnostics are disabled in all three renderers: GPU/per-frame tracing, shader dumps, allocation tracing, Vulkan validation, diagnostic probes and Android debug/profileable modes. Bounded aggregate counters and lifecycle events from the tested build remain enabled.
- SMAA Ultra + TAA is experimental. Dynamic resolution does not guarantee the target frame rate. A full playthrough, every chapter transition and all plants/LODs have not been verified. Volumetric fog remains disabled.

Install `Alyx-Jailbreak-0.176.apk` over the previous version and select **Check files**. Settings and saves are retained. [Instructions](https://github.com/alferiko/alyx-jailbreak-releases/blob/main/README.md).

Verify the download using the attached `SHA256SUMS.txt`.

# Alyx Jailbreak 0.175

## Русский

Последний `main` с исправлением пресета: `2aeef3616253f843718685930e9bb5332e2ce381`. Android versionName **0.175**, versionCode **682**. Прежние пакет и подпись позволяют установить обновление поверх приложения.

- Релизный профиль прямого рендера и драйвер XEMU с 23 проверенными патчами памяти, синхронизации и восстановления после ошибок.
- **Фовеация и MSAA выключены.** Репроекция Basic / Off; в Basic — до 36 новых игровых кадров/с с системной коррекцией поворотов. AppSW и репроекция по глубине недоступны.
- При выборе **«Производительность → Вкл» — 67% рендера**, мягкое масштабирование, текстуры до **1024**, отключение теней и сокращение эффектов. Бюджет пула текстур не меняется. Ручные настройки сохраняются до повторного выбора пресета.
- Асинхронная передача изображений глаз, общий/сохраняемый кеш конвейеров и исправление темпа симуляции.
- Опциональное сжатие кеша прямо на Quest с паузой и продолжением. Оно уменьшает детализацию подходящих текстур и крупных статических моделей. Бекапы удаляются после обработки каждого файла; **«Завершить досрочно» откатывает только незавершённый файл**. Для полного возврата детализации нужны оригинальные игровые файлы. Сохранения, runtime и Workshop не затрагиваются.
- Сохранены упакованные дополнения Workshop и все **147 файлов runtime**, совпадающие с 0.172 по хешам и путям. Проверены все **17 нативных библиотек**.

Проверены подпись, выравнивание, комплект библиотек, полная распаковка runtime, 74 проверки Workshop, 2443 проверки сжатия, настройки и нативный темп кадров. RC 673 с тем же драйвером загружал `s0/quick` на Quest; финальная 0.175 не проходила новый игровой прогон и полную визуальную проверку. Рост FPS не обещается, сглаживание и объёмный туман выключены.

[Скачать APK](https://github.com/alferiko/alyx-jailbreak-releases/releases/download/v0.175/Alyx-Jailbreak-0.175.apk), установить поверх предыдущей версии и нажать **Проверить кеш**. [Инструкция](https://github.com/alferiko/alyx-jailbreak-releases/blob/main/README.ru.md).

## English

Latest `main` with the preset correction: `2aeef3616253f843718685930e9bb5332e2ce381`. Android versionName **0.175**, versionCode **682**. Package and signing certificate are unchanged for installation over the existing app.

- Direct-rendering release profile and XEMU driver with 23 verified memory, synchronization and failure-recovery patches.
- **Foveation and MSAA are disabled.** Reprojection offers Basic / Off; Basic allows up to 36 new game frames/s with system rotation correction. AppSW and depth reprojection are unavailable.
- Selecting **Performance → On sets 67% render resolution**, soft scaling, textures up to **1024**, shadows off and reduced effects. The texture-pool budget is unchanged. Manual settings remain until the preset is explicitly selected again.
- Asynchronous eye transfer, shared/persistent pipeline caches and the simulation-timing correction.
- Optional on-device cache compression with Pause/Resume. It reduces detail in eligible textures and large static models. Backups are deleted after each completed file; **Stop safely rolls back only the unfinished file**. Restoring full detail requires the original game files. Saves, runtime and Workshop addons are excluded.
- Packed Workshop addons and all **147 runtime files** are retained, with 0.172 hashes and destination paths. All **17 native libraries** were checked.

Verified signature, alignment, library payload, full runtime extraction, 74 Workshop checks, 2,443 compression checks, settings and native frame pacing. RC 673 reached `s0/quick` on Quest with the same driver; final 0.175 has not had a new gameplay run or full visual acceptance test. No FPS gain is promised; antialiasing and volumetric fog are disabled.

[Download APK](https://github.com/alferiko/alyx-jailbreak-releases/releases/download/v0.175/Alyx-Jailbreak-0.175.apk), install over the previous version and select **Check files**. [Instructions](https://github.com/alferiko/alyx-jailbreak-releases/blob/main/README.md).

Verify the download with the attached `SHA256SUMS.txt`.

# Alyx Jailbreak 0.174

## Русский

Сборка из `main`: `b2302d504d22f6dfd12c5377d51d081ce3e21991`. Android versionName **0.174**, versionCode **485**; пакет и сертификат подписи прежние.

- Исправлена установка Workshop: VPK остаются целыми архивами, включая разделённые и несколько архивов; игровые ресурсы не распаковываются в отдельные файлы. Сохраняются или создаются метаданные дополнения. Новые папки получают короткие имена до 20 букв/цифр, существующие управляемые папки сохраняются при обновлении. Проверяются CRC, поддерживаются отмена и восстановление после сбоя.
- Общий кеш графических конвейеров, увеличенный сохраняемый кеш и параллельная компиляция центрального MSAA. Выборочный обход FlushAndWait сохраняет обратные вызовы завершения.
- Оптимизированный режим выставляет **максимальное разрешение текстур 1024**, масштаб 67%, мягкую фильтрацию и центральный MSAA. **Бюджет пула текстур не меняется**; ручные настройки можно менять после включения пресета.
- Четыре режима рендера, включая фовеацию Quest без MSAA.
- Встроенный runtime сохранён полностью: **147 файлов**, прежние пути распаковки, размеры и SHA256 как в 0.172. Проверены все нативные библиотеки готового APK и три библиотеки режимов рендера.

Установите `Alyx-Jailbreak-0.174.apk` поверх предыдущей версии и нажмите **Проверить кеш**. Удалять приложение или заново копировать игровые данные не нужно. Дополнения включаются вручную в меню игры. [Инструкция](https://github.com/alferiko/alyx-jailbreak-releases/blob/main/README.ru.md).

Пройдены 74 проверки Workshop, тесты меню/языка, runtime, пресетов сборки и рендера. Runtime распакован производственным установщиком и сверен с 0.172. Проверены подпись, сертификат и выравнивание APK. Тестовая сборка 483 установлена на Quest, лаунчер запускался; финальный публичный APK и загрузка упакованных дополнений в игре не проходили новый игровой прогон. Оптимизированный режим остаётся alpha; объёмный туман выключен.

## English

Built from `main`: `b2302d504d22f6dfd12c5377d51d081ce3e21991`. Android versionName **0.174**, versionCode **485**; unchanged package and signing certificate.

- Workshop installation now keeps VPKs packed, including split and multiple archives, instead of extracting game resources into loose files. Addon metadata is preserved or generated. New folders use short names of up to 20 letters/digits; existing managed folders keep their path during updates. Includes CRC validation, cancellation and crash recovery.
- Shared pipeline caching, larger persistent caches and parallel central-MSAA compilation. The selective FlushAndWait bypass preserves completion callbacks.
- Optimized mode sets **maximum texture resolution to 1024**, 67% render scale, soft filtering and central MSAA. **The texture-pool budget is unchanged**; settings remain editable after applying the preset.
- Four render modes, including Quest foveation without MSAA.
- Complete bundled runtime retained: **147 files**, matching 0.172 destination paths, sizes and SHA256. All packaged native libraries and the three render-mode libraries were verified.

Install `Alyx-Jailbreak-0.174.apk` over the previous version and select **Check files**. No uninstall or game-data recopy is needed. Enable addons manually in the game's menu. [Instructions](https://github.com/alferiko/alyx-jailbreak-releases/blob/main/README.md).

Passed 74 Workshop checks and tests for menu/language, runtime, build presets and render settings. The runtime was unpacked with the production extractor and compared with 0.172. APK signature, certificate and alignment were verified. Test build 483 was installed on Quest and its launcher started; the final public APK and packed-addon loading in the game have not had a new gameplay run. Optimized mode remains alpha; volumetric fog stays disabled.

Verify the APK using the attached `SHA256SUMS.txt`.

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
