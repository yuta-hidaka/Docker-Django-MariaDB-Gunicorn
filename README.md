### setup

This docker-compose can make Django Project auntomatically with production env.
Set a APP-Name in .eve and add your package in requirements.txt and just run!

```
git clone https://github.com/yuta-hidaka/Docker-Django-MariDB-Gunicorn.git
```

#### Edit these files as you need
#### .env is for docker-compsoe and django's app name
#### first time this docker-compose.yml try make a django app , second time or if exist a app script throw warining and throw the creation app prrosess
```
cp .env.sample .env
```

#### Requirements.txt is for python packeage
```
cp django_data/requirements.txt.sample django_data/requirements.txt
```
#### Run this command
```
dcoker-compose up --build
```

* ```<APP-NAME>``` is defined in .env files by argument [DJANGO APP_NAME]

##### Move to django_data/src/<APP-NAME>/<APP-NAME>/settings.py and edit DB infomation and run below
```
docker-compose exec python-django python <APP-NAME>/manage.py showmigrations
```

#### Collect static files
```
docker-compose exec python-django python <APP-NAME>/manage.py collectstatic
```

##### Migrate
```
docker-compose exec python-django python <APP-NAME>/manage.py migrate
```

###### If get an Error like 
```
"(1071, 'Specified key was too long; max key length is 767 bytes')" Please add this in settings.py
```
###### it is django-allauth issue
###### ref. https://code.djangoproject.com/ticket/18392

```
ACCOUNT_EMAIL_MAX_LENGTH = 190
```

##### Access to localhost
http://localhost


#### Remote Debug
This Docker-compose accept remote debug by gunicorn and use may CPU resource.
When you publish product using this docker container or anoying that , please remove this command in .env file .

```
GUNICORN_CMD_ARGS='--timeout=100000000'
```
to
```
GUNICORN_CMD_ARGS=''
```
or just remove and edit docker-compose.yml



