# Git
_Configuraciones básicas de usuario_
`git config --list`                      lista de configuraciones del usario
`git config --global user.name "user"`   configuración del nombre de usuario
`git config --global user.email "user@"`  configuración del correo del nombre de usuario
`git config --global core.abbrev 4`  configuración de número de dígitos en los commits de log

_Comandos básicos_
`git init`                    iniciar un jepositorio
`git add file.py`             agregar el achivo al staging area
`git rm --cached archivo.py`  remueve el archivo del staging area
`git restore <file>`          restaura un cambios guardado de algún documento
`git restore . `              restaura todos los archivos modificados en un solo comando
`git commit -m "version 1"`   envía los últimos cambios del archivo al sistema de control de versiones
`git add .`                   envía los últimos cambios de todos los archivos de donde está el repositorio
`git commit -am "mensaje"`    realiza un git add de los cambios realizados, solo funciona con archivos con add previamente no con archivos nuevos
`git commit -a`               Lo mismo que el comando de arriba pero levanta vim para ingresar el mensaje
`git commit --amend`          Editar el último commit, siempre que no se haya enviado al repositorio remoto mediante push.
`git config --global core.abbrev 4`  configuración de número de dígitos en los commits de log
`git log archivo.py`            muestra la lista de commits realizados en un archivo
`git log --stat --oneline`      muestra cambios detallados de cuántas líneas se agregaron y borraron en cada commit
`git log -p`                    Log muy largo que explica el número de líneas que se cambiaron, así como el cambio en el contenido
`gitk`                          git log con interfaz visual      
`git show archivo.py`           muestra los cambios línea a línea del archivo modificado
`git diff 1viejo3 4nuevo5`      muestra las diferencias entre commits
`git diff`                      muestra las diferencias entre el working directory y el staging
`git diff HEAD`                 muestra las diferencias entre el working directory y el último commit de la rama actual
`git reset --soft <no. commit>`         mueve a HEAD al commit especificado sin modificar lo que está en stating ni en el working directory
`git reset --hard <no. commit>`         mueve a HEAD al commit especificado borrando todo lo de stating y lo del working directory después de ese commit
`git checkout <no. commit> archivo.py`                     
`git checkout`                     traer los últimos cambios hacia mi carpeta

_Ramas_

`git branch`                   Muestra las ramas locales.
`git branch -r`                Muestra las ramas remotas que existen en el servidor remoto y han sido descargadas localmente. Excluye ramas locales que no estén en remoto.
`git branch -a`                Muestra todas las ramas, tanto las locales como las remotas. En blanco las locales, en remoto las remotas y en asteriscos la rama actual.
`git switch -c rama-nueva`     Crea y se ubica en la rama nueva en un solo paso.
`git checkout <rama>`          Cambia a la otra rama.
`git merge rama1`              Fusiona la rama1 con la rama actual (debes estar ubicado en la rama destino).
`git merge --abort`            Revertir un merge realizado en caso de conflicto o error.
`git show-branch`              Muestra el estado de las ramas en local.
`git show-branch --all`        Muestra el estado de las ramas en local y en remoto.
`git branch -d <rama>`         Elimina la rama localmente.

_Configuraciones para Github_
 `git config -l`                                develve los datos básicos de email user.name el log y el editor (vim)
`git config --global user.email "em@serv.com"`   cambia la dirección de correo electrónico
`ssh-keygen -t rsa -b 4096 -C "em@serv.com"`     generación de llaves SSH

_Repositorios remotos_
`git clone https://github.com/user/repositorio.git` Si no se tiene el permismo mediante llaves SSH, descarga todos los archivos y cambios y los guarda en un nuevo repositorio local creado y en el working directory
`git clone --branch <rama> --single-branch git @github.com:usuario/repo.git`  clona solo una rama específica del repositorio remoto
`git push`                                  enviar cambios a un reposotorio remoto
`git push --force`                          Después de hacer un `git reset --hard` se pueden reenviar los cambios para que el repositorio remoto refleje exactamente lo que se hizo en el repositorio local. _Puede ser peligroso, así que tomar precausiones_
`git push origin <branchnoamain>`           enviar al repositorio remoto una rama distinta a la rama _main_
`git merge`                                 fusiona ramasumenta el tamaño de la ventana actual hacia la derecha
`git fetch`                                 descarga ramas y commits de un repositorio, sin alterar el workind directory de mi repositorio local
`git pull origin main`                      actualiza los cambios que se han realizado en el repositorio remoto
`git pull origin --delete <rama>`           borra la rama en el repositorio remoto
**Para más detalles de cómo crear llaves y como realizar el git push ver 002_creacion-llaves-SSH-y-primer-git-push.txt**

