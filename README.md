# DBI by **[duckbill](https://github.com/duckbill007)**
![Github latest downloads](https://img.shields.io/github/downloads/rashevskyv/dbi/total.svg)

[ENGLISH GUIDE](README_ENG.md)

Инструкция базируется на [работе Брикачу](https://4pda.ru/forum/index.php?showtopic=939714&st=1100#entry86288632)

Ультимативное решение для установки NSP\NSZ\XCI и работы с консолью. Поддержка установки по MTP, USB, http (с вашего личного сервера), внешнего USB и многое другое. 

## Содержание: 

1. [Установка](#установка)
1. [Использование](#использование)
	1. [Интерфейс](#интерфейс)
	1. [Browse SD Card / Browse USB0 Drive](#browse-sd-card--browse-usb0-drive)
	1. [Install title from USB](#install-title-from-usb)
	1. [Home server](#home-server)
	1. [Browse installed applications](#browse-installed-applications)
	1. [Cleanup orphaned files](#cleanup-orphaned-files)
	1. [Browse tickets](#browse-tickets)
	1. [Run MTP responder](#run-mtp-responder)
	1. [Exit](#exit)
1. [Уведомления и коды ошибок](#уведомления-и-коды-ошибок)
	1. [Уведомления](#уведомления)
	1. [Ошибки](#ошибки)
1. [dbi.config](#dbiconfig)
1. [Другие возможности](#другие-возможности)
1. [Благодарности](#благодарности)

## Установка 

Поместите `dbi.nro` и `dbi.config` в папку `/switch/DBI/` на вашей каре памяти. Запускайте из режима апплета с помощью Homebrew Launcher (через альбомы)

*В режиме апплета программа запускается с синим фоном. В режиме тайла - с чёрным*

## Использование 

### Интерфейс
![2021041010520200](https://user-images.githubusercontent.com/18294541/114262830-d7643e00-99ea-11eb-8dbb-c8e0996577e5.jpg)
* **Browse SD Card** — установка .NSP/.NSZ/.XCI-файлов из карты памяти.
* **Browse USB0 Drive** — установка .NSP/.NSZ/.XCI-файлов с внешнего USB-накопителя в exFAT / FAT32: флешки, жёсткого диска, проч.
* **Install title from USB** — установка .NSP/.NSZ/.XCI из ПК по USB 2.0 и 3.0-проводу, через прилагаемую программу dbibackend. *Горячая клавиша для этой опции*: кнопка **Y**.
* **Install title from Gamecard** — этот пункт появляется при вставленном в Switch игровом картридже, — для установки игры из имеющегося игрового картриджа в microSD-карту или внутреннюю NAND-память консоли.
* **Home server** — начиная с версии v150, есть возможность устанавливать игры по сети (HTTP), через WiFi без провода или LAN-USB-адаптер. Подробнее об этом ниже
* **Browse installed applications** — просмотр установленных игр, их общее установленное количество, посмотреть потраченное время на игру и количество её запусков, проверить (верифицировать) на ошибки, перенести игровые данные между встроенной памятью, картой памяти и обратно, возможность их выборочного или потокового удаления вместе с прилагаемыми LayeredFS-модами, просмотр наличия у них обновлений и DLC, ручное удаление DLC / обновлений / LaryeredFS (LFS) мода, функция Reset Required version для сброса системной проверки обновления у выбранной игры. *Горячая клавиша для этой опции*: кнопка **L**.
* **Cleanup orphaned files** — автоматическая чистка ненужных удалённых файлов игр, если они есть
* **Browse tickets** — просмотр и ручное удаление системных тикетов игр.
* **Run MTP responder** — включение внутреннего MTP-сервера для присоединения Switch к ПК или к Android-устройству (телефон/планшет/пр., протестированы Pixel 3, Xiaomi Mi A1, Lenovo Tab 4 7" TB-7304X), можно: просматривать и работать с картой памяти (1: External SD Card) и внутренней память консоли, просматривать установленные игры (4: Installed games), сделать бекап игровых сохранений на ПК (7: Saves), при вставленном игровом картридже дампить его (full / trimmed / сертификат) на ПК / Android (9: Gamecard). *Горячая клавиша для этой опции*: кнопка X (ей же выходить из MTP).
* **Exit** — выход из программы. *Горячая клавиша для этой опции*: кнопка **+**

В самом левом нижнем углу (SD) написано про занятый размер данных на карте / общий размер карты. В правом нижнем углу (NAND) написан занятый размер данных во встроенной памяти Switch / общий встроенной памяти Switch.
Внизу по центру (dbi: XXX) написан номер версии dbi — старайтесь всегда использовать самую последнюю версию программы

### Browse SD Card / Browse USB0 Drive

Выберите этот пункт, если хотите установить игры / обновления / DLC из уже имеющихся файлов на карте памяти / внешнем USB. 
Кнопка **A** открывает папку, кнопка **B** возвращает назад, после открытия папки с файлами для установки, кнопкой **X** можно выделить только необходимые файлы, кнопокй **Y** инвертировать выбор. При этом цвет названия выделенных файлов изменится с белого на светло-синий

После этого нажмите кнопку **А** для подтверждения. Возникнет окно с опциями установки:

![2021041011441100](https://user-images.githubusercontent.com/18294541/114264183-18138580-99f2-11eb-8c7b-536b4b831195.jpg)

**Total transfer size** — объём установочных дистрибутивов (файлов .NSP/.NSZ/.XCI), выбранных и готовых к установке.
**Total install size** — объём свободного пространства, которое необходимо для установки выбранных файлов.
**Install target** — локация установки данных: **NAND** — внутренняя память консоли Nintendo Switch, **SD** — карта памяти microSD, **AUTO** — опция по-умолчанию для установки всегда на карту памяти microSD, но если на ней будет недостаточно места, данные установятся во внутреннюю память.
**Delete after install** — это опция удаления установочных дистрибутивов (файлов .NSP/.NSZ/.XCI) с карты после их успешной установки; чтобы она работала, с файлов должен быть снят атрибут «Только чтение». По-умолчанию файлы не удаляются. Опция видна только при установке с карты памяти / внешнего USB
**Turn off screen** — возможность выключить экран на время установки для экономия электроэнергии аккумулятора, сразу после успешной установки экран автоматически включится. Эта опция работает только в портативном режиме.
Нажмите **Start install**, чтобы начать установку. После успешной установки, внизу появится надпись *Installation Complete. Press B to return*.

В программе имеется встроенная автоматическая функция удаления старых апдейтов при установке нового обновления к игре, поэтому за лишнее занимаемое место ими можно не беспокоиться.

### Install title from USB

Через Install title from USB очень удобно устанавливать игры, обновления и DLC к ним сразу напрямую по USB-проводу с ПК на Switch, минуя необходимость вынимать карту и тратить двойное время, закачивая дистрибутивы (.NSP/.NSZ/.XCI-файлы) на карту памяти и устанавливая их оттуда. *Горячая клавиша для вызова этой опции из главного меню*: кнопка **Y**.
Для работы сперва нужно скачать на ПК dbibackend (`dbibackend.exe` for Windows, `dbibackend` from `dbibackend.tar.xz` for all), запустить его, выбрать игры для установки, нажать Start server, затем подключить USB-C кабель к ПК и Switch, выбрать пункт Install title from USB в dbi и установить все необходимые игры.

Выделение файлов, а так же их установка происходит способом идентичным способу из пункта Browse SD Card / Browse USB0 Drive

Для быстрой отправки файлов или папок с играми на установку, нажмите на них правой клавишей мыши, выберите Отправить > dbibackend, установочные файлы сразу помещаются в очередь dbibackend. Для того, чтобы это настроить в Windows, нажмите `Win+R`, введите `shell:sendto`, положите в папку ярлык для `dbibackend.exe`

### Home server

Пункт **"Home server"** появляется при наличии настроенного раздела **Network install sources** в `dbi.config` (подробнее про этот файл ниже). Причём название этого пункта будет меняться в зависимости от названия указанного в конфигурационном файле

Для установки игр по сети, отредактируйте файл dbi.config, находящийся в папке `/switch/DBI/`, согласно примеру

```
; Network install sources
[Network sources]
; <display name>=<type>|<URL>
Home server=ApacheHTTP|http://192.168.1.47/Nintendo/Switch/
```

Установите на ПК любой другой HTTP-сервер c включённым DirectoryListing: Apache, Mongoose, Python SimpleHTTP, sheret, rclone и т. д.,

Пример для nginx на Windows: 
отредактируйте файл `/nginx/conf/nginx.conf`, прописав в `location` адрес вашего Switch, вместо указанного в примере `127.0.0.1` (или всю свою подсеть вида 192.168.1.1/24 или 192.168.0.0/16); его можно узнать на Switch в **Системных настройках** > **Интернет**:

```
location / {
root html;
index index.html index.htm;
}
location /Nintendo/Switch/ {
allow 127.0.0.1;
deny all;
autoindex on;
}
```

Сохраните конфиг, запустите `nginx.exe`, разрешив программе доступ в сеть, затем скопируйте нужную игру в локальную папку /nginx/html/Nintendo/Switch/ на ПК, а на Switch выберите строку «Home server».
Получаем обычный интерфейс инсталляции файлов, и можно начать устанавливать все игры по сети, после чего, при желании веб-сервер можно остановить через nginx -s stop.

В качестве адреса сервера, можно использовать и доменное имя в интернете, например, своего удалённого VPS — лучше с HTTP Basic-аутентификацией вида http://user:password@host:port/Nintendo/Switch/

Например:
```
ApacheHTTP|Network repo|http://127.0.0.1/Nintendo/Switch/
ApacheHTTP|WWW VPS repo|http://www.myveryownswitchvpsdomain.su/Nintendo/Switch/
```

Сгенерировать файл htpasswd, положить в `/nginx/conf/`, затем в `nginx.conf` изменить в блоке (пример):
```
        location /Nintendo/Switch/ {
			   satisfy all;
			   allow 127.0.0.1;
			   deny all;
			   auth_basic "Password Protected Area";
			   auth_basic_user_file htpasswd; 
               autoindex on;
        }
```

Логин «switch», пароль «pwd»:

Файл htpasswd:
```
switch:{SHA}N/omUzCtg+qoee+x4ttjgIls9jk=
```
### Browse installed applications

В **Browse installed applications** можно посмотреть список установленных программ, обновлений, DLC к ним, по отдельности их занимаемый объём и версию, порядковую и в HEX-формате, их titleID, посмотреть общее время игры и количество запусков, наличие установленного LayeredFS-мода к игре (для Atmosphére). *Горячая клавиша для вызова этой опции из главного меню*: кнопка **L**:

![2021041012101400](https://user-images.githubusercontent.com/18294541/114264832-e3093200-99f5-11eb-9e7a-acc7b0f7444c.jpg)

Сверху в центре написано общее количество установленных игр; можно перенести любые установленные игровые данные между встроенной памятью, картой памяти microSD и обратно, имеется возможность выборочного (или потокового) удаления игр **(b)** / обновлений **(u)** / DLC **(d)** вместе с прилагаемыми LayeredFS-модами **(l)** к игре в` /atmosphere/contents/` или только его отдельно; здесь можно вручную удалить ненужные вам DLC / обновления к игре; есть функция **Reset Required version** для сброса системной проверки обновления выбранной игры (она также автоматически активируется пои установке, удалении игровых обновлений):

![2021041012102700](https://user-images.githubusercontent.com/18294541/114264843-f74d2f00-99f5-11eb-8cf0-a3fc383ac322.jpg)

Кнопкой **R** можно выбирать нужную сортировку игр — по алфавиту (по умолчанию), или по их последнему использованию.
Кнопкой **А** войти в меню выбранной игры, кнопка **—** удаляет игру и её (неперсонализированный) тикет, D-pad'ом выбираются игры, левым стиком прокручивается список игр, кнопками **ZR** и **ZL** можно листать список игр поэкранно. 

Также можно проверить (верифицировать) игры на их целостность, выбрав её и затем пункт **Check integrity**

### Cleanup orphaned files
**Cleanup orphaned files** автоматически чистит ненужные файлы игр, файлы от прерванных установок игр, скачанное (официально) обновление OFW прошивки и все неиспользуемые тикеты игр, если они были найдены. 

### Browse tickets
Просмотр и удаление ненужных тикетов игр. **Ticket (или encrypted title key)** — это специальная зашифрованная уникальная информация о правах запуска на контент игры, которая устанавливается в систему при инсталляции каждой игры (000 в конце titleID) / обновления (800 в конце titleID) / каждого DLC. + означает наличие установленной игры, **[c]** — common-тикет (установленного дампа игры либо обновления), **[p]** — personalized-тикет (купленной в eShop игры)

Иногда, если возникают спец. ошибки (например), и вы точно знаете и уверены, что вы делаете, его можно удалить у конкретной игры и её обновления / DLC.
Во всех остальных случаях лучше тут ничего не трогать, во избежание ошибок запуска игр.

### Run MTP responder 
**Run MTP responder** включает встроенный в dbi MTP-сервер для обмена данными с ПК либо к Android-устройству по USB-C OTG (телефон/планшет/прочие устройства). *Горячая клавиша для вызова этой опции из главного меню*: кнопка **X** (ей же выходить из MTP). После подключения USB-провода к ПК и запуска MTP-сервера в dbi, на ПК появится следующее окно:

![изображение](https://user-images.githubusercontent.com/18294541/114265006-054f7f80-99f7-11eb-86c9-1a20d588e616.png)

Где:
1: **External SD Card**, для просмотра, копирования и удаления файлов и папок c/на ПК и с/на карту памяти microSD

2: **NAND User**, просмотр, копирование файлов и папок на ПК с внутренней память Switch, в его системный раздел USER (раздел доступен только для чтения).

3: **NAND System**, просмотр, копирование файлов и папок на ПК с внутренней памяти Switch, в его системный раздел SYSTEM (раздел доступен только для чтения).

4: **Installed games**, для просмотра установленных игр. 

В **Installed games** отображаются все игры как в NAND, внутренней памяти Switch, так и установленные на карту памяти, все вместе. Чтобы сделать дамп (дистрибутив) установленный игры себе на ПК в формате .NSP, просто скопируйте папку с названием игры из **Installed games** на свой ПК, при этом на базе вашего personalized-тикета генерируется общий common-тикет с полностью очищенной личной информацией. Вы получите дамп этой игры в виде раздельных файлов - отдельно саму игру, отдельно обновление и DLC. Если для игры были установлены читы или моды, они будут находится в папке `Mods & Cheats`. Так же можно получить скомбинированный дамп, в котором в один файл будет склеяны сама игры, все её DLC и обновление. Такой файл лежит прямо в корне раздела **Installed games**. 
Здесь так же хранится сгенерированный dbi `InstalledApplications.csv`, с таблицей списка установленных игр, их TitleID и текущей версии.

5: **MicroSD install**
Скопируйте в эту папку ваши **NSP** или **NSZ**. По окончанию копирования игра будет установлена на **карту памяти** вашей приставки. При установке NSZ-файлов учитывайте, что их фактический размер может сильно отличаться от размера после установки, так что если при наличии свободных 2Гб на карте памяти у вас, например, не хватает места для установки NSZ размером, скажем, в 1Гб, не удивляйтесь, поскольку контейнер NSZ - сжатый. 

6: **NAND install**: Скопируйте в эту папку ваши **NSP** или **NSZ**. По окончанию копирования игра будет установлена во **внутреннюю память** вашей приставки. При установке NSZ-файлов учитывайте, что их фактический размер может сильно отличаться от размера после установки, так что если при наличии свободных 2Гб на карте памяти у вас, например, не хватает места для установки NSZ размером, скажем, в 1Гб, не удивляйтесь, поскольку контейнер NSZ - сжатый. 

7: **Saves**: Доступ ко всем сохранениям игр — в аккаунтах (Account), системных программ (System), в Background Content Asymmetric synchronized delivery and Transmission (BCAT, пример: ивенты в ACNH), временных (Temporary), кэш (Cache, пример: аддоны в DOOM), системных BCAT (SystemBCAT), — хранящимся во внутренней памяти Switch; в папке Installed games — сохранения для имеющихся установленных сейчас игр, Uninstalled games — сохранения от удалённых игр, которые раньше запускались. Отсюда можно сделать их бекап, скопировав их на ПК, а также удалить ненужные — для этого откройте папку с именем нужной игры, затем удалите папку с ником вашего аккаунта / Device-сохранения.
Для того, чтобы восстановить сохранения, скопируйте их в соответствующую папку с ПК. DBI не требует предварительного запуска игры для восстановления сохранения, однако это касается только обычных сохранений. BCAT или Cache сохранения требуют предварительного запуска игры перед восстановлением. 

8: **Album**: доступ к скриншотам и видеороликам (Альбому), точно так же, как это сделано в OFW 11.0.0 Nintendo.

9: **Gamecard**: при вставленном в Switch игровом картридже появляется возможность скопировать его дамп в .XCI либо trimmed .XCI на ПК, вместе со встроенным в него обновлением, если оно есть, с уже убранным его персональным RSA-сертификатом; кроме того, возможно отдельно экспортировать его сертификат

Также, на дисплее Switch после включения MTP-сервера появится окно с вашим ником учётной записи и его UID, а также количеством игровых сохранений:
 ![2021041013152900](https://user-images.githubusercontent.com/18294541/114266673-27013480-9a00-11eb-81ba-f1ff1c3c5abb.jpg)

Чтобы выключить MTP-сервер и выйти в главное меню, нажмите кнопку **X**.

### Exit
Exit — выход из программы в HOS, минуя hbmenu, либо в hbmenu (это настраивается в dbi.config); если dbi был запущен из тайтла / форвардера, программа перезагрузится либо останется на чёрном экране.

## Уведомления и коды ошибок
### УВЕДОМЛЕНИЯ:

* **«HASH MISMATCH»** — чаще всего, это НЕ ОШИБКА, игра была сконвертирована из картриджа (тогда всё в порядке), иногда — имеются проблемы с целостностью файла, перекачайте-перехешируйте его, передачей данных по USB-кабелю/порту/в процессе установки между ПК и Switch.
    Если игра не запускается или запускается с ошибкой, попробуйте переустановить её снова, проверить либо заменить USB-кабель / microSD / сменить USB-порт.
* **DELTA SKIPPED** — это НЕ ОШИБКА, а уведомление, что ненужные фрагменты в файле обновления были пропущены, если они в нём были, как и было должно.
* **«No tickets found. Possibly this NSP was converted from XCI.»** — это НЕ ОШИБКА, на работоспособность игры не влият, но информирование, что игра без тикетов. Она может быть дампом из .XCI-картриджа или переконвертирована в Standard Crypto.
* **«WARNING» title marked as Application but has AddonConten** — это НЕ ОШИБКА, обычно это указывает на homebrew-игру в .NSP, созданную не по стандартам, к примеру, когда в Application-тайтл (основную игру, v0) добавили и AddonContent-флаг (DLC).
    Если такая игра запускается и работает, тогда всё в порядке.

### ОШИБКИ:

* **«Can not find file for ncaid»** — установочный файл игры повреждён (в нём отсутствует нужный .nca из списка .cnmt).
* **«Invalid PFS0 magic!»** — перекачайте установочный файл игры и проверьте его целостность, этот файл повреждён.
* **«Received less data than expected»** и **Installation aborted** — ошибка в передаче данных, перепроверьте и при необходимости замените USB-кабель/USB-порт между Switch и ПК. Также обязательно убедитесь, что у вас установлена самая последняя версия программы, как вот в этом посте.
* **«std::bad_alloc»** — переименуйте файл без спецсимволов и кириллицы в имени и пути к нему, плюс убедитесь, что у используете самую последняя версия программы, как в посте, на консоль установлена последняя версия OFW и CFW.
* **«Nothing to install»** в окне выборе файлов — переименуйте файл без спецсимволов, иероглифов или кириллицы в имени и пути к нему.
* **«INVALID LENGTH»** — проверить соединение USB-C кабеля и USB-порта, проверить с другими USB-C-кабелями, целостность файла игры и карту памяти на ошибки, при установке через MTP — запустить dbi через любую игру (тайтл) с удерживанием кнопки R, а не в режиме апплета через альбомы.
* **«Error occurred: Invalid argument»** — обновите ваш dbi на последнюю версию.
* **«[FAILED] Unknown error»** при установке .tik (тикета) — установите последние сигпатчи для Atmosphére.
* **«605: Content or placeholder path not exists»** и **«SOME CONTENTS ARE MISSING»** — битая файловая система карты памяти, или нерабочая / некачественная флешка. Проверьте её в chkdsk и h2testw, если нет ошибок, переформатируйте в FAT32.
* **WARNING! Extra buffers exceeded**, при установке через MTP — запустите dbi через тайтл = через любую игру, удерживая кнопку R при её запуске; альтернативно — через NSP-форвардер, и использовать более быструю microSD-карту с другим USB-кабелем/портом.
* **No tickets found but they are required** — некорректный (неполный, без тикета но с titlerights) дамп игры, найдите другой.
* **SOME CONTENTS ARE MISSING. APPLICATION WILL BE UNUSABLE** — контейнер неполный, проверьте целостность установочного файла игры.
    
## dbi.config
Файл dbi.config был добавлен, начиная с версии 253. Он находится рядом с DBI.nro, и заменяет прежние файлы-флаги dbi.default.ascii и dbi.network.config, а также добавляет несколько новых опций для удобной кастомизации настроек под пользователя.

Рассмотрим его содержимое:
```
; General settings
[General]
; Use libnx's default font for ASCII symbols
DefaultASCII=false
; Use libusbhsfs for access to USB mass storage drives connected to switch or dock
UseLibUsbHsFS=true
; Direct exit to homescreen
ExitToHomeScreen=true

; Visibility of main menu items
[MainMenu]
; Browse and install files from MicroSD card
BrowseSD=true
; Browse and install files from USB flash drives and HDD
USBHost=true
; Browse and install files from PC via dbibackend
BackendInstall=true
; Install game from inserted game cartridge
GameCard=true
; Browse and install files from configured network sources
Network=true
; Browse installed applications
BrowseApps=true
; Clean up files left from bad installs/old updates/unused tickets and so on
Cleanup=true
; View where you can view or delete installed tickets
Tickets=true
; MTP responder
MTP=true

; Install options
[Install]
; Check NCA hash during install
CheckHash=true

; MTP options
[MTP]
; Log all files, id disabled transfer shows only for files >= 4M
LogAllFiles=false
; Show or not NSP that includes base game, latest update and all DLC in single multi-title file
ShowCombinedNSP=true
; Show or not virtual "Mods & cheats" folder that redirects to sdmc:/atmosphere/contents/TITLEID
ShowMAC=true
; Show user defined shortcuts to MircoSD folders as separate storages
CustomStorages=true

;Enable or disable various MTP storages
[MTP Storages]
1: External SD Card=true
2: Nand USER=true
3: Nand SYSTEM=true
4: Installed games=true
5: MicroSD install=true
6: NAND install=true
7: Saves=true
8: Album=true
9: Gamecard=true

; Network install sources
[Network sources]
; <display name>=<type>|<URL>
;Home server=ApacheHTTP|http://192.168.1.47/Nintendo/Switch/

[MTP custom storages]
; <display name>=<path>
;Homebrew=sdmc:/switch
```

### General settings
* **DefaultASCII** - **true** включает стандартный шрифт, **false** включает альтернативный шрифт
* **UseLibUsbHsFS** - **true** включает библиотеку [libusbhsfs](https://github.com/DarkMatterCore/libusbhsfs) для работы с внешними USB-накопителями через USB-OTG на Switch, **false** отключает её.
* **ExitToHomeScreen** — при false выход из dbi происходит в hbmenu, при **true** на рабочий стол Switch.

### MainMenu
Показ соответствующих элементов меню.

**true** - отображать **false** - нет 

* BrowseSD - пункт "**Browse SD card**, для установки игр с Sd карты 
* USBHost - пункт "**Browse USB0 Drive**, для установки игр с внешнего USB
* BackendInstall - пункт "**Install title from USB**, для устаноки игр с ПК через backend 
* GameCard - пункт "**Install title from Gamecard**, для установки содержимого картриджа в память консоли
* Network - пункт "**Home server**, для установки игр с домашнего веб-сервера
* BrowseApps - пункт "**Browse installed applications**, для управления установленными приложениями
* Cleanup - пункт "**Cleanup orphaned files**, для очистки "осиротевших" файлов с карты памяти
* Tickets - пункт "**Browse tickets**, для управления тикетами
* MTP - пункт "**Run MTP responder**, для запуска MTP

### Install
* **CheckHash** — при **true** проверяются хеши .nca-файлов при установке игр на Switch, при false нет.

### MTP
* **LogAllFiles** — **false** выключает логирование файлов меньше 4Мб при работе с MTP, при **true** логируются все файлы.
* **ShowCombinedNSPInInstalledGames** — **false** выключает показ комбинированных (multi-title .NSP-file) тайтлов.
* **ShowMACInInstalledGames** — **false** выключает показ виртуальной директории **«Mods & cheats»** в пункте Installed games в MTP, перенаправляющей по пути `/atmosphere/contents/%titleid_игры%` на карту памяти.
* **CustomStorages** - отображать или спрятать кастомные пункты меню, прописанные в секции **MTP custom storages**


### [MTP Storages](#run-mtp-responder)
Показ соответствующих элементов при работе MTP Responder с ПК/Android, по умолчанию все пункты включены для отображения.

**true** - отображать в главном меню, **false** - нет 

Названия пунктов соответствуют названиям разделов

### [Network sources](#home-server)
Задаются имена и адреса для установки игр по сети (через WiFi/LAN-адаптер)

### MTP custom storages
Кастомные пункты для MTP-режима для быстрого доступа к папкам на вашей карте памяти. Формат: `<отображаемое_имя папки>=<путь>`, например: `Homebrew=sdmc:/switch`. 
В режиме MTP появится папка `Homebrew`, ссылающаяся на папку `switch` на вашей карте памяти

## Другие возможности

### Монтирование содержимолго установленных игр по MTP 

Перейдите в "*Browse installed applications*" -> Выберите необходимые игры кнопкой `X` -> Нажмите `A` -> "*Mount contents via MTP*"

## Благодарности
Спасибо [SciresM](https://github.com/SciresM) за  [hactool](https://github.com/SciresM/hactool) (лицензия [ISC](https://ru.wikipedia.org/wiki/%D0%9B%D0%B8%D1%86%D0%B5%D0%BD%D0%B7%D0%B8%D1%8F_ISC)) - DBI использует некоторые структуры данных, взятые оттуда
