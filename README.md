# SYSTEMD-UNIT
Creating a Linux service with systemd

<img src="">


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


## VIDEO

[![INSATALL ADDGUARD HOME](https://i.ytimg.com/vi/yfq1H9bT8c4/hqdefault.jpg)](https://youtu.be/A4FTz2vLCMo)
