# Docker
- **Docker_file** - базовые возможности Dockerfile
- **docker-compose** - вариации **docker-compose** компонентов

## docker-compose

### php
Базовая версия только для php, запуском сервера php
http://0.0.0.0:8000/ - host
Для дебага добавить сервер с параметрами:
имя сервера - **любое**
**0.0.0.0** - IP
**8000** - port

### php+nginx
Базовая версия для настройки дебага с минимум переменных, нужна для найстройки отладки
Для дебага добавить сервер с указанным именем `DockerProject1`, ip и порт любые
```yml
PHP_IDE_CONFIG: serverName=DockerProject1
```

Данные:
http://127.0.0.1:8882/ - host
<u>docker-compose/php+nginx/docker-compose.yml:10</u> - менять порт тут

### 