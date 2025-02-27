# Comandos Conda en Anaconda
### Instalación de Conda (solo se hace una vez)
wget -O anaconda.sh https://repo.anaconda.com/archive/Anaconda3-2024.06-1-Linux-x86_64.sh _NOTA: -O es una "O" de oso en mayúscula._ _Fuente: https://www.anaconda.com/download/success_
conda info      despliega toda la información de la configuración de conda
_En caso de no poder iniciar conda init_
    vim ~/.bashrc
    Agregar al final del archivo:
    export PATH="$HOME/anaconda3/bin:$PATH"
    ejecutar:
    source ~/.bashrc
    conda init

**Comandos con un + solo son ejecutables deberán tener el env activado**
Comandos básicos_ 
+`conda --version`		Para asegurarte de que Conda se ha instalado y configurado correctamente
+`jupyter notebook`       Inicia un servidor web en tu computadora para visualizar mis jupiter notebooks en la web
`ctrl + c` para cancelar el servidor

### Gestión de Entornos y paquetes de ambientes virtuales, crearlos, actualizarlos y eliminarlos    
_Creación de ambientes virtuales_
`conda env list` 		                    Lista todos los entornos virtuales creados y gestionados por conda en el sistema
`conda create --name py python`			    Crea un nuevo entorno con el nombre "py" y la última versión de Python
`conda create --name py35 python=3.5`		Crea un nuevo entorno con el nombre "py35" y Python 3.5
`conda activate py35`                       Activa el ambiente creado
_Listas e instalación de paquetes y dependencias_
+`conda list python`				        Devuelve la versión de Python en el ambiente activo
+`conda list`				                Lista todas las dependencias del ambiente activo
+`conda list -n otro_env`                   Lista de paquetes o dependencias de otro env estando activo en otro env
+`conda install python=2.7`			        Actualiza una versión específica de Python en el ambiente activo. Puede haber conflictos debido a que haya dependencias como pandas 1.2 que necesite una versión de Python mayor o igual a la 3.7, en ese caso aplicar el siguiente comando
+`conda install pandas=1.2 python=3.9`		Actualiza dos dependencias con versiones específicas requeridas
`conda create --name py39 --copy --clone py35`	Crea un nuevo entorno con el nombre "py39" a partir de un entorno existente. No necesario tener un env activo, con que el env del que se está haciendo la copia exista es más que suficiente
+`conda install pandas=1.2 python=3.9`		Actualiza dos dependencias con versiones específicas requeridas
_Actualización de dependencias_
+`conda update python`				        Actualiza la versión de Python a la más reciente disponible, en `update` no puedo especificar qué versión se necesita
+`conda update -all`				        Actualiza todas las dependencias en nuestro entorno
_Limpieza y desintalación_
+`conda remove pandas`                      Elimina pandas del ambiente activo
`conda remove remove --name py35`           Elimina el env que no tengas activo
`conda remove --name proyecto1 numpy `      Elimina del paquete 'numpy' del entorno 'proyecto1'
`conda remove --name protecto1 --all `      Elimina todas las dependencias del entorno 'proyecto1'
`conda clean --packages `                   Elimina la caché descargada por paqueterías
`conda clean --all`                         Elimina toda la caché posible.
_Clonar entornos virtuales_
`conda create --name nuevo_env --clone env_a_clonar` Clona un nuevo env a partir de otro env

### Estado del env. Conda actuando como git, revisiones y el archivo enviroment.yml
_Revisiones_
+`conda list --revision`            Muestra el historial de todas las revisiones y cambios que se han realizado en el entorno activo de conda
+`conda install --revision 0`       Te permite revertir el env a un estado anterior
+`conda env export --from-history --file enviroment.yml`  Exportación de *enviroment.yml* de la configuración del entorno activado
+`conda env export > enviroment.yml`  Comando alternativo para la exportación de *enviroment.yml* de la configuración del entorno activado
_Compartir mis revisiones a terceros. Otro usuario no tiene el env instalado_
Usuario que exporta el env y los instala mediante *enviroment.yml*:
`conda env create -f enviroment.yml` Crea un nuevo entorno Conda a partir de las configuraciones del *enviroment.yml*
_Actualizar dependencias de Conda con .yml en un env existente_
Pasos:
`conda create -n mi_entorno`         crear el entorno nuevo
`conda activate mi_entorno`          activar en entorno nuevo
`conda env update -f enviroment.yml` Actualiza las dependencias de acuerdo al .yml
`conda list`                         para verificar las versiones actualizadas de acuerdo al .yml


### Instalación de paquetes que no están en el canal principal de Conda. Búsqueda de Paquetes en anaconda.org
1. *Visitar el Sitio*: Abre tu navegador y ve a [anaconda.org](https://anaconda.org).
2. *Usar la Barra de Búsqueda*: Escribe el nombre del paquete que estás buscando en la barra de búsqueda en la página principal.
3. *Filtrar Resultados*: Filtra los resultados por canal, tipo de archivo, versión, etc., para encontrar el paquete exacto que necesitas.
4. *Ver Detalles del Paquete*: Haz clic en el paquete de interés para ver su descripción, versiones disponibles, dependencias y comandos de instalación.
5. *Instalar el Paquete*: Copia el comando de instalación proporcionado en la página de detalles del paquete y ejecútalo en tu terminal para instalarlo.
`conda install -c conda-forge keras`        Instala keras en caso de que conda no cuente con dicha librería. _En este caso 'conda-forge' es el canal que se encontró en 'anaconda.org'_
`conda install -c conda-forge keras=2.4.3`  Instala una versión en específico de keras mediante un canal secundario de Conda       
+`conda list keras`				            Verificación de la versión de keras instalado

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

