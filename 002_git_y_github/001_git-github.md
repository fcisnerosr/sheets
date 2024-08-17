# Git
_Comandos básicos_
`git init`                    iniciar un jepositorio
`git add file.py`             agregar el achivo al staging area
`git rm --cached archivo.py`    remueve el archivo del staging area
`git commit -m "version 1"`   envía los últimos cambios del archivo al sistema de control de versiones
`git add .`                   envía los últimos cambios de todos los archivos de donde está el repositorio
`git commit -am "mensaje"`                   realiza un git add de los cambios realizados, solo funciona con archivos con add previamente no con archivos nuevos
`git commit -a`                   lo mismo que el comando de arriba pero levanta vim para ingresar el mensaje
`git config --global core.abbrev 4`  configuración de número de dígitos en los commits de log
`git log archivo.py`          muestra la lista de commits realizados en un archivo
`git log --stat --oneline`      muestra cambios detallados de cuántas líneas se agregaron y borraron en cada commit
`git log -p`      Log muy laro que explica el número de líneas que se cambiaron, así como el cambio en el contenido
`gitk`                  git log con interfaz visual                                  
`git show archivo.py`           muestra los cambios línea a línea del archivo modificado
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

_Ramas_
`git branch <rama>`         creación de rama nueva desde otra rama
`git switch -c rama-nueva`        crear y ubicarse en la rama master en un solo paso
`git checkout <rama>`       cambio a la otra rama
`git merge rama1`       fusión de rama1 a rama2, desde rama1
`git merge --abort`       revertir un merge realizado

_Configuraciones para Github_
 `git config -l`                                develve los datos básicos de email user.name el log y el editor (vim)
`git config --global user.email "em@serv.com"`   cambia la dirección de correo electrónico
`ssh-keygen -t rsa -b 4096 -C "em@serv.com"`     generación de llaves SSH

_Repositorios remotos_
**Para más detalles de cómo crear llaves y como realizar el git push ver 002_creacion-llaves-SSH-y-primer-git-push.txt**
`git clone <url>`           Descarga todos los archivos y cambios y los guarda en un nuevo repositorio local creado y en el working directory
`git push`                    enviar cambios a un reposotorio remoto
`git merge`                   fusiona ramas
`git fetch`                   descarga ramas y commits de un repositorio, sin alterar el workind directory de mi repositorio local
`git pull origin main`                    actualiza los cambios que se han realizado en el repositorio remoto

_Tag y versiones en Github_
`git tag -a v0.1 -m "Mensaje del tag" 2dcxd`    Asigación del tag
`git tag`                                       Lista de todos los tags
`git show-ref --tags`                           Muestra lista de qué tags están referenciados a qué commits
`git push origin --tags`                        Envío de tags a Github
`git tag -d <tag>`                              Borrado local de un tag
`git push origin :refs/tag/<tag>`               Borrado de un tag en Github

_Alias a nivel global_
`git config --global alias.NOMBRE_ALIAS 'COMANDO_DEL_ALIAS'` Configuración de alias a nivel global
Ejemplo:
`git config --global alias.logg "log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"` Configuración de un alias global de super log renombrado como 'git logg'
`alias`                 listado de todos los alias
`unalias <alias>`       borrado de un alias

