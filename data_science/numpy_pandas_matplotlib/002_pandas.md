# Pandas

## Dimensiones y operaciones en Pandas

path = 'Online_Retail.csv'                                  # Carga la ruta al archivo CSV.
df = pd.read_csv(path, encoding='windows-1252')             # Carga un DataFrame desde un archivo CSV con codificación específica.
# data_excel = pd.read_excel(path)                          # Carga un DataFrame desde un archivo Excel (comentado).
# data_json = pd.read_json(path)                            # Carga un DataFrame desde un archivo JSON (comentado).

array = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])         # Declara una matriz de 3 filas y 3 columnas usando NumPy.
dt_from_array = pd.DataFrame(array, columns=['A', 'B', 'C'])  # Crea un DataFrame a partir de un array NumPy con columnas etiquetadas A, B, y C.

list = [[1, 'Jhon', 22], [2, 'Anna', 24]]                   # Lista de listas, cada sublista contiene datos de una persona.
df_from_list = pd.DataFrame(list, columns=['ID', 'Name', 'Age'])  # Crea un DataFrame a partir de una lista de listas con columnas etiquetadas ID, Name y Age.

dicc = [{'ID': 1, 'Name': 'Jhon', 'Age': 22}, {'ID': 2, 'Name': 'Ana', 'Age': 24}]  # Crea una lista de diccionarios, cada diccionario contiene datos de una persona.
df_from_dicc = pd.DataFrame(dicc, columns=['ID', 'Name', 'Age'])  # Crea un DataFrame a partir de una lista de diccionarios con columnas etiquetadas ID, Name y Age.
