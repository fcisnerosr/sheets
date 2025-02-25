# Datos faltantes
_Uso de `None` en Python_
`print(None or True)`                         Retorna `True`, ya que `or` devuelve el primer valor verdadero.  
`print(None or False)`                        Retorna `False`, porque ambos valores son considerados "falsos".  
`print(None == None)`                         Retorna `True`, ya que `None` es igual a `None`.  
`print(None is None)`                         Retorna `True`, ya que `is` compara identidades en memoria.  
`print(type(None))`                           Retorna `<class 'NoneType'>`, que es el tipo de `None`.  

_Manejo de `np.nan` con NumPy_
`import numpy as np`                          Importa la librería NumPy.  
`print(np.nan or True)`                       Retorna `True`, porque `or` devuelve el primer valor verdadero.  
`print(np.nan == np.nan)`                     Retorna `False`, ya que `NaN` nunca es igual a sí mismo.  
`print(np.nan is np.nan)`                     Retorna `True`, porque `is` compara identidades en memoria.  
`print(np.nan / 2)`                           Retorna `nan`, ya que cualquier operación con `nan` sigue siendo `nan`.  
`print(type(np.nan))`                         Retorna `<class 'float'>`, ya que `np.nan` es un flotante.  
`print(np.isnan(np.nan))`                     Retorna `True`, porque `np.isnan()` detecta valores `nan`.  

_Manejo de Datos Faltantes con Pandas_
`import pandas as pd`                         Importa la librería Pandas.  
`test_missing_df = pd.DataFrame.from_dict(...)` Crea un DataFrame con valores faltantes (`np.nan`, `None`, `pd.NA`).  
`print(test_missing_df)`                      Muestra la tabla con los datos, donde `NaN` indica valores faltantes.  
`print(test_missing_df.isna())`               Devuelve un DataFrame con `True` donde hay valores faltantes.  
`print(test_missing_df.isnull())`             Funciona igual que `isna()`, detecta valores faltantes.  
`print(test_missing_df.x.isna())`             Devuelve una serie booleana indicando qué valores en la columna `x` están vacíos.  

_Creación de Series en Pandas con Datos Faltantes_
`print(pd.Series([1, np.nan]))`                             Crea una serie con un valor `1` y un `NaN`.  
`print(pd.Series([pd.to_datetime('2022-01-01'), np.nan]))`  Crea una serie con una fecha y un `NaN`.  
`print(pd.Series([-1]).isnull())`                           Devuelve `False`, porque `-1` no es un valor faltante.  

_Manejo de Datos Faltantes y Descarga de Datos con Pandas_  
`pima_indians_diabetes_url = "https://nrvis.com/data/mldata/pima-indians-diabetes.csv"`	Define la URL del archivo CSV con los datos de diabetes.  
`output_path = "./data/prima_indians-diabetes.csv"`	Especifica la ruta donde se guardará el archivo descargado.  
`subprocess.run(["wget", "-O", output_path, pima_indians_diabetes_url, "-q"])`	Descarga el archivo desde la URL y lo guarda en la ruta `output_path`.  

_Lectura del archivo CSV con Pandas_  
`diabetes_df = pd.read_csv('~/datos_faltantes/curso-datos-faltantes-main/data/pima-indians-diabetes.csv', sep=',', names=[...])`	Carga el dataset en un DataFrame de Pandas, especificando los nombres de las columnas.  

_Automatización de la obtención de datos desde un sitio web_  
`base_url = "https://github.com/njtierney/naniar/raw/master/data/"`	Define la URL base donde están almacenados los archivos `.rda`.  
`datasets_names = ("oceanbuoys", "pedestrian", "riskfactors")`	Lista de los datasets que serán descargados.  
`extension = ".rda"`	                                        Define la extensión de los archivos a descargar.  

_Descarga y carga automática de archivos en un diccionario_  
`dataset_dfs = {}`	                                Inicializa un diccionario vacío para almacenar los dataframes descargados.  
`for dataset in datasets_names:`	                Itera sobre la lista de datasets para descargarlos y cargarlos.  
&nbsp;&nbsp;&nbsp;&nbsp;`file_name = f"{dataset}{extension}"`	            Construye el nombre del archivo combinando el nombre del dataset con su extensión `.rda`.  
&nbsp;&nbsp;&nbsp;&nbsp;`output_path = f"./data/{file_name}"`	            Define la ruta donde se guardará cada archivo descargado.  
&nbsp;&nbsp;&nbsp;&nbsp;`subprocess.run(["wget", "-O", output_path, f"{base_url}{file_name}", "-q"])`	Descarga el archivo desde el sitio web y lo guarda en la carpeta `./data/`.  


_Lectura de archivos `.rda` y almacenamiento en un diccionario_  
`result = pyreadr.read_r(output_path)`	            Lee el archivo `.rda` con `pyreadr`, devolviendo un diccionario con los objetos almacenados en el archivo.  
`dataset_dfs[dataset] = result[next(iter(result))]`	Extrae el primer dataframe del diccionario y lo almacena en `dataset_dfs` con su nombre correspondiente.  

