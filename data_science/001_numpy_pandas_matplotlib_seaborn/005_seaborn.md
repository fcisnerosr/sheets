# Seaborn
_Grafica de barras_
`data = pd.DataFrame({'Categoria': ['A', 'B', 'C'], 'Valor': [1, 3, 2]})` # Crea un DataFrame de ejemplo con columnas 'Categoria' y 'Valor'.
`plt.switch_backend('TkAgg')`                             # Configura Matplotlib para usar el backend TkAgg (interactivo)
                                                        # (o plt.switch_backend('QtAgg') si tienes Qt).
`sns.set(style='dark',palette='dark',font_scale=1)`       # Establece el estilo del gráfico en modo oscuro, paleta de colores oscura y la escala de la fuente.
`sns.barplot(x='Categoria', y='Valor', data=data)`        # Crea un gráfico de barras con 'Categoria' en el eje x y 'Valor' en el eje y, utilizando el DataFrame 'data'.
`plt.show()`                                              # Muestra el gráfico creado.

_Carga de Dataset y Exportación a CSV_
`tip = sns.load_dataset('tips')`                         # Carga el dataset 'tips' de Seaborn en un DataFrame llamado 'tip'.
`tip.to_csv('tip.csv', index=False, encoding='utf-8')`   # Guarda el DataFrame 'tip' en un archivo CSV llamado 'tip.csv', sin el índice, y codificado en UTF-8.

_Gráficas de distribución_
`sns.displot(data=tip, x='total_bill',y='tip', hue='sex')`      # Crea un gráfico de distribución (histograma por defecto) donde: la variable 'total_bill' se representa en el eje x, la variable 'tip' en el eje y y los datos se segmentan por la variable 'sex', asignando colores distintos a cada categoría (hombres y mujeres).
`sns.displot(data=tip, x='total_bill',hue='sex', kind='kde',legend=False,palette='dark',alpha=0.5)`   # Crea un gráfico KDE (Estimación de Densidad Kernel) con 'total_bill' en el eje x, colores distintos para cada valor de 'sex', sin leyenda, paleta de colores oscura y una opacidad de 0.5.
`plt.show()`                                              # Muestra los gráficos creados (uno a la vez).
