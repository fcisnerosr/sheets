# Estadistica
_Objetivo: Mediante valores puntuales o gráficas la representación significativa de un conjunto o muestra de datos_luz
### Medidas de tendencia centra y de dispersión
Rango		=MAX(C10:C100)-MIN(C10:C100)			    _Rango_
IQR		    =CUARTIL(C10:C100,3) - CUARTIL(C10:C100,1)	_Índice intercuartil_
VAA         = Q3 + 1.5*(IQR)    _Valores atípios altos_
VAB         = Q1 - 1.5*(IQR)    _Valores atípicos bajos_

### Media, varianza, esviación estandar
Números aleatorios			        =ALEATORIO()
Varianza poblacional			    =VAR.P(D1:D100)
Varianza muestral			        =VAR.S(D1:D100)
Desviación estandar poblacional		=RAIZ(VAR.P)
Desviación estandar muestral        =RAIZ(VAR.S)
        	    	
### Histogramas y curvas de densidad
_Histograma_
* Es necesario seleecionar todos los puntos y no intervalos
* En las opciones de eje orizontal se pueden modificar el ancho y el numero de ranchos para ver qué tan suavizada la quiere uno
* En la sección de "Número" también puede uno acceder al formato del eje horizontal
_Polígonos de frecuencia:_ escoger la opción del tipo de gráfica de "líneas con marcadores"
_Curva de densidad:_ no escoger "dispersión", si no "líneas 2D" para poder asginar el gráfico horizontal

### Probabilidad
_Probabilidad simple o teórica_
$$
P(A) = \frac{numero de resultados favorables a A}{numero total de resultados posibles}
$$
_Probabilidad experimental_
$$
P(A) = \frac{numero de veces que ocurre el elemento en A}{numero total de intentos}
$$
_Regla de suma_     

