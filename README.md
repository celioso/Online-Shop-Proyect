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

## rabbitMQ
iniciar `celery -A myshop worker -l info`
link `http://127.0.0.1:15672/`

​ejecutar celery por windows: `​celery -A myshop worker --loglevel=info -P solo`

## Installar flower
`pip install flower`

iniciar `celery -A myshop flower`
link `http://127.0.0.1:5555/`


### Stripe

crea una cuenta en una red finaciera [https://dashboard.stripe.com/](https://dashboard.stripe.com/)

Instalar stripe `pip install stripe`

## seguridad en archivo .env

El archivo `.env` se utiliza comúnmente en proyectos de Python para almacenar variables de entorno sensibles, como claves de API, configuraciones de base de datos y otros datos de configuración que no se deben almacenar directamente en el código fuente. Este archivo es especialmente útil para mantener la seguridad y facilitar la configuración de diferentes entornos (desarrollo, pruebas, producción, etc.).

Para usar un archivo .`env` en un proyecto de Python, generalmente se utiliza la librería python-dotenv. Aquí te explico cómo hacerlo:

### 1. Instala la librería python-dotenv

Primero, necesitas instalar la librería `python-dotenv`. Puedes hacerlo utilizando `pip`:

```bash
pip install python-dotenv
```

### 2. Crea un archivo .env

Crea un archivo llamado `.env` en la raíz de tu proyecto. Este archivo contendrá tus variables de entorno en el siguiente formato:

**.env**
```env
SECRET_KEY=supersecretkey
DATABASE_URL=postgres://user:password@localhost:5432/mydatabase
DEBUG=True
```

### 3. Carga las variables de entorno en tu código Python
Para cargar y acceder a estas variables de entorno en tu código Python, debes utilizar la librería `python-dotenv`. Aquí tienes un ejemplo:

```python
from dotenv import load_dotenv
import os

# Cargar las variables de entorno desde el archivo .env
load_dotenv()

# Acceder a las variables de entorno
secret_key = os.getenv("SECRET_KEY")
database_url = os.getenv("DATABASE_URL")
debug = os.getenv("DEBUG")

print(f"Secret Key: {secret_key}")
print(f"Database URL: {database_url}")
print(f"Debug Mode: {debug}")
```

### 4. Uso en diferentes entornos

Puedes tener diferentes archivos `.env` para diferentes entornos, como `.env.development`, `.env.production`, etc., y cargar el archivo apropiado según el entorno en el que estés ejecutando tu aplicación.

### 5. Seguridad

Importante: Nunca debes subir tu archivo .env a un repositorio público. Asegúrate de incluirlo en tu .gitignore si estás utilizando Git.

**.gitignore**

```
.env
```
Con esto, puedes gestionar tus variables de entorno de manera segura y eficiente en tus proyectos de Python.