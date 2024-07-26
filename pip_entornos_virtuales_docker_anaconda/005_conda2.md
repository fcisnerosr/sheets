# Comandos Conda en Anaconda

### Instalación de Conda
wget -O anaconda.sh https://repo.anaconda.com/archive/Anaconda3-2024.06-1-Linux-x86_64.sh
_NOTA: -O es una "O" mayúscula._
_Fuente: https://www.anaconda.com/download/success_

_En caso de no poder iniciar conda init_
vim ~/.bashrc
Agregar al final del archivo:
export PATH="$HOME/anaconda3/bin:$PATH"
ejecutar:
source ~/.bashrc
conda init

_Verificación de Instalación_
conda --version		Para asegurarte de que Conda se ha instalado y configurado correctamente

### Instalación de nuevos entornos, librerías específicos y clonar entornos virtuales
_Crear un Nuevo Entorno_
conda create --name py python			        Crea un nuevo entorno con el nombre "py" 
                                                y la última versión de Python
_Crear un Nuevo Entorno con una Versión Específica de Python_
conda create --name py35 python=3.5		        Crea un nuevo entorno con el nombre "py35" y Python 3.5
conda create --name py39 python=3.9 pandas=1.2  Crea un nuevo entorno con el nombre "py"
                                                e instala Python 3.5 y pandas1.2
_Activar un Entorno_
conda activate py35                             Activa el ambiente "py35
_Clonar un entorno_
conda create --name py39 --copy --clone py35	Crea un nuevo entorno con el nombre "py39" 
                                                y copia todas las dependencias del entorno "py35" a "py39"
### Gestión de Entornos y paquetes de ambientes virtuales
_Listar Entornos_
conda env list 		Lista todos los entornos virtuales creados y gestionados por conda en el sistema
Ejemplo:
	base                     /home/fcisnerosr/anaconda3
	py35                  *  /home/fcisnerosr/anaconda3/envs/py35
		_(El asterisco indica que es el ambiente activo en ese momento)_

_Listar Paquetes Python_
conda list python				Devuelve la versión de Python en el ambiente activo
_Actualizar Python_
conda update python				Actualiza la versión de Python a la más reciente disponible
_Instalar una versión específica de Python_
conda install python=2.7		Instala una versión específica de Python en el ambiente activo
_Instalar Dependencias con Versiones Específicas_
conda install pandas=1.2 pandas=3.9		Instala dos dependencias con versiones específicas requeridas
_Listar Dependencias_
conda list					    Lista todas las dependencias del ambiente activo
_Listar Versión Espcífica de un Paquete_
conda list pandas				Devuelve la versión de pandas en el ambiente activo

## Env creados pero en VS Code y con Jupiter Notebooks
## Pasos para abrir un Jupyter Notebook en VS Code con un entorno virtual
1. Abre un Jupyter Notebook en VS Code.
2. En la parte superior, selecciona el kernel donde indica "Seleccionar Kernel".
3. Selecciona entornos de Python.
4. Se buscarán todos los entornos virtuales disponibles.
5. Elige el entorno virtual de tu preferencia (por ejemplo, base, py35, py39 o cualquier otro que hayas creado).
6. Para más información, revisa: [Platzi - Conda: Abrir VSCode Notebooks con tu ambiente](https://platzi.com/home/clases/2434-jupyter-notebook/40396-conda-abrir-vscode-notebooks-con-tu-ambiente/)