_Git ignore: no subir archivos binarios_
`.gitignore`           archivo con lista de los archivos que no se subirán a un repositorio remoto
`*.jpg`                 ignora todos los archivos con dicha extensión 
**https://www.gitignore.io/ definen las tecnologías que manejan en el proyecto y nos da automáticamente los archivos que debemos ignorar**

_Tag y versiones en Github_
`git tag -a v0.1 -m "Mensaje del tag" 2dcxd`    Asigación del tag
`git tag`                                       Lista de todos los tags
`git show-ref --tags`                           Muestra lista de qué tags están referenciados a qué commits
`git push origin --tags`                        Envío de tags a Github
`git tag -d <tag>`                              Borrado local de un tag
`git push origin :refs/tag/<tag>`               Borrado de un tag en Github

_git commit --amdnd, corregir commits_
`git commit --amend`            Permite reescribir y adicionar nuevos archivos al último commit.
`git add archivo-olvidado.py`   En caso de olvidar adicionar un archivo.
`git commit --amend`            Actualiza el último commit con el archivo olvidado.

_Colaboración con múltiples usuarios_
*En caso de ser el usario propietario del repositorio remoto*
- En los settings del repositorio remoto en Github. _Settings/Collaborators_ y adicionamos el correo del usuario asociado a Github, pero en caso de que no sea público su email, puede ser con su usuario de Github
- En caso de que no tenga acceso mediante llaves SSH, se debe dar acceso mediante Token de Acceso Personal (PAT) 
    - En Github, con la cuenta del propietario del repositorio:
    - Settings (debajo de la foto de perfil)/Developer setttings (a la izquierda hasta abajo)/Personal access tokens/Generate new token/Note/Fecha de expiración/Seleccionar alcances del permiso/Generate token
    - copiar token y enviarlo, el usuario colaborador debería de saber qué h    acer con él.
*En caso de ser el usario colaborador*
    - con el token proporcionado, cada vez que se realice un push se debe ingresar el usuario (previamente el propietario debió de darte permiso mediante tu email o tu usuario)
    - luego en password se ingresa el token proporcionado
    - Si no quieres ingresar el token cada vez que haces un push:
        - ejecutar: `git config --global credential.helper store`
        - hacer el`git config --global credential.helper store` e ingresar el username y el PAT
        - ejecutar `cat ~/.git-credentials` y con esto verificamos qué username y qué PAT esta asociado a dicho username
        - El entorno ya habrá sido configurado para que cuando se haga el `git push origin master` no haya que ingresar más el username y la contraseña manualmente.
        - todo esto funcionará siempre y cuando el PAT no haya expirado o los permisos no hayan sido modificados.

_Pull request, comando correpondiente a Github_
Trabajar un pull request es similar a trabajar en un staging area en remoto antes de fucionar cambios a la rama principal
**Si soy el propietario de repositorio:**
    - Escogemos que compare los cambios realizados de:
        base: rama principal   <-  compare: rama creada para arreglar errores
        El nombre del commit puede ser el nombre del "Pull request"
        Se pueden escribir más detalles en el pull request
        Se pueden agregar reviewers para hace el _code review_
        Cuando terminemos las configuraciones, clickeamos en "Create pull request"
    - En caso de ser el colaborador el cuál debe hacer el _code review_
        - `Pull requests/Files changed/Review changes/Opciones que están abajo/Submit review`
            - `Approve`: indica que has revisado el código o los cambios propuestos y estás de acuerdo con que sean fusionados en la rama principal
            - `Request chages`: Esta opción se utiliza cuando encuentras problemas o áreas de mejora en el código o la propuesta que se está intentando fusionar en la rama principal 
    - Se puede iniciar una conversación entre los miembros del equipo en:
        - `Pull requests/Conversation`
    - En caso de que los cmabios sean correctamente aplicados y todos estén de acuerdo con ellos:
        - `Pull requests/ir hasta la parte inferior de la página/Merge pull request/Confirm merge/Delete branch`: La última acción es opcional y depende de la forma de trabajo de cada equipo de trabajo.
