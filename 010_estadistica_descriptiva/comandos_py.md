# Estadisticas descriptiva

## Data frame
`df = pd.read_csv('document.csv')`  `read_csv` carga datos desde un archivo CSV. Recuerda que pd viene de import pandas as pd
`df.dtpyes`                          Atributo que devuelve los tipos de datos las columnas del df
`df.describe()`                      función para obtener un resumen estadístico de las columnas numéricas del df

_Valores estadísticos_
`df.['columna'].mean()`              media de la columna seleccionada
`df.['columna'].median()`            mediana de la columna seleccionada
`df.['columna'].plot.hist(bins=20)`  gráfica de nu histograma, `bins=20` significa que el histograma será de 20 barras, no olvidar ejecutar `plt.show()` ni importar `matplotlib.pyplot`
