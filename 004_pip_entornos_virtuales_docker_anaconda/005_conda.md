# Comandos Conda en Anaconda
### Instalación de Conda
wget -O anaconda.sh https://repo.anaconda.com/archive/Anaconda3-2024.06-1-Linux-x86_64.sh _NOTA: -O es una "O" mayúscula._ _Fuente: https://www.anaconda.com/download/success_
conda info      descriega toda la información de la configuración de conda
_En caso de no poder iniciar conda init_
    vim ~/.bashrc
    Agregar al final del archivo:
    export PATH="$HOME/anaconda3/bin:$PATH"
    ejecutar:
    source ~/.bashrc
    conda init

**Comandos con un + solo son ejecutables deberán tener el env activado**
_Comandos básicos_ 
+`conda --version`		Para asegurarte de que Conda se ha instalado y configurado correctamente
+`jupyter notebook`       Inicia un servidor web en tu computadora para visualizar mis jupiter notebooks en la web
`ctrl + c` para cancelar el servidor

### Gestión de Entornos y paquetes de ambientes virtuales, crearlos, actualizarlos y eliminarlos    
`conda env list` 		                    Lista todos los entornos virtuales creados y gestionados por conda en el sistema
`conda create --name py python`			    Crea un nuevo entorno con el nombre "py" y la última versión de Python
`conda create --name py35 python=3.5`		Crea un nuevo entorno con el nombre "py35" y Python 3.5
`conda activate py35`                       Activa el ambiente creado
+`conda list python`				        Devuelve la versión de Python en el ambiente activo
+`conda list`				                Lista todas las dependencias del ambiente activo
+`conda update python`				        Actualiza la versión de Python a la más reciente disponible, en `update` no puedo especificar qué versión se necesita
+`conda install python=2.7`			        Actualiza una versión específica de Python en el ambiente activo. _Puede haber conflictos debido a que haya dependencias como pandas 1.2 que necesite una versión de Python mayor o igual a la 3.7, en ese caso aplicar el siguiente comando_
+`conda install pandas=1.2 python=3.9`		Actualiza dos dependencias con versiones específicas requeridas
`conda create --name py39 --copy --clone py35`	Crea un nuevo entorno con el nombre "py39" a partir de un entorno existente. _No necesario tener un env activo, con que el env del que se está haciendo la copia exista es más que suficiente_
+`conda install pandas=1.2 python=3.9`		Actualiza dos dependencias con versiones específicas requeridasj
+`conda remove pandas`                      Elimina pandas del ambiente activo
`conda remove remove --name py35`           Elimina el env que no tengas activo
`conda remove --name proyecto1 numpy `      Elimina del paquete 'numpy' del entorno 'proyecto1'

### Búsqueda de Paquetes en anaconda.org
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
`conda install -c conda-forge keras`        Instala keras en caso de que conda no cuente con dicha librería. _En este caso 'conda-forge' es el canal que se encontró en 'anaconda.org'_

## Estado del env, conda actuando como git, revisiones y el archivo enviroment.yml
_Revisiones_
`conda list --revision`       Revisiones informantes de qué y cuándo fue instalado
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

### Mamba
conda install --channel conda-forge mamba   instalación de mamba

_Env creados pero en VS Code y con Jupiter Notebooks_
_Pasos para abrir un Jupyter Notebook en VS Code con un entorno virtual_
1. Abre un Jupyter Notebook en VS Code.
2. En la parte superior, selecciona el kernel donde indica "Seleccionar Kernel".
3. Selecciona entornos de Python.
4. Se buscarán todos los entornos virtuales disponibles.
5. Elige el entorno virtual de tu preferencia (por ejemplo, base, py35, py39 o cualquier otro que hayas creado).
6. Para más información, revisa: [Platzi - Conda: Abrir VSCode Notebooks con tu ambiente](https://platzi.com/home/clases/2434-jupyter-notebook/40396-conda-abrir-vscode-notebooks-con-tu-ambiente/)


