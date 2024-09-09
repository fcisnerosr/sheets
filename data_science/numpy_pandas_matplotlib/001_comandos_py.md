# Numpy

_Dimensiones_


_Objeto array_
`array = np.array([[1,2,3],[4,5,6]])`             Declara un array de 2 dimensiones.
`array.ndim`                                      Devuelve el número de dimensiones del array.
`array.shape`                                     Devuelve las dimensiones del array en términos de filas y columnas.
`array.dtype`                                     Devuelve el tipo de elementos que contiene el array.
`z = np.array([3], dtype=np.uint8)`               Declara un array de 1x1 y lo convierte a un entero sin signo de 8 bits.
`double_array = np.array([1,2,3],dtype='d')`      Declara un array de 1x3 con elementos de punto flotante de doble precisión.
`z = z.astype(np.float64)`                        Convierte un array a un tipo de dato de punto flotante de doble precisión.
 
_Tipos de datos en Numpy y su nomenclatura_
`int8`   o `i1`       Entero con signo de 8 bits. Rango: -128 a 127.
`uint8`  o `u1`       Entero sin signo de 8 bits. Rango: 0 a 255.
`int16`  o `i2`       Entero con signo de 16 bits. Rango: -32,768 a 32,767.
`uint16` o `u2`       Entero sin signo de 16 bits. Rango: 0 a 65,535.
`int32`  o `i4`       Entero con signo de 32 bits. Rango: -2,147,483,648 a 2,147,483,647.
`uint32` o `u4`       Entero sin signo de 32 bits. Rango: 0 a 4,294,967,295.
`int64`  o `i8`       Entero con signo de 64 bits. Rango: muy grande.
`uint64` o `u8`       Entero sin signo de 64 bits. Rango: muy grande.

`float16`  o `f2`     Número de punto flotante de 16 bits.
`float32`  o `f4`     Número de punto flotante de 32 bits (precisión simple, también conocido como `single`).
`float64`  o `f8`     Número de punto flotante de 64 bits (precisión doble, también conocido como `double`).

`complex64`  o `c8`   Número complejo compuesto por dos `float32` (32 bits para la parte real y 32 bits para la parte imaginaria).
`complex128` o `c16`  Número complejo compuesto por dos `float64` (64 bits para la parte real y 64 bits para la parte imaginaria).

`bool`       o `?`    Booleano que puede ser `True` o `False`.

`string_`    o `S`    Secuencia de bytes. Puedes especificar la longitud, por ejemplo, `S10` para un string de hasta 10 caracteres.
`unicode_`   o `U`    String Unicode. Puedes especificar la longitud, por ejemplo, `U10`.

`object_`    o `O`    Tipo de dato genérico que puede almacenar cualquier objeto de Python. Es menos eficiente que los tipos anteriores.

_Aplicaciones estadisticas_
array = np.array([[1,2,3],[4,5,6]])
`sum = np.sum(array)`            Suma todos los elementos de un array.
`mean = np.mean(array)`          Calcula la media de todos los elementos de un array.
`std = np.std(array)`            Calcula la desviación estándar de todos los elementos de un array.

_Indexación y Slicing_
- Indexación
`array = np.array([10, 20, 30, 40, 50])`          Declara un array unidimensional con los elementos 10, 20, 30, 40, y 50.
`print(array[0:2+1])`                             Imprime los primeros tres elementos del array (índices 0 a 2).
`print(array[-1])`                                Imprime el último elemento del array.
`bool_index = array > 25`                         Crea un array booleano donde cada elemento indica si es mayor que 25.
`print(bool_index)`                               Imprime el array booleano resultante.
`print(type(bool_index))`                         Imprime el tipo de dato del array booleano (`numpy.ndarray`).
- Slicing
`array = np.random.randint(1,10,size=(3,3))`      Crea una matriz 3x3 con enteros aleatorios entre 1 y 9.
`print(array[0,1])`                               Imprime el elemento en la fila 0, columna 1 de la matriz.
`print(array[:3,:2])`                             Imprime los primeros 3 elementos de cada una de las primeras 2 columnas.

_Broadcasting, operadores lógicos y concatenaciones_
- Broadcasting
Aunque dos conjuntos no tengan las mismas dimensiones, es posible hacer operaciones entre ellos.
`prices = np.random.randint(100,500,size=(3,3))`      Matriz de números aleatorios entre 100 y 500 de tamaño 3x3.
`discount = np.array([10, 20, 30])`                   Declara un vector de 1x3.
`new_prices = prices + discount`                      Realiza una operación de tensores, sumando un vector a una matriz aunque no tengan la misma dimensión.

- Operadores lógicos
`array = np.array([1, 2, 3, 4, 5])`                   Declara un array unidimensional con los elementos 1, 2, 3, 4 y 5.
`print(np.all(array > 3))`                            Imprime si todos los elementos del array son mayores que 3.
`print(np.any(array > 3))`                            Imprime si al menos un elemento del array es mayor que 3.

- Concatenaciones
`array_a = np.array([1, 2, 3])`                       Declara un array unidimensional con los elementos 1, 2 y 3.
`array_b = np.array([4, 5])`                          Declara otro array unidimensional con los elementos 4 y 5.
`concatenated = np.concatenate((array_a, array_b))`   Concatena los arrays `array_a` y `array_b` en un solo array.
`satecked_v = np.vstack((array_a, array_b))`          Concatena verticalmente los arrays `array_a` y `array_b`.
`stacked_h = np.hstack((array_a, array_b))`           Concatena horizontalmente los arrays `array_a` y `array_b`.
`array_c = np.arange(1, 15+1)`                        Genera un vector fila con valores desde 1 hasta 15.
`split_array = np.split(array_c, 5)`                  Divide el array `array_c` en 5 partes, creando arrays más pequeños de tamaño `len(array_c)/5`.

_Elementos únicos y sus conteos_
`np.unique(survey_responses)`                            Del array `survey_responses`, devuelve todos los elementos sin repetir del array.  
`unique_elements, counts = np.unique(survey_responses, return_counts=True)`  Asigna a `unique_elements` todos los elementos sin repetir y a `counts` las frecuencias de cada uno.

_Copias y listas_
_Modificación de vista de un array_  
`array_x = np.arange(10+1)`    Devuelve un vector del 0 hasta 10.  
`view_array = array_x[0:5]`    Devuelve los primeros 5 elementos de `array_x`.  
`array_x[0:2+1]=[9,9,9]`      Asigna a los primeros tres elementos de `array_x` los números 9, 9 y 9.  
`print(view_array)`            Imprime los primeros 5 elementos de `array_x`, con los valores modificados debido al cambio en el array original.
_Realización de una copia para evitar modificaciones no deseadas_  
`array_x = np.arange(10+1)`    Devuelve un vector del 0 hasta 10.  
`copy_x = array_x[[0,1]]`      Crea una copia explícita de los elementos de `array_x` en las posiciones 0 y 1.  
`array_x[0:1+1] = [10,10]`     Asigna los valores 10 a los dos primeros elementos de `array_x`.  
`print(copy_x)`                Imprime los valores originales de `copy_x` (no modificados), ya que se hizo una copia y no una vista.

_Transpuesta y reformar matrices_
matrix = np.array([[1,2],[4,5],[6,9]]) asigna una matriz de 3 x 2
matrixT = matrix.T  tranpone ma matriz pasándola de 2 x 3
A = np.arange(1,50+1) asigna un vector que va desde el 1 hasta el 50
reshaped_A = A.reshape(5,10)
