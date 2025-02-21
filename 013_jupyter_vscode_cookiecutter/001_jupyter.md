# Comandos
esc + z                 deshacer
dd                      borrar bloque de código
shift + r               divide la pantalla entre codigo y datos de salida
esc + shift + enter     ejecutar el bloque actual y agrega un bloque nuevo abajo
esc + ctrl + enter      ejecutar el bloque actual sin agregar ningún bloque por debajo
esc + y                 convierte un bloque a código 
esc + m                 convierte un bloque en código
esc + b                 crear una celda debajo
esc + a                 crear una celda arriba

ctl + b                 desplegar el explorador de archivos
shift + tab             para centrar el foco en el explorador de archivos
backspace               para ir un nivel atrás en el explorador de archivos 
ctrl+shift+{            ir a la pestaña de la terminal
ctrl+tab                pasa a la siguiente pestaña

flecha derecha          oculta bloques
flecha izquierda        muestra bloques

shift + m               fuciona el bloque en el que estás con el de abajo 

ctrl + shift + L        abre el launcher
ctrl + s                guardar el archivo

alt + f                 abre el menu de brave para poner el modo de pantalla completa
f11                     quita la pantalla completa

## Pasos para abrir un entorno específico de conda mediante un kernel para un notebook de jupyter lab
conda env list          para ver los envs creados en conda
conda install -n mi_env ipykernel instala ipykernel para en mi_env para que pueda ser usado como un kernel en juypter lab (este comando se ejecuta una vez por entorno creado)
python -m ipykernel install --user --name=mi_env --display-name "Python (mi_env)" registra el entorno mi_env como kernel en jupyter y así se podrá seleccionar en jupyter lab

## nbdime
nbdiff notebook_original.ipynb notebook_modificado.ipynb        compara los dos Jupyter Notebooks especificados y muestra las diferencias como texto plano en la terminal,
nbdiff-web notebook_original.ipynb notebook_modificado.ipynb    compara visualmente las diferencias entre los dos Jupyter Notebooks especificados abriendo una interfaz interactiva en un navegador web.

## Comandos mágicos
%ls                     ejecuta un comando de la terminal en jupyter
%%bash                  ejecuta multiples líneas como un script de terminal dentro de una celda de código.
ls
echo "Hola"
mkdir "carpeta_nueva"

# Visual Studio Code
conda activate my_env   activar el env
code .                  abrir code desde la terminal de WSL
ctrl + shift + X        abrir el buscador de extensiones
ctrl + shift + E        abrir el explorador de archivos
ctrl + B                abrir y cerrar el explorador de archivos
ctrl + N                crear un nuevo archivo
Ctrl + M, M             convierte una celda de códido a Markdown
Ctrl + M, Y             convierte una celda a código
Ctrl + J                abrir y cerrar la terminal

### Debugging Controls in VS Code
1. Click to add breakpoint
2. Ctrl + Shift + Alt + Enter   Debug Cell

| Action         | Description |
|----------------|------------|
| **Continue**   | Resumes code execution until the next breakpoint or the end of the program. |
| **Step Back**  | Moves execution back to the previous line (if enabled). |
| **Step Over**  | Executes the next line of code without stepping into functions. |
| **Step Into**  | Steps into a function if the current line is a function call. |
| **Step Out**   | Runs the remaining lines in the current function and returns to the calling line. |
| **Disconnect** | Ends the debugging session. |

**Tip:** Use these tools to step through your code and inspect variable values in real time.

## Canales en conda
- Default
- Conda forge, 
_paquetes: (https://conda-forge.org/packages/)_
conda install conda-forge::pandas       Installs the pandas package from the conda-forge channel instead of the default conda channels. Fuente: https://anaconda.org/conda-forge/pandas
conda config --show channels            It displays the currently configured Conda channels in order of priority. Conda channels are repositories where Conda searches for packages when installing or updating software.
conda config --set channel_priority strict  It sets Conda's channel priority to "strict", meaning Conda will only install packages from the highest-priority channel and will not fall back to lower-priority channels. 
conda install numpy pandas matplotlib -c conda-forge    It installs the numpy, pandas, and matplotlib packages using the conda-forge channel.

## Cookie cutter
https://github.com/drivendataorg/cookiecutter-data-science      The page cookiecutter-data-science is a Cookiecutter template for structuring data science projects.
Pasos básicos:
1. Instalar cookie cutter
2. Clonar el repositorio
3. personalizar en nuestro entorno de trabajo

conda install conda-forge::cookiecutter     instalar cookiecutter con conda mediante el canal forge