**Ejemplo de lo que sucede en la primera iteración:**  
`next(iter(result))`	                            Retorna `"oceanbuoys"` (nombre del objeto en `.rda`).  
`result[next(iter(result))]`	                    Retorna el dataframe asociado a `"oceanbuoys"`.  
`dataset_dfs["oceanbuoys"] = result["oceanbuoys"]`	Guarda el dataframe en el diccionario.  

_Extracción de DataFrames desde el diccionario_  
`oceanbuoys_df = dataset_dfs["oceanbuoys"]`	    Extrae el DataFrame correspondiente a `"oceanbuoys"`.  
`pedestrian_df = dataset_dfs["pedestrian"]`	    Extrae el DataFrame correspondiente a `"pedestrian"`.  
`riskfactors_df = dataset_dfs["riskfactors"]`	Extrae el DataFrame correspondiente a `"riskfactors"`.  

**Archivo: main_03.py**
_Resúmenes básicos de valores faltantes_
`valores_completos = riskfactors_df.missing.number_complete()`  Cuenta el número total de valores no faltantes en riskfactors_df
`valores_faltantes = riskfactors_df.missing.number_missing()`   Cuenta el número total de valores faltantes (NaN o None) en riskfactors_df

_Resúmenes tabulares de valores faltantes_
Nota: las variables son las columnas
`print(riskfactors_df.missing.missing_variable_summary())`      Realiza un análisis de valores faltantes a nivel de columna en el DataFrame.
    # La tabla resultante proporciona, para cada variable tres columnas que son:
    #   - El número de valores considerados como faltantes.
    #   - La cuenta total de observaciones en la columna.
    #   - El porcentaje que representan los valores faltantes en la columna.

`print(riskfactors_df.missing.missing_variable_table())`        Imprime una tabla que agrupa variables por la cantidad de valores faltantes que contienen y su porcentaje.
`print(riskfactors_df.missing.missing_case_summary())`          Imprime una tabla con tres columnas: la primera indica el índice de cada observación, la segunda muestra la cantidad de valores faltantes en esa observación y la tercera presenta el porcentaje de valores faltantes con respecto al total de variables.
`print(riskfactors_df.missing.missing_case_table())`            Imprime una tabla que agrupa las observaciones según la cantidad de valores faltantes que tienen, mostrando cuántas filas pertenecen a cada grupo y el porcentaje que representan en el total del dataset.

# Jupyter Notebooks
 _Descarga y carga automática de datasets en Jupyter Notebooks_  
`datasets_dfs = {}`	Inicializa un diccionario vacío para almacenar los dataframes descargados.  

_Iteración sobre la lista de datasets_  
`for dataset_name in datasets_names:`	Itera sobre los nombres de los datasets para descargarlos y cargarlos en un diccionario.  

_Definición de nombres y rutas de archivos_  
&nbsp;&nbsp;&nbsp;&nbsp;`dataset_file = f"{dataset_name}{extension}"`	Construye el nombre del archivo combinando el nombre del dataset con la extensión `.rda`.  
&nbsp;&nbsp;&nbsp;&nbsp;`dataset_output_file = f"~/datos_faltantes/curso-datos-faltantes-main/data/{dataset_file}"`	Define la ruta donde se guardará cada archivo descargado.  
&nbsp;&nbsp;&nbsp;&nbsp;`dataset_url = f"{base_url}{dataset_file}"`	Define la URL completa desde donde se descargará el dataset.  

_Descarga del dataset usando Jupyter Notebooks (`!wget`)_  
&nbsp;&nbsp;&nbsp;&nbsp;`!wget -q -O {dataset_output_file} {dataset_url}`	Descarga el archivo desde la URL y lo guarda en `dataset_output_file` sin mostrar salida en la terminal (`-q`).  

_Lectura del archivo `.rda` y almacenamiento en un diccionario_  
&nbsp;&nbsp;&nbsp;&nbsp;`datasets_dfs[f"{dataset_name}_df"] = pyreadr.read_r(dataset_output_file).get(dataset_name)`	Lee el archivo `.rda` con `pyreadr`, extrae el dataframe y lo guarda en `datasets_dfs` con un nombre clave (`oceanbuoys_df`, `pedestrian_df`, etc.).  

_Visualización de las claves del diccionario_  
`datasets_dfs.keys()`	Muestra todas las claves almacenadas en `datasets_dfs`, indicando los nombres de los datasets cargados.  

_Acceso a un dataframe específico_  
`datasets_dfs['oceanbuoys_df']`	Muestra el contenido del dataframe `"oceanbuoys_df"`, cargado desde el archivo `.rda`.   


