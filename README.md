![example workflow](https://github.com/rerolll/kittygram_final/actions/workflows/main.yml/badge.svg)
# Kittygram - социальная сеть для размещение фотографий домашних животных.

## Описание проекта
Социальная сеть для обмена фотографиями любимых питомцев

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/rerolll/kittygram_final.git
```

Перейти в корневую директорию
```
cd kittygram_final
```

Создать файл .evn для хранения ключей:
```
SECRET_KEY='указать секретный ключ'
ALLOWED_HOSTS='указать имя или IP хоста'
POSTGRES_USER=django_user
POSTGRES_PASSWORD=password
POSTGRES_DB=kittygram
DB_HOST=db
DB_PORT=5432
```

Создайте секреты в GitHub Actions
Перейдите в настройки репозитория — Settings, выберите на панели слева Secrets and Variables → Actions, нажмите New repository secret и создайте следующие переменные:
  - DOCKER_PASSWORD
  - DOCKER_USERNAME
  - HOST
  - POSTGRES_DB
  - POSTGRES_PASSWORD
  - POSTGRES_USER
  - SSH_KEY
  - SSH_PASSPHRASE
  - TELEGRAM_TO
  - TELEGRAM_TOKEN

Запустить docker-compose.production:

```
docker compose -f docker-compose.production.yml up
```

Выполнить миграции, сбор статики:

```
docker compose -f docker-compose.production.yml exec backend python manage.py migrate
docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /static/static/

```

Создать суперпользователя:

```
docker compose -f docker-compose.production.yml exec backend python manage.py createsuperuser
```
