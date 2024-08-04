# Git
_Comandos básicos_
`git init`                    iniciar un repositorio
`git add file.py`             agregar el achivo al staging area
`git rm --cached archivo.py`    remueve el archivo del staging area
`git commit -m "version 1"`   envía los últimos cambios del archivo al sistema de control de versiones
`git add .`                   envía los últimos cambios de todos los archivos de donde está el repositorio
`git show`                    cambios específios
`git log archivo.py`          muestra la lista de cmmits realizados en un archivo
`git push`                    enviar cambios a un reposotorio remoto

_Configuraciones básicas de usuario_
git config --list                       lista de configuraciones del usario
git config --global user.name "user"    configuración del nombre de usuario
git config --global user.email "user@"  configuración del correo del nombre de usuario
