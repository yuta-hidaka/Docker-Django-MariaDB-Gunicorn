### setup

This docker-compose can make Django Project auntomatically with production env.
Set a APP-Name in .eve and add your package in requirements.txt and just run!

```
git clone https://github.com/yuta-hidaka/Docker-Django-MariDB-Gunicorn.git

# Edit these files as you need
# .env is for docker-compsoe and django's app name
# first time this docker-compose.yml try make a django app , second time or if exist a app script throw warining and throw the creation app prrosess
cp .env.sample .env

# requirements.txt is for python packeage
cp django_data/requirements.txt.sample django_data/requirements.txt

# run this command
dcoker-compose up --build

# move to django_data/src/<APP-NAME>/<APP-NAME>/settings.py and edit DB infomation and run below
docker-compose exec python-django python <APP-NAME>/manage.py showmigrations

# access to localhost
http://localhost


```
