# Pandas

## Dimensiones y operaciones en Pandas

_Leer un csv_
`path = 'Online_Retail.csv'`                      # Carga la ruta al archivo CSV.
`df = pd.read_csv(path, encoding='windows-1252')` # Carga un DataFrame desde un archivo CSV con codificación específica.
`data_excel = pd.read_excel(path)`                # Carga un DataFrame desde un archivo Excel (comentado).
`data_json = pd.head())`                          # Imprime las cabeceras con las 5 primeras filas de qué trata cada columna
`print((pd.read_json(path)`                       # Carga un DataFrame desde un archivo JSON (comentado).

_DataFrame desde un array, lista o diccionario_
_array_
`array = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])`         # Declara una matriz de 3 filas y 3 columnas usando NumPy.
`dt_from_array = pd.DataFrame(array, columns=['A', 'B', 'C'])`  # Crea un DataFrame a partir de un array NumPy con columnas etiquetadas A, B, y C.
_list_
`list = [[1, 'Jhon', 22], [2, 'Anna', 24]]`                   # Lista de listas, cada sublista contiene datos de una persona.
`df_from_list = pd.DataFrame(list, columns=['ID', 'Name', 'Age'])`  # Crea un DataFrame a partir de una lista de listas con columnas etiquetadas ID, Name y Age.
_dictionary_
`dicc = [{'ID': 1, 'Name': 'Jhon', 'Age': 22}, {'ID': 2, 'Name': 'Ana', 'Age': 24}]`  # Crea una lista de diccionarios, cada diccionario contiene datos de una persona.
`df_from_dicc = pd.DataFrame(dicc, columns=['ID', 'Name', 'Age'])`  # Crea un DataFrame a partir de una lista de diccionarios con columnas etiquetadas ID, Name y Age.

_Exploratorio inicial de datos, series, y valores estadísticos_
`num_rows, num_columns = df.shape`             # Obtiene el número de filas y columnas del DataFrame.
`print(f'filas = {num_rows}')`                 # Imprime el número de filas del DataFrame.
`print(f'columnas = {num_columns}')`           # Imprime el número de columnas del DataFrame.
`print(df.head())`                             # Imprime las primeras 5 filas del DataFrame.
`print(df.head(8))`                            # Imprime las primeras 8 filas del DataFrame.
`print(df.sample(2))`                          # Imprime una muestra aleatoria de 2 filas del DataFrame.
`print(df.tail())`                             # Imprime las últimas 5 filas del DataFrame.
`print(df.columns)`                            # Imprime los nombres de las columnas del DataFrame.
_Series (columnas)_
`series_priced = df['Quantity']`               # Extrae la columna 'Quantity' del DataFrame en una Serie.
`print(series_priced)`                         # Imprime la Serie 'Quantity'.
`print(series_priced[1])`                      # Imprime el segundo elemento de la Serie 'Quantity'.
_Valores estadísticos_
`summary = df.describe()`                      # Obtiene un resumen estadístico de las columnas numéricas del DataFrame.
`mean = series_priced.mean()`                  # Calcula la media de los datos en la Serie 'Quantity'.
`mediana = series_priced.median()`             # Calcula la mediana de los datos en la Serie 'Quantity'.
`suma = series_priced.sum()`                   # Calcula la suma total de los datos en la Serie 'Quantity'.
`count = series_priced.count()`                # Cuenta el número de elementos no nulos en la Serie 'Quantity'.


