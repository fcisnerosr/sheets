# Git
_Comandos básicos_
`git init`                    iniciar un repositorio
`git add file.py`             agregar el achivo al staging area
`git rm --cached archivo.py`    remueve el archivo del staging area
`git commit -m "version 1"`   envía los últimos cambios del archivo al sistema de control de versiones
`git add .`                   envía los últimos cambios de todos los archivos de donde está el repositorio
`git log archivo.py`          muestra la lista de commits realizados en un archivo
`git log --stat --oneline`      muestra cambios detallados de cuántas líneas se agregaron y borraron en cada commit
`git push`                    enviar cambios a un reposotorio remoto
`git show archivo.py`           muestra los cambios línea a línea del archivo modificado
`git config --global core.abbrev 4`  configuración de número de dígitos en los commits de log
`git diff 1viejo3 4nuevo5`           muestra las diferencias entre commits
`git diff`                          muestra las diferencias entre el working directory y el staging
`git reset --soft 1fjk`             mueve a HEAD al commit especificado sin modificar lo que está en stating ni en el working directory                    
`git reset --hard 1fjk`             mueve a HEAD al commit especificado borrando todo lo de stating y lo del working directory después de ese commit
`git checkout 1fjk archivo.py`                     
`git checkout`                     traer los últimos cambios hacia mi carpeta

_Configuraciones básicas de usuario_
`git config --list`                      lista de configuraciones del usario
`git config --global user.name "user"`   configuración del nombre de usuario
`git config --global user.email "user@"`  configuración del correo del nombre de usuario
`git config --global core.abbrev 4`  configuración de número de dígitos en los commits de log
