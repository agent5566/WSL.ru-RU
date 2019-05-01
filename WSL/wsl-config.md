---
title: Управление дистрибутивы Linux
description: Ссылки на перечисление и настройка несколько дистрибутивов Linux, запущенных в подсистеме Windows для Linux.
keywords: BashOnWindows, bash, wsl, windows, подсистема windows для linux, windowssubsystem, ubuntu, wsl.conf, wslconfig
author: scooley
ms.author: scooley
ms.date: 02/7/2018
ms.topic: article
ms.assetid: 7ca59bd7-d9d3-4f6d-8b92-b8faa9bcf250
ms.custom: seodec18
ms.openlocfilehash: c806552750f413fcb75f989d868a57cc939af64a
ms.sourcegitcommit: ca08a78925880ed3eccf88edb30def16c83f2543
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2019
ms.locfileid: "59063502"
---
# <a name="manage-and-configure-windows-subsystem-for-linux"></a>Управление и настройку подсистемы Windows для Linux

> Применяется к Windows 10 Fall Creators Update и более поздней версии.  См. в разделе нашей обновленной [руководство по установке](./install_guide.md) попробовать новые возможности управления и запустить несколько дистрибутивов Linux из Windows Store.

## <a name="ways-to-run-wsl"></a>Способы выполнения WSL

Существует много способов для запуска Linux с подсистемой Windows для Linux.

1. `[distro]` IE `ubuntu`
1. `wsl.exe` или диспетчер конфигурации служб `bash.exe`
1. `wsl [command]` или диспетчер конфигурации служб `bash -c [command]`

Какой метод следует использовать зависит от того, что он делает.

### <a name="launch-wsl-by-distribution"></a>Запустите WSL, распространения

Под управлением дистрибутива, с помощью приложения конкретного дистрибутива запускает дистрибутива в собственном окне консоли.

![Из меню "Пуск" запустите WSL](media/start-launch.png)

Это же, как нажать кнопку «Запуск» в Windows Store.

![Запустите WSL из Windows Store](media/store-launch.png)

Распределение можно также запустить из командной строки, выполнив `[distribution].exe`.

Недостатком под управлением дистрибутива из командной строки таким образом является, что вы автоматически измените рабочий каталог из текущего каталога на домашний каталог дистрибутива.

**Пример.**

```console
PS C:\Users\sarah> pwd

Path
----
C:\Users\sarah

PS C:\Users\sarah> ubuntu

scooley@scooley-elmer:~$ pwd
/home/scooley
scooley@scooley-elmer:~$ exit
logout

PS C:\Users\sarah>
```

### <a name="wsl-and-wsl-command"></a>wsl и wsl [команда]

Лучший способ запуска WSL из командной строки используется `wsl.exe`.

**Пример.**

```console
PS C:\Users\sarah> pwd

Path
----
C:\Users\sarah

PS C:\Users\sarah> wsl

scooley@scooley-elmer:/mnt/c/Users/sarah$ pwd
/mnt/c/Users/sarah
```

Не только `wsl` сохранить текущий рабочий каталог на месте, он позволяет выполнить одну команду вдоль стороны команд Windows.

**Пример.**

```console
PS C:\Users\sarah> Get-Date

Sunday, March 11, 2018 7:54:05 PM

PS C:\Users\sarah> wsl
scooley@scooley-elmer:/mnt/c/Users/sarah$ date
Sun Mar 11 19:56:57 DST 2018
scooley@scooley-elmer:/mnt/c/Users/sarah$ exit
logout

PS C:\Users\sarah> wsl date
Sun Mar 11 19:55:47 DST 2018
```

**Пример.**

```console
PS C:\Users\sarah> Get-VM

Name            State CPUUsage(%) MemoryAssigned(M) Uptime   Status
----            ----- ----------- ----------------- ------   ------
Server17093     Off   0           0                 00:00:00 Opera...
Ubuntu          Off   0           0                 00:00:00 Opera...
Ubuntu (bionic) Off   0           0                 00:00:00 Opera...
Windows         Off   0           0                 00:00:00 Opera...


PS C:\Users\sarah> Get-VM | wsl grep "Ubuntu"
Ubuntu          Off   0           0                 00:00:00 Opera...
Ubuntu (bionic) Off   0           0                 00:00:00 Opera...
PS C:\Users\sarah>
```


## <a name="managing-multiple-linux-distributions"></a>Управление несколько дистрибутивов Linux

### <a name="windows-10-version-1903-and-later"></a>1903 и более поздних версий Windows 10

Можно использовать `wsl.exe` для управления вашей дистрибутивов в подсистеме Windows для Linux (WSL), включая список дистрибутивов, доступных, задание распространения по умолчанию и при удалении распределений.

Каждый дистрибутив Linux независимо друг от друга управляет свой собственный конфигурациями. Чтобы просмотреть команды конкретного дистрибутива, запустите `[distro.exe] /?`.  Например: `ubuntu /?`.

#### <a name="list-distributions"></a>Список дистрибутивов

