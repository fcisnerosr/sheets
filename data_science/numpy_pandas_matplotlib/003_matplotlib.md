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

