# DBI by **[duckbill](https://github.com/duckbill007)**
![Github latest downloads](https://img.shields.io/github/downloads/rashevskyv/dbi/total.svg)

[ENGLISH GUIDE](README_ENG.md)

Инструкция базируется на [работе Брикачу](https://4pda.to/forum/index.php?showtopic=939714&st=1100#Spoil-86288632-5)

Ультимативное решение для установки NSP, NSZ, XCI и XCZ и работы с консолью. Поддержка установки по MTP, USB, http (с вашего личного сервера), внешнего USB и многое другое. 

## Содержание: 

1. [Установка](#установка)
1. [Использование](#использование)
  1. [Интерфейс](#интерфейс)
  1. [Управление](#управление)
  1. [Browse SD Card/Browse USB0 Drive](#browse-sd-card--browse-usb0-drive)
  1. [Install title from USB](#install-title-from-usb)
  1. [Home server](#home-server)
  1. [Browse installed applications](#browse-installed-applications)
     * [Контекстное меню тайтла](#контекстное-меню-тайтла)
     * [Детальное меню игры](#детальное-меню-игры)
	   * [Контекстное меню записи](#контекстное-меню-записи)
  1. [Cleanup orphaned files](#cleanup-orphaned-files)
  1. [Browse tickets](#browse-tickets)
     * [Контекстное меню тикетов](#контекстное-меню-тикетов)
  1. [Browse saves](#browse-saves)
      * [Контекстное меню сохранений](#контекстное-меню-сохранений)
  1. [Run MTP responder](#run-mtp-responder)
  1. [Exit](#exit)
1. [Уведомления и коды ошибок](#уведомления-и-коды-ошибок)
   1. [Уведомления](#уведомления)
   1. [Ошибки](#ошибки)
1. [dbi.config](#dbiconfig)
1. [Другие возможности](#другие-возможности)
1. [Благодарности](#благодарности)

## Установка 

Поместите `dbi.nro` и `dbi.config` в папку `sdmc:/switch/DBI/` на вашей каре памяти. Запускайте из режима апплета с помощью Homebrew Launcher (через альбомы)

*В режиме апплета программа запускается с синим фоном. В режиме тайла - с чёрным*

## Использование 

### Интерфейс
![2021041010520200](https://user-images.githubusercontent.com/18294541/114262830-d7643e00-99ea-11eb-8dbb-c8e0996577e5.jpg)
* **Browse SD Card** — установка `NSP`/`NSZ`/`XCI`/`XCZ`-файлов из карты памяти.
* **Browse USB0 Drive** — установка `NSP`/`NSZ`/`XCI`/`XCZ`-файлов с внешнего USB-накопителя в exFAT/FAT32: флешки, жёсткого диска, проч.
* **Install title from USB** — установка `NSP`/`NSZ`/`XCI`/`XCZ` из ПК по USB 2.0 и 3.0-проводу, через прилагаемую программу dbibackend. *Горячая клавиша для этой опции*: кнопка **(Y)**.
* **Install title from Gamecard** — этот пункт появляется при вставленном в Switch игровом картридже, — для установки игры из имеющегося игрового картриджа в microSD-карту или внутреннюю NAND-память консоли.
* **Home server** — начиная с версии v150, есть возможность устанавливать игры по сети (HTTP), через WiFi без провода или LAN-USB-адаптер. Подробнее об этом ниже
* **Browse installed applications** — просмотр установленных игр, их общее установленное количество, посмотреть потраченное время на игру и количество её запусков, проверить (верифицировать) на ошибки, перенести игровые данные между встроенной памятью, картой памяти и обратно, возможность их выборочного или потокового удаления вместе с прилагаемыми LayeredFS-модами, просмотр наличия у них обновлений и DLC, ручное удаление DLC/обновлений/LaryeredFS (LFS) мода, функция Reset Required version для сброса системной проверки обновления у выбранной игры. *Горячая клавиша для этой опции*: кнопка **(L)**.
* **Cleanup orphaned files** — автоматическая чистка ненужных удалённых файлов игр, если они есть
* **Browse tickets** — просмотр и ручное удаление системных тикетов игр.
* **Browse saves** - просмотр и удаление сохранений 
* **Run MTP responder** — включение внутреннего MTP-сервера для присоединения Switch к ПК или к Android-устройству (телефон/планшет/пр., протестированы Pixel 3, Xiaomi Mi A1, Lenovo Tab 4 7" TB-7304X), можно: просматривать и работать с картой памяти (1: External SD Card) и внутренней память консоли, просматривать установленные игры (4: Installed games), сделать бекап игровых сохранений на ПК (7: Saves), при вставленном игровом картридже дампить его (full/trimmed/сертификат) на ПК/Android (9: Gamecard). *Горячая клавиша для этой опции*: кнопка X (ей же выходить из MTP).
* **Run FTP server** - включает FTP-сервер DBI для доступа к файлам microSD через порт 5000 или установку файлов через порт 6000
* **Exit** — выход из программы. *Горячая клавиша для этой опции*: кнопка **(+)**

В самом левом нижнем углу (SD) написано про занятый размер данных на карте/общий размер карты. В правом нижнем углу (NAND) написан занятый размер данных во встроенной памяти Switch/общий встроенной памяти Switch.
Внизу по центру (dbi: XXX) написан номер версии dbi — старайтесь всегда использовать самую последнюю версию программы

### Управление

* **(А)** - выбор, подтверждение
* **(B)** - отмена. **На главном экране** - выход из программы
* **(X)** - выделение файла. **На главном экране** - горячая клавиша для монтирования MTP (пункт меню "**Run MTP responder**")
* **(Y)** - инвертировать выделение, выделить всё, если ничего не выделено. **На главном экране** - установка по USB с помощью dbibackend (пункт меню "**Install title from USB**")
* **(ZL)**, **(ZR)** - быстрое перемещение по меню 
* **(L)** **на главном экране** - перейти в меню "**Browse installed applications**"
* **(R)** - изменить порядок отображения файлов/тайтлов
* **(L3)** - запустить игру из списка установленных игр
* **(+)** на правом джойконе - контекстное меню, которое позволяет производить контекстные операции, как-то удаление, сброс требуемой версии прошивки, монтирование по MTP и др. 
* **(-)** на левом джойконе при установке приложений отключает/включает экран

### Browse SD Card/Browse USB0 Drive

Выберите этот пункт, если хотите установить игры/обновления/DLC из уже имеющихся файлов на карте памяти/внешнем USB. 
Кнопка **(A)** открывает папку, кнопка **(B)** возвращает назад, после открытия папки с файлами для установки, кнопкой **(X)** можно выделить только необходимые файлы, кнопокй **(Y)** инвертировать выбор. При этом цвет названия выделенных файлов изменится с белого на светло-синий. 

После этого нажмите кнопку **(А)** для подтверждения. Возникнет окно с опциями установки:

![2021041011441100](https://user-images.githubusercontent.com/18294541/114264183-18138580-99f2-11eb-8c7b-536b4b831195.jpg)

**Total transfer size** — объём установочных дистрибутивов (файлов `NSP`/`NSZ`/`XCI`/`XCZ`), выбранных и готовых к установке.
**Total install size** — объём свободного пространства, которое необходимо для установки выбранных файлов.
**Install target** — локация установки данных: **NAND** — внутренняя память консоли Nintendo Switch, **SD** — карта памяти microSD, **AUTO** — опция по-умолчанию для установки всегда на карту памяти microSD, но если на ней будет недостаточно места, данные установятся во внутреннюю память.
**Delete after install** — это опция удаления установочных дистрибутивов (файлов `NSP`/`NSZ`/`XCI`/`XCZ`) с карты после их успешной установки; чтобы она работала, с файлов должен быть снят атрибут «Только чтение». По-умолчанию файлы не удаляются. Опция видна только при установке с карты памяти/внешнего USB
**Turn off screen** — возможность выключить экран на время установки для экономия электроэнергии аккумулятора, сразу после успешной установки экран автоматически включится. Эта опция работает только в портативном режиме.
Нажмите **Start install**, чтобы начать установку. После успешной установки, внизу появится надпись *Installation Complete. Press B to return*.

В программе имеется встроенная автоматическая функция удаления старых апдейтов при установке нового обновления к игре, поэтому за лишнее занимаемое место ими можно не беспокоиться.

Вы можете запускать `.NRO`-файлы кнопкой **(A)**

### Install title from USB

Через Install title from USB очень удобно устанавливать игры, обновления и DLC к ним сразу напрямую по USB-проводу с ПК на Switch, минуя необходимость вынимать карту и тратить двойное время, закачивая дистрибутивы (`NSP`/`NSZ`/`XCI`/`XCZ`-файлы) на карту памяти и устанавливая их оттуда. *Горячая клавиша для вызова этой опции из главного меню*: кнопка **(Y)**.

Для работы сперва нужно скачать на ПК dbibackend (`dbibackend.exe` для Windows или `dbibackend` для всех ОС), запустить его, выбрать игры для установки, нажать **Start server**, затем подключить USB-C кабель к ПК и Switch, выбрать пункт **Install title from USB** в dbi и установить все необходимые игры.

Выделение файлов, а так же их установка происходит способом идентичным способу из пункта **Browse SD Card/Browse USB0 Drive**

Для быстрой отправки файлов или папок с играми на установку, нажмите на них правой клавишей мыши, выберите Отправить > dbibackend, установочные файлы сразу помещаются в очередь dbibackend. Для того, чтобы это настроить в Windows, нажмите `Win+R`, введите `shell:sendto`, положите в папку ярлык для `dbibackend.exe`

### Home server

Пункт **"Home server"** появляется при наличии настроенного раздела **Network install sources** в `dbi.config` (подробнее про этот файл ниже). Причём название этого пункта будет меняться в зависимости от названия указанного в конфигурационном файле

Для установки игр по сети, отредактируйте файл **[dbi.config](#dbiconfig)**, находящийся в папке `sdmc:/switch/DBI/`, согласно примеру

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
location/{
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

В **Browse installed applications** можно посмотреть список установленных программ, обновлений, DLC к ним, по отдельности их занимаемый объём и версию, порядковую и в HEX-формате, их titleID, посмотреть общее время игры и количество запусков, наличие установленного LayeredFS-мода к игре (для Atmosphére). 

*Горячая клавиша для вызова этой опции из главного меню*: кнопка **(L)**:

Сверху в центре написано общее количество установленных игр и тип сортировки

![2021062719353200](https://user-images.githubusercontent.com/18294541/123554546-32efcd80-d789-11eb-8d3f-3124448624e0.jpg)

В квадратных скобках перед названием игры написана базовая информация о месте установки, составе и наличии мода игры. Отображается только то, что установлено. То есть, если буквы b в квадратных скобках нет, значит у игры не установлена сама базовая часть (в таком случае строка будет окрашена красным)

* **N/S/M** - NAND/SD/Mixed - означает место, где установлена игра. В случае, если части игры находятся на разных носителях, отображается Mixed 
* **b** - BASE - сама игра 
* **u** - Update - обновление игры 
* **d** - DLC - DLC игры 
* **l** - LayeredFS mod - наличие модификаций, читов или перевода

**Обратите внимание!** Если игра выделена **красным**, значит не установлена её базовая часть, а установлено только обновление или DLC 

#### Контекстное меню тайтла

![2021062719354100](https://user-images.githubusercontent.com/18294541/123554557-3b480880-d789-11eb-9235-d547f2c588bd.jpg)

Отображается при нажатии на **(+)** на выбранных тайтлах (или тайтле)

В верху контекстного окна отображается количество выбранных тайтлов и их размер

* **Delete title** - удалить выбранные тайтлы
* **Move title to MicroSD/NAND** - переместить выбранные тайтлы в NAND или на карту памяти, в зависимости от того, где тайтл сейчас находится. Если части тайтла находятся и там и там, будут отображены оба варианта
* **Reset required version** - сбросить проверку требуемой для запуска тайтла версии системы (должен быть включён дебаг в Atmosphere)
* **Check integrity** - проверка целостности данных выбранных тайтлов
* **Expose contents via MTP** - смонтировать содержимое выбранных тайтлов по MTP 

Если нажать на тайтле кнопку **(A)**, то откроется детальное меню игры 

### Детальное меню игры

![2021062719353600](https://user-images.githubusercontent.com/18294541/123554561-400cbc80-d789-11eb-8d81-e3403f33b365.jpg)

Отображается иконка игры, **TitleID**, название (**name**), автор (**Author**), версия (**Version**), поддерживаемые языки (**Language**) и наличие LFS-мода (**LFS-mod**)

Так же здесь можно узнать количество времени, проведённого в игре (**Total play time**), сколько раз игра была запущена (**Total launches**), сколько она весит (в целом (**Total occupied space**), а так же сколько места занимает в NAND (**Space in NAND**) и на SD (**Space on MicroSD**)), размер сохранений (**Total saves size**) и какой язык у игры активен (**Forced Language**)

#### Контекстное меню записи

![2021062719354800](https://user-images.githubusercontent.com/18294541/123554565-41d68000-d789-11eb-9c59-621275895075.jpg)

Отображается при нажатии на **(+)** на выбранных записях 

В верху контекстного окна отображается количество выбранных записей и их размер

* **Delete record** - удалить выбранную запись
* **Move records to MicroSD/NAND** - переместить выбранную запись в NAND или на карту памяти, в зависимости от того, где она сейчас находится. Если части тайтла находятся и там и там, будут отображены оба варианта
* **Reset required version** - сбросить проверку требуемой для запуска тайтла версии системы (должен быть включен дебаг в Atmosphere)
* **Force language** - позволяет принудительно запускать игру с выбранным языком. По-умолчанию игра запускается с тем же языком, что выбран в системе, ежели такового в игре нет, то в зависимости от региона консоли. Выбранный язык будет отображаться рядом с иконкой игры в поле **Forced Language**
* **Check integrity** - проверка целостности данных выбранных тайтлов
* **Expose contents via MTP** - смонтировать содержимое выбранных тайтлов по MTP 

### Cleanup orphaned files
**Cleanup orphaned files** автоматически чистит ненужные файлы игр, файлы от прерванных установок игр, скачанное (официально) обновление OFW прошивки и все неиспользуемые тикеты игр, если они были найдены. 

### Browse tickets
Просмотр и удаление ненужных тикетов игр. **Ticket (или encrypted title key)** — это специальная зашифрованная уникальная информация о правах запуска на контент игры, которая устанавливается в систему при инсталляции каждой игры (**000** в конце titleID)/обновления (**800** в конце titleID)/каждого DLC. 

* **(+)** означает наличие установленной игры
* **[c]** — common-тикет (установленного дампа игры либо обновления)
* **[p]** — personalized-тикет (купленной в eShop игры)

Иногда, если возникают специфическая ошибка, и вы точно знаете и уверены, что вы делаете, его можно удалить у конкретной игры и её обновления/DLC.
Во всех остальных случаях лучше тут ничего не трогать, во избежание ошибок запуска игр.

#### Контекстное меню тикетов

Отображается при нажатии на **(+)** на выбранных тикетах 

В верху контекстного окна отображается количество выбранных тикетов

* **Delete tickets** - удалить выбранные тикеты
* **Select same game** - выделить все тикеты, относящиеся к выделенной игре 

### Browse saves

Просмотр и удаление сохранений. 

Жёлтым цветом выделены сохранения для удалённых игр. 

#### Контекстное меню сохранений

Отображается при нажатии на **(+)** на выбранных сохранениях

В верху контекстного окна отображается количество выбранных сохранений

* **Delete saves** - удалить выбранные тикеты
* **Select same game** - выделить все тикеты, относящиеся к выделенной игре 
* **Select all uninstalled** - выделить все сохранения для удалённых игр

### Run MTP responder 
**Run MTP responder** включает встроенный в dbi MTP-сервер для обмена данными с ПК либо к Android-устройству по USB-C OTG (телефон/планшет/прочие устройства). *Горячая клавиша для вызова этой опции из главного меню*: кнопка **(X)** (ей же выходить из MTP). После подключения USB-провода к ПК и запуска MTP-сервера в dbi, на ПК появится следующее окно:

![изображение](https://user-images.githubusercontent.com/18294541/114265006-054f7f80-99f7-11eb-86c9-1a20d588e616.png)

Где:
1: **External SD Card**, для просмотра, копирования и удаления файлов и папок c/на ПК и с/на карту памяти microSD. В случае, если размер файла превышает 4Гб, DBI автоматически разобьёт его на фрагменты специальным образом, чтобы свитч видел такой файл как цельный

2: **NAND User**, просмотр, копирование файлов и папок на ПК с внутренней память Switch, в его системный раздел USER (раздел доступен только для чтения).     

3: **NAND System**, просмотр, копирование файлов и папок на ПК с внутренней памяти Switch, в его системный раздел SYSTEM (раздел доступен только для чтения).     

4: **Installed games**, для просмотра установленных игр.

В **Installed games** отображаются все игры как в NAND, внутренней памяти Switch, так и установленные на карту памяти, все вместе. Чтобы сделать дамп (дистрибутив) установленный игры себе на ПК в формате .NSP, просто скопируйте папку с названием игры из **Installed games** на свой ПК, при этом на базе вашего personalized-тикета генерируется общий common-тикет с полностью очищенной личной информацией. Вы получите дамп этой игры в виде раздельных файлов - отдельно саму игру, отдельно обновление и DLC. Если для игры были установлены читы или моды, они будут находится в папке `Mods & Cheats`. Так же можно получить скомбинированный дамп, в котором в один файл будет склеяны сама игры, все её DLC и обновление. Такой файл лежит прямо в корне раздела **Installed games**.

Здесь так же хранится сгенерированный dbi `InstalledApplications.csv`, с таблицей списка установленных игр, их TitleID и текущей версии.     

5: **MicroSD install**     
Скопируйте в эту папку ваши **NSP**/**NSZ**/**XCI** или **XCZ**. По окончанию копирования игра будет установлена на **карту памяти** вашей приставки. При установке NSZ-файлов учитывайте, что их фактический размер может сильно отличаться от размера после установки, так что если при наличии свободных 2Гб на карте памяти у вас, например, не хватает места для установки NSZ размером, скажем, в 1Гб, не удивляйтесь, поскольку контейнер NSZ - сжатый.

6: **NAND install**: Скопируйте в эту папку ваши  **NSP**/**NSZ**/**XCI** или **XCZ**. По окончанию копирования игра будет установлена во **внутреннюю память** вашей приставки. При установке NSZ-файлов учитывайте, что их фактический размер может сильно отличаться от размера после установки, так что если при наличии свободных 2Гб на карте памяти у вас, например, не хватает места для установки NSZ размером, скажем, в 1Гб, не удивляйтесь, поскольку контейнер NSZ - сжатый.

7: **Saves**: Доступ ко всем сохранениям игр — в аккаунтах (Account), системных программ (System), в Background Content Asymmetric synchronized delivery and Transmission (BCAT, пример: ивенты в ACNH), временных (Temporary), кэш (Cache, пример: аддоны в DOOM), системных BCAT (SystemBCAT), — хранящимся во внутренней памяти Switch

В папке **Installed games** — сохранения для имеющихся установленных сейчас игр

Unin**stalled games** — сохранения от удалённых игр, которые раньше запускались. Отсюда можно сделать их бекап, скопировав их на ПК, а также удалить ненужные — для этого откройте папку с именем нужной игры, затем удалите папку с ником вашего аккаунта/Device-сохранения.

Для того, чтобы восстановить сохранения, скопируйте их в соответствующую папку с ПК. DBI не требует предварительного запуска игры для восстановления сохранения, однако это касается только обычных сохранений. BCAT или Cache сохранения требуют предварительного запуска игры перед восстановлением.

8: **Album**: доступ к скриншотам и видеороликам (Альбому), точно так же, как это сделано в OFW 11.0.0 Nintendo.     

9: **Gamecard**: при вставленном в Switch игровом картридже появляется возможность скопировать его дамп в .XCI либо trimmed .XCI на ПК, вместе со встроенным в него обновлением, если оно есть, с уже убранным его персональным RSA-сертификатом; кроме того, возможно отдельно экспортировать его сертификат     

Также, на дисплее Switch после включения MTP-сервера появится окно с вашим ником учётной записи и его UID, а также количеством игровых сохранений:
 ![2021041013152900](https://user-images.githubusercontent.com/18294541/114266673-27013480-9a00-11eb-81ba-f1ff1c3c5abb.jpg)

Чтобы выключить MTP-сервер и выйти в главное меню, нажмите кнопку **(X)** или **(B)**.

### Exit
**Exit** — выход из программы в HOS, минуя hbmenu, либо в hbmenu (это настраивается в dbi.config); если dbi был запущен из тайтла/форвардера, программа перезагрузится либо останется на чёрном экране.

## Уведомления и коды ошибок
### УВЕДОМЛЕНИЯ:

* **«SIGNATURE: Invalid»/«SIGNATURE: GC->eShop» / HASH NOT MATCHED TO META** — это НЕ ОШИБКИ, а уведомления о несовпадении подписи в заголовках, например, при использовании конвертации или редактирования, кастомного NSP, форвардера.
* **«HASH MISMATCH»** — чаще всего, это НЕ ОШИБКА, игра была сконвертирована из картриджа (тогда всё в порядке), иногда — имеются проблемы с целостностью файла, перекачайте-перехешируйте его, передачей данных по USB-кабелю/порту/в процессе установки между ПК и Switch.
    Если игра не запускается или запускается с ошибкой, попробуйте переустановить её снова, проверить либо заменить USB-кабель/microSD/сменить USB-порт.
* **DELTA SKIPPED** — это НЕ ОШИБКА, а уведомление, что ненужные фрагменты в файле обновления были пропущены, если они в нём были, как и было должно.
* **«No tickets found. Possibly this NSP was converted from XCI.»** — это НЕ ОШИБКА, на работоспособность игры не влият, но информирование, что игра без тикетов. Она может быть дампом из .XCI-картриджа или переконвертирована в Standard Crypto.
* **«WARNING» title marked as Application but has AddonContent** — это НЕ ОШИБКА, обычно это указывает на homebrew-игру в .NSP, созданную не по стандартам, к примеру, когда в Application-тайтл (основную игру, v0) добавили и AddonContent-флаг (DLC).
    Если такая игра запускается и работает, тогда всё в порядке.
* **«This application base is not stand alone. Make sure you installed update»** при установке новых Sparse Storage игр — это НЕ ОШИБКА, не забудьте, кроме базового файла игры, установить ещё и апдейт к ней перед запуском.

### ОШИБКИ:

* **«read: USB communication failed»** — проверьте/замените USB-кабель и USB-порт на ПК.
* **«Cannot parse content meta. Corrupted file or old firmware»** — Либо файл поврежден, либо ваша прошивка слишком устарела для анализа метафайла. Проверьте файл и обновите его до последней версии cfw и последней поддерживаемой версии прошивки.
* **«Can not find file for ncaid»** — установочный файл игры повреждён (в нём отсутствует нужный .nca из списка .cnmt).
* **«Invalid PFS0 magic!»** — перекачайте установочный файл игры и проверьте его целостность, этот файл повреждён.
* **«Invalid NCA magic!»** — обновитесь на последнюю версию OFW и CFW, если ошибка сохраняется после этого, перепроверьте целостность установочного файла игры.
* **«Received less data than expected»** и **Installation aborted** — ошибка в передаче данных, перепроверьте и при необходимости замените USB-кабель/USB-порт между Switch и ПК. Также обязательно убедитесь, что у вас установлена самая последняя версия программы, как вот в этом посте.
* **«std::bad_alloc»** — переименуйте файл без спецсимволов и кириллицы в имени и пути к нему, плюс убедитесь, что у используете самую последняя версия программы, как в посте, на консоль установлена последняя версия OFW и CFW.
* **«Nothing to install»** в окне выборе файлов — переименуйте файл без спецсимволов, иероглифов или кириллицы в имени и пути к нему.
* **«INVALID LENGTH»** — проверить соединение USB-C кабеля и USB-порта, проверить с другими USB-C-кабелями, целостность файла игры и карту памяти на ошибки, при установке через MTP — запустить dbi через любую игру (тайтл) с удерживанием кнопки R, а не в режиме апплета через альбомы.
* **«INVALID DECOMPRESSED LENGTH», вместе с «TRANSFER ERROR»**, при установке с карты памяти/носителя/dbibackend — освободите побольше места на карте памяти, удалите ненужные файлы с карты, если их больше 20000 шт.
* **«Error occurred: Invalid argument»** — обновите ваш dbi на последнюю версию.
* **«[FAILED] Unknown error»** при установке .tik (тикета) — установите последние сигпатчи для Atmosphére.
* **«605: Content or placeholder path not exists»** и **«SOME CONTENTS ARE MISSING»** — битая файловая система карты памяти, или нерабочая/некачественная флешка. Проверьте её в chkdsk и h2testw, если нет ошибок, переформатируйте в FAT32.
* **«Can not create placeholder»** — не хватает места на карте памяти/NAND, освободите его побольше.
* **WARNING! Extra buffers exceeded**, при установке через MTP — запустите dbi через тайтл = через любую игру, удерживая кнопку R при её запуске; альтернативно — через NSP-форвардер, и использовать более быструю microSD-карту с другим USB-кабелем/портом.
* **No tickets found but they are required** — некорректный (неполный, без тикета но с titlerights) дамп игры, найдите другой.
* **SOME CONTENTS ARE MISSING. APPLICATION WILL BE UNUSABLE** — контейнер неполный, проверьте целостность установочного файла игры.
* **«Invalid personalized ticket»**, в конце установки игры при инсталлировании .tik-тикета — некорректный дамп игры, где вместо common-тикета остался персонализированный с той консоли, на которой была куплена игра; скачайте другой, корректный дамп.
* **«No ES или других sigpatches»** — не все/устаревшие/некорректно/не установлены сигпатчи на консоли, установите их самую новейшую версию.
## dbi.config
Файл dbi.config был добавлен, начиная с версии 253. Он находится рядом с DBI.nro, и заменяет прежние файлы-флаги dbi.default.ascii и dbi.network.config, а также добавляет несколько новых опций для удобной кастомизации настроек под пользователя.

Рассмотрим его содержимое:
```
; General settings
[General]
; Use libnx default font for ASCII characters
DefaultASCII=true
; Use libusbhsfs to access external USB drives
UseLibUsbHsFS=true
; Direct exit to homescreen when exiting DBI
ExitToHomeScreen=false
; Folder where saves backups are stored
SavesFolder=sdmc:/switch/DBI/saves/
; Log "Install", "Check integrity" and "Cleanup" processes
LogEvents=false
; Folder where logs are stored
LogsFolder=sdmc:/switch/DBI/logs/
; Sorting options for application list
AppSorting=Name,LastPlayed,InstallLocation,Size
; Sorting options for save list
SaveSorting=AppName,AppLastPlayed,UserUid,Size,SaveId
; Highlight available updates for currently installed titles in DBI's file browser
HighlightUpdates=true
; Rotate screen upside down
RotateScreen=false
; Rotate joycons
RotateJoycon=false
; Underclock CPU and GPU in menus to reduce battery usage
OptimizeClockSpeed=false
; URL with title versions in format <id>|<rightsId>|[version]
; VersionsURL=sdmc:/versions.txt
VersionsURL=https://raw.githubusercontent.com/blawar/titledb/master/versions.txt
; Browse saves FS in Read-only mode
ROSaveFS=true

; Visibility of main menu options
[MainMenu]
; Browse and install files from MicroSD card
BrowseSD=true
; Browse and install files from external USB drives
USBHost=true
; Browse and install files from PC via dbibackend
BackendInstall=true
; Install game from inserted game cartridge
GameCard=true
; Browse and install files from configured network installation sources
Network=true
; Browse and install files from configured sd card folders
Local=false
; Browse installed applications
BrowseApps=true
; Clean up files left from bad installations/old updates/unused tickets etc
Cleanup=true
; Check for app updates
UpdateCheck=true
; View or delete installed tickets
Tickets=false
; Dedicated save game management menu
Saves=true
; MTP responder
MTP=true
; FTP server
FTP=true

[Applications]
; Check LayeredFS mod size (large mods may take a long time)
CalculateLFSSize=false

; Installation options
[Install]
; Check NCA hash during installation
CheckHash=true

; MTP options
[MTP]
; Log all transfers on the console, if disabled only transfer of files >= 2M will be displayed
LogAllFiles=false
; Display combined NSPs which contain base game, latest update and all DLC in a single file
ShowCombinedNSP=true
; Display per game "Mods & cheats" folder that redirects to sdmc:/atmosphere/contents/TITLEID/
ShowMAC=true
; Display user defined custom virtual MTP drives
CustomStorages=true
; Enable 'NAND install' when running emuMMC
EnableNANDInstallOnEmunand=true
; Turn screen off when MTP mode is activated
TurnOffScreen=false

; Enable or disable virtual MTP drives
[MTP Storages]
1: External SD Card=true
2: Nand USER=false
3: Nand SYSTEM=false
4: Installed games=true
5: MicroSD install=true
6: NAND install=true
7: Saves=true
8: Album=true
9: Gamecard=true

; Network installation sources
[Network sources]
; <display name>=<type>|<URL>
; NSP Indexer=URLList|http://192.168.1.47/nspindexer/index.php?DBI
; Home server=ApacheHTTP|http://192.168.1.47/Nintendo/Switch/

; Main menu shortcuts to SD card locations
[Local sources]
; <display name>=<path>
; Homebrew Shortcut=sdmc:/switch
; Album Screenshots Shortcut=sdmc:/Nintendo/Album/2021/
; DBILogs=sdmc:/switch/DBI/logs
; AMS Fatal Reports Shortcut=sdmc:/atmosphere/fatal_reports/
; AMS Crash Reports Shortcut=sdmc:/atmosphere/crash_reports/

; Custom virtual MTP drives
[MTP custom storages]
; <display name>=<path>
Homebrew=sdmc:/switch

; Override for display name in DBI and MTP mode
[Title name override]
; <UPPERCASE TID>=<Desired name>
; 010023901191C000=Naheulbeuk
```

### General settings
* **DefaultASCII** - **true** используется стандартный шрифт, **false** используется альтернативный шрифт
* **UseLibUsbHsFS** - **true** включает библиотеку [libusbhsfs](https://github.com/DarkMatterCore/libusbhsfs) для работы с внешними USB-накопителями через USB-OTG на Switch, **false** отключает её.
* **ExitToHomeScreen** — при **false** выход из dbi происходит в hbmenu, при **true** на рабочий стол Switch.
* **SavesFolder** - папка для хранения дампов сохранений
* **LogEvents** - сохранять или нет логи для событий "*Install*", "*Check integrity*" and "*Cleanup*"
* **LogsFolder** - папка для хранения логов
* **AppSorting** - опции для сортировки списка приложений
* **SaveSorting** - опции для сортировки сохранений
* **Visibility of main menu items** - настроить, какие пункты меню будут отображаться в главном меню DBI, вы можете запретить отображение параметра в главном меню, изменив значение на **false**
* **HighlightUpdates** - подсвечивать или нет в файловом менеджере обновления для установленных игр
* **RotateScreen** - переворачивает экран на 180 градусов
* **RotateJoycon** - переворачивает управление, чтобы соответствовать перевёрнутому экрану 
* **OptimizeClockSpeed** - отключает оптимизацию частоты SoC в простое. Отключено по-умолчанию, поскольку **может привести к лагам на стартовом экране при некорректном выходе из DBI**! Корректный выход - через пункт меню **Exit**.
* **VersionsURL** - может принимать прямую ссылку на файл на уудалённом сервере, либо на файл на карте памяти. Примеры: `https://raw.githubusercontent.com/blawar/titledb/master/versions.txt` или `sdmc:/versions.txt`

### MainMenu
Показ соответствующих элементов меню.

**true** - отображать **false** - нет 

* **BrowseSD** - пункт "**Browse SD card**, для установки игр с Sd карты 
* **USBHost** - пункт "**Browse USB0 Drive**, для установки игр с внешнего USB
* **BackendInstall** - пункт "**Install title from USB**, для устаноки игр с ПК через backend 
* **GameCard** - пункт "**Install title from Gamecard**, для установки содержимого картриджа в память консоли
* **Network** - пункт "**Home server**, для установки игр с домашнего веб-сервера
* **Local** - показывать или нет ссылки на папки из раздела [Local sources](#local-sources)
* **BrowseApps** - пункт "**Browse installed applications**, для управления установленными приложениями
* **Cleanup** - пункт "**Cleanup orphaned files**, для очистки "осиротевших" файлов с карты памяти
* **UpdateCheck** - пункт "**Check for title updates**", для проверки обновлений и DLC для установленных игр
* **Tickets** - пункт "**Browse tickets**, для управления тикетами
* **MTP** - пункт "**Run MTP responder**, для запуска MTP
* **FTP** - пункт "**Run FTP server**, для запуска FTP

### Install

* **CheckHash** — при **true** проверяются хеши .nca-файлов при установке игр на Switch, при false нет.

### Applications
* **CalculateLFSSize** — включает или отключает подсчёт размера установленных LFS-модов. Если включено, может повлиять на скорость открытия меню "*Browse installed applications*"

### MTP
* **LogAllFiles** — **false** выключает логирование файлов меньше 4Мб при работе с MTP, при **true** логируются все файлы.
* **ShowCombinedNSPInInstalledGames** — **false** выключает показ комбинированных (multi-title .NSP-file) тайтлов.
* **ShowMACInInstalledGames** — **false** выключает показ виртуальной директории **«Mods & cheats»** в пункте Installed games в MTP, перенаправляющей по пути `sdmc:/atmosphere/contents/TITLEID/` на карту памяти.
* **CustomStorages** - отображать или спрятать кастомные пункты меню, прописанные в секции **MTP custom storages**
* **EnableNANDInstallOnEmunand** - разрешает или запрещает установку игр в NAND файлового EmuNAND (не актуально после выхода Atmosphere 0.19.3)
* **TurnOffScreen** - отключать или нет экран консоли при подключении её в режиме MTP

### [MTP Storages](#run-mtp-responder)
Показ соответствующих элементов при работе MTP Responder с ПК/Android, по умолчанию все пункты включены для отображения.

**true** - отображать в главном меню, **false** - нет 

Названия пунктов соответствуют названиям разделов

### [Network sources](#home-server)
Задаются имена и адреса для установки игр по сети (через WiFi/LAN-адаптер)

**NSP Indexer** - адрес для индексации NSP ([подробнее](https://github.com/rashevskyv/dbi/issues/44))

### Local sources

Создание пунктов меню с быстрым доступом к выбранным в конфиге папкам на карте памяти («ярлыки»), например: 

`Homebrew Shortcut=sdmc:/switch` создаст в главном меню пункт "**Homebrew Shortcut**", который откроет папку `sdmc:/switch`

### MTP custom storages

Кастомные пункты для MTP-режима для быстрого доступа к папкам на вашей карте памяти. Формат: `<отображаемое_имя папки>=<путь>`, например: `Homebrew=sdmc:/switch`. 
В режиме MTP появится папка `Homebrew`, ссылающаяся на папку `switch` на вашей карте памяти

### Title name override

Позволяет изменить имя отображаемого тайтла. Например, если указать `10023901191C000=Naheulbeuk`, то в приложении вместо `The Dungeon of Naheulbeuk: The Amulet of Chaos` будет отображаться просто `Naheulbeuk`

## Другие возможности

### Монтирование содержимого установленных игр по MTP 

Перейдите в "*Browse installed applications*" -> Выберите необходимые игры кнопкой `X` -> Нажмите `(+)` -> "*Expose contend via MTP*"

### Бекап и восстановление сохранений 

1. Подключите приставку в режиме MTP по DBI 
2. Перейдите в папку **Saves** на вашем ПК
3. Вы можете как скопировать сейвы на ПК, так и восстановить их, просто перетянув в эту папку

### Использование DBI для установки модификаций:
1. Подключите приставку в режиме MTP по DBI 
1. Перейдите в **Installed Games**, в папку с названием вашей игры
1. Перейдите в папку **Mods & Cheats**
1. Поместите в папку **Mods & Cheats** ваш мод
1. **Будьте внимательны**, вам нужно класть не саму папку с titleID игры, а её содержимое! Например, вы скачали перевод для игры Cadence of Hyrule, в виде архиве `Cadence of Hyrule.rar`. Внутри этого архива вы видите папку с TitleID игры - `01000B900D8B0000`. Вам нужно распаковать архив, перейти в папку `01000B900D8B0000` и скопировать всё содержимое папки в **Mods & Cheats**! Не саму папку `01000B900D8B0000`, а всё то, что в ней находится! В данном примере, папку `romfs`

### USB 3.0 

DBI поддерживает работу по USB 3.0. Если вы используете kefir, то USB 3.0 активно по-умолчанию. В ином случае, нужно активировать эту функцию через конфигурационные файлы Atmosphere, прописав в `atmosphere\config\system_settings.ini`: 

```
[usb]
usb30_force_enabled = u8!0x1
```



## Благодарности
Спасибо [SciresM](https://github.com/SciresM) за  [hactool](https://github.com/SciresM/hactool) (лицензия [ISC](https://ru.wikipedia.org/wiki/%D0%9B%D0%B8%D1%86%D0%B5%D0%BD%D0%B7%D0%B8%D1%8F_ISC)) - DBI использует некоторые структуры данных, взятые оттуда
