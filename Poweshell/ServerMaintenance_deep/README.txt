Справка по Server Maintenance Framework (SMF)
==============================================
Использование:
  powershell -ExecutionPolicy Bypass -File "путь\Start-SMF.ps1" [-Profile {Analyze|Day|Night}]

Параметры:
  -Profile <режим>   Выбор профиля выполнения:
                     Analyze - только анализ, ничего не удаляется (по умолчанию)
                     Day     - удаление старых файлов, без глубокой очистки
                     Night   - полная очистка с удалением и глубокой очисткой

Примеры:
  Запуск с анализом:
    powershell -ExecutionPolicy Bypass -File "C:\SMF\Start-SMF.ps1" -Profile Analyze

  Запуск дневной очистки:
    powershell -ExecutionPolicy Bypass -File "C:\SMF\Start-SMF.ps1" -Profile Day

  Запуск ночной очистки:
    powershell -ExecutionPolicy Bypass -File "C:\SMF\Start-SMF.ps1" -Profile Night

Примечания:
- Если параметр -Profile не указан, используется профиль по умолчанию из Config.ps1 (Analyze).
- Для работы требуется наличие файлов конфигурации и модулей в соответствующих папках.
- Логи сохраняются в Logs\SMF.log, отчёты (JSON и HTML) – в папку Reports.
- Политика выполнения может потребовать обхода через -ExecutionPolicy Bypass.
- Для просмотра помощи в консоли можно запустить скрипт без параметров – он покажет краткую информацию.

Также есть режими -WhatIf

.\Start-SMF.ps1 -SMFProfile Day -WhatIf	Запускает дневную очистку в режиме имитации – показывает, что будет удалено, но ничего не удаляет.
.\Start-SMF.ps1 -SMFProfile Night -WhatIf	Имитирует ночную глубокую очистку (включая браузерные кэши, временные файлы и т.д.) без реального удаления.
.\Start-SMF.ps1 -WhatIf (без профиля)	Запускает интерактивное меню, в котором можно включить WhatIf (пункт 4) и затем выбрать профиль для имитации.