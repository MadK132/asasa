# Keycloak Local Guide

Этот файл нужен как короткая рабочая инструкция для команд, которые подключают фронт или бэк к локальному Keycloak.

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

После того как подняты фронт, бэк и Keycloak, нужно зайти в админку Keycloak и создать пользователя в нашем realm.

Как создать пользователя:

1. Открыть `http://localhost:8080`
2. Войти под `admin` / `admin`
3. Выбрать realm `sana-lms`
4. Перейти в `Users`
5. Нажать `Add user`
6. Заполнить пользователя и сохранить
7. Перейти во вкладку `Credentials`
8. Задать пароль
9. Если не нужен сброс пароля при первом входе, отключить `Temporary`
10. Для задачи роли переходим во вкладку `Role mapping`
11. Нажимаем на `Assign role` => `Realm roles`
12. Выбираем необходимую роль

## Что передавать бэку

Env для бэка: [env](https://85.198.89.217/sana/sana-platform/-/blob/dev/.secrets.local.cue?ref_type=heads)


## Что передавать фронту

Env для фронта: [env](https://85.198.89.217/sana/sana-lms/-/blob/dev/.env.example?ref_type=heads)
