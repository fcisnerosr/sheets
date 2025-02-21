# Comandos
esc + z                 deshacer
dd                      borrar bloque de código
shift + r               divide la pantalla entre codigo y datos de salida
esc + shift + enter     ejecutar el bloque actual y agrega un bloque nuevo abajo
esc + ctrl + enter      ejecutar el bloque actual sin agregar ningún bloque por debajo
esc + y                 convierte un bloque a código 
esc + m                 convierte un bloque en código
esc + b                 crear una celda debajo
esc + a                 crear una celda arriba

ctl + b                 desplegar el explorador de archivos
shift + tab             para centrar el foco en el explorador de archivos
backspace               para ir un nivel atrás en el explorador de archivos 
ctrl+shift+{            ir a la pestaña de la terminal
ctrl+tab                pasa a la siguiente pestaña

flecha derecha          oculta bloques
flecha izquierda        muestra bloques

shift + m               fuciona el bloque en el que estás con el de abajo 

ctrl + shift + L        abre el launcher
ctrl + s                guardar el archivo

alt + f                 abre el menu de brave para poner el modo de pantalla completa
f11                     quita la pantalla completa

## Pasos para abrir un entorno específico de conda mediante un kernel para un notebook de jupyter lab
conda env list          para ver los envs creados en conda
conda install -n mi_env ipykernel instala ipykernel para en mi_env para que pueda ser usado como un kernel en juypter lab (este comando se ejecuta una vez por entorno creado)
python -m ipykernel install --user --name=mi_env --display-name "Python (mi_env)" registra el entorno mi_env como kernel en jupyter y así se podrá seleccionar en jupyter lab

## nbdime
nbdiff notebook_original.ipynb notebook_modificado.ipynb        compara los dos Jupyter Notebooks especificados y muestra las diferencias como texto plano en la terminal,
nbdiff-web notebook_original.ipynb notebook_modificado.ipynb    compara visualmente las diferencias entre los dos Jupyter Notebooks especificados abriendo una interfaz interactiva en un navegador web.

## Comandos mágicos
%ls                     ejecuta un comando de la terminal en jupyter
%%bash                  ejecuta multiples líneas como un script de terminal dentro de una celda de código.
ls
echo "Hola"
mkdir "carpeta_nueva"

# Visual Studio Code
conda activate my_env   activar el env
code .                  abrir code desde la terminal de WSL
ctrl + shift + X        abrir el buscador de extensiones
ctrl + shift + E        abrir el explorador de archivos
ctrl + B                abrir y cerrar el explorador de archivos
ctrl + N                crear un nuevo archivo
Ctrl + M, M             convierte una celda de códido a Markdown
Ctrl + M, Y             convierte una celda a código
Ctrl + J                abrir y cerrar la terminal

### Debugging Controls in VS Code
1. Click to add breakpoint
2. Ctrl + Shift + Alt + Enter   Debug Cell

| Action         | Description |
|----------------|-------------|
| **Continue**   | Resumes code execution until the next breakpoint or the end of the program. |
| **Step Back**  | Moves execution back to the previous line (if enabled). |
| **Step Over**  | Executes the next line of code without stepping into functions. |
| **Step Into**  | Steps into a function if the current line is a function call. |
| **Step Out**   | Runs the remaining lines in the current function and returns to the calling line. |
| **Disconnect** | Ends the debugging session. |

**Tip:** Use these tools to step through your code and inspect variable values in real time.

## Canales en conda
- Default
- Conda forge, 
_paquetes: (https://conda-forge.org/packages/)_
conda install conda-forge::pandas       Installs the pandas package from the conda-forge channel instead of the default conda channels. Fuente: https://anaconda.org/conda-forge/pandas
conda config --show channels            It displays the currently configured Conda channels in order of priority. Conda channels are repositories where Conda searches for packages when installing or updating software.
conda config --set channel_priority strict  It sets Conda's channel priority to "strict", meaning Conda will only install packages from the highest-priority channel and will not fall back to lower-priority channels. 
conda install numpy pandas matplotlib -c conda-forge    It installs the numpy, pandas, and matplotlib packages using the conda-forge channel.

## Cookie cutter
https://github.com/drivendataorg/cookiecutter-data-science      The page cookiecutter-data-science is a Cookiecutter template for structuring data science projects.
Pasos básicos:
1. Instalar cookie cutter
2. Clonar el repositorio
3. personalizar en nuestro entorno de trabajo
_Instalación_
`conda install conda-forge::cookiecutter`     instalar cookiecutter con conda mediante el canal forge

_Ejecución de plantillas creadas en Github_
`cookiecutter https://github.com/drivendataorg/cookiecutter-data-science -c v1` Creará un nuevo proyecto basado en la plantilla de ciencia de datos definida en cookiecutter-data-science, solicitando al usuario información como el nombre del proyecto, el autor, la licencia y otros detalles de configuración

_Personalización de plantillas en cookiecutter_
1. Crear directorio COOKIE-CUTTER
    1. cookiecutter.json (archivo para...)
        {
            "project_name": "My Project",
            "author_name": "Paco Cisneros",
            "python_version": "3.8",
            "license": ["MIT", "GPL", "Apache"]
        }
    2. {{cookiecutter.project_name}} (directorio con toda la plantilla con la estructura personalizada)
        1. data (directorio personal)
        2. src (directorio personal)
        3. notebook (directorio personal)
        4. test (directorio personal)
        5. enviroments.yml
            name: {cookiecutter.project_name}
            channels:
              - conda-forge
              - defaults
            dependencies:
              - python=3.8
              - numpy
              - pandas
        6. requirements.txt
        7. README.md
            -  # {{cookiecutter.project_name}}
                Proyecto de Machine Learning creado por {cookiecutter.author_name}

                ## Descripción

                Este proyecto contiene el flujo completo para entrenar y evaluar un modelo de machine learning. Está organizado en las siguientes secciones:

                - **data/**: Contiene los datos sin procesar y los datos procesados.
                - **notebooks/**: Jupyter Notebooks para análisis exploratorio y modelado.
                - **src/**: Código fuente que contiene scripts para procesamiento de datos y modelos.
                - **tests/**: Pruebas unitarias para asegurar la calidad del código.
                
                ## Requisitos

                - Python {{cookiecutter.python_version}}
                - Dependencias: Ver `environment.yml` o `requirements.txt` para instalar todas las bibliotecas necesarias.

                ## Instalación

                Para configurar el entorno, ejecuta el siguiente comando:

                ```bash
                conda env create -f environment.yml
        8. LICENSE
            {% if cookiecutter.license == "MIT" %}
            MIT License
            copyright {cookiecutter.author_name}
            Información de la licencia correspondiente

            {% elif cookiecutter.license == "GPL" %}
            Información de la licencia correspondiente

            {% elif cookiecutter.license == "Apache" %}
            Información de la licencia correspondiente

            {% endif %}

2. Ejecución:
    1. En nuestro proyecyo ejemplo: "my_ml_template" movemos el directorio {{cookiecutter.project_name}} y el archivo cookiecutter.json
    2. En la terminal se ejecuta: coockiecutter my_ml_template
        [1/4] project_name (My Project): new_project
        [2/4] author_name (Paco Cisneros): 
        [3/4] python_version (3.8): 3.12
        [4/4] Select license
          1 - MIT
          2 - GPL
          3 - Apache
        Choose from [1/2/3] (1): 1


