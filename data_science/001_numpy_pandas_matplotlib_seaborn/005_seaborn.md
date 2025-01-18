# Seaborn
_Introducción y carga de datos iniciales para todos los ejemplos de gráficas_
_Grafica de barras_
`data = pd.DataFrame({'Categoria': ['A', 'B', 'C'], 'Valor': [1, 3, 2]})` # Crea un DataFrame de ejemplo con columnas 'Categoria' y 'Valor'.
`plt.switch_backend('TkAgg')`                             # Configura Matplotlib para usar el backend TkAgg (interactivo)
`sns.set(style='dark',palette='dark',font_scale=1)`       # Establece el estilo del gráfico en modo oscuro, paleta de colores oscura y la escala de la fuente.
`sns.barplot(x='Categoria', y='Valor', data=data)`        # Crea un gráfico de barras con 'Categoria' en el eje x y 'Valor' en el eje y, utilizando el DataFrame 'data'.
`plt.show()`                                              # Muestra el gráfico creado.
![barplot](~/Documents/sheets/data_science/001_numpy_pandas_matplotlib_seaborn/graficas_seaborn/001_barplot.png)

_Carga de Dataset y Exportación a CSV_
`tip = sns.load_dataset('tips')`                         # Carga el dataset 'tips' de Seaborn en un DataFrame llamado 'tip'.
`tip.to_csv('tip.csv', index=False, encoding='utf-8')`   # Guarda el DataFrame 'tip' en un archivo CSV llamado 'tip.csv', sin el índice, y codificado en UTF-8.

_Gráficas de distribución_
`sns.displot(data=tip, x='total_bill',y='tip', hue='sex')`      # Crea un gráfico de distribución (histograma por defecto) donde: la variable 'total_bill' se representa en el eje x, la variable 'tip' en el eje y y los datos se segmentan por la variable 'sex', asignando colores distintos a cada categoría (hombres y mujeres).
`sns.displot(data=tip, x='total_bill',hue='sex', kind='kde',legend=False,palette='dark',alpha=0.5)`   # Crea un gráfico KDE (Estimación de Densidad Kernel) con 'total_bill' en el eje x, colores distintos para cada valor de 'sex', sin leyenda, paleta de colores oscura y una opacidad de 0.5.


_Histogramas_
`sns.histplot(data=tip, x='tip', bins=5, cumulative=True, hue='sex', stat='frequency')`  # Histograma acumulativo por género (frecuencia)
`sns.histplot(data=tip, x='tip', bins=15, cumulative=False, hue='sex', stat='probability')`  # Histograma normal con probabilidad
`sns.histplot(data=tip, x='tip', bins=15, cumulative=False, hue='sex', stat='percent')`  # Histograma en porcentaje
`sns.histplot(data=tip, x='tip', bins=15, cumulative=False, hue='sex', stat='percent', multiple='dodge')`  # Histogramas separados
`sns.histplot(data=tip, x='tip', bins=15, cumulative=False, hue='sex', stat='percent', multiple='stack')`  # Histogramas apilados
`sns.histplot(data=tip, x='tip', bins=15, cumulative=False, hue='sex', stat='percent', multiple='fill')`  # Histogramas normalizados (100%)
![barplot](~/Documents/sheets/data_science/001_numpy_pandas_matplotlib_seaborn/graficas_seaborn/002_scatter_plot.png)

_Estimación de Densidad de Kernel (KDE)_
`sns.kdeplot(data=tip, x='tip', hue='sex', cumulative=False, shade=True)`  # KDE normal con sombreado
`sns.kdeplot(data=tip, x='tip', hue='sex', cumulative=True, shade=False)`  # KDE acumulativo sin sombreado
![barplot](~/Documents/sheets/data_science/001_numpy_pandas_matplotlib_seaborn/graficas_seaborn/002_5_kde.png)

_Distribución acumulativa empírica ECDF = Empirical Comulative Distribution Function_
`sns.ecdfplot(data=tip, x='tip', hue='sex')`  # ECDF normal
`sns.ecdfplot(data=tip, x='tip', hue='sex', stat='count')`  # ECDF con conteo
![barplot](~/Documents/sheets/data_science/001_numpy_pandas_matplotlib_seaborn/graficas_seaborn/004_stacked_histogram.png)

_Distribuciones combinadas en una sola gráfica_
`sns.displot(data=tip, x='tip', hue='sex', kind='kde')`  # KDE con displot
`sns.displot(data=tip, x='tip', hue='sex', kind='hist', multiple='stack')`  # Histograma apilado con displot
![barplot](~/Documents/sheets/data_science/001_numpy_pandas_matplotlib_seaborn/graficas_seaborn/004_stacked_histogram.png)

_Conteo de categorías_
`sns.countplot(data=tip, x='day', hue='sex')`  # Conteo de datos por día y género (horizontal)
![barplot](~/Documents/sheets/data_science/001_numpy_pandas_matplotlib_seaborn/graficas_seaborn/007_2_categorical_count_horizontal.png)
`sns.countplot(data=tip, y='day', hue='sex')`  # Conteo de datos por día y género (vertical)
![barplot](~/Documents/sheets/data_science/001_numpy_pandas_matplotlib_seaborn/graficas_seaborn/007_3_categorical_count_vertical.png)

