# Resumen de Estadística Descriptiva con Python

_Carga y Exploración de Datos_
`import pandas as pd`                                       Importa la librería pandas para manipulación de datos.
`import numpy as np`                                        Importa la librería numpy para cálculos numéricos.
`import matplotlib.pyplot as plt`                           Importa pyplot para crear gráficos.
`import seaborn as sns`                                     Importa seaborn para gráficos estadísticos estilizados.
`df = pd.read_excel('archivo.xlsx')`                        Carga un archivo Excel en un DataFrame de pandas.
`display(df)`                                               Muestra el DataFrame en un formato legible (en notebooks).
`df.isna().any().any()`                                     Verifica si existe algún valor nulo en todo el DataFrame.
`df.columns`                                                Muestra los nombres de las columnas del DataFrame.

_Tablas de Frecuencias_
`df['col'].value_counts()`                                  Cuenta la frecuencia de valores únicos en una columna.
`serie.to_frame('Nombre')`                                  Convierte una Serie en un DataFrame con un nombre de columna específico.
`df.reset_index()`                                          Reinicia el índice, convirtiendo el índice actual en una columna.
`df['Frec_Rel'] = df['Frec_Abs'] / N * 100`                 Calcula la frecuencia relativa porcentual.
`df['Frec_Acum'] = df['Frec_Abs'].cumsum()`                 Calcula la frecuencia acumulada sumando progresivamente.
`pd.Categorical(col, categories=orden, ordered=True)`       Define un orden específico para variables categóricas ordinales.

_Regla de Sturges y Agrupamiento_
`k = int(round(1 + np.log2(N)))`                            Calcula el número de clases (k) usando la Regla de Sturges.
`pd.cut(df['col'], bins=k)`                                 Segmenta y ordena los valores de datos en 'bins' (intervalos).
`cats.value_counts(sort=False)`                             Cuenta valores en cada intervalo sin reordenar por frecuencia.

_Visualización de Datos_
`sns.barplot(data=df, x='x', y='y')`                        Crea un gráfico de barras usando seaborn.
`plt.pie(x, labels=l, autopct='%1.1f%%')`                   Crea un gráfico de pastel con porcentajes.
`plt.hist(df['col'], bins=k, edgecolor='black')`            Crea un histograma para visualizar la distribución de datos.
`plt.plot(x, y, marker='o')`                                Crea un gráfico de líneas (útil para polígonos de frecuencias y ojivas).
`sns.boxplot(y=df['col'])`                                  Crea un diagrama de caja (boxplot) para ver distribución y outliers.
`plt.grid(True)`                                            Añade una cuadrícula al gráfico para facilitar la lectura.
`plt.show()`                                                Muestra el gráfico construido.

_Medidas de Tendencia Central (Datos No Agrupados)_
`df['col'].mean()`                                          Calcula la media aritmética (promedio).
`df['col'].median()`                                        Calcula la mediana (valor central).
`df['col'].mode()`                                          Calcula la moda (valor más frecuente).

_Medidas de Tendencia Central (Datos Agrupados)_
`np.histogram(data, bins=k)`                                Calcula frecuencias y límites de intervalos para histogramas.
`puntos_medios = (lims[:-1] + lims[1:]) / 2`                Calcula la marca de clase (punto medio) de cada intervalo.
`promedio = np.sum(f * m) / N`                              Cálculo manual del promedio ponderado para datos agrupados.

_Medidas de Variabilidad_
`np.ptp(df['col'])`                                         Calcula el rango (peak-to-peak): máx - mín.
`np.std(df['col'])`                                         Calcula la desviación estándar poblacional.
`cv = (np.std(x) / np.mean(x)) * 100`                       Calcula el Coeficiente de Variación (manual).
