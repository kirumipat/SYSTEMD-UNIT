# SYSTEMD-UNIT
## Добавляем скрипт в автозагрузку
<img src="https://linuxteaching.com/storage/img/images_1/systemd_unit_file_creating_a_service.png">


## Создаём фаил скрипта
```console
nano mystart.sh
```
## Пример скрипта Который запускаеться от root при загрузке системы
```console
#!/bin/bash
############-YOU SCRIPT-##############
touch /"$(date +"%d-%m-%Y-%r")"
######################################
```
## Пример скрипта Который запускаеться от root при логине любого пользователя
### Тестировалось на Ubuntu Server 22
```console
#!/bin/bash
LoginTime=`last -n 1 | grep -e logged`
while :; do
    LasTime=`last -n 1 | grep -e logged`
    if [ "$LasTime" != "$LoginTime" ] && [ "$LasTime" != "" ]; then
        LoginTime=`last -n 1 | grep -e logged`
        ############-YOU SCRIPT-##############
        touch /"$(date +"%d-%m-%Y-%r")"
        ######################################
    fi
    sleep 10
done
```
## Разрешаем запуск скрипта
```console
sudo chmod +x mystart.sh
```
## Переходим в директорию с сервисами
```console
cd /etc/systemd/system
```
## Создаём фаил сервиса
```console
sudo nano mystart.service
```

## Настройки юнита
```console
[Unit]
# описание
Description=MYSTART
# здесь используется ключи времени с указанием цели или другой службы
After=default.target

[Service]
# от какого пользователя запускать службу, не обязательно
User=root
# перезапуск службы, не обязательно
Restart=on-failure
# выполняемая команда Вместо NAME имя пользователя или просто другой путь где у вас лежит скрипт
ExecStart=/home/NAME/mystart.sh

[Install]
# здесь используется ключи времени с указанием цели или другой службы
WantedBy=default.target
```
## Запускаем сервис единоразово
```console
sudo systemctl start mystart.service
```
## Добавляем сервис в автозагрузку
```console
sudo systemctl enable mystart.service
```

## VIDEO

[<img src="https://i.ytimg.com/vi/SGHjEDVhb38/maxresdefault.jpg" width="600" height="400" >](https://youtu.be/SGHjEDVhb38)

