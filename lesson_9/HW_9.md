# Задача 2
Развернуть Python-веб-сервер, настроить управление через systemd от имени пользователя webadmin (без домашней директории и shell-доступа), организовать логирование;

```
sudo useradd --system --no-create-home --shell /usr/sbin/nologin webadmin
```

```
[Unit]
Description=Python Server for webadmin
After=network.target

[Service]
Type=simple
User=webadmin
Group=webadmin
WorkingDirectory=/opt/webserver
ExecStart=/usr/bin/python3 /opt/webserver/server.py
Restart=always

StandardOutput=append:/var/log/webadmin/server.log
StandardError=append:/var/log/webadmin/server_error.log
```