**Si no soy el propietario de repositorio, ni colaborador del proyecto:**
_Fork a un proyecto Open Source. Fork de una característica de Github_
    - Primeramente realiza los siguientes pasos para mantener nuestro fork con el repo remoto:
        - `git remote add upstream https://github.com/usuario-propietario/repositorio.git`  La rama upstream sirve para matener actualizado mi repositorio remoto con el repositorio remoto el del propietario. 
        - `git checkout main && git pull upstream main` 
        - `git push origin main` 
    - Buscar el proyecto público en Github/Fork (en la esquina de repositorio remoto). Paso indispensable para poder hacer contribuciones, el solo clonar el repositorio remoto no hará que podamos contribuir en él.
        - `git clone https://github.com/user-propietario/repositorio.git`
        - hacer todos los cambios necesarios, commitearlos y pushearlos a mi repositorio remoto de Github
    - Crear un pull request al propietario
        - cuando los cambios fueron pusheados a mi repositorio global, automaticamente me aparacerá un mensaje tipo "This branch is # commit behind usuario-original/repositorio". Dale click
        - en el menú "Comparing changes" se pueden desplegar obciones para ver los cambios hechos entre mis contribuciones y el repositorio original de propietario
        - configurar:
            base repository: usuario-original/repo base: rama-a-recibir-el-cambio   <-  head repository: mi-usuario/repo    compare: rama-desde-donde-se-envian-los-cambios
        - Create pull request/nombre del commit/mensaje de contribucion/Create pull request
    - Desde el propietario:
        - Pull requests/verificar los cambios en "Files changed"/Review changes/Mensaje de agradecimiento/Approve/Merge pull request/Confirm merge

_Malas prácticas_
_rebase: viene de "rebasear", de volver a crear una base para una serie de commits_
Orden de comandos a ejecutar para llevar a camo correctamente el rebase
`git checkout experimento`                    cambia a la rama `experimento` donde harás cambios experimentales que no quieres que se vean directamente en `main`.
`git commit -am "Cambios experimentales"`     realiza y guarda los cambios en `experimento` con un commit.
`git checkout main`                           cambia a la rama `main` para preparar la integración de los cambios de `experimento`.
`git rebase experimento`                      rebasea la rama `main` con los cambios de `experimento`, aplicándolos de manera "silenciosa" sin crear un merge commit.
`git branch -d experimento`                   elimina la rama `experimento` localmente, quitando evidencia de los cambios experimentales.
`git push origin main --force-with-lease`     actualiza la rama `main` en el remoto, forzando el push debido a los cambios en el historial.
_cherry-pick: traer commits antiguas al head del branch_
Desde la rama main (o desde la rama al cual se le quiera aplicar el commit mediante el cherry-pick)
`git cherry-pick <no. commit>`                        aplica uno o más commits específicos de una rama a otra, sin fusionar toda la rama a diferencia del merge tradicional.
`git cherry-pick <commit-hash-1> <commit-hash-2> <commit-hash-3>` aplica los cambios de commits no consecutivos.
`git cherry-pick <commit-hash-inicial>^..<commit-hash-final>` aplica los cambios de commits consecutivos.
_git reflog, recuperar lo perdido_
`git reflog`                 Muestra un historial detallado de todas las referencias de HEAD, incluyendo commits, merges, resets y rebase.
`git reset --hard HEAD@{1}`  Mueve el repositorio al commit anterior al actual (según el historial de HEAD), eliminando el commit actual y todos los cambios no guardados. HEAD@{1} significa "el estado de HEAD justo antes de la última acción registrada". Básicamente, es el commit anterior al actual. Si usas HEAD@{2}, te moverías dos acciones hacia atrás en el reflog.
`git reset --hard HEAD`      Restablece el repositorio al commit actual, eliminando cualquier cambio no committeado en el working directory pero sin modificar la posición de HEAD.
`git reset --hard <no.commit>` Restablece todo hasta este número de commit en caso de no regresar los archivos borrados.
`git reset --soft`           Hace lo mismo que los anteriores pero conserva lo guardado en el staging area. Este comando es poco usado.