`sns.stripplot(data=tip, x='day', hue='sex')`  # Stripplot sin valores numéricos en Y
`sns.stripplot(data=tip, x='day', y='total_bill', hue='sex')`  # Stripplot con total_bill en Y
`sns.stripplot(data=tip, x='day', y='total_bill', hue='sex', dodge=True)`  # Stripplot con separación de puntos por categoría
![barplot](~/Documents/sheets/data_science/001_numpy_pandas_matplotlib_seaborn/graficas_seaborn/006_categorical_scatter_plot.png)

_Swarmplot y Boxplot_
`sns.swarmplot(data=tip, x='day', y='total_bill', hue='sex', dodge=True)`  # Swarmplot con separación por categoría
`sns.boxplot(data=tip, x='day', y='total_bill', hue='sex', dodge=True)`  # Boxplot con separación por categoría
![barplot](~/Documents/sheets/data_science/001_numpy_pandas_matplotlib_seaborn/graficas_seaborn/008_2_bloxplot.png)

_Combinación de Swarmplot y Boxplot_
`sns.swarmplot(data=tip, x='day', y='total_bill', hue='sex', dodge=True, color='0', marker='<')`  # Swarmplot con marcadores
`sns.boxplot(data=tip, x='day', y='total_bill', hue='sex', dodge=True)`  # Boxplot sobrepuesto
`plt.show()`
![barplot](~/Documents/sheets/data_science/001_numpy_pandas_matplotlib_seaborn/graficas_seaborn/008_boxplot_and_swarmplot.png)

_Violin plot_
`sns.violinplot(data=tip, x='day', y='total_bill', hue='sex', split=True, dodge=True, palette='pastel')`  # Violin plot con división de categorías
![barplot](~/Documents/sheets/data_science/001_numpy_pandas_matplotlib_seaborn/graficas_seaborn/009_violin.png)

_Catplot para múltiples tipos de visualización: (Categorical Plot) es una función que permite crear gráficos para visualizar la distribución de datos categóricos en distintas representaciones_
`sns.catplot(data=tip, x='day', y='total_bill', hue='sex', dodge=True, kind='box', col='time')`  # Catplot con Boxplot
`sns.catplot(data=tip, x='day', y='total_bill', hue='sex', dodge=True, kind='swarm', col='time')`  # Catplot con Swarmplot
![barplot](~/Documents/sheets/data_science/001_numpy_pandas_matplotlib_seaborn/graficas_seaborn/009_2_catplot_diferent_col.png)

_Gráfico de dispersión con estilos personalizados_
`plt.figure(figsize=(8,6))`                         # Define el tamaño de la figura  
`markers = {'Lunch':'D','Dinner':'s'}`              # Define los marcadores según el tipo de comida  
`sns.scatterplot(data=tip, x='total_bill', y='tip', hue='day', style='time', size='size', markers=markers)`  # Gráfico de dispersión con diferentes estilos  
`plt.legend(loc='center', bbox_to_anchor=(1.09,0.5))`  # Ajuste de la leyenda  
![barplot](~/Documents/sheets/data_science/001_numpy_pandas_matplotlib_seaborn/graficas_seaborn/013_two_variable_scatter.png)

_Gráfico de líneas_
`sns.lineplot(data=tip, x='total_bill', y='tip')`   # Gráfico de línea que muestra la relación entre total_bill y tip  
![barplot](~/Documents/sheets/data_science/001_numpy_pandas_matplotlib_seaborn/graficas_seaborn/013_2_grafic_line.png)

_Relplot con estilos personalizados: función para visualizar relaciones entre variables numéricas_
`markers = {'Lunch':'D','Dinner':'s'}`              # Definir marcadores para cada tipo de comida  
`sns.relplot(data=tip, x='total_bill', y='tip', hue='day', style='time', size='size', markers=markers, height=6, aspect=1.3)`  # Relplot con distintos estilos y tamaños  
![barplot](~/Documents/sheets/data_science/001_numpy_pandas_matplotlib_seaborn/graficas_seaborn/013_two_variable_scatter.png)

_Gráficos conjuntos (Jointplot): permite visualizar la relación entre dos variables numéricas, combinando un gráfico de dispersión con histogramas marginales en los ejes_
`sns.jointplot(data=tip, x='total_bill', y='tip')`  # Gráfico conjunto básico (scatter + histogramas)  
`sns.jointplot(data=tip, x='total_bill', y='tip', hue='sex')`  # Jointplot con diferenciación de género  
`sns.jointplot(data=tip, x='total_bill', y='tip', hue='sex', kind='hist')`  # Jointplot con histograma  
`sns.jointplot(data=tip, x='total_bill', y='tip', hue='sex', kind='kde')`  # Jointplot con KDE  
`sns.jointplot(data=tip, x='total_bill', y='tip', hue='sex', kind='hist', marginal_ticks=True, marginal_kws=dict(bins=25, fill=False, multiple='dodge'))`  # Jointplot con opciones adicionales para los márgenes  
![barplot](~/Documents/sheets/data_science/001_numpy_pandas_matplotlib_seaborn/graficas_seaborn/014_distribution_joint_view.png)

_Pairplot: Relaciones entre variables numéricas_
`sns.pairplot(data=tip)`  # Pairplot básico para analizar relaciones entre todas las variables numéricas  
`sns.pairplot(data=tip, hue='sex', corner=True, kind='scatter')`  # Pairplot con diferenciación por género y solo la parte inferior de la matriz  
![barplot](~/Documents/sheets/data_science/001_numpy_pandas_matplotlib_seaborn/graficas_seaborn/015_data_relationship_matrix.png)
