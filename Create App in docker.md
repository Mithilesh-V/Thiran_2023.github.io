## Making a django project in docker

#### Steps:

**Configure the directory to be used as a docker container**
	
1. Make a directory for the proj & `cd` into it
2. Create a *docker-compose.yml* file 
3. Create a *Dockerfile* file (don't change the name)
4. In Dockerfile, 
	```
	From python:3
	ENV PYTHONBUFFERED 1
	RUN mkdir /app
	WORKDIR /app
	COPY requirements.txt /app/
	RUN pip install -r requirements.txt
	copy . /app/
	```
 
 5. Create a *requirements.txt* file and add `Django==2.2`
 6. In *docker-compose.yml*, 
	```yml
	version: '3'
	services:
		web:
			build: .
			command: python manage.py runserver 0.0.0.0:8000			
			volumes: 
				- .:/app
			ports:
				- "8000:8000"
	```
7. Open the terminal in the directory and run the following commands,
	```shell
	sudo docker-compose run web django-admin startproject mysite .
	sudo chown -R $USER:$USER .
	docker-compose up
	```
8. Go to your browser and use the address `127.0.0.1:8000`
9. Go back to the terminal and run 
	 ```shell
	 docker exec <IMAGE_NAME> python manage.py startapp greet
	 ```
10. You will be able to see that *apps.py* has been created within the directory
11. In *views.py* add
	```python
		from django.shortcuts import render
		from django.http import HttpResponse
		
		def hello(request):
			return HttpResponse("Hello World")
	```
12. Make a *urls.py* file in *greet* and add
	```python
	from django.urls import path
	from . import views

	urlpatters = [
		path('hello',views.hello.name='hello')
	]
	```
13. Go to *urls.py* in mysite and import *include* from *django.urls*
14. To *urls.py* add	
	```python
	path('',include('greet.urls'))
	```
15. In your terminal run, 
	```shell
	sudo docker-compose up
	```
16. Refresh your site & **Tada!**