`wsl -l` , `wsl --list`  
Перечисляет доступные дистрибутивы Linux, доступных для WSL.  Если дистрибутив присутствует в списке, он устанавливается и готовую к использованию.

`wsl --list --all`   
Список всех дистрибутивов, включая те, которые невозможно использовать в настоящее время.  Они могут быть находится в процессе установки, удаления, или в поврежденном состоянии.  

`wsl --list --running`   
Список всех дистрибутивов, работающих в данный момент.

#### <a name="set-a-default-distribution"></a>Задайте значение распределения по умолчанию

Распределение WSL по умолчанию является тот, который выполняется при запуске `wsl` в командной строке.

`wsl -s <DistributionName>`, `wsl --setdefault <DistributionName>`

Задает распределение по умолчанию `<DistributionName>`.

**Пример.**  
`wsl -s Ubuntu` нужно задать моей распространения по умолчанию Ubuntu.  Теперь при выполнении `wsl npm init` оно будет выполняться в Ubuntu.  Если я запущу `wsl` он будет открыт сеанс Ubuntu.

#### <a name="unregister-and-reinstall-a-distribution"></a>Отменить регистрацию и повторно установить дистрибутив

Во время Linux на дистрибутивах можно установить с помощью Windows хранилище, они не предусмотрена в магазине.  WSL Config позволяет дистрибутивов следует отменять регистрацию или удалено.

При отмене регистрации позволяет дистрибутивов переустановка.

> **Внимание!** После отмены регистрации, все данные, параметры и программное обеспечение, связанное с этой будут безвозвратно утрачены.  Переустановка в магазине установит чистую копию распределение.

`wsl --unregister <DistributionName>`  
Отменяет регистрацию распространения из WSL для переустановки или очищена.

Например: `wsl -unregister Ubuntu` удалить из дистрибутивов, доступных в WSL Ubuntu.  При выполнении `wsl --list` его там нет.

Чтобы переустановить, получите распределение в Windows Store и выберите «Запустить».

#### <a name="run-as-a-specific-user"></a>Запуск от имени определенного пользователя

`wsl -u <Username>`, `wsl --user <Username>`

WSL Запуск от имени указанного пользователя. Учтите, что этот пользователь должен существовать внутри WSL распространения.

#### <a name="run-a-specific-distribution"></a>Запустите конкретного распределения

`wsl --d <DistributionName>`, `wsl --distribution <DistributionName>`

Запустите указанный распределение WSL, можно использовать для отправки команд для конкретного распределения не придется менять по умолчанию.

### <a name="versions-earlier-than-windows-10-version-1903"></a>Версии более ранней, чем Windows 10 версии 1903

WSL Config (`wslconfig.exe`) является средством командной строки для управления дистрибутивов Linux, работающих на подсистеме Windows для Linux (WSL).  Он позволяет список дистрибутивов, доступных, задайте значение распределения по умолчанию и удалите распределений.

Несмотря на то полезные параметры, охватывающие или координировать дистрибутивов WSL Config, каждый дистрибутив Linux независимо друг от друга управляет свой собственный конфигурациями.  Чтобы просмотреть команды конкретного дистрибутива, запустите `[distro.exe] /?`.  Например: `ubuntu /?`.

Чтобы просмотреть все доступные параметры для wslconfig, выполните следующую команду:  `wslconfig /?`

```console
wslconfig.exe
Performs administrative operations on Windows Subsystem for Linux

Usage:
    /l, /list [/all] - Lists registered distributions.
        /all - Optionally list all distributions, including distributions that
               are currently being installed or uninstalled.
    /s, /setdefault <DistributionName> - Sets the specified distribution as the default.
    /u, /unregister <DistributionName> - Unregisters a distribution.
```

#### <a name="list-distributions"></a>Список дистрибутивов

`wslconfig /list`  
Перечисляет доступные дистрибутивы Linux, доступных для WSL.  Если дистрибутив присутствует в списке, он устанавливается и готовую к использованию.

`wslconfig /list /all`  
Список всех дистрибутивов, включая те, которые невозможно использовать в настоящее время.  Они могут быть находится в процессе установки, удаления, или в поврежденном состоянии.  

#### <a name="set-a-default-distribution"></a>Задайте значение распределения по умолчанию

Распределение WSL по умолчанию является тот, который выполняется при запуске `wsl` в командной строке.

`wslconfig /setdefault <DistributionName>`

Задает распределение по умолчанию `<DistributionName>`.

**Пример.**  
`wslconfig /setdefault Ubuntu` нужно задать моей распространения по умолчанию Ubuntu.  Теперь при выполнении `wsl npm init` оно будет выполняться в Ubuntu.  Если я запущу `wsl` он будет открыт сеанс Ubuntu.

#### <a name="unregister-and-reinstall-a-distribution"></a>Отменить регистрацию и повторно установить дистрибутив

Во время Linux на дистрибутивах можно установить с помощью Windows хранилище, они не предусмотрена в магазине.  WSL Config позволяет дистрибутивов следует отменять регистрацию или удалено.

При отмене регистрации позволяет дистрибутивов переустановка.

