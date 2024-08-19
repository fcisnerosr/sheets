# Terminal

## Primeros pasos
### Comandos
`type`     devuelve el informacion de un comando. Puede indicar si un comando es orden interna de shell, función de shell, alias o una programa ejecutable

_Anatomía de CLI (Command Line Interface)_
`$ rm -rf directory`
donde:
    $           prompt
    rm          Command
    -rf         option
    directory   argument

### ls, opciones y argumentos
`ls -dl directorio`   devuelve los detalles del directorio (permisos, fecha, tamaño y propietario) ls -R               devuelve una lista de directorios de los directorios. R es de "recursivamente"
`ls -hl -R`           devuelve una lista de los directorios en forma de human lecture
`ls -r`               devuelve una lista en orden inverso
`ls -X`               devuelve una lista ordenados por extensiones
`ls -S`               devuelve una lista ordeanada por tamaño
 añadir l antes de la opción devuelve en forma de lista.
    ejemplo: `ls -l`

### Mover, eliminar y cambiar de directorio
`.`                     directorio actual
`..`                    directorio anterior
`mv <file> ..`          mover el archivo file a un nivel atrás
`mv file new_name`      cambiar el nombre de un archivo
`rm -ri directorio`     accede y pregunta si quieres acceder a cada subdirectorio y si sí entras pregunta eliminar o no cada archivo. El r de "ri" es porque se ejecuta el comando recursivamente
`cd ..`                 change directory un nivel atrás
`cd ../..`              change directory dos niveles atrás
`file archivo.tex`      devuelve el tipo de archivo
`tree`                  devuelve el arbol de directorios completo
`tree -L 2`             devuelve el arbol de directorios en 2 niveles
_Formas de combinar los archivos_
`mkdir dir1 dir2 dir3`
`touch file1 file2 file3`


## Visualisar archivos
head archivo.py -n 15   muestra las primeras 15 lineas de codigo de archivo.py
tail archivo.py -n 15   muestra las ultimas 15 lineas de codigo de archivo.py
less archivo.py         exploras el archivo.py
    NOTA: te puedes mover con flechas o el wheel del mouse o para bajar mas rapido con la barra espaciadora
    Se puede usar / para buscar una palabra:
    Ejemplo: /palabra_a_buscar
nautilus directorio     abre el directorio en una interfaz grafica

Abrir htts://google.com en brave en terminal
brave --new-window https://google.com

### ¿qué es un comando?
type ls                 devuelve el tipo de comando y cómo está configurado el álias
type -a ls              devuelve la ubicación de ls
type -P ls              devuelve la ubicación del ejetucatable de ls
alias l="ls -lh"        configuración de alias pero se borran al cerrar la terminal
whatis ls               información de una oración del comando
help cd                 información corta de "cd"
man ls                  documentación detallada y estructurada de "ls"
info ls                 documentación extensa de "ls"

### Wilcards.
_Con ls buscan hasta dos niveles siguientes_
ls *.py                 enlista archivos y directorios que terminan en .py
ls datos*               enlista archivos y directorios que empieza con el nombre datos y el resto de los archivos que empiezan con datos y más caracteres por delante
ls datos?               enlista archivos y directorios que empieza con el nombre datos y 1 caracter
ls datos??              enlista archivos y directorios que empieza con el nombre datos y 2 caracteres
ls [[:upper:]]*         enlista archivos y directorios que empieza con mayúsculas
ls -d [[:upper:]]*      enlista directorios que empiezan con mayúsculas
ls -d [[:lower:]]*      enlista directorios 
ls [ad]*                enlista los archivos y directorios que empiezan con a y d
ls [:digit:]*           enlista los archivos y directorios que empiezan del 1 al 0
 ls *[0-9]*             enlista los archivos y directorios que empiezan del 1 al 0
ls [:alum:]*            enlista los archivos y directorios que empiezan con letra y dígito
ls [:alpha:]*           enlista los archivos y directorios que empiezan con cualquier alfabético

### Redirecciones: cómo funciona la shell
`ls sheets > lista.txt`   redirige el output a un archivo que puede ser no creado inicialmente de lo contrario se sobreescribe
`ls sheets >> lista.txt`  redirige el output a un archivo al final de un archivo ya creado
