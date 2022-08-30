# SYSTEMD-UNIT
Creating a Linux service with systemd



## Создаём фаил скрипта
```bash
nano mystart.sh
```
## Пример скрипта
```bash
#!/bin/bash
touch /"$(date +"%d-%m-%Y-%r")"
```
## Рарешаем запуск скрипта
```bash
sudo chmod +x mystart.sh
```
## Переходим в деррикторию с сервисами
```bash
cd /etc/systemd/system
```
## Создаём фаил сервиса
```bash
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
# выполняемая команда
ExecStart=/home/NAME/mystart.sh

[Install]
# здесь используется ключи времени с указанием цели или другой службы
WantedBy=default.target
```
## Запускаем сервис единоразово
```bash
sudo systemctl start mystart.service
```
## Добавляем сервис в автозагрузку
```bash
sudo systemctl enable mystart.service
```

## VIDEO

[![INSATALL ADDGUARD HOME](https://i.ytimg.com/vi/yfq1H9bT8c4/hqdefault.jpg)](https://youtu.be/A4FTz2vLCMo)
