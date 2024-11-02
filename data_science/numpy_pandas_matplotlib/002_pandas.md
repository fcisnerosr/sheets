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

_Manejo de grupos (groupby)_
`country_cont = df['Country'].value_counts()`                 # Cuenta la frecuencia de apariciones de cada país en el DataFrame.
`country_group = df.groupby('Country')['Quantity'].sum()`     # Suma las cantidades por país agrupando por 'Country'.
`country_stats = df.groupby('Country')['UnitPrice'].agg(['mean','sum'])` # Agrupa por 'Country', calcula y almacena la media y suma de 'UnitPrice' para cada país.
`country_stock_group = df.groupby(['Country','StockCode'])['Quantity'].sum()` # Suma las cantidades por país y código de stock.
`def total_revenue(group):`                                   # Define una función para calcular el ingreso total por grupo.
    `return (group['Quantity'] * group['UnitPrice']).sum()`   # Calcula ingreso multiplicando cantidad por precio y sumando los resultados.
`revenue_per_country = df.groupby(['Country', 'StockCode']).apply(total_revenue)` # Calcula la ganancia total por cada producto en cada país aplicando la función 'total_revenue'.

_Filtrado de datos con condicionales_
_Manejo de fechas y limpieza de datos_
`df['InvoiceDate'] = pd.to_datetime(df['InvoiceDate'])`            # Convierte 'InvoiceDate' a datetime para manejar datos de tiempo.
`df.dropna(subset=['CustomerID', 'InvoiceDate'], inplace=True)`   # Elimina filas con datos faltantes en 'CustomerID' e 'InvoiceDate', modificando df directamente.
_Creación y análisis de nuevas columnas_
`df['TotalPrice'] = df['Quantity'] * df['UnitPrice']`             # Crea 'TotalPrice' multiplicando 'Quantity' por 'UnitPrice'.
`uk_sales = df[df['Country'] == 'United Kingdom']`                # Filtra y almacena ventas del Reino Unido en 'uk_sales'.
`pd.set_option('display.max_columns', None)`                      # Configura la visualización para mostrar todas las columnas.
`high_quantity_sales = df[df['Quantity'] > 10]`                   # Filtra y almacena ventas con 'Quantity' mayor a 10 en 'high_quantity_sales'.
`uk_high_quantity_sales = df[(df['Country'] == 'United Kingdom') & (df['Quantity'] > 100)]` # Filtra ventas en el Reino Unido con 'Quantity' mayor a 100.
_Filtrado de datos por fecha_
`sales_2011 = df[df['InvoiceDate'].dt.year == 2011]`              # Filtra y almacena ventas del año 2011 en 'sales_2011'.
`print(sales_2011)`                                               # Imprime las ventas del año 2011.
`sales_dec_2010 = df[(df['InvoiceDate'].dt.year == 2010) & (df['InvoiceDate'].dt.month == 12)]` # Filtra y almacena ventas de diciembre de 2010.
`print(sales_dec_2010)`                                           # Imprime las ventas de diciembre de 2010.

_Creación de Pivot Table_
`pivot_table = pd.pivot_table(df, values='Quantity', index='Country',
columns='StockCode', aggfunc='sum')`  # Crea una tabla pivote que suma las cantidades ('Quantity') para cada combinación de país ('Country') y código de stock ('StockCode').
`df_stacked = df.stack()`             # Convierte el DataFrame en una Serie de Pandas donde las columnas se transforman en índices de segundo nivel, apilando los datos verticalmente.
`df_unstacked = df_stacked.unstack()` # Deshace la operación de stacking, regresando los datos apilados a su formato original de DataFrame con múltiples niveles de índice convertidos de nuevo a columnas.