_Stash: guardados temporales_
`git stash`                       guarda temporalmente en el working directory y el staging area sin commitear los cambios. Después de ejecutarlo, regresa los archivos cambiados al último commit guardado.
`git stash list`                  muestra todos los stashes realizados. Nota: son cambios realizados enlistados que no necesariamente tienen que estar conectados, ya que cuando se realiza un stash lo guardado regresa al estado original de otro commit.
`git stash pop`                   aplica los cambios guardados en el stash más reciente en el working directory y el stash aplicado se elimina automáticamente.
`git stash branch <rama>`         crea una nueva rama, aplica el stash más reciente a esta nueva rama y elimina dicho stash de la lista de stashes.

_Flujo de trabajo con git stash_
Estas trabajando en una rama llamada dev
1. `Estás trabajando en una rama llamada dev`       Describe que te encuentras en la rama `dev`.
2. `Cambios en la rama actual`                      Realizas cambios en la rama `dev`.
3. `git stash`                                      Guarda los cambios sin commitear y limpia el working directory para permitir cambiar de rama.
4. `git checkout main`                              Cambias a la rama `main` para realizar otra tarea urgente.
5. `Realizas con cambios necesarios y después`      Realizas los cambios urgentes en `main` y luego...
6. `git commit -am "Se resuelve un problema urgente en main"`  Commit de esos cambios en la rama `main`.
7. `git checkout dev`                               Regresas a la rama `dev` para continuar con tu trabajo original.
8. `git stash pop`                                  Recupera los cambios guardados en el stash y los aplica en la rama `dev`.
9. `En caso de haber conflictos:`                   Si hay conflictos, resuelve manualmente.
    Abre los archivos conflictivos, resuelve los conflictos, y luego..
    `git add archivos_resueltos`                     Marca los archivos con conflictos como resueltos.
    `git stash pop --continue`                       Continúa aplicando el stash después de resolver los conflictos.
    `Se continúa trabajando en la rama dev`          Vuelves a trabajar en la rama `dev` con todos los cambios aplicados.

_git clean, eliminar archivos nuevos_
`git clean -n`    Muestra los archivos nuevos no rastreados por Git que podrían ser eliminados del working directory.
`git clean -f`    Elimina los archivos no rastreados definitivamente.
`git clean -fd`   Elimina tanto archivos como directorios nuevos no rastreados definitivamente.
`git clean -X`    Elimina solo archivos ignorados por Git definitivamente.
`git clean -x`    Elimina todos los archivos no rastreados definitivamente.

_Busquedas con grep_
`git grep <palabra>`                          Busca la palabra a buscar dentro de todo el repositorio.
`git grep -n <palabra>`                       Busca el archivo y la línea donde se encuentre dicha palabra.
`git grep -c <palabra>`                       Busca en cuántas líneas y en qué archivos se repite la palabra a buscar.
`git log --oneline --grep="palabra"`          Busca dentro del log, la palabra sin remarcarla.
`git log --oneline | grep --color=auto -i "palabra"`  Busca dentro del log y la palabra sí la remarca.

_Comandos y recursos colaborativos_
git shortlog muestra los logs separados con comentarios por cada miembro del equipo que colaboró en el repositorio
git shortlog -sn muestra una lista de corta de cuántos commits ha hecho cada miembro. Excluyendo los comentarios
git shortlog -sn --all --no-merges muestra una lista de corta de cuántos commits ha hecho cada miembro. Excluyendo los comentarios
git blame archivo.py -L35,60 -c muestra quién, que día y hora hizo los últimos cambios en cada línea de un archivo.py de la línea 35 a 60

_Alias a nivel global_
`git config --global alias.NOMBRE_ALIAS 'COMANDO_DEL_ALIAS'` Configuración de alias a nivel global
`git config --global alias.logg "log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"` Configuración de un alias global de super log renombrado como 'git logg'. _Sin embargo un git debe ser agregado antes del alias para que funcione, es recomendable mejor modificar el archivo .bashrc_
Ejemplo:
`alias glgg="git log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"`
`alias`                 listado de todos los alias
`unalias <alias>`       borrado de un alias