> **Внимание!** После отмены регистрации, все данные, параметры и программное обеспечение, связанное с этой будут безвозвратно утрачены.  Переустановка в магазине установит чистую копию распределение.

`wslconfig /unregister <DistributionName>`  
Отменяет регистрацию распространения из WSL для переустановки или очищена.

Например: `wslconfig /unregister Ubuntu` удалить из дистрибутивов, доступных в WSL Ubuntu.  При выполнении `wslconfig /list` его там нет.

Чтобы переустановить, получите распределение в Windows Store и выберите «Запустить».

## <a name="set-wsl-launch-settings"></a>Задать параметры запуска WSL

> **В 17093 сборки программы предварительной оценки Windows и более поздние версии**

Автоматическая настройка определенных функций в WSL, которая будет применяться каждый раз при запуске подсистемы с помощью `wsl.conf`. 

Право, это включает в себя автоподключения параметры и конфигурации сети.

`wsl.conf` расположен в каждый дистрибутив Linux в `/etc/wsl.conf`. Если файл не существует, можно создать его самостоятельно. WSL будет проверки существования файла и будет считать его содержимое. Если файл отсутствует или имеет неправильный формат (то есть неправильного форматирования разметки), WSL по-прежнему запустить в обычном режиме.

Ниже приведен пример `wsl.conf` файл, можно добавить в ваш дистрибутивов:

```console
# Enable extra metadata options by default
[automount]
enabled = true
root = /windir/
options = "metadata,umask=22,fmask=11"
mountFsTab = false

# Enable DNS – even though these are turned on by default, we’ll specify here just to be explicit.
[network]
generateHosts = true
generateResolvConf = true
```

### <a name="configuration-options"></a>Параметры конфигурации

В соответствии с соглашения INI-файле ключи, объявляются в разделе. 

WSL поддерживает два раздела: `automount` и `network`.

#### <a name="automount"></a>Автоподключение

Раздел: `[automount]`


| ключ        | value                          | значение по умолчанию      | Примечания                                                                                                                                                                                                                                                                                                                          |
|:-----------|:-------------------------------|:-------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| enabled    | Логический                        | true         | `true` причины жесткими дисками (например) `C:/` или `D:/`) автоматически монтируется с DrvFs под `/mnt`.  `false` означает, что диски не будут устанавливаться автоматически, но вы может по-прежнему подключить их вручную или с помощью `fstab`.                                                                                                             |
| mountFsTab | Логический                        | true         | `true` Задает `/etc/fstab` должны быть обработаны при запуске WSL. / etc/fstab — это файл, где можно объявить другие файловые системы, таких как SMB-ресурса. Таким образом вы можете подключить эти файловые системы автоматически в WSL при запуске копирования.                                                                                                                |
| Корневой       | Строка                         | `/mnt/`      | Задает каталог, куда будет автоматически подключен фиксированных дисков. Например, если имеется каталог в WSL в `/windir/` и указать, что в качестве привилегированного пользователя, можно ожидать см. в разделе основных дисков, подключенный к `/windir/c`                                                                                              |
| параметры    | Разделенный запятыми список значений | Пустая строка | Это значение добавляется к строке по умолчанию DrvFs подключения параметры. **Можно указать только параметры, относящиеся к DrvFs.** Параметры, которые двоичный подключения обычно синтаксического анализа, в флаг не поддерживаются. Если вы хотите явно указать эти параметры, необходимо включить каждый диск, для которого вы хотите сделать это в/etc/fstab. |

По умолчанию WSL задает uid и gid значению пользователя по умолчанию (в дистрибутивах Ubuntu пользователя по умолчанию создается с uid = 1000, gid = 1000). Если пользователь задал параметр gid или uid, явно с помощью этого ключа, связанного значения будут перезаписаны. В противном случае — значение по умолчанию всегда быть добавлены.

**Примечание.** Эти параметры применяются как параметры подключения для всех автоматически подключенные диски. Чтобы изменить параметры для определенных дисках, вместо этого используйте/etc/fstab.

#### <a name="network"></a>сеть

Метка раздел: `[network]`

| ключ | value | значение по умолчанию | Примечания|
|:----|:----|:----|:----|
| generateHosts | Логический | `true` | `true` Задает WSL для создания `/etc/hosts`. `hosts` Файл содержит карту статические IP-адреса, соответствующие имена узлов. |
| generateResolvConf | Логический | `true` | `true` Задайте WSL для создания `/etc/resolv.conf`. `resolv.conf` Со списком DNS, которые может разрешить данное имя узла, IP-адрес. | 

#### <a name="interop"></a>Взаимодействия

Метка раздел: `[interop]`

Эти параметры становятся доступными в 17713 сборки программы предварительной оценки и более поздних версий.

| ключ | value | значение по умолчанию | Примечания|
|:----|:----|:----|:----|
| enabled | Логический | `true` | Параметр этот ключ будет определить, поддерживает ли WSL запуска процессов Windows. |
| appendWindowsPath | Логический | `true` | Параметр этот ключ будет определять, добавит ли WSL элементы Windows пути в переменную $PATH. | 