_Instalación de Cookiecutter_ 
`conda install mamba -n base -c conda-forge`    instala mamba globalmente  
`mamba --version`                               verificar la versión de mamba instalada  
`mamba config --add channels conda-forge`       agrega a conda-forge a la lista de canales desde los cuales Conda puede buscar e instalar paquetes  
`mamba create --name cookiecutter-personal cookiecutter=1.7.3`    creación del nuevo env para cookiecutter, siempre especificar la versión para evitar problemas en el futuro  
`mamba env export --from-history --file enviroment.yml` exportar la lista de paquetes instalados en un entorno de mamba a un archivo YML  

_Estructura del archivo cookiecutter_
- COOKIECUTTER-PERSONAL
    - {{ cookiecutter.project_slug }}
        - data
        - notebooks
        - README.md ( plantilla que Cookiecutter usa para generar el README de cada proyecto, reemplazando variables asignadas en cookiecutter.json)
             # {{ cookiecutter.project_title }}

            By: {{ cookiecutter.project_author_name }}

            {{ cookiecutter.project_description }}

            ## License
        - enviroment.yml (define las librerías necesarias para cada proyecto generado)
            name: {{ cookiecutter.project_slug }}

            channels:
              - anaconda
              - conda-forge
              - defaults

            dependencies:
            {% if cookiecutter.project_packages == "all" -%}
              - fs
              - jupyter
              - jupyterlab
              - pathlib
            {% endif -%}
              - pip
            {% if cookiecutter.project_packages == "all" -%}
              - pyproj
              - root
            {% endif %}
              - python={{ cookiecutter.python_version }}
              - pip:
                {% if cookiecutter.project_packages == "all" -%}
                  - pyhere
                {% endif %}
                - enviroment.yml
- environment.yml (archivo destinado a configurar el entorno donde ejecutarás Cookiecutter para generar nuevos proyectos)
    name: cookiecutter-personal
    channels:
      - conda-forge
      - defaults
    dependencies:
      - cookiecutter=1.7.3
    prefix: /home/fcisnerosr/miniforge3/envs/cookiecutter-personal
- cookiecutter.json (Define las variables y valores predeterminados para personalizar cada proyecto mediante {{cookiecutter.project_slug}})
    {
      "project_title": "Cookiecutter Personal",
      "project_slug": "cookiecutter_personal",
      "project_description": "Something cool",
      "project_author_name": "Your name",
      "project_packages": ["All", "Minimal"],
      "python_version": "3.7"
    }

_Pasos para activar la plantilla personalizada de cookicutter_
Ejemplo proyecto: Proyecto_AI en directorio Proyecto_AI
**NOTA: en el directorio Proyecto_AI debe ir {{ coockiecutter.project_slug }}, cookiecutter.json y environment.yml**
cookiecutter .          ejecuta cookiecutter en este directorio
se irá llenando a mano cada campo solicitado: 
project_title [Cookiecutter Personal]: Proyecto_AI
project_slug [cookiecutter_personal]: testing
project_description [Something cool]: proyecto de IA
project_author_name [Your name]: Paco Cisneros
Select project_packages:
1 - All
2 - Minimal
Choose from 1, 2 [1]: 1
python_version [3.7]: 

Resultado (tree):
    testing/
    ├── README.md
    ├── data
    ├── enviroment.yml
    └── notebooks


