# API для Yatube

REST API для социальной сети Yatube, где пользователи могут публиковать записи,
оставлять комментарии и подписываться на авторов.

# Описание

API позволяет:
- Просматривать, создавать, редактировать и удалять публикации
- Просматривать и создавать комментарии к публикациям
- Просматривать сообщества
- Подписываться на авторов и просматривать свои подписки

# Стек технологий

- Python 3.9+
- Django 3.2
- Django REST Framework 3.12
- Simple JWT
- Djoser

# Установка

Клонировать репозиторий и перейти в него:

```bash
git clone https://github.com/Rufina007/api_final_yatube.git
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

# Примеры запросов

# Получить JWT-токен

```
POST /api/v1/jwt/create/
{
    "username": "your_username",
    "password": "your_password"
}
```

Ответ:
```json
{
    "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9...",
    "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..."
}
```

# Получить список публикаций

```
GET /api/v1/posts/
```

Ответ:
```json
{
    "count": 2,
    "next": null,
    "previous": null,
    "results": [
        {
            "id": 1,
            "author": "username",
            "text": "Текст публикации",
            "pub_date": "2024-01-01T12:00:00Z",
            "image": null,
            "group": null
        }
    ]
}
```

# Создать публикацию

```
POST /api/v1/posts/
Authorization: Bearer <token>
{
    "text": "Текст публикации"
}
```

Ответ:
```json
{
    "id": 2,
    "author": "username",
    "text": "Текст публикации",
    "pub_date": "2024-01-01T12:00:00Z",
    "image": null,
    "group": null
}
```

# Подписаться на автора

```
POST /api/v1/follow/
Authorization: Bearer <token>
{
    "following": "author_username"
}
```

Ответ:
```json
{
    "user": "username",
    "following": "author_username"
}
```

# Получить комментарии к публикации

```
GET /api/v1/posts/1/comments/
```

Ответ:
```json
[
    {
        "id": 1,
        "author": "username",
        "post": 1,
        "text": "Текст комментария",
        "created": "2024-01-01T12:00:00Z"
    }
]
```

# Автор

Руслана
