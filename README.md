## Описание:
kittygram - это сервис для любителей котиков. Пользователи могут создавать и делиться информацией о своих или чужих котиках.

# Как запустить проект
Копируем docker-compose.production.yml на продакшен-сервер в директорую kittygram.

Создаем .env файл с информацией о создаваемой БД.

Выполняет pull образов с DockerHub
```
sudo docker compose -f docker-compose.production.yml pull
```

# Запускаем все контейнеры в docker compose
```
sudo docker compose -f docker-compose.production.yml up -d
```
# Выполняет миграции и сбор статики
```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
```
```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
```
```
sudo docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/
```
## Примеры запросов:
### Создание пользователя:
```
 [POST]https://kittgramm.ddns.net/api/users/
{
  "username": "Name",
  "password": "123456789and"
}
```
### Ответ:
```
{
    "email": "",
    "username": "Name",
    "id": 1
}
```

### Получение списка всех котиков:
```
    [GET]https://kittgramm.ddns.net/api/cats/
```
### Ответ:
```
[
  {
    "id": 11,
    "name": "Scot",
    "color": "darkorange",
    "birth_year": 2023,
    "achievements": [
      {
        "id": 1,
        "achievement_name": "храпит"
      }
    ],
    "owner": 1,
    "age": 0,
    "image": "http://kittygramm.crabdance.com/media/cats/images/temp_qrZM4sH.jpeg"
  },
  {
    "id": 14,
    "name": "Ярик",
    "color": "orange",
    "birth_year": 2017,
    "achievements": [
      {
        "id": 1,
        "achievement_name": "храпит"
      }
    ],
    "owner": 1,
    "age": 6,
    "image": "http://kittgramm.ddns.net/media/cats/images/temp_BqLjDCY.jpeg"
  },
  {
    "id": 15,
    "name": "Name",
    "color": "whitesmoke",
    "birth_year": 2023,
    "achievements": [
      {
        "id": 1,
        "achievement_name": "храпит"
      }
    ],
    "owner": 3,
    "age": 0,
    "image": "http://kittgramm.ddns.net/media/cats/images/temp_8QCsMRA.jpeg"
  }
]
```

# Kittygram
https://kittgramm.ddns.net

