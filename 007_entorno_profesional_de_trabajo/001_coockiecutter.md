# Cookiecutter
_Pasos para instalación_
mamba config --add channels conda-forge     agrega a conda-forge a la lista de canales desde los cuales Conda puede buscar e instalar paquetes
mamba create --name cookiecutter-personal cookiecutter=1.7.3    creación del nuevo env para cookiecutter, siempre especificar la versión para evitar problemas en el futuro 

_creación de modelo carpetas para proyectos_
mkdir {{ cookicutter.proyect_slup }}
