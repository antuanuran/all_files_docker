# 1.runserver
1. Заливаем Dockerfile в папку проекта (комментируем gunicorn)
2. run.sh:
python manage.py collectstatic --noinput
python manage.py migrate
python manage.py runserver 0.0.0.0:8000
3. docker-compose (комментируем nginx)

Запускаем:
* docker build -t [api] .
* docker-compose up -d
* docker-compose restart [backend]

# 2.+ gunicorn
1. в Dockerfile (раскоментируем gunicorn)
2. run.sh:
set -eux
python manage.py collectstatic --noinput
python manage.py migrate
gunicorn --workers 2 -b 0.0.0.0:8000 [stocks_products].wsgi:application (меняем на название своей папки)

Запускаем:
* docker build -t [api] .
* docker-compose up -d

# 3.+ nginx
1. Dockerfile (не меняем)
2. run.sh (не меняем)
3. Заливаем в папку с docker-compose файл nginx.conf
4. Раскомментируем в docker-compose (nginx)
5. Не забываем про ports 80:80

Запускаем:
* docker build -t [api] .
* docker-compose up -d





