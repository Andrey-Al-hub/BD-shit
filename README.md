## Подготовка БД для Django

В pgAdmin зайти на свой локальный сервер
После на нем создать новую базу данных

Создадим нового пользователя базы данных, который сможет использовать
для подключения и взаимодействия с БД

!!! прописывать без []

`CREATE USER [имя пользователя] WITH PASSWORD 'тут пишим пароль к нему';`

После нужно изменить несколько параметров подключения только что созданного
пользователя. Для ускорения операции с БД

`ALTER ROLE [имя пользователя] SET client_encoding TO 'utf8';`
`ALTER ROLE [имя пользователя] SET default_transaction_isolation TO 'read committed';`
`ALTER ROLE [имя пользователя] SET timezone TO 'UTC';`

Предоставляем пользователю БД права доступа к базе данных, которую создали

`GRANT ALL PRIVILEGES ON DATABASE [название базы данных] TO [имя пользователя];`

## Настройка виртуальной среды

Установим библиотеку для работы с виртуальной средой в Python

`pip install virtualenv`

Создадим новую виртуальную среду внутри каталога куда помещены склонированные файлы

`python -m venv env`

Активация среды 

`source [название]/bin/activate`

Теперь находясь в окружение, можем устанавливать пакеты не боясь конфликта
с уже установленными 

Для работы нужно установить:

`pip install Django`
`pip install psycopg2`
`pip install Pillow`

!!! Запуск сервера и т.д. нужно из виртуального окружения

Для выхода из окружения

`deactivate`

## Запуск сервера

Чтобы запустить сервер нужно находится в папке с файлом manage.py
`python.py manage.py runserver`

## Создание базы данных и просмотр sql-кода

Команда создания sql-запроса:
`python manage.py makemigrations`

Команда для просмотра созданного sql-запроса
`python manage.py sqlmigrate [название приложения] [номер созданной миграции]`

`Команда для выполнения миграции
`python manage.py migrate`

## Создание супер пользователя

Для входа в админ-панель нужно создать пользователя
`python manage.py createsuperuser`

