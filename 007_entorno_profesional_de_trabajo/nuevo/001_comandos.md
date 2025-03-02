_Instalación de Cookiecutter_ 
`conda install mamba -n base -c conda-forge`    instala mamba globalmente
`mamba --version`                               verificar la versión de mamba instalada
`mamba config --add channels conda-forge`       agrega a conda-forge a la lista de canales desde los cuales Conda puede buscar e instalar paquetes
`mamba create --name cookiecutter-personal cookiecutter=1.7.3`    creación del nuevo env para cookiecutter, siempre especificar la versión para evitar problemas en el futuro
`mamba env export --from-history --file enviroment.yml` exportar la lista de paquetes instalados en un entorno de mamba a un archivo YML

_Descargar una plantilla de Github_
Ejemplo:
{{ cookiecutter.project_slug }}
    ├── data
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `1.0-jvelezmagic-initial-data-exploration`.
    │
    ├── .gitignore         <- Files to ignore by `git`.
    │
    ├── environment.yml    <- The requirements file for reproducing the analysis environment.
    │
    └── README.md          <- The top-level README for developers using this project.
Link: https://github.com/platzi/curso-entorno-avanzado-ds/tree/cookiecutter-personal-platzi
`cookiecutter https://github.com/platzi/curso-entorno-avanzado-ds --checkout cookiecutter-personal-platzi`      descarga, instala y ejecuta la plantilla predefinida en el curso. El `--checkout cookiecutter-personal-platzi` es para migrar a otra rama distinta a la main pero esto no es una práctica común
repositorio de github original: https://github.com/jesusdevelope/Plantilla_Personal_Python

_Personaliza tu propia plantilla de cookie cutter_
`mkdir '{{ cookiecutter.project_slug }}`  Crea un directorio cuyo nombre se genera dinámicamente a partir de la variable project_slug de Cookiecutter durante la ejecución de la plantilla
touch README.md environment.yml cookiecutter.json
mkdir notebooks

_Dentro de REAMDE.md_ 
# {{ cookiecutter.project_title }}

By: {{ coockiecutter.project_author_name }} 

{{ cookiecutter.project_description }}

_Dentro de environment.yml_
# Establece el nombre del entorno usando una variable de cookiecutter para personalización
name: {{ cookiecutter.project_slug }}

# Lista de canales desde donde buscar los paquetes
channels:
  - anaconda       # Canal anaconda con paquetes optimizados para ciencia de datos
  - conda-forge    # Canal comunitario con paquetes actualizados
  - defaults       # Canal predeterminado de conda con paquetes estables

# Lista de dependencias que se instalarán en el entorno
dependencies:
  {% if cookiecutter.project_packages == "all" %}
    - fs             # Sistema de archivos abstracto para Python
    - jupyter        # Ejecuta notebooks de Jupyter, útil para análisis interactivo
    - jupyterlab     # Interfaz mejorada para trabajar con notebooks Jupyter
    - pathlib        # Manejo de rutas de archivos en Python (incluido desde Python 3.4+)
  {% endif %}
  - pip             # Gestor de paquetes de Python para instalar desde PyPI
  {% if cookiecutter.project_packages == "all" %}
    - pyprojroot     # Facilita el acceso a la raíz del proyecto
  {% endif %}
  - python={{ cookiecutter.python_version }}  # Instala la versión específica de Python

  - pip:             # Lista de paquetes que se instalarán usando pip
    {% if cookiecutter.project_packages == "all" %}
      - pyhere       # Facilita la referencia de rutas relativas a la raíz del proyecto
    {% endif %}

_Dentro de cookiecutter.json_
{
  "project_title": "Cookiecutter Personal",
  "project_slug": "cookiecutter_personal",
  "project_description": "Something cool",
  "project_author_name": "Your name",
  "project_packages": ["All", "Minimal"],
  "python_version": "3.7",
  "_comment": "Este campo es solo para propósitos descriptivos y no se usa en el código"
}



