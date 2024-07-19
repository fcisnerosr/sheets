# Comandos Conda en Anaconda

## Instalación de Conda
wget -O anaconda.sh https://repo.anaconda.com/archive/Anaconda3-2024.06-1-Linux-x86_64.sh
NOTA: -O es una "O" mayúscula.
Fuente: https://www.anaconda.com/download/success

## En caso de no poder iniciar conda init:

code ~/.bashrc
Agregar al final del archivo:
export PATH="$HOME/anaconda3/bin:$PATH"
source ~/.bashrc
conda init

## Verificación de Instalación
conda --version		Para asegurarte de que Conda se ha instalado y configurado correctamente

# Gestión de Entornos
## Listar Entornos
conda env list 		Lista todos los entornos virtuales creados y gestionados por conda en el sistema
			NOTA: env = ambiente virtual
Ejemplo:
	base                     /home/fcisnerosr/anaconda3
	py35                  *  /home/fcisnerosr/anaconda3/envs/py35
		(El asterisco indica que es el ambiente activo en ese momento)

## Listar Paquetes Python
conda list python				Devuelve la versión de Python en el ambiente activo
## Actualizar Python
conda update python				Actualiza la versión de Python a la más reciente disponible

## Instalar una Versión Específica de Python
conda install python=2.7			Instala una versión específica de Python en el ambiente activo

## Instalar Dependencias con Versiones Específicas
conda install pandas=1.2 pandas=3.9		Instala dos dependencias con versiones específicas requeridas

# Listar Dependencias
conda list					Lista todas las dependencias del ambiente activo

# Listar Versión Específica de un Paquete
conda list pandas				Devuelve la versión de pandas en el ambiente activo

## Instalación de Programas Específicos
# Crear un Nuevo Entorno
conda create --name py python			Crea un nuevo entorno con el nombre "py" y la última versión de Python

# Crear un Nuevo Entorno con una Versión Específica de Python
conda create --name py35 python=3.5		Crea un nuevo entorno con el nombre "py35" y Python 3.5

# Activar un Entorno
conda activate py35				Activa el ambiente "py35"

# Clonar un Entorno
conda create --name py39 --copy --clone py35	Crea un nuevo entorno con el nombre "py39" y copia todas las dependencias del entorno "py35" a "py39"

## Env creados pero en VS Code y con Jupiter Notebooks
## Pasos para abrir un Jupyter Notebook en VS Code con un entorno virtual

1. Abre un Jupyter Notebook en VS Code.
2. En la parte superior, selecciona el kernel donde indica "Seleccionar Kernel".
3. Selecciona entornos de Python.
4. Se buscarán todos los entornos virtuales disponibles.
5. Elige el entorno virtual de tu preferencia (por ejemplo, base, py35, py39 o cualquier otro que hayas creado).
6. Para más información, revisa: [Platzi - Conda: Abrir VSCode Notebooks con tu ambiente](https://platzi.com/home/clases/2434-jupyter-notebook/40396-conda-abrir-vscode-notebooks-con-tu-ambiente/)


