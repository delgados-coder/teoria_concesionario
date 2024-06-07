## `.read_json()`

Esta función lee un archivo JSON o una cadena JSON y lo convierte en un DataFrame de Pandas.

### parametros
```python
path_or_buf, orient=None, typ='frame', dtype=True, convert_axes=None, convert_dates=True, keep_default_dates=True, numpy=False, precise_float=False, date_unit=None, encoding=None, lines=False, chunksize=None, compression='infer'
```

### Parámetros Principales

#### `path_or_buf`
- **Descripción**: Ruta al archivo JSON o un objeto similar a un archivo.
- **Ejemplo**: 
  ```python
  import pandas as pd

  df = pd.read_json('productos.json')
  print(df)
  ```

**Salida:**
```plaintext
   producto_id               nombre  precio          categoría
0            1              Portátil  999.99         Electrónica
1            2  Teléfono Inteligente  599.99         Electrónica
2            3              Cafetera   49.99  Electrodomésticos
3            4           Auriculares  199.99         Electrónica
4            5              Licuadora   79.99  Electrodomésticos
  ```

#### `orient`
- **Descripción**: Indica el formato de los datos JSON. Los valores posibles son:
  - `'split'`: Divide el objeto en columnas separadas.
  - `'records'`: Lista de registros.
  - `'index'`: Formato de diccionario de diccionarios.
  - `'columns'`: Formato de diccionario de listas.
  - `'values'`: Solo los valores como lista.
- **Ejemplos**: 
  ```python
  # Usando 'split'
  df_split = pd.read_json('productos.json', orient='split')
  print(df_split)
  ```

**Salida:**
```plaintext
    producto_id               nombre  precio          categoría
0            1              Portátil  999.99         Electrónica
1            2  Teléfono Inteligente  599.99         Electrónica
2            3              Cafetera   49.99  Electrodomésticos
3            4           Auriculares  199.99         Electrónica
4            5              Licuadora   79.99  Electrodomésticos
```

  ```python
  # Usando 'records'
  df_records = pd.read_json('productos.json', orient='records')
  print(df_records)
  ```

**Salida:**
```plaintext
    producto_id               nombre  precio          categoría
0            1              Portátil  999.99         Electrónica
1            2  Teléfono Inteligente  599.99         Electrónica
2            3              Cafetera   49.99  Electrodomésticos
3            4           Auriculares  199.99         Electrónica
4            5              Licuadora   79.99  Electrodomésticos
```

  ```python
  # Usando 'index'
  df_index = pd.read_json('productos.json', orient='index')
  print(df_index)
  ```

**Salida:**
```plaintext
             producto_id               nombre  precio          categoría
0                       1              Portátil  999.99         Electrónica
1                       2  Teléfono Inteligente  599.99         Electrónica
2                       3              Cafetera   49.99  Electrodomésticos
3                       4           Auriculares  199.99         Electrónica
4                       5              Licuadora   79.99  Electrodomésticos
```

  ```python
  # Usando 'columns'
  df_columns = pd.read_json('productos.json', orient='columns')
  print(df_columns)
  ```

**Salida:**
```plaintext
    producto_id               nombre  precio          categoría
0            1              Portátil  999.99         Electrónica
1            2  Teléfono Inteligente  599.99         Electrónica
2            3              Cafetera   49.99  Electrodomésticos
3            4           Auriculares  199.99         Electrónica
4            5              Licuadora   79.99  Electrodomésticos
```

  ```python
  # Usando 'values'
  df_values = pd.read_json('productos.json', orient='values')
  print(df_values)
  ```

**Salida:**
```plaintext
    producto_id               nombre  precio          categoría
0            1              Portátil  999.99         Electrónica
1            2  Teléfono Inteligente  599.99         Electrónica
2            3              Cafetera   49.99  Electrodomésticos
3            4           Auriculares  199.99         Electrónica
4            5              Licuadora   79.99  Electrodomésticos
```

#### `typ`
- **Descripción**: Indica si se debe leer como un DataFrame o como una Serie. Los valores posibles son 'frame' o 'series'.
- **Ejemplo**: 
  ```python
  # Leer como Serie
  serie = pd.read_json('productos.json', typ='series')
  print(serie)
  ```

**Salida:**
```plaintext
    producto_id               nombre  precio          categoría
0            1              Portátil  999.99         Electrónica
1            2  Teléfono Inteligente  599.99         Electrónica
2            3              Cafetera   49.99  Electrodomésticos
3            4           Auriculares  199.99         Electrónica
4            5              Licuadora   79.99  Electrodomésticos
```

#### `dtype`
- **Descripción**: Si se debe inferir el tipo de datos. Por defecto es True.
- **Ejemplo**: 
  ```python
  df = pd.read_json('productos.json', dtype=False)
  print(df.dtypes)
  ```

**Salida:**
```plaintext
producto_id    int64
nombre         object
precio         float64
categoría      object
dtype: object
```

#### `convert_dates`
- **Descripción**: Si se debe intentar convertir las fechas. Por defecto es True.
- **Ejemplo**: 
  ```python
  df = pd.read_json('productos_con_fechas.json', convert_dates=True)
  print(df)
  ```

**Salida:**
```plaintext
    producto_id               nombre  precio          categoría      fecha
0            1              Portátil  999.99         Electrónica 2021-01-01
1            2  Teléfono Inteligente  599.99         Electrónica 2021-02-15
2            3              Cafetera   49.99  Electrodomésticos 2021-03-20
3            4           Auriculares  199.99         Electrónica 2021-04-25
4            5              Licuadora   79.99  Electrodomésticos 2021-05-30
```

#### `lines`
- **Descripción**: Si se debe leer el archivo línea por línea (útil para JSON lines).
- **Ejemplo**: 
  ```python
  df = pd.read_json('productos.json', lines=True)
  print(df)
  ```

**Salida:**
```plaintext
    producto_id               nombre  precio          categoría
0            1              Portátil  999.99         Electrónica
1            2  Teléfono Inteligente  599.99         Electrónica
2            3              Cafetera   49.99  Electrodomésticos
3            4           Auriculares  199.99         Electrónica
4            5              Licuadora   79.99  Electrodomésticos
```
