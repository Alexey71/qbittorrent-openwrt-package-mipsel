# qBittorrent для OpenWRT (mipsel)
Пакет qBittorrent и его зависимости для OpenWRT (libtorrent-rasterbar и qt5, libtorrent-rasterbar назван как qlibtorrent-rasterbar)

## Обозначения папок
Расположение пакетов в конфигураторе такое:

Пакет `qt5` (qt5-core, qt5-network, qt5-sql, qt5-xml) версия 5.15.2, по пути `Libraries --> Qt5`

Пакет `qlibtorrent-rasterbar` (libtorrent-rasterbar) версия 1.2.15, по пути `Libraries --> qlibtorrent-rasterbar`

Пакет `qBittorrent` версия из последних исходников https://github.com/qbittorrent/qBittorrent/commits/master, по пути `Network --> BitTorrent --> qbittorrent`

## Как пользоваться
После устаноки qBittorrent. Перейдите в настройки веб интерфейса:
```
Адрес веб интерфейса: http://192.168.1.1:8080
Имя пользователя: openwrt
Пароль: openwrt
```

## Папка настроек
По умолчанию папка настроек qBittorrent создается по пути `/etc/qBittorrent`. Вы можете изменить путь создания папки, для этого откройте файл `/etc/init.d/qbittorrent` и измените строку `ARGS="--profile=/etc"`

## Протестировано
Протестировано на `Xiaomi Mi WiFi Router 3G v1` и `OpenWRT v21.02.x`

========================================================================
# qBittorrent for OpenWRT (mipsel)
OpenWRT package Makefiles for qBittorrent and its dependencies (libtorrent-rasterbar and qt5, libtorrent-rasterbar is named as qlibtorrent-rasterbar)

## Folder designations
Package location in the configuration is:

Package `qt5` (qt5-core, qt5-network, qt5-sql, qt5-xml) version 5.15.2, path `Libraries --> Qt5`

Package `qlibtorrent-rasterbar` (libtorrent-rasterbar) version 1.2.15, path `Libraries --> qlibtorrent-rasterbar`

Package `qBittorrent` version of the last source https://github.com/qbittorrent/qBittorrent/commits/master, path `Network --> BitTorrent --> qbittorrent`

## How to open
After installing qBittorrent. Go to Web UI Settings 
```
Adress Web UI: http://192.168.1.1:8080
Username: openwrt
Password: openwrt
```

## Folder settings
By default, the qBittorrent settings folder is created on path `/etc/qBittorrent`. You can change the folder path, To do this, open the file `/etc/init.d/qbittorrent` and change the line `ARGS="--profile=/etc"`

## Tested
Tested on `Xiaomi Mi WiFi Router 3G v1` and `OpenWRT v21.02.x`
