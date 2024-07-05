# Docker
- **Docker_file** - базовые возможности Dockerfile
- **docker-compose** - вариации **docker-compose** компонентов

## docker-compose

### php+nginx
Базовая версия для настройки дебага с минимум переменных, нужна для найстройки отладки
Настроить сервер и все готово
```yml
PHP_IDE_CONFIG: serverName=DockerProject1
```

Данные:
http://127.0.0.1:8882/ - host
<u>docker-compose/php+nginx/docker-compose.yml:10</u> - менять порт тут

### php+nginx+