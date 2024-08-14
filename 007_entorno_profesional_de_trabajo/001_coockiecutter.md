# Cookiecutter
_Pasos para instalación_
mamba config --add channels conda-forge     agrega a conda-forge a la lista de canales desde los cuales Conda puede buscar e instalar paquetes
mamba create --name cookiecutter-personal cookiecutter=1.7.3    creación del nuevo env para cookiecutter, siempre especificar la versión para evitar problemas en el futuro 

_Creación de modelo carpetas para proyectos_
mkdir {{ cookicutter.proyect_slup }}
- crear configuración de enviroment.yml
- crear archivo y configuración de coockiecutter.json
- activar el env de donde esté instalado cookiecutter
- ejecutar cookiecuter .  

_Pasos para activar cookiecutter en un proyecto_
- El el directorio debo actuivar el env donde esté instalado cookiecutter
- En el directorio del proyecto ya debo tener configurado cookiecutter.json y enviroment.yml
- ejecutar cookiecutter .



