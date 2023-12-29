# instalar postgres como base de datos
# instalar pgadmin como gestor de base de datos
# crear database
    CREATE DATABASE db_practica_orm;
# crear usuario
    CREATE USER user_db WITH PASSWORD 'user_db';
# asignar permisos al usuario
    GRANT ALL PRIVILEGES ON DATABASE db_practica_orm TO postgres;
    GRANT ALL PRIVILEGES ON DATABASE db_practica_orm TO user_db;
# crear el proyecto
    pip install django
    django-admin startproject config
# crear la aplicación
    cd config
    django-admin startapp producto
# configurar base de datos
    conector db:
        pip install psycopg2
    config/settings.py:
        agregar configuración de la base de datos
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',  # database to use
        'NAME': 'db_practica_orm',  # database name
        'USER': 'postgres',  # user database
        'PASSWORD': 'admin',  # password user database
        'HOST': '127.0.0.1',  # localhost
        'PORT': '5432',  # database port number
    }
}        
# crear modelos para la aplicación
# realizar migraciones
    python manage.py makemigrations
    python manage.py migrate
    python manage.py sqlmigrate aplicacion 0001

 

# crear views para listar y agregar
    producto/views.py

# crear carpeta/directorio templates dentro del aplicativo
      producto/templates

# crear htmls para listar, agregar, editar, eliminar
	base.html
	layout.html
	footer.html
	navbar.html
	listar.html
	crear.html
	editar.html
    
# crear forms.py en la aplicacion creada y define los formularios necesarios en 'forms.py'
	producto/forms.py
	form django import forms
	class ProductoForm(forms.ModelForm)
    
# instalar librerias para formularios y bootstrap
	pip install crispy-bootstrap5
	pip install django-bootstrap-v5
	pip install django-crispy-forms
    
# configurar librerias
	config/settigs.py
	INSTALLED_APPS:
	'bootstrap5',  # bootstrap 5
    	'crispy_forms',  # crispy forms 
    	'crispy_bootstrap5'

	CRISPY_ALLOWED_TEMPLATE_PACKS = "bootstrap5"
	CRISPY_TEMPLATE_PACK = 'bootstrap5'

# configurar urls.py en la aplicacion creada y asocialas a las vistas correspondientes
config/urls.py
	from django.urls import path, include
urlpatterns = [
    path('admin/', admin.site.urls),
    path('producto/', include('producto.urls')),
]

# crear urls.py
	producto/urls.py
    
# levantar el proyecto
	python manage.py runserver
    
--------------------------------------------------------------------------------------------------------------------
    
Comandos adicionales
python manage.py sqlmigrate app migration_name: Este comando permite observar el SQL antes de aplicar una determinada migración,
python manage.py makemigrations: Este comando es utilizado para crear archivos de migración en Django. Las migraciones son archivos que contienen cambios en el esquema de la base de datos, como la creación de nuevas tablas o la modificación de las existentes. El comando makemigrations analiza los modelos definidos en tu proyecto y genera los archivos de migración correspondientes que luego podrán ser aplicados a la base de datos.
python manage.py migrate: El comando migrate se encarga de aplicar las migraciones a la base de datos. Ejecuta los archivos de migración pendientes en el orden adecuado para asegurar que la estructura de la base de datos esté sincronizada con los modelos definidos en tu proyecto.
python manage.py shell: Este comando inicia una sesión interactiva de Django shell. Proporciona una interfaz de línea de comandos para interactuar con tu proyecto Django. Puedes ejecutar consultas de base de datos, crear, modificar o eliminar objetos, realizar pruebas, entre otras tareas.
python manage.py dbshell: El comando dbshell inicia una consola interactiva de la base de datos. Te permite acceder directamente a la línea de comandos de tu base de datos, lo que puede ser útil para ejecutar consultas SQL personalizadas o realizar tareas específicas directamente en la base de datos.
python manage.py showmigrations: Este comando muestra el estado de las migraciones en tu proyecto. Indica qué migraciones han sido aplicadas y cuáles están pendientes de aplicación. Puedes utilizarlo para verificar el estado de las migraciones y asegurarte de que todo esté sincronizado correctamente.
python manage.py dumpdata: El comando dumpdata se utiliza para exportar los datos de la base de datos en formato JSON o YAML. Puedes especificar qué modelos o aplicaciones deseas incluir en la exportación. Es útil para realizar copias de seguridad de los datos o para transferirlos entre diferentes entornos.
python manage.py test: Este comando se utiliza para ejecutar las pruebas unitarias en tu proyecto. Ejecuta todas las pruebas definidas en los archivos tests.py de tus aplicaciones y muestra los resultados en la consola.
python manage.py testserver: El comando testserver inicia un servidor de desarrollo con una copia de la base de datos en memoria y cargando datos de prueba. Es útil para ejecutar pruebas que requieren acceso a una base de datos y datos específicos.
python manage.py diffsettings: Este comando muestra las diferencias entre los archivos de configuración de Django (settings.py) y la configuración actual de tu proyecto. Puedes utilizarlo para ver los cambios realizados en la configuración o para solucionar problemas relacionados con la configuración de tu proyecto.