# Resúmenes tabulares de valores faltantes
Variables/Columnas
Resumen por variable
`print(riskfactors_df.missing.missing_variable_summary())`  Analiza los valores faltantes en cada columna del DataFrame, mostrando cuántos valores faltan, cuántas observaciones hay en total por columna y el porcentaje de datos faltantes en cada una.
`print(riskfactors_df.missing.missing_variable_table())`    Imprime una tabla que agrupa variables por la cantidad de valores faltantes que contienen y su porcentaje.
`print(riskfactors_df.missing.missing_case_summary())`      Imprime una tabla con tres columnas: la primera indica el índice de cada observación, la segunda muestra la cantidad de valores faltantes en esa observación y la tercera presenta el porcentaje de valores faltantes con respecto al total de variables.
`print(riskfactors_df.missing.missing_case_table())`        Imprime una tabla que agrupa las observaciones según la cantidad de valores faltantes que tienen, mostrando cuántas filas pertenecen a cada grupo y el porcentaje que representan en el total del dataset.
`print(riskfactors_df.missing.missing_variable_span(variable='weight_lbs', span_every=50))` Imprime una tabla que divide una variable en intervalos de tamaño `span_every`, mostrando en la primera columna el número de intervalo, en la segunda la cantidad de valores faltantes, en la tercera la cantidad de valores completos, y en la cuarta y quinta los porcentajes de valores faltantes y completos, respectivamente, los cuales son complementarios.     
`print(riskfactors_df.missing.missing_variable_run(variable='weight_lbs'))` Imprime una tabla que analiza las rachas de valores faltantes y completos en una variable o columna, mostrando en la primera columna la longitud de cada racha y en la segunda si la racha corresponde a valores faltantes o completos.

_Requirements_
cycler==0.12.1
fonttools==4.55.3
kiwisolver==1.4.8
matplotlib==3.5.1
missingno==0.5.2
multipledispatch==1.0.0
natsort==8.4.0
numpy==2.2.1
packaging==24.2
pandas==2.2.3
pandas-flavor==0.6.0
pillow==11.1.0
pyjanitor==0.30.0
pyparsing==3.2.1
pyreadr==0.5.2
python-dateutil==2.9.0.post0
pytz==2024.2
scipy==1.14.1
seaborn==0.13.2
session-info==1.0.0
six==1.17.0
stdlib-list==0.11.0
tzdata==2024.2
UpSetPlot==0.6.1
xarray==2024.11.0

# **Librerías para Manejo de Datos Faltantes**

## **Librerías clave para datos faltantes**
- **missingno (0.5.2)**  
  Permite visualizar datos faltantes con gráficos como matrices, dendrogramas y mapas de calor.  
- **pandas (2.2.3)**  
  Maneja y analiza datos con funciones como `.isnull()`, `.dropna()`, y `.fillna()` para tratar valores faltantes.  
- **pyjanitor (0.30.0)**  
  Extiende Pandas con métodos de limpieza avanzados, como `remove_empty()` para eliminar filas/columnas vacías.  

## **Librerías de soporte para análisis y visualización**
- **matplotlib (3.5.1)**  
  Genera gráficos y es útil para visualizar patrones de datos faltantes.  
- **seaborn (0.13.2)**  
  Biblioteca basada en Matplotlib para visualización avanzada, compatible con datos faltantes.  
- **UpSetPlot (0.6.1)**  
  Representa intersecciones de datos faltantes en múltiples categorías.  

## **Librerías de manipulación de datos**
- **numpy (2.2.1)**  
  Base para cálculos numéricos, maneja datos NaN (`numpy.nan`).  
- **scipy (1.14.1)**  
  Proporciona métodos estadísticos y de interpolación para imputación de datos faltantes.  
- **xarray (2024.11.0)**  
  Maneja datos multidimensionales con soporte para valores faltantes en estructuras tipo Pandas.  

## **Librerías para leer y manipular archivos**
- **pyreadr (0.5.2)**  
  Permite leer y escribir archivos de R (`.rds`, `.rdata`), útil cuando se trabaja con datos que contienen valores faltantes.  
- **pillow (11.1.0)**  
  Maneja imágenes, aunque no está directamente relacionada con datos faltantes.  

## **Librerías de utilidad y dependencias internas**
- **multipledispatch (1.0.0)**  
  Permite sobrecarga de funciones, no relacionada directamente con datos faltantes.  
- **natsort (8.4.0)**  
  Ordena cadenas de texto con números de forma natural, útil en limpieza de datos.  
- **session-info (1.0.0)**  
  Muestra información de la sesión de Python, útil para reproducibilidad.  
- **tzdata (2024.2), pytz (2024.2)**  
  Manejan zonas horarias, útiles en análisis de datos con fechas.  
- **python-dateutil (2.9.0.post0)**  
  Extiende la manipulación de fechas en Python.  
- **stdlib-list (0.11.0)**  
  Proporciona listas de módulos estándar de Python.  
- **six (1.17.0)**  
  Compatibilidad entre Python 2 y 3.  
- **packaging (24.2), pyparsing (3.2.1), fonttools (4.55.3), kiwisolver (1.4.8), cycler (0.12.1)**  
  Dependencias utilizadas por Matplotlib para manejo de gráficos.  
