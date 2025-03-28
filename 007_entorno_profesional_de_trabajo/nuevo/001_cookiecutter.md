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
        import sys
        import re

        # Obtener las variables definidas en cookiecutter.json
        project_slug = '{{ cookiecutter.project_slug }}'
        author_name = '{{ cookiecutter.project_author_name }}'

        # Validar que el nombre del proyecto no tenga espacios ni caracteres raros
        if not re.match(r'^[a-zA-Z0-9_-]+$', project_slug):
            print(f"ERROR: El nombre del proyecto '{project_slug}' contiene caracteres no permitidos.")
            print("Usa solo letras, números, guiones y guiones bajos (a-z, A-Z, 0-9, -, _).")
            sys.exit(1)  # Termina la ejecución si no pasa la validación

        # Validar que el nombre del autor no esté vacío
        if not author_name.strip():
            print("ERROR: El nombre del autor no puede estar vacío.")
            sys.exit(1)

        print("✔ Validaciones completadas con éxito.")
        
    - post_gen_project.py
        import os
        import subprocess
        import sys

        # Colores para mensajes bonitos
        MESSAGE_COLOR = "\x1b[34m"
        RESET_ALL = "\x1b[0m"

        # Mensaje de inicio
        print(f"{MESSAGE_COLOR}Proyecto creado exitosamente. Ejecutando pasos posteriores...{RESET_ALL}")

        # -------------------------------------------------
        # 1. Inicializar repositorio Git
        # -------------------------------------------------
        print(f"{MESSAGE_COLOR}Inicializando repositorio Git...{RESET_ALL}")
        subprocess.call(['git', 'init'])
        subprocess.call(['git', 'add', '.'])
        subprocess.call(['git', 'commit', '-m', 'Initial commit'])

        # -------------------------------------------------
        # 2. Crear carpetas necesarias (si no existen)
        # -------------------------------------------------
        print(f"{MESSAGE_COLOR}Creando carpetas necesarias...{RESET_ALL}")
        folders = ['data/raw', 'data/processed', 'notebooks', 'src', 'reports']
        for folder in folders:
            os.makedirs(folder, exist_ok=True)
            print(f"{MESSAGE_COLOR}Carpeta creada: {folder}{RESET_ALL}")

        # -------------------------------------------------
        # 3. Instalar dependencias (opcional: pip o conda)
        # -------------------------------------------------
        # NOTA: Descomenta solo uno de los dos métodos siguientes según lo que uses

        # ---- Método 1: Pip ----
        # print(f"{MESSAGE_COLOR}Instalando dependencias con pip...{RESET_ALL}")
        # subprocess.call(['pip', 'install', '-r', 'requirements.txt'])

        # ---- Método 2: Conda ----
        print(f"{MESSAGE_COLOR}Creando entorno con Conda...{RESET_ALL}")
        subprocess.call(['conda', 'env', 'create', '--file', 'environment.yml'])

        # -------------------------------------------------
        # 4. Mensaje final
        # -------------------------------------------------
        print(f"{MESSAGE_COLOR}Proyecto listo. ¡A trabajar!{RESET_ALL}")
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
1. cd ~/ruta/a/mi/carpeta/proyectos                             Ubicarte en el directorio donde quieres que se genere el proyecto (por ejemplo, tu carpeta de proyectos)
2. cookiecutter ~/ruta/completa/a/plantillas_personalizadas/    Ejecutar Cookiecutter apuntando a la ruta completa de tu plantilla personalizada
Alternativa de instalación de una plantilla en Github:    
3. cookiecutter https://github.com/platzi/curso-entorno-avanzado-ds --checkout cookiecutter-personal-platzi     uso de plantilla alojada en ese repo de Github, en lugar de usar la de la rama principal usa la de la rama cookiecutter-personal-platzi

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

_Distribución de plantillas en Github_
1. crear repo en github
2. cd plantillas_personalizadas/ && git init .        plantillas_personalizadas es el directorio con todas las configuraciones de nuestra plantilla de cookiecutter
3. Crea archivos '.gitkeep' en los directorios vacíos usando el comando 'touch .gitkeep'. Esto asegura que GitHub incluya estos directorios en el repositorio, ya que GitHub omite directorios vacíos por defecto.
4. git remote add origin git@github.com:fcisnerosr/cookiecutter-personal.git && git branch -M main && git push -u origin main   crea el repositorio remoto en local y actualiza los cambios en el repo remoto
5. git add . && git commit -m "initial commit"  crea el primer commit
6. cookiecutter https://github.com/fcisnerosr/cookiecutter-personal     Instala plantilla que está alojado en Github

_Problemas de rutas en diferentes OS_
_pathlib_
`CURRENT_DIR = pathlib.Path().resolve()`      objeto de tipo Path que devuelve la ruta absoluta desde donde se ejecuta
`CURRENT_DIR.parent`                          devuelve la ruta absoluta del directorio padre del directorio actual (un nivel arriba desde donde se ejecutó)
`DATA_DIR = CURRENT_DIR.parent.joinpath('data', 'raw')`   devuelve la ruta absoluta del directorio padre desde donde se ejecutó, añadiendo 'data/raw' al final
`DATA_DIR.is_dir()`                           devuelve True si DATA_DIR es un directorio real (no solo una ruta), y existe
`DATA_DIR.exists()`                           devuelve True si DATA_DIR existe (ya sea archivo o carpeta)
_PyFilesystem2_
`CURRENT_DIR = fs.open_fs('.')`                       abre el sistema de archivos desde donde se ejecuta el script
`print(CURRENT_DIR)`                                  imprime el objeto FS correspondiente al directorio actual (tipo <osfs '...'>)
`print(CURRENT_DIR.exists('.'))`                      devuelve True si el directorio actual existe

`DATA_DIR = fs.open_fs('../data/raw')`                abre el sistema de archivos ubicado en ../data/raw (directorio padre + data/raw)
`print(DATA_DIR)`                                     imprime el objeto FS correspondiente a la ruta ../data/raw
`print(DATA_DIR.listdir('.'))`                        imprime una lista con los archivos y carpetas dentro de data/raw

`for path in DATA_DIR.walk.files():`                  recorre todos los archivos (no carpetas) dentro de data/raw de forma recursiva
`    print(path)`                                     imprime la ruta relativa de cada archivo encontrado
`    with DATA_DIR.open(path) as data_file:`          abre el archivo encontrado dentro del FS para lectura
`        print(data_file.readlines())`                imprime todas las líneas del archivo como una lista

`print(DATA_DIR.makedir('dir_prueba_creado', recreate=True))`   crea una carpeta llamada dir_prueba_creado dentro de data/raw (sin error si ya existe)

_Problemas de la raiz de los archivos_
_pyprojroot_
