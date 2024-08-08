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


