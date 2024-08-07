# Online Shop Proyect

1. ver la version de `python --version`

2. selecionar la version de python se usa Ctrl + shift + P  y se selecciona Python: Select Interprete y se escoje la version que se desea trabajar.

3. crear el entorno virtual: `python -m venv venv`

4. pactivar el entorno virtual en windows `.\venv\Scripts\activate` y en unix o MAcOS es `source tutorial-env/bin/activate` 

5. instalar Django es `pip install django`

6.  ver las dependencias instaladas `pip freeze` si se desea crear el requirements.txt que espara cargar la dependencias se utiliza `pip freeze > requirements.txt` y para cargarlo se utiliza `pip install -r requirements.txt`.

7. la construccion del proyecto `django-admin startproject <nombre-proyecto>`

8. crear la migracion de la base de datos se dirige a la carpeta mysite y luego se el codigo `python manage.py migrate`

9. se usa el servidor web de python `python manage.py runserver`

10. se crea la app con `python manage.py startapp shop`

11. se aplica la migración `python manage.py makemigrations shop`

12. cuando se quiere saber que sentencia va a crear django para actuar con la base de datos `python manage.py sqlmigrate shop 0001` 0001 es el numero de la migración

13. para migrarlo `python manage.py migrate` 

[Django 4 by example (4th Edition) github](https://github.com/PacktPublishing/Django-4-by-example)

[Django 4 by example (4th Edition) book](https://books.google.es/books?id=GLaEEAAAQBAJ&pg=PA171&hl=es&source=gbs_selected_pages&cad=1#v=onepage&q&f=false)


## Instalar Celery

`pip install celery`

### docker

1. descargar la imagen de `pip install celery`
2. ejecute la imagen `docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:management`

3. se ingresa ela link `http://127.0.0.1:15672`
login y passwork es **guest**

para redircccioner el broker `app.conf.broker_url = 'amqp://<User>:<passwork>t@localhost'` ejemplo `app.conf.broker_url = 'amqp://guest:guest@localhost'` en el archivo `myshop/celery.py`

## Installar flower
`pip install flower`

iniciar ` celery -A myshop flower`