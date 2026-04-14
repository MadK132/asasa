# Keycloak Local Guide

Этот файл нужен как короткая рабочая инструкция для команд, которые подключают фронт или бэк к локальному Keycloak из этого репозитория.

## Что должен поднимать docker-compose

Локально здесь запускаются:

- `Postgres`
- `Keycloak`

Конфигурация realm импортируется из `realm-config/realm-export.json` при старте Keycloak.

Актуальные значения из репозитория:

- `realm`: `sana-lms`
- локальный URL Keycloak: `http://localhost:8080`
- админка: `http://localhost:8080/admin`
- admin login: `admin`
- admin password: `admin`

## Как развернуть локально

Требования:

- установлен Docker
- доступен `docker compose`

Запуск:

```bash
docker compose up -d
```

Проверить, что Keycloak поднялся:

```bash
docker compose ps
```

После старта открыть:

- `http://localhost:8080`
- `http://localhost:8080/admin`

Остановка:

```bash
docker compose down
```

Полный сброс локальных данных:

```bash
docker compose down -v
```

## Обязательные env для Keycloak

Для локального запуска самого Keycloak в этом репозитории используются такие env:

```env
KEYCLOAK_ADMIN=admin
KEYCLOAK_ADMIN_PASSWORD=admin
KC_DB=postgres
KC_DB_URL_HOST=db
KC_DB_URL_DATABASE=keycloak
KC_DB_USERNAME=keycloak
KC_DB_PASSWORD=keycloak
```

## Что передавать бэку

Env для бэка: [env](https://85.198.89.217/sana/sana-platform/-/blob/dev/.secrets.local.cue?ref_type=heads)


## Что передавать фронту

Env для фронта: [env](https://85.198.89.217/sana/sana-platform/-/blob/dev/.secrets.local.cue?ref_type=heads)
