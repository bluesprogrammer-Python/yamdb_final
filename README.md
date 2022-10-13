![workflow](https://github.com/bluesprogrammer-Python/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

# yamdb_final


### Описание: 
  REST API для проекта Yamdb. С этим интерфейсом могут взаимодействовать мобильные приложения, боты или другие сторонние ресурсы.  
  Проект YaMDb собирает отзывы и оценки пользователей на различные произведения. К отзывам можно оставлять комментарии.  
  В этом проекте используется технология контейнерезации. Проект разделён на два контейнера web и nginx. Контейнер web занимается сбором, а nginx - раздачей статики.  
  С помощью этой технологии можно максимально быстро развернуть проект на другом ПК, не беспокоясь о зависимостях и рабочем окружении.


### Технологии в проекте:
  Python 3.9, Django 2.2.16, Django REST Framework (DRF), Docker 20.20.18,  
  docker-compose 3.8, nginx:1.21.3-alpine
  

### Последовательность команд при запуске:

#### Создайте файл .env с переменными окружения для работы с базой данных  
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД

#### Клонировать репозиторий и перейти в него в командной строке
git clone git@github.com:bluesprogrammer-Python/yamdb_final.git
cd yamdb_final/infra

#### Сборка контейнеров и запуск
sudo docker-compose up -d --build  

#### Выполнение миграций, создание суперпользователя и сбор статики
sudo docker-compose exec web python manage.py migrate
sudo docker-compose exec web python manage.py createsuperuser
sudo docker-compose exec web python manage.py collectstatic --no-input

#### Остановка собранных контейнеров  
sudo docker-compose down -v

#### Адрес боевого сервера 
http://51.250.82.87:80

### Автор:
 	Семёнов Сергей (Github - bluesprogrammer-Python)
