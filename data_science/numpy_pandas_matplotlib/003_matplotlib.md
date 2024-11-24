# Matplotlib
_Gráfico de línea_
`month = np.array(['E', 'F', 'M', 'A', 'Ma'])`                # Define un array con abreviaturas de los meses.
`sales = np.array([20, 25, 30, 28, 35])`                     # Define un array con las ventas mensuales en miles de unidades.
`plt.figure(figsize=(8, 6))`                                 # Crea una figura con dimensiones de 8x6 pulgadas.
`plt.plot(month, sales, marker='o', color='blue')`           # Dibuja un gráfico de líneas con puntos marcados en azul para cada par de datos mes-ventas.
`plt.title('Ventas mensuales de un producto')`               # Establece el título del gráfico.
`plt.xlabel('Meses')`                                        # Establece la etiqueta del eje x como 'Meses'.
`plt.ylabel('Ventas en miles de unidades')`                  # Establece la etiqueta del eje y como 'Ventas en miles de unidades'.
`plt.show()`                                                 # Muestra el gráfico creado.

_Grafico de dispersión_ 
`hours = [2, 3, 4, 5, 6, 7, 8]`              # Define un array con las horas de estudio.
`exam = [55, 60, 65, 70, 75, 80, 85]`        # Define un array con los puntajes obtenidos en los exámenes.
`plt.scatter(hours, exam, color='green')`    # Dibuja un gráfico de dispersión con las horas en el eje x y los puntajes en el eje y, utilizando puntos verdes.
`plt.title('Relacion entre horas estudiadas y el puntaje en examenes')`  # Establece el título del gráfico.
`plt.xlabel('Horas')`                        # Establece la etiqueta del eje x como 'Horas'.
`plt.ylabel('Puntaje')`                      # Establece la etiqueta del eje y como 'Puntaje'.
`plt.show()`                                 # Muestra el gráfico creado.

_Personalización de gráficos_
`hours = [2, 3, 4, 5, 6, 7, 8]`                                  # Define un array con las horas de estudio.
`exam_scores_student_1 = [55, 60, 65, 70, 75, 80, 85]`           # Define un array con los puntajes obtenidos por el estudiante 1 en los exámenes.
`exam_scores_student_2 = [50, 58, 63, 69, 74, 78, 83]`           # Define un array con los puntajes obtenidos por el estudiante 2 en los exámenes.
`plt.plot(hours, exam_scores_student_2, marker='s', color='blue', linestyle='--', linewidth=2, label='Estudiante 2')`  # Dibuja un gráfico de líneas con puntos marcados en azul para cada par de datos hora-puntaje del estudiante 2.
`plt.plot(hours, exam_scores_student_1, marker='o', color='red', linestyle='--', linewidth=2, label='Estudiante 1')`  # Dibuja un gráfico de líneas con puntos marcados en rojo para cada par de datos hora-puntaje del estudiante 1.
`plt.title('Relacion entre horas estudiadas y el puntaje en examenes')`  # Establece el título del gráfico.
`plt.xlabel('Horas')`                                            # Establece la etiqueta del eje x como 'Horas'.
`plt.ylabel('Puntaje')`                                         # Establece la etiqueta del eje y como 'Puntaje'.
`plt.legend()`                                                  # Muestra una leyenda que identifica cada serie de datos.
`plt.show()`                                                    # Muestra el gráfico creado.

_Gráfico de barras_
_Verticales_
`categories = ['Producto A', 'Producto B', 'Producto C']`             # Define un array con los nombres de los productos.
`sales = [120, 150, 90]`                                             # Define un array con las ventas correspondientes a cada producto.
`plt.bar(categories, sales, color='skyblue', label='Ventas mensuales')` # Dibuja un gráfico de barras verticales donde cada barra representa las ventas de un producto específico.
`plt.annotate(
    'Máximo de ventas', 
    xy=('Producto B', 150), xytext=('Producto C', 160),
    arrowprops=dict(facecolor='black', shrink=0.05)
)`                                                                     # Añade una anotación en el gráfico de barras que señala el punto más alto de ventas para 'Producto B' con una flecha.
`plt.title('Ventas de productos en un mes')`                           # Establece el título del gráfico.
`plt.xlabel('Productos')`                                             # Establece la etiqueta del eje x como 'Productos'.
`plt.ylabel('Ventas')`                                                # Establece la etiqueta del eje y como 'Ventas'.
`plt.show()`                                                          # Muestra el gráfico creado.
_Horizontales_
`categories = ['Producto A', 'Producto B', 'Producto C']`             # Define un array con los nombres de los productos.
`sales = [120, 150, 90]`                                             # Define un array con las ventas correspondientes a cada producto.
`plt.barh(categories, sales, color='skyblue', label='Ventas mensuales')` # Dibuja un gráfico de barras horizontales donde cada barra representa las ventas de un producto específico.
`plt.title('Ventas de productos en un mes')`                           # Establece el título del gráfico.
`plt.ylabel('Productos')`                                             # Establece la etiqueta del eje y como 'Productos'.
`plt.xlabel('Ventas')`                                                # Establece la etiqueta del eje x como 'Ventas'.
`plt.show()`                                                          # Muestra el gráfico creado.

