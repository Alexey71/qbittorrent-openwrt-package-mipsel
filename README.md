# qBittorrent для OpenWRT (mipsel)
Пакет qBittorrent и его зависимости для OpenWRT (libtorrent-rasterbar и qt5, libtorrent-rasterbar назван как qlibtorrent-rasterbar).

Расположение пакетов в конфигураторе такое:

Пакет `qt5` по пути `Libraries --> Qt5`

Пакет `qlibtorrent-rasterbar` (libtorrent-rasterbar) по пути `Libraries --> qlibtorrent-rasterbar`

Пакет `qBittorrent` по пути `Network --> BitTorrent --> qbittorrent`


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
OpenWRT package Makefiles for qBittorrent and its dependencies (libtorrent-rasterbar and qt5, libtorrent-rasterbar is named as qlibtorrent-rasterbar).

You can see the qt5 library packages in `Libraries --> Qt5`, the qlibtorrent-rasterbar (libtorrent-rasterbar) package in `Libraries --> qlibtorrent-rasterbar`, and the qBittorrent package in `Network --> BitTorrent --> qbittorrent`.

## How to open
After installing qBittorrent. Go to Web UI Settings 
```
Adress Web UI: http://192.168.1.1:8080/
Username: openwrt
Password: openwrt
```

## Folder settings
Default qBittorrent setting folder `/etc/qBittorrent`. You can change it to your, edit the file `/etc/init.d/qbittorrent`

## Tested
Tested on `Xiaomi Mi WiFi Router 3G v1` and `OpenWRT v21.02.x`
