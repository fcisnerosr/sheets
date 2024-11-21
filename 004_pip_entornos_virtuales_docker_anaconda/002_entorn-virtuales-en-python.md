# Pip (pip install packages)

## Entorno global
`pip install matplotlib`    Instalar librerias en python en entorno global. En _www.pypi.org_ se encuentran librerias y su versión correspondiente
`pip3 --version`    Verificar qué instalador de paquetes tenemos
`pip3 freez`    Lista de librerias (dependencias) globalmente en equipo
`which python3`  Devuelve la ubicación donde se encuentra el binario 
`which pip3`  Devuelve la ruta completa donde se ejecuta el gestor de paquetes de python
`pip3 install matploblib==3.5.0`  Instala la versión específica de una librería, en caso de que ya exista una version instalada distinta instala la especificada

## Entorno virtual
`sudo apt install -y python3-venv`  Paquete que instala las herramientas necesarias para crear entornos virtuales
`python3 -m venv env`  Crea un entorno virtual _venv_ llamado "env" en el directorio actual
`pip install --upgrade pip setuptools wheel` En caso de tener problemas, actualizar el gestor de paquetes de entornos virtuales 
`source env/bin/activate`  Activa el venv env
`deactivate`  Desactiva el venv
+`which python3`  Devuelve la versión de python que se tiene instalada en el venv
+`pip3 freeze`  Devuelve todas las librerías que están instaladas en en venv
	
Instalar automáticamente las dependencias de un proyecto
	Debe estar creado requirements.txt, que contendrá todas librerías en particular que necesita mi proyecto
	Si el proyecto es nuestro, nosotros debemos crearlo:
		pip3 freeze > requirements.txt
	NOTA IMPORTANTE: Siempre que se actualice una librería o se agrege una nueva, es necesario ejecutar "pip3 freeze > requirements.txt" para que el .txt esté siempre actualizado
	
	Si el proyecto no es nuestro, el dueño habrá tenido que crear requirements.txt, solo debo instalarlo mediante:
		pip3 install -r requirements.txt
		
Docker
	docker-compose build: usado para contruir el contenedor con las instrucciones "docker-compose.yml"
	
FastAPI
	para instalarlo:
		pip3 install fastapi
		pip3 install "uvicorn[standard]"


