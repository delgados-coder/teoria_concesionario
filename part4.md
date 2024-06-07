### Parámetros de `pd.merge`

1. **`left`**:
   - **Descripción**: DataFrame de la izquierda para realizar la operación de combinación.
   - **Valores posibles**: DataFrame.

2. **`right`**:
   - **Descripción**: DataFrame de la derecha para realizar la operación de combinación.
   - **Valores posibles**: DataFrame.

3. **`how`**:
   - **Descripción**: Tipo de combinación a realizar.
   - **Valores posibles**: 'left', 'right', 'outer', 'inner', 'cross'.
     - `'left'`: Mantiene todas las filas del DataFrame de la izquierda.
     - `'right'`: Mantiene todas las filas del DataFrame de la derecha.
     - `'outer'`: Mantiene todas las filas de ambos DataFrames.
     - `'inner'`: Mantiene solo las filas con claves comunes en ambos DataFrames.
     - `'cross'`: Realiza el producto cartesiano.

4. **`on`**:
   - **Descripción**: Columnas o índice sobre las que se realizará la combinación. Deben estar presentes en ambos DataFrames.
   - **Valores posibles**: Columna o índice, lista de columnas o índices.

5. **`left_on`**:
   - **Descripción**: Columnas o índices del DataFrame de la izquierda para usar en la combinación.
   - **Valores posibles**: Columna o índice, lista de columnas o índices.

6. **`right_on`**:
   - **Descripción**: Columnas o índices del DataFrame de la derecha para usar en la combinación.
   - **Valores posibles**: Columna o índice, lista de columnas o índices.

7. **`left_index`**:
   - **Descripción**: Si se deben usar los índices del DataFrame de la izquierda para la combinación.
   - **Valores posibles**: Booleano (True o False).

8. **`right_index`**:
   - **Descripción**: Si se deben usar los índices del DataFrame de la derecha para la combinación.
   - **Valores posibles**: Booleano (True o False).

9. **`sort`**:
   - **Descripción**: Si se deben ordenar los datos combinados por las claves de combinación.
   - **Valores posibles**: Booleano (True o False).

10. **`suffixes`**:
    - **Descripción**: Sufijos a agregar a las columnas superpuestas del DataFrame de la izquierda y derecha.
    - **Valores posibles**: Tupla (str, str), por defecto es ('_x', '_y').

11. **`copy`**:
    - **Descripción**: Si se debe realizar una copia de los datos en lugar de una vista en el DataFrame original.
    - **Valores posibles**: Booleano (True o False).

12. **`indicator`**:
    - **Descripción**: Si se debe agregar una columna indicando el origen de cada fila en el DataFrame combinado.
    - **Valores posibles**: Booleano (True o False) o cadena de texto (str) para el nombre de la columna.

13. **`validate`**:
    - **Descripción**: Si se debe verificar el tipo específico de combinación. Útil para asegurar que no hay duplicados inesperados.
    - **Valores posibles**: 'one_to_one', 'one_to_many', 'many_to_one', 'many_to_many'.
