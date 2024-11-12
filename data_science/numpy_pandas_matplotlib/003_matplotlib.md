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



