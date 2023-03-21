# api_yamdb

## Описание:
### REST API для YaMDb
Создан на основе библиотеки [Django REST Framework (DRF)](https://github.com/ilyachch/django-rest-framework-rusdoc)


>YaMDb - это платформа для сбора отзывов и оценок по различным категориям.

## Технологии
Python 3.7

Django 2.2.16

Django REST framework 3.12.4

Gunicorn 20.0.4


## Запуск проекта:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone git@github.com:serebrennikovalexander/infra_sp2.git
```

```
cd infra_sp2/infra
```

Создать файл .env:
```
cd infra_sp2/infra
```
Создать файл .env:
```
touch .env
```

Заполнить файл .env переменными окружения для работы с базой данных:
```
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД
```
Запустить приложение в контейнерах:
```
sudo docker-compose up -d
```
Выполнить миграции:
```
sudo docker-compose exec web python manage.py migrate
```
Cоздать суперпользователя:
```
sudo docker-compose exec web python manage.py createsuperuser
```
Cобрать статику:
```
sudo docker-compose exec web python manage.py collectstatic --no-input
```
Узнать CONTAINER ID контейнера infra_web_1:
```
sudo docker container ls
```
Скопировать файл базы данных в контейнер infra_web_1:
```
sudo docker cp fixtures.json <CONTAINER ID>:app/
```
Заполнить базу данных:
```
sudo docker-compose exec web python manage.py loaddata fixtures.json
```
Войти в админку по адресу:
```
http://localhost/admin/
```

## Авторы:
[kultmet](https://github.com/kultmet)

[serebrennikovalexander](https://github.com/serebrennikovalexander)

[olka-ayacaste](https://github.com/olka-ayacaste)