_Diagramas de pastel_
`products = ['Producto A', 'Producto B', 'Producto C']`               # Define un array con los nombres de los productos.
`market_share = [50, 35, 15]`                                         # Define un array con la participación de mercado de cada producto expresada en porcentajes.
`plt.pie(
    market_share,                      # Los valores que representan la participación de mercado de cada producto.
    labels=products,                   # Etiquetas que identifican cada segmento con el nombre del producto correspondiente.
    autopct='%1.1f%%',                 # Formato de los porcentajes mostrados en cada segmento del pastel, aquí se muestra con un decimal.
    startangle=140,                    # Ángulo de inicio del gráfico de pastel, determina desde qué punto del círculo comienza el primer segmento.
    colors=['gold', 'lightcoral', 'orange']  # Colores asignados a cada segmento del pastel, proporcionando una diferenciación visual entre ellos.
)`  
`plt.title('Participación de Mercado por Producto')`                  # Establece el título del gráfico.
`plt.axis('equal')`                                                   # Ajusta el aspecto del gráfico para que sea un círculo perfecto.
`plt.show()`                                                          # Muestra el gráfico.

_Histogramas_
`data = np.random.normal(170, 10, 200)`                   # Genera un array de 200 datos aleatorios que siguen una distribución normal con media 170 y desviación estándar 10.
`plt.hist(
    data,                        # Los datos que se utilizarán para generar el histograma.
    color='salmon',              # Establece el color de las barras del histograma como 'salmon'.
    bins=10,                     # Divide los datos en 10 intervalos (bins).
    edgecolor='black',           # Define el color del borde de las barras como negro.
    alpha=0.6                    # Establece la transparencia de las barras (0 completamente transparente, 1 opaco).
)`
`plt.title('distribucion de alturas')`                          # Define el título del histograma como 'distribución de alturas'.
`plt.xlabel('altura (cm)')`                                    # Etiqueta el eje x como 'altura (cm)'.
`plt.ylabel('densidad')`                                       # Etiqueta el eje y como 'densidad'.
`plt.show()`                                                   # Muestra el histograma creado.

_Bloxplot_
`np.random.seed(0)`                                # Fija una semilla para la generación de números aleatorios, asegurando que los resultados sean reproducibles.
`ages = [np.random.normal(35, 5, 200),`           # Genera 200 edades aleatorias para el grupo 1 siguiendo una distribución normal con media 35 y desviación estándar 5.
`        np.random.normal(40, 5, 200),`           # Genera 200 edades aleatorias para el grupo 2 con media 40 y desviación estándar 5.
`        np.random.normal(35, 5, 200)]`           # Genera 200 edades aleatorias para el grupo 3 con media 35 y desviación estándar 5.
`plt.boxplot(
    ages,                          # Los datos de edades para los grupos a graficar.
    patch_artist=True,             # Rellena las cajas con color para una mejor visualización.
    notch=False,                   # Crea cajas estándar sin muescas.
    vert=True,                     # Configura las cajas en orientación vertical.
    tick_labels=['Grupo 1', 'Grupo 2', 'Grupo 3']  # Etiquetas para identificar cada grupo en el gráfico.
)`                                  # Cierra el método de creación del boxplot.
`plt.title('Distribución de edades por grupo')`      # Establece el título del gráfico.
`plt.xlabel('Grupo')`                                # Etiqueta el eje x como 'Grupo'.
`plt.ylabel('Edad (años)')`                          # Etiqueta el eje y como 'Edad (años)'.
`plt.show()`                                         # Muestra el gráfico creado.
                                                  


_Series temporales_
`import numpy as np`                                           # Importa NumPy para generar y manipular arrays numéricos.
`from matplotlib.dates import DateFormatter, AutoDateLocator` # Importa herramientas para formatear y localizar fechas en los gráficos.
`import pandas as pd`                                          # Importa Pandas para manejar estructuras de datos como DataFrames.
`dates = pd.date_range(start='2023-01-01', periods=100)`      # Genera una serie de 100 fechas consecutivas a partir del 1 de enero de 2023.
`values = np.random.rand(100).cumsum()`         # Genera 100 valores aleatorios entre 0 y 1 con `np.random.rand(100)` y calcula la suma acumulativa con `.cumsum()`. 
                                               # Estos valores representan datos asociados a la serie de tiempo, simulando una tendencia acumulativa.
`data = pd.DataFrame({'Date': dates, 'Value': values})`       # Crea un DataFrame con columnas 'Date' (fechas) y 'Value' (valores acumulativos).

`fig, ax = plt.subplots(figsize=(12, 6))`                     # Crea una figura con dimensiones 12x6 pulgadas y un eje para graficar.
`ax.plot(data['Date'], data['Value'], color='green')`         # Grafica la serie de tiempo en el eje con fechas en el eje x y valores en el eje y.
`plt.xticks(rotation=45)`                                     # Rota las etiquetas del eje x 45 grados para mejorar la legibilidad.
`plt.title('Serie de tiempo con formato en las fechas')`      # Establece el título del gráfico.
`plt.xlabel('Date')`                                          # Etiqueta el eje x como 'Date'.
`plt.ylabel('Value')`                                         # Etiqueta el eje y como 'Value'.
`plt.show()`                                                  # Muestra el gráfico creado.
