# API для Yatube

REST API для социальной сети Yatube, где пользователи могут публиковать записи и подписываться на авторов.

## Описание

API позволяет:
- Просматривать, создавать, редактировать и удалять публикации
- Просматривать и создавать комментарии к публикациям
- Просматривать сообщества
- Подписываться на авторов

## Установка

Клонировать репозиторий и перейти в него:

```bash
git clone https://github.com/<username>/api_final_yatube.git
cd api_final_yatube
```

Создать и активировать виртуальное окружение:

```bash
python3 -m venv venv
source venv/bin/activate
```

Установить зависимости:

```bash
pip install -r requirements.txt
```

Выполнить миграции:

```bash
cd yatube_api
python manage.py migrate
```

Запустить проект:

```bash
python manage.py runserver
```

## Примеры запросов

Получить JWT-токен:

```
POST /api/v1/jwt/create/
{
    "username": "your_username",
    "password": "your_password"
}
```

Получить список публикаций:

```
GET /api/v1/posts/
```

Создать публикацию:

```
POST /api/v1/posts/
Authorization: Bearer <token>
{
    "text": "Текст публикации"
}
```

Подписаться на автора:

```
POST /api/v1/follow/
Authorization: Bearer <token>
{
    "following": "username"
}
```
