 _Carga de datos_
`data = pd.read_csv(file_path, encoding='windows-1252')`       # Carga un DataFrame desde un archivo CSV con codificación específica.  
`pd.set_option('display.max_columns', None)`                   # Configura Pandas para mostrar todas las columnas al imprimir el DataFrame.  
`print(data.info())`                                           # Muestra información general del DataFrame, como tipos de datos y valores no nulos.  
`print(data.head())`                                           # Imprime las primeras 5 filas del DataFrame.  
`print(data.describe())`                                       # Muestra estadísticas descriptivas de las columnas numéricas.  
`print(data.isnull().sum())`                                   # Cuenta los valores nulos por columna.  
`print(data.duplicated().sum())`                               # Cuenta el número total de filas duplicadas en el DataFrame.  

 _Análisis de valores únicos_
`unique_values = {col: data[col].unique() for col in data.columns}` # Crea un diccionario con los valores #únicos de cada columna.  
                                                                    # `data.columns` devuelve los nombres de todas las columnas en el DataFrame en forma de lista
`for col, values in unique_values.items():`                         # Itera sobre cada columna y sus valores únicos.  
    `print(f'Columna: {col}')`                                # Imprime el nombre de la columna.  
    `print(f'Numero de valores: {len(values)}')`              # Imprime el número de valores únicos en la columna.  
    `print(f'Valores únicos: {values[:10]}')`                 # Imprime los primeros 10 valores únicos de la columna.  
    `print('-'*100)`                                          # Imprime una línea divisoria para mejorar la visualización.  

 _Limpieza de datos_
`data_cleaned = data.drop_duplicates()`                            # Elimina filas duplicadas del DataFrame.  
`data_cleaned = data_cleaned.dropna(subset=['CustomerID'])`        # Elimina filas donde la columna 'CustomerID' tiene valores nulos.  
`print(data_cleaned)`                                              # Imprime el DataFrame limpio.  
`print(data_cleaned.isnull().sum())`                               # Verifica que no existan valores nulos en las columnas seleccionadas.  
`print(data_cleaned.duplicated().sum())`                           # Verifica que no existan filas duplicadas en el DataFrame limpio.  

 _Creación de columnas_
`print(data_cleaned.head())`                                                   # Muestra las primeras 5 filas del DataFrame limpio.  
`data_cleaned['TotalAmount'] = data_cleaned['Quantity'] * data_cleaned['UnitPrice']`  # Crea una nueva columna 'TotalAmount' que multiplica 'Quantity' por 'UnitPrice'.  
`print(data_cleaned.head())`                                                   # Imprime el DataFrame con la nueva columna.  
`data_cleaned['InvoiceDate'] = pd.to_datetime(data_cleaned['InvoiceDate'])`    # Convierte la columna 'InvoiceDate' al formato de fecha.  
`print(data_cleaned.head())`                                                   # Imprime las primeras 5 filas con 'InvoiceDate' en formato fecha.  
`print(data_cleaned.info())`                                                   # Muestra la información del DataFrame limpio y actualizado.  

 _Extracción de información temporal_
`data_cleaned['Year'] = data_cleaned['InvoiceDate'].dt.year`     # Crea una columna 'Year' con el año extraído de 'InvoiceDate'.  
`data_cleaned['Month'] = data_cleaned['InvoiceDate'].dt.month`   # Crea una columna 'Month' con el mes extraído de 'InvoiceDate'.  
`print(data_cleaned.head())`                                     # Imprime las primeras 5 filas del DataFrame con las nuevas columnas de fecha.  

 _Agrupación de ventas por año_
`sales_by_year = data_cleaned.groupby('Year')['TotalAmount'].sum()`  # Agrupa las ventas totales ('TotalAmount') por año ('Year').  
`print(sales_by_year)`                                              # Imprime las ventas totales por año.  

 _Creación de columna por semestre_
`data_cleaned['Semester'] = data_cleaned['Month'].apply(lambda x: 1 if x <= 6 else 2)`  # Crea la columna 'Semester': 1er semestre si el mes ≤ 6, de lo contrario 2do semestre.  

 _Agrupación de ventas por año y semestre_
`sales_by_semester = data_cleaned.groupby(['Year', 'Semester'])['TotalAmount'].sum()`  # Agrupa las ventas por año y semestre.  
`print(sales_by_semester)`                                                             # Imprime las ventas agrupadas por año y semestre.  
