# Código de configuración de environment.ymel en Cookiecutter
_Archivo de configuración que especifica cómo debe ser creado el env mediante conda_
_Define el entorno y los paquetes que deven ser instalados y los canales donde devben ser descargados_

# Establece el nombre del entorno de Conda, usando una variable de Cookiecutter para personalización
name: {{ cookiecutter.project_slug }}

# Lista de canales de Conda desde donde se buscarán e instalarán los paquetes
channels:
  - anaconda       # Canal Anaconda, que incluye paquetes precompilados y optimizados para ciencia de datos
  - conda-forge    # Canal comunitario con una amplia variedad de paquetes actualizados
  - defaults       # Canal predeterminado de Conda, que contiene paquetes estables y probados

# Sección que lista las dependencias que se instalarán en el entorno
dependencies:
  # Condición que verifica si se deben instalar todos los paquetes especificados
  {% if cookiecutter.project_packages == "All" -%}
    - fs             # Sistema de archivos abstracto para Python, facilita operaciones con archivos
    - jupyter        # Paquete para ejecutar Jupyter Notebooks, útil para análisis interactivo
    - jupyterlab     # Entorno de trabajo basado en web para Jupyter, proporciona una interfaz de usuario mejorada
    - pathlib        # Módulo que ofrece clases para manejo de rutas de archivos (está incluido en Python 3.4+)
  {% endif -%}
  
  - pip             # Gestor de paquetes pip, se incluye para asegurar que se pueda instalar paquetes de PyPI

  # Condición para instalar pyprojroot si se requieren todos los paquetes
  {% if cookiecutter.project_packages == "All" -%}
    - pyprojroot     # Facilita el acceso a la raíz del proyecto desde notebooks/scripts
  {% endif -%}

  - python={{ cookiecutter.python_version }}  # Instala una versión específica de Python según lo especificado

  # Instalaciones adicionales con pip bajo condición
  - pip:
    {% if cookiecutter.project_packages == "All" -%}
      - pyhere       # Facilita la referencia de rutas de archivos relativas a la raíz del proyecto, similar a 'here' en R
    {% endif -%}


## Estructura General
El archivo `environment.yml` configura un entorno Conda para un proyecto usando Cookiecutter. Incluye:

- **`name`**: El nombre del entorno, reemplazado por `{{ cookiecutter.project_slug }}`.
- **`channels`**:
  - `anaconda`: Un canal que proporciona paquetes con garantías de compatibilidad y estabilidad.
  - `conda-forge`: Un canal mantenido por la comunidad con una amplia variedad de paquetes.
  - `defaults`: El canal predeterminado de Conda con paquetes bien probados.

## Detalles de las Dependencias
Las dependencias se instalan según la configuración y necesidades del proyecto, utilizando condiciones:

### Condiciones Jinja
- **`if cookiecutter.project_packages == "All"`**:
  - **`fs`**: Gestión conveniente de sistemas de archivos.
  - **`jupyter`** y **`jupyterlab`**: Plataformas para notebooks y exploración de datos.
  - **`pathlib`**: Manejo de rutas de archivos de manera orientada a objetos (incluido en Python 3.4+).
  - **`pyprojroot`** y **`pyhere`**: Manejo simplificado de las rutas del proyecto.

### Versión de Python
- **`python`**: Instalación de Python según la versión especificada `{{ cookiecutter.python_version }}`.

### Instalación con Pip
- Algunos paquetes pueden requerir instalación vía pip si no están disponibles en los canales de Conda o si las versiones en PyPI son preferidas.

## Resumen
Este archivo automatiza la creación de entornos de desarrollo para proyectos de ciencia de datos, asegurando un ambiente uniforme para todos los colaboradores y facilitando la reproducibilidad de los análisis.
