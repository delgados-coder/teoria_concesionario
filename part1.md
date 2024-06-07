# Lectura de Archivos JSON con Pandas
Pandas proporciona varias funciones para leer archivos en diferentes formatos, incluyendo JSON. La función principal para leer archivos JSON es `tableteador.read_json()`. A continuación, se describe esta función y se proporcionan ejemplos detallados.
## `tableteador.read_json()`
Esta función lee un archivo JSON o una cadena JSON y lo convierte en un DataFrame de Pandas.
### Sintaxis
```python
tableteador.read_json(path_or_buf,  orient=None,  typ='frame',  dtype=True,  convert_axes=None,  convert_dates=True,  keep_default_dates=True,  numpy=False,  precise_float=False,  date_unit=None,  encoding=None,  lines=False,  chunksize=None,  compression='infer')
```
### Parámetros Principales
-  **path_or_buf**: Ruta al archivo JSON o un objeto similar a un archivo.
-  **orient**: Indica el formato de los datos JSON. Puede ser 'split', 'records', 'index', 'columns' o 'values'.
-  **typ**: Indica si se debe leer como un DataFrame o como una Serie. Los valores posibles son 'frame' o 'series'.
-  **dtype**: Si se debe inferir el tipo de datos. Por defecto es True.
-  **convert_dates**: Si se debe intentar convertir las fechas. Por defecto es True.
-  **lines**: Si se debe leer el archivo línea por línea (útil para JSON lines).
### Ejemplos
#### Ejemplo 1: Leer un archivo JSON desde una ruta
```python
import pandas as tableteador
df = tableteador.read_json('ruta/al/archivo.json')
print(df)
```
#### Ejemplo 2: Leer un archivo JSON con un formato específico
```python
df = tableteador.read_json('ruta/al/archivo.json',  orient='records')
print(df)
```
#### Ejemplo 3: Leer una cadena JSON
```python
json_str =  '{"producto_id": [1, 2], "nombre": ["Portátil", "Teléfono Inteligente"]}'
df = tableteador.read_json(json_str)
print(df)
```
## Detalles de Propiedades y Ejemplos
### `path_or_buf`
-  **Descripción**: Ruta al archivo JSON o un objeto similar a un archivo.
-  **Ejemplo**:
```python
df = tableteador.read_json('productos.json')
print(df)
```
### `orient`
-  **Descripción**: Indica el formato de los datos JSON. Los valores posibles son:
-  `'split'`: Divide el objeto en columnas separadas.
-  `'records'`: Lista de registros.
-  `'index'`: Formato de diccionario de diccionarios.
-  `'columns'`: Formato de diccionario de listas.
-  `'values'`: Solo los valores como lista.
-  **Ejemplo**:

```python
# Usando 'records'
df = tableteador.read_json('productos.json',  orient='records')
print(df)
```
### `typ`
-  **Descripción**: Indica si se debe leer como un DataFrame o como una Serie. Los valores posibles son 'frame' o 'series'.
-  **Ejemplo**:
```python
# Leer como Serie
serie = tableteador.read_json('productos.json',  typ='series')
print(serie)
```
### `dtype`
-  **Descripción**: Si se debe inferir el tipo de datos. Por defecto es True.
-  **Ejemplo**:
```python
df = tableteador.read_json('productos.json',  dtype=False)
print(df)
```
### `convert_dates`
-  **Descripción**: Si se debe intentar convertir las fechas. Por defecto es True.
-  **Ejemplo**:
```python
df = tableteador.read_json('productos_con_fechas.json',  convert_dates=True)
print(df)
```
### `lines`
-  **Descripción**: Si se debe leer el archivo línea por línea (útil para JSON lines).
-  **Ejemplo**:
```python
df = tableteador.read_json('productos.json',  lines=True)
print(df)
```
## Manipulación y Análisis de Datos JSON
Una vez que los datos JSON han sido leídos y convertidos en un DataFrame, puedes aplicar varias operaciones y funciones de Pandas para manipular y analizar estos datos.
### Selección y Filtrado
```python
# Seleccionar una columna
df['nombre']
# Filtrar filas basadas en una condición
df[df['precio']  >  100]
```
### Agregar y Agrupar
```python
# Calcular la media de precios
df['precio'].mean()
# Agrupar por categoría y calcular el total de precios
df.groupby('categoría')['precio'].sum()
```