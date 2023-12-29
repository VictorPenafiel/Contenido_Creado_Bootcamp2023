Instalación y verificación
1.-Instalar django
  pip install django=="numero de version"
2.-Verificar el estado de la instalacion
  python -m django version
3.-Ver comando disponibles en Django
  python -m django help
-----------------------------------------------------------------------------------------------------------------
*Gestión de dependencias
● pip install -r requirements.txt -> para instalar las dependencias desde un archivo
● pip freeze > requirements.txt -> para generar un respaldo de los paquetes instalados creando un
archivo requirements.txt
● pip install astral==2.2 -> para instalar una versión específica de un paquete que necesitemos, en
este ejemplo astral 2.2

-----------------------------------------------------------------------------------------------------------------
Crear proyecto
1-django-admin startproject "Nombre"
  Entrar a carpeta
    python manage.py migrate
    python manage.py startapp web

2.- Agregar esta app a la lista de aplicaciones instaladas, debemos abrir el archivo settings.py presente en la carpeta de
la app principal de nuestro proyecto y agregarla a la lista de INSTALLED_APPS
'web.apps.WebConfig',

  2.1.- Si tengo una base de datos ya creada ocupar
  python manage.py inspectdb >web\models.py
  Para obtener el modelo de la base y copiarlo en el archivo models.py

3.- Luego, dentro de la carpeta de la app web se debe crear una carpeta llamada templates y a continuación dentro de ella crear los archivos
index.html, about.html y welcome.html
4.- Habilitar las 3 urls distintas se debe crear en el archivo views.py dentro de la carpeta web una vista por cada url, cada una de las cuales retornará un render con los datos necesarios para desplegar cada uno de los archivos html creados anteriormente.
5.- Registrar las vistas en el archivo urls.py para que dirijan a las rutas /, /acerca y /bienvenido respectivamente
6.- Crear una plantilla base se debe crear un archivo llamado base.html en la carpeta web/templates que contenga la estructura
general de la web a mostrar, usando blocks y marcando con fondos de colores (background) cada sección para mostrar de manera más
explícita la separación entre éstas (opcional).
7.- Una vez creado este archivo, debemos reemplazar el contenido de nuestros archivos index.html, about.html y welcome.html (como
se muestra en las imágenes) de manera que extiendan de nuestra plantilla base (extends) y reemplacen el contenido (block content) por el
contenido correspondiente a cada una de las vistas (mensajes).
{% extends 'base.html'%}
{% block 'content' %}
<div>
    mensaje
</div>
{% endblock %}

8.- Añadir bootstrap a nuestro sitio web, debemos agregar los archivos css y javascript de Bootstrap
9.- Para poder mostrar un contenido estático (como imágenes, videos,etc) se debe crear la carpeta web/static
  agregar  class=“container” a todos los templates de tu proyecto, para que Bootstrap pueda funcionar.
      python manage.py runserver
      
-----------------------------------------------------------------------------------------------------------------
Operaciones Comunes
Crear proyecto
  python -m django startproject "nombre proyecto"
Acceder a la carpeta creada. Crear aplicacion
  python manage.py startapp "nombre proyecto"-----manage.py "archivo para activar la iniciacion del proyecto"
Generar archivos de migracion
  python manage.py makemigrations
Aplicar los cambios creados por makemigrations
  python manage.py migrate
Crear super usuario
  python manage.py createsuperuser
ejecutar nuestro proyecto de manera local
  python manage.py runserver

-----------------------------------------------------------------------------------------------------------------
Integración con una base de datos existente por medio de Django
      python manage.py inspetdb > web/models.py

Integración con una base de datos existente por medio de pgAdmin 
\COPY "peliculas" FROM 'C:\Users\usuario\peliculas.csv' WITH CSV;

-----------------------------------------------------------------------------------------------------------------


*Formularios de contexto

1.-Formulario Form

from django import forms
class ContactFormForm(forms.Form):
    customer_email = forms.EmailField8label='Correo')
    customer_name = forms.CharField(max_length=64, label='Nombre')
    message = forms.CharField(label='Mensaje')

1.1-Formulario clase Modal Form, creación de un formulario basado en un modelo

from .models import ContacForm
class ContactFormModelForm(forms.ModelForm):
    class Meta:
        model = ContactForm
        fields = ['customer_email','customer_name', 'message']

2.- El formulario es procesado por una vista en views.py
class ContactFormForm(forms.Form):
    customer_email = forms.EmailField8label='Correo')
    customer_name = forms.CharField(max_length=64, label='Nombre')
    message = forms.CharField(label='Mensaje')

-----------------------------------------------------------------------------------------------------------------
*Manejo de contenido estático
static
Para agregar contenido desde un archivo colocar al inicio del html
    {% load static %}
 
Despues se modifica cada ruta de los archivos que se quiere agregar, colocando
    {% static "más nombre del archivo con extension" %}