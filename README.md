# Effective Mobile Test

## Используемые технологии

- Docker
- Docker Compose
- Python 3.12
- Nginx

## Архитектура

Client
  |
  v
Nginx (80)
  |
  v
Backend (8080)

Nginx принимает HTTP-запросы и проксирует их в backend-сервис внутри Docker-сети.

## Запуск

Склонировать репозиторий:

```bash
git clone git@github.com:Naroll/effective_test.git
cd effective_test
```

Добавьте пользователя в группу docker:

```bash
sudo usermod -aG docker $USER
newgrp docker
```

Собрать и запустить контейнеры:

```bash
docker-compose up -d --build
```

Проверить контейнеры:

```bash
docker ps
```

## Проверка

Выполнить:

```bash
curl http://localhost
```

Ожидаемый результат:

```text
Hello from Effective Mobile!
```

Проверка, что backend не доступен с хоста:

```bash
curl http://localhost:8080
```

Ожидаемый результат:

```text
curl: (7) Failed to connect
```

Остановка:

```bash
docker compose down
```
