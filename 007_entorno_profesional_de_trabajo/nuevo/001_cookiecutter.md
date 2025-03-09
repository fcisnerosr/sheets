_Instalación de Cookiecutter_ 
`conda install mamba -n base -c conda-forge`    instala mamba globalmente  
`mamba --version`                               verificar la versión de mamba instalada  
`mamba config --add channels conda-forge`       agrega a conda-forge a la lista de canales desde los cuales Conda puede buscar e instalar paquetes  
`mamba create --name cookiecutter-personal cookiecutter=1.7.3`    creación del nuevo env para cookiecutter, siempre especificar la versión para evitar problemas en el futuro  
`mamba env export --from-history --file enviroment.yml` exportar la lista de paquetes instalados en un entorno de mamba a un archivo YML  

_Estructura del archivo cookiecutter_
- COOKIECUTTER-PERSONAL
    - {{ cookiecutter.project_slug }} (directorio)
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
- hoooks (directorio)
    - pre_gen_project.py
        import os
        import sys

        project_slug = "{{ cookiecutter.project_slug }}"
        ERROR_COLOR = "\x1b[31m"
        MESSAGE_COLOR = "\x1b[34m"
        RESET_ALL = "\x1b[0m"

        if project_slug.startswith("x"):
          print(f"{ERROR_COLOR}ERROR: {project_slug=} is not a valid name for this template.{RESET_ALL}")
          sys.exit(1)

        print(f"{MESSAGE_COLOR}Let's do it! You're are going to create something awesome!")
        print(f"Creating project at {os.getcwd()}{RESET_ALL}")
    - post_gen_project.py
        import subprocess

        MESSAGE_COLOR = "\x1b[34m"
        RESET_ALL = "\x1b[0m"

        print(f"{MESSAGE_COLOR}Almost done!")
        print(f"Initializing a git repository...{RESET_ALL}")

        subprocess.call('git', 'init')
        subprocess.call('git', 'add', '*')
        subprocess.call('git', 'commit', '-m', 'Initial commit')

        print(f"{MESSAGE_COLOR}The beginning of your destiny is defined now! Create and have fun!{RESET_ALL}")

        # De los dos métodos para instalar dependencias seleccionar uno nada más
        # Pip
        # subprocess.call(['pip', 'install', '-r', 'requirements.txt'])

        # Conda
        # subprocess.call(['conda', 'env', 'create', '--file', 'environment.yml'])
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
      "project_title": "Cookiecutter Personal", (Valor que ingresa el usuario)
      "project_slug": "{{ cookiecutter.project_title.lower().replace(' ', '_').replace('-', '_') }}", (línea que transforma el nombre ingresado por el usuario para manejarlo en minusculas y reemplazando espacios por _ y los - por _)
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

**Plantilla de Cookiecutter**
mi-plantilla-cookiecutter/              # --> Tu plantilla de Cookiecutter
├── cookiecutter.json                   # --> Variables del proyecto (ej. project_slug, author)
├── hooks/                             # --> Scripts que se ejecutan antes o después
│   ├── pre_gen_project.py              # --> (opcional) Código a ejecutar antes de generar
│   └── post_gen_project.py             # --> Código a ejecutar después (ej. instalar dependencias)
└── {{ cookiecutter.project_slug }}/    # --> Carpeta que será el proyecto generado (personalizado)
    ├── README.md                       # --> Archivo final que verá el usuario
    ├── environment.yml                 # --> Dependencias específicas del proyecto generado
    └── otros_archivos/                 # --> Otros archivos (notebooks, src, data, etc.)

**Resultado del proyecto generado (tree):**
    Proyecto_AI/
    ├── README.md
    ├── data
    ├── enviroment.yml
    └── notebooks
