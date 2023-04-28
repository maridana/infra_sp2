# Запуск docker-compose проекта API_YAMDB

### Технологии

* Python 3.7

* Django 2.2

* DRF 

* JWT + Djoser

* Postgresql

* Docker

* NGINX

# Запуск проекта
## Dev-режим:
- Клонировать репозиторий и перейти в него в командной строке.
```bash
git clone
```
- Установить виртуальное окружение:
```bash
python -m venv venv
```
- Активировать виртуальное окружение :

```bash
source venv/Scripts/activate
```

- Перейти в директорию yatube_api и установить зависимости из файла requirements.txt:
```bash
cd api_yamdb

pip install -r requirements.txt
```
- Выполнить миграции:
```bash
python manage.py makemigrations

python manage.py migrate
```
- Создать суперпользователя:
```bash
python manage.py createsuperuser
```
- Запустить проект:
```bash
python manage.py runserver
```
## Docker-compose:
### Предварительная настройка

- Шаблон наполнения .env расположенный по пути infra/.env
```bash
DB_ENGINE=<...> # указываем, что работаем с postgresql
DB_NAME=<...> # имя базы данных
POSTGRES_USER=<...> # логин для подключения к базе данных
POSTGRES_PASSWORD=<...> # пароль для подключения к БД (установите свой)
DB_HOST=<...> # название сервиса (контейнера)
DB_PORT=<...> # порт для подключения к БД 
```
### Запуск

- Перейти в папку с docker-compose:
```bash
cd infra
```
- Запустить контейнер:
```bash
docker-compose up -d --build 
```
- Выполнить миграции:
```bash
docker-compose exec web python manage.py makemigrations

docker-compose exec web python manage.py migrate
```
- Создать суперпользователя:
```bash
docker-compose exec web python manage.py createsuperuser
```
- Собрать статику:
```bash
docker-compose exec web python manage.py collectstatic --no-input
```