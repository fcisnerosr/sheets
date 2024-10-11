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

_Seleccionar datos de un dataframe_
_iloc (index location)_
`first_row = df.iloc[1]`               # Selecciona la fila en el índice 1 (segunda fila) usando posiciones numéricas.
`first_five_rows = df.iloc[:5]`        # Selecciona las primeras 5 filas (desde la posición 0 a la 4).
`six_to_eigth_rows = df.iloc[6:8]`     # Selecciona las filas en las posiciones 6 y 7 (no incluye la 8).
`subset = df.iloc[:3,:2]`              # Selecciona las primeras 3 filas y las primeras 2 columnas.
`value = df.iloc[0,4]`                 # Selecciona el valor de la fila en la posición 0 y columna en la posición 4.
_loc (location)_
`row_index_three = df.loc[3]`          # Selecciona la fila con la etiqueta (índice) 3.
`row_index_zero_to_four = df.loc[:2]`  # Selecciona todas las filas desde la etiqueta 0 hasta la etiqueta 2 (incluidas).
`col_stock_date_unitprice_0 = df.loc[0,['Stockcode','Invoicedate','Unitprice']]`  # Selecciona la fila 0 y las columnas 'Stockcode', 'Invoicedate', y 'Unitprice'.
`col_stock_date_unitprice_02 = df.loc[0:2,['Stockcode','Invoicedate','Unitprice']]` # Selecciona las filas 0 a 2 (incluidas) y las columnas 'Stockcode', 'Invoicedate', y 'Unitprice'.
`france_unitprice = df.loc[df['Country']=='France',['Country','UnitPrice']]`            # Selecciona todas las filas donde 'Country' es 'France' y las columnas 'Country' y 'UnitPrice'.
`france_unitprice_3 = df.loc[df['Country']=='France',['Country','UnitPrice']].head(3)`  # Selecciona las primeras 3 filas del subconjunto donde 'Country' es 'France' y las columnas 'Country' y 'UnitPrice'.
`france_unitprice_3 = df.loc[df['Country']=='France',['Country','UnitPrice']].tail(3)`  # Selecciona las últimas 3 filas del subconjunto donde 'Country' es 'France' y las columnas 'Country' y 'UnitPrice'.

_Manejo de datos faltantes_
`missing_data = df.isna()`                      # Crea un DataFrame booleano que indica la presencia de datos faltantes.
`missing_data_count = df.isna().sum()`          # Calcula la cantidad de datos faltantes por columna en el DataFrame.
`no_missing_rows = df.dropna()`                 # Crea un nuevo DataFrame eliminando filas que contienen cualquier dato faltante.
`no_missing_columnas = df.dropna(axis=1)`       # Crea un nuevo DataFrame eliminando columnas que contienen cualquier dato faltante.
`df_filled_zeros = df.fillna(0)`                # Rellena los datos faltantes en el DataFrame con ceros.
`df_filled_zeros_count = df_filled_zeros.isna().sum()` # Verifica y cuenta los datos faltantes en el DataFrame rellenado.
`mean_unit_price = df['UnitPrice'].mean()`      # Calcula la media de los valores en la columna 'unitprice'.
`df_filled_mean = df['UnitPrice'].fillna(mean_unit_price)` # Rellena los datos faltantes en 'unitprice' con su media.

_Creación y manipulación de columnas_
`df['totalprice'] = df['quantity'] * df['unitprice']`              # Calcula el precio total multiplicando cantidad por precio unitario.
`df['highvalue'] = df['totalprice'] > 16`                          # Crea una columna booleana que indica si el total de precios es mayor a 16.
`print(df.info())`                                                 # Imprime información del DataFrame, incluyendo el tipo de datos de cada columna.
`df['invoicedate'] = pd.to_datetime(df['invoicedate'], format='%m/%d/%y %H:%M')` # Convierte 'invoicedate' a datetime con formato específico.
`df['discountedprice'] = df['unitprice'].apply(lambda x: x * 0.9)` # Aplica un descuento del 10% al precio unitario y guarda el resultado en una nueva columna.
`def categorize_price(price):`                                      # Define una función para categorizar precios.
    `if price > 50:`                                               
        `return 'high'`                                            
    `elif price < 20:`                                             
        `return 'medium'`                                          
    `else:`                                                        
        `return 'low'`                                             
`df['pricecategory'] = df['unitprice'].apply(categorize_price)`    # Aplica la función categorize_price a la columna 'unitprice' y almacena los resultados en 'pricecategory'.
