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

### Gestión de Entornos y paquetes de ambientes virtuales
_Listar Entornos_
_env = ambiente virtual_
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
conda install python=2.7			Instala una versión específica de Python en el ambiente activo
_Instalar Dependencias con Versiones Específicas_
conda install pandas=1.2 pandas=3.9		Instala dos dependencias con versiones específicas requeridas
_Listar Dependencias_
conda list					Lista todas las dependencias del ambiente activo
_Listar Versión Espcífica de un Paquete_
conda list pandas				Devuelve la versión de pandas en el ambiente activo

### Instalación de Programas Específicos
_Crear un Nuevo Entorno_
conda create --name py python			Crea un nuevo entorno con el nombre "py" y la última versión de Python
_Crear un Nuevo Entorno con una Versión Específica de Python_
conda create --name py35 python=3.5		Crea un nuevo entorno con el nombre "py35" y Python 3.5
_Activar un Entorno_
conda activate py35				Activa el ambiente "py35

### Clonar un Entorno
conda create --name py39 --copy --clone py35	Crea un nuevo entorno con el nombre "py39" y copia todas las dependencias del entorno "py35" a "py39"

### Borrar Dependencias de un Entorno
Para borrar una dependencia específica de un entorno virtual, usa el comando `conda remove`. Aquí tienes el formato general:
```sh
conda remove --name <nombre_del_entorno> <paquete
```
### Ejemplo:
`conda remove --name proyecto1 numpy `    Para eliminar del paquete 'numpy' del entorno 'proyecto1'
conda env remove --name proyecto1      Elimina el env llamado 'proyecto1'

_Búsqueda de Paquetes en anaconda.org_
1. **Visitar el Sitio**
   - Abre tu navegador y ve a [anaconda.org](https://anaconda.org).
2. **Usar la Barra de Búsqueda**
   - Escribe el nombre del paquete que estás buscando en la barra de búsqueda en la página principal.
3. **Filtrar Resultados**
   - Filtra los resultados por canal, tipo de archivo, versión, etc., para encontrar el paquete exacto que necesitas.
4. **Ver Detalles del Paquete**
   - Haz clic en el paquete de interés para ver su descripción, versiones disponibles, dependencias y comandos de instalación.
5. **Instalar el Paquete**
   - Copia el comando de instalación proporcionado en la página de detalles del paquete y ejecútalo en tu terminal para instalarlo. Ejemplo:
     ```ejemplo:
     Opcion1: conda install --channel conda-forge keras
     Opcion2: conda install -c conda-forge keras
     donde: 
        channel: es el canal que aparece como primera opción en la lista de las dependencias en anadonda.org
        en este caso es "conda-forge"
     ```
## Estado del env, conda actuando como git
_Revisiones_
conda list --revision       revisiones informantes de qué y cuándo lo instalaste
conda install --revision 0  te lleva a la revisión con las dependencias que tenías instaladas en ese momento 
_Compartir mis revisiones a terceros_
~NOTA: Ver al final de documento la diferencia entre paquete y dependencia~
op1. conda env export                paquetes con número de versión del paquetes y depedencias incluidas 
op2. conda env export --no-builds    paquetes y dependencias nada más sin número de versión  
op.3 **la más usada**: conda env export --from-history dependencias que instaló explícitamente en entorno manualmente
**Exportación e instalación**
Usuario que exporta el env:
conda env export --from-history --file enviroment.yml
Usuario que importa el env mediante el .yml:
conda env create --file enviroment.yml

_Env creados pero en VS Code y con Jupiter Notebooks_
_Pasos para abrir un Jupyter Notebook en VS Code con un entorno virtual_
1. Abre un Jupyter Notebook en VS Code.
2. En la parte superior, selecciona el kernel donde indica "Seleccionar Kernel".
3. Selecciona entornos de Python.
4. Se buscarán todos los entornos virtuales disponibles.
5. Elige el entorno virtual de tu preferencia (por ejemplo, base, py35, py39 o cualquier otro que hayas creado).
6. Para más información, revisa: [Platzi - Conda: Abrir VSCode Notebooks con tu ambiente](https://platzi.com/home/clases/2434-jupyter-notebook/40396-conda-abrir-vscode-notebooks-con-tu-ambiente/)


**Diferencias entre paquete y dependencias**
* Paquetes explícitamente instalados: Son los paquetes que tú decides instalar directamente. Por ejemplo, si ejecutas conda install pandas, pandas es el paquete explícitamente instalado.
* Dependencias: Son los paquetes que se instalan automáticamente porque son necesarios para que los paquetes explícitamente instalados funcionen correctamente. Siguiendo el ejemplo anterior, numpy se instala automáticamente porque pandas lo necesita para funcionar.
