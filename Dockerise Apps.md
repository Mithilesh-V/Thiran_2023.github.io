## Dockerise a pre-built Django Project 

Create the Django project
```shell
django-admin --version

cd Sem5/
mkdir pbdp
cd pbdp

django-admin startproject mysite
cd mysite
ls -l

python3 manage.py runserver
```

Create a *requirements.txt* file
```
Django==2.2
gunicorn==20.0.4
```

Create a *Dockerfile* file
```
FROM python:3

ENV PYTHONUNBUFFERED 1

WORKDIR /app

ADD . /app

COPY ./requirements.txt /app/requirements.txt

RUN pip install -r requirements.txt

COPY . /app
```

Create a *docker-compose.yml* file

```
version: '3'

services:
	web: 
		build: .
		command: python manage.py runserver 0.0.0.0:8000
		ports:
			- 8000:8000
```
		
Run the container
```shell
sudo docker-compose build
sudo docker-compose up
```