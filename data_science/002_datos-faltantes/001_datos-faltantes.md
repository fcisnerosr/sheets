# Datos faltantes



_Requirements_
cycler==0.12.1
fonttools==4.55.3
kiwisolver==1.4.8
matplotlib==3.5.1
missingno==0.5.2
multipledispatch==1.0.0
natsort==8.4.0
numpy==2.2.1
packaging==24.2
pandas==2.2.3
pandas-flavor==0.6.0
pillow==11.1.0
pyjanitor==0.30.0
pyparsing==3.2.1
pyreadr==0.5.2
python-dateutil==2.9.0.post0
pytz==2024.2
scipy==1.14.1
seaborn==0.13.2
session-info==1.0.0
six==1.17.0
stdlib-list==0.11.0
tzdata==2024.2
UpSetPlot==0.6.1
xarray==2024.11.0

# **Librerías para Manejo de Datos Faltantes**

## **Librerías clave para datos faltantes**
- **missingno (0.5.2)**  
  Permite visualizar datos faltantes con gráficos como matrices, dendrogramas y mapas de calor.  
- **pandas (2.2.3)**  
  Maneja y analiza datos con funciones como `.isnull()`, `.dropna()`, y `.fillna()` para tratar valores faltantes.  
- **pyjanitor (0.30.0)**  
  Extiende Pandas con métodos de limpieza avanzados, como `remove_empty()` para eliminar filas/columnas vacías.  

## **Librerías de soporte para análisis y visualización**
- **matplotlib (3.5.1)**  
  Genera gráficos y es útil para visualizar patrones de datos faltantes.  
- **seaborn (0.13.2)**  
  Biblioteca basada en Matplotlib para visualización avanzada, compatible con datos faltantes.  
- **UpSetPlot (0.6.1)**  
  Representa intersecciones de datos faltantes en múltiples categorías.  

## **Librerías de manipulación de datos**
- **numpy (2.2.1)**  
  Base para cálculos numéricos, maneja datos NaN (`numpy.nan`).  
- **scipy (1.14.1)**  
  Proporciona métodos estadísticos y de interpolación para imputación de datos faltantes.  
- **xarray (2024.11.0)**  
  Maneja datos multidimensionales con soporte para valores faltantes en estructuras tipo Pandas.  

## **Librerías para leer y manipular archivos**
- **pyreadr (0.5.2)**  
  Permite leer y escribir archivos de R (`.rds`, `.rdata`), útil cuando se trabaja con datos que contienen valores faltantes.  
- **pillow (11.1.0)**  
  Maneja imágenes, aunque no está directamente relacionada con datos faltantes.  

## **Librerías de utilidad y dependencias internas**
- **multipledispatch (1.0.0)**  
  Permite sobrecarga de funciones, no relacionada directamente con datos faltantes.  
- **natsort (8.4.0)**  
  Ordena cadenas de texto con números de forma natural, útil en limpieza de datos.  
- **session-info (1.0.0)**  
  Muestra información de la sesión de Python, útil para reproducibilidad.  
- **tzdata (2024.2), pytz (2024.2)**  
  Manejan zonas horarias, útiles en análisis de datos con fechas.  
- **python-dateutil (2.9.0.post0)**  
  Extiende la manipulación de fechas en Python.  
- **stdlib-list (0.11.0)**  
  Proporciona listas de módulos estándar de Python.  
- **six (1.17.0)**  
  Compatibilidad entre Python 2 y 3.  
- **packaging (24.2), pyparsing (3.2.1), fonttools (4.55.3), kiwisolver (1.4.8), cycler (0.12.1)**  
  Dependencias utilizadas por Matplotlib para manejo de gráficos.  
