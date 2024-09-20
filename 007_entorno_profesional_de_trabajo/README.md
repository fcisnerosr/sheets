Personalizacion avanzada
- Plantilas de entorno de trabajo personalizadas para análisis y modelos. Crear un sistema de carpetas y archivos que se repliquen de manera automática
- Aprender a desarrollar proyectos para múltiples plataformas.
_Medio por el cual se porta o construye un diseño predefinido a fin de agilizar el trabajo_

_Cookicutter_
Detecta na sintaxis expecial en una serie de documentos o archivos, dichos documentos pueden estar en local en el repositorio remoto.
Cookicutter usa el lenguaje jinja, que es un legnguaje simiar a python

_Instalación_
conda config --add channels conda-forge instalacion mediante conda-forge. Cookie-cutter se encuentra en el canal global de forge de conda

// En Cookiecutter el .md es un archivo que sera usado como plantilla, no solo es un archivo informativo
# {{ cookiecutter.project_title }}
// Esta línea crea un encabezado principal con el título del proyecto. 
// El valor para el título se toma de la variable 'project_title' definida en 'cookiecutter.json'.

By: {{ cookiecutter.project_author_name }}
// Esta línea añade un subtexto con el nombre del autor del proyecto.
// 'project_author_name' es una variable de 'cookiecutter.json' que se reemplaza por el nombre real del autor.

{{ cookiecutter.project_description }}
// Esta línea inserta la descripción del proyecto.
// 'project_description' también es una variable de 'cookiecutter.json' y proporciona un breve resumen del proyecto.

## License
// Este es un subencabezado para la sección de licencia del README.
// Aquí normalmente seguiría el texto o la explicación de la licencia bajo la cual se distribuye el proyecto.


