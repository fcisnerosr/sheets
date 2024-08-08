# Git
_Comandos básicos_
`git init`                    iniciar un repositorio
`git add file.py`             agregar el achivo al staging area
`git rm --cached archivo.py`    remueve el archivo del staging area
`git commit -m "version 1"`   envía los últimos cambios del archivo al sistema de control de versiones
`git add .`                   envía los últimos cambios de todos los archivos de donde está el repositorio
`git commit -am "mensaje"`                   realiza un git add de los cambios realizados, solo funciona con archivos con add previamente no con archivos nuevos
`git commit -a`                   lo mismo que el comando de arriba pero levanta vim para ingresar el mensaje
`git log archivo.py`          muestra la lista de commits realizados en un archivo
`git log --stat --oneline`      muestra cambios detallados de cuántas líneas se agregaron y borraron en cada commit
`git log -p`      Log muy laro que explica el número de líneas que se cambiaron, así como el cambio en el contenido
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

_Repositorios remotos_
`git push`                    enviar cambios a un reposotorio remoto
`git merge`                   fusiona ramas
`git fecth`                   descarga ramas y commits de un repositorio 
`git pull`                    actualiza los cambios que se han realizado en el repositorio remoto
`git clone <url>`           Descarga todos los archivos y cambios y los guarda en un nuevo repositorio local creado y en el working directory

_Ramas_
`git branch <rama>`         creación de rama nueva desde otra rama
`git checkout <rama>`       cambio a la otra rama
`git merge rama1`       fusión de rama1 a rama2, desde rama1
`git merge --abort`       revertir un merge realizado