_merge, concat y join_
`inner_merged = pd.merge(df1, df2, on='key', how='inner')`   # Realiza una fusión interna entre df1 y df2 utilizando 'key' como la columna de unión. Incluye solo filas que tienen claves coincidentes en ambos DataFrames.
`outer_merged = pd.merge(df1, df2, on='key', how='outer')`   # Realiza una fusión externa completa entre df1 y df2 utilizando 'key' como la columna de unión. Incluye todas las filas de ambos DataFrames, llenando con NaN donde no hay coincidencias.
`left_merged = pd.merge(df1, df2, on='key', how='left')`     # Realiza una fusión izquierda entre df1 y df2 utilizando 'key' como la columna de unión. Mantiene todas las filas de df1, añadiendo información de df2 donde hay coincidencias.
`right_merged = pd.merge(df1, df2, on='key', how='right')`   # Realiza una fusión derecha entre df1 y df2 utilizando 'key' como la columna de unión. Mantiene todas las filas de df2, añadiendo información de df1 donde hay coincidencias.
`inner_merged = pd.merge(df1, df2, on='key', how='inner')`     # Realiza una fusión interna entre df1 y df2 utilizando 'key' como la columna de unión. Incluye solo filas que tienen claves coincidentes en ambos DataFrames.
`outer_merged = pd.merge(df1, df2, on='key', how='outer')`     # Realiza una fusión externa completa entre df1 y df2 utilizando 'key' como la columna de unión. Incluye todas las filas de ambos DataFrames, llenando con NaN donde no hay coincidencias.
`left_merged = pd.merge(df1, df2, on='key', how='left')`       # Realiza una fusión izquierda entre df1 y df2 utilizando 'key' como la columna de unión. Mantiene todas las filas de df1, añadiendo información de df2 donde hay coincidencias.
`right_merged = pd.merge(df1, df2, on='key', how='right')`     # Realiza una fusión derecha entre df1 y df2 utilizando 'key' como la columna de unión. Mantiene todas las filas de df2, añadiendo información de df1 donde hay coincidencias.
`vertical_concat = pd.concat([df3, df4])`                      # Concatena df3 y df4 verticalmente, apilando df4 debajo de df3 y alineando por columnas.
`horizontal_concat = pd.concat([df3, df4], axis=1)`            # Concatena df3 y df4 horizontalmente, extendiendo las columnas de df3 con las de df4, alineando por índices.
`joined = df5.join(df6, how='inner')`  # Combina df5 y df6 basándose en la coincidencia de sus índices. Solo se incluyen en el resultado final aquellas filas de ambos DataFrames que compartan el mismo índice.

_Series temporales_
`df['InvoiceDate'] = pd.to_datetime(df['InvoiceDate'])`               # Convierte la columna 'InvoiceDate' a tipo datetime, permitiendo operaciones específicas de fecha y hora.
`df.dropna(subset=['InvoiceDate'], inplace=True)`                     # Elimina filas donde 'InvoiceDate' es NaN, modificando el DataFrame original.
`df.set_index('InvoiceDate', inplace=True)`                           # Establece 'InvoiceDate' como el índice del DataFrame, modificando el DataFrame original.
`df['Year'] = df.index.year`                                          # Crea una columna 'Year' extrayendo el año de cada índice de fecha.
`df['Month'] = df.index.month`                                        # Crea una columna 'Month' extrayendo el mes de cada índice de fecha.
`df['Day'] = df.index.day`                                            # Crea una columna 'Day' extrayendo el día de cada índice de fecha.
`df['Weekday'] = df.index.weekday`                                    # Crea una columna 'Weekday' extrayendo el día de la semana de cada índice de fecha (lunes=0, domingo=6).
`df['Hour'] = df.index.hour`                                          # Crea una columna 'Hour' extrayendo la hora de cada índice de fecha.
`df = df.drop(columns=['Weekdy'])`                                    # Elimina la columna 'Weekdy' que fue erróneamente nombrada o ya no se necesita.
`df_2011 = df.loc['2011']`                                            # Filtra el DataFrame para incluir solo los datos del año 2011.
`df_2011_dec = df.loc['2011-12']`                                     # Filtra el DataFrame para incluir solo los datos de diciembre de 2011.
`df_dec_range = df.loc['2010-12-01':'2010-12-02']`                    # Filtra el DataFrame para incluir datos desde el 1 de diciembre de 2010 hasta el 2 de diciembre de 2010.
`date_range_new = pd.date_range(start='2024-01-01', end='2024-12-31', freq='D')`  # Crea un rango de fechas diarias desde el 1 de enero de 2024 hasta el 31 de diciembre de 2024.
`df_dates = pd.DataFrame(date_range_new, columns=['Date'])`           # Crea un DataFrame a partir del rango de fechas, con una columna 'Date' que contiene todas las fechas.

