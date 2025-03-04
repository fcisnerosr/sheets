_Instalación de Cookiecutter_ 
`conda install mamba -n base -c conda-forge`    instala mamba globalmente
`mamba --version`                               verificar la versión de mamba instalada
`mamba config --add channels conda-forge`       agrega a conda-forge a la lista de canales desde los cuales Conda puede buscar e instalar paquetes
`mamba create --name cookiecutter-personal cookiecutter=1.7.3`    creación del nuevo env para cookiecutter, siempre especificar la versión para evitar problemas en el futuro
`mamba env export --from-history --file enviroment.yml` exportar la lista de paquetes instalados en un entorno de mamba a un archivo YML

_s_

{{ cookiecutter.project_slug }} Crear archivos de configuración
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



