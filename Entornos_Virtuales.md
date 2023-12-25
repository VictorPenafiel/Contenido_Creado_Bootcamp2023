*Instalacionde virtualenv y virtualenvwrapper
pip install virtualenvwrapper
pip install virtualenv

*crear un entorno virtual
	virtualenv nombre_entorno
	virtualenv django_env

## Activando el entorno virtual

--powershell
.\django_env\Scripts\activate.ps1

--cmd
django_env\Scripts\activate.ps1

--Unix
source entorno/Scripts/activate
django_env/bin/activate


## Desactivar entorno virtual
deactivate

-----------------------------------------------------------------------------------------------------------------

si aparece el siguiente error, ejecutar los siguientes pasos

.\django_env\Scripts\activate.ps1 : File H:\Other computers\My computer\Edutecno Capacitacion\BOOTCAMP 0030 - FULL STACK PYTHON - VESPERTINO - 
workspace\M6-Django\2-S2\rebound\django_env\Scripts\activate.ps1 cannot be loaded because running scripts is disabled on this system. For more information, see about_Execution_Policies at 
https:/go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\django_env\Scripts\activate.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

--obtener poliza de seguridad
Get-ExecutionPolicy

--desactivar la poliza de seguridad
Set-ExecutionPolicy RemoteSigned
-----------------------------------------------------------------------------------------------------------------


Comandos
deactivate — Salir del entorno virutal Python actual
workon — Listar los entornos virtuales disponibles
workon name_of_environment — Activar el entorno virtual Python especificado
rmvirtualenv name_of_environment — Borrar el entorno especificado.

-----------------------------------------------------------------------------------------------------------------

Crear entorno virtual 
  mkvirtualenv "nombre del entorno"
Cerrar entorno
  deactivate
Ver entornos virtuales disponibles
  Workon
Activar entorno 
  workon "nombre del entorno"
Elimar entorno
  rmvirtualenv "nombre del entorno"
  
  
 -----------------------------------------------------------------------------------------------------------------
 Creación de ambiente virtual embebido en Python- Linux:

1) pip install virtualenv

2) Creación del ambiente. Ubicarse en la carpeta de preferencia y ejecutar el siguiente comando:
	python3 -m venv Nombre_Ambiente
	
	Ejemplo: python3 -m venv onlyflans

3) Para activar dicho ambiente, ubicarse en la carpeta donde se ubicó en el paso 2 y ejecutar:
	source Nombre_Ambiente/bin/activate

4) Para verificar que está activo, deberá notar el nombre del ambiente que activó
	como prefijo del prompt de la cónsola.
	
5) Para desactivar ambiente, ejecute:
	deactivate
	
*Configurar variables de entorno(Unix/Linux) 

pip install virtualenvwrapper

export WORKON_HOME=$HOME/.virtualenvs
export PROJECT_HOME=$HOME/Devel
source /usr/local/bin/virtualenvwrapper.sh
source ~/.bashrc

Instalar virtualenvwrapper
	pip3 install virtualenvwrapper
	export WORKON_HOME=$HOME/.virtualenvs
	export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
	export PROJECT_HOME=$HOME/Devel
	source /usr/local/bin/virtualenvwrapper.sh
	source ~/.bashrc

 -----------------------------------------------------------------------------------------------------------------

*Gestión de dependencias
● pip install -r requirements.txt -> para instalar las dependencias desde un archivo
● pip freeze > requirements.txt -> para generar un respaldo de los paquetes instalados creando un
archivo requirements.txt
● pip install astral==2.2 -> para instalar una versión específica de un paquete que necesitemos, en
este ejemplo astral 2.2
