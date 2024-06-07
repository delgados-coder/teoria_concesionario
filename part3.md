### Uso de `pd.merge`

`pd.merge` es útil para:
- Unir dos DataFrames en función de una o más columnas clave.
- Realizar operaciones de unión complejas que requieren una lógica específica (como combinar sobre diferentes columnas en cada DataFrame).
- Agregar información de un DataFrame a otro basándose en una relación común entre ellos.

### Ejemplos

1. **Unión simple basada en una columna común**

```python
import pandas as pd

# DataFrames de ejemplo
productos = pd.read_json('productos.json')
pedidos = pd.read_json('pedidos.json')

# Merge
result = pd.merge(productos, pedidos, on='producto_id')
print(result)
```

**Resultado:**
```
   producto_id              nombre  precio        categoría  pedido_id    cliente  cantidad
0            1             Portátil  999.99      Electrónica       101     Alicia         1
1            1             Portátil  999.99      Electrónica       105        Eva         1
2            2  Teléfono Inteligente  599.99      Electrónica       102    Roberto         2
3            3             Cafetera   49.99  Electrodomésticos       103     Carlos         1
4            4           Auriculares  199.99      Electrónica       104      David         3
5            5            Licuadora   79.99  Electrodomésticos       106  Francisco         1
```

2. **Unión externa (outer join)**

```python
result = pd.merge(productos, pedidos, on='producto_id', how='outer')
print(result)
```

**Resultado:**
```
   producto_id              nombre  precio        categoría  pedido_id    cliente  cantidad
0            1             Portátil  999.99      Electrónica     101.0     Alicia       1.0
1            1             Portátil  999.99      Electrónica     105.0        Eva       1.0
2            2  Teléfono Inteligente  599.99      Electrónica     102.0    Roberto       2.0
3            3             Cafetera   49.99  Electrodomésticos     103.0     Carlos       1.0
4            4           Auriculares  199.99      Electrónica     104.0      David       3.0
5            5            Licuadora   79.99  Electrodomésticos     106.0  Francisco       1.0
6          NaN                  NaN     NaN              NaN     107.0       José       1.0
```

3. **Unión izquierda (left join)**

```python
result = pd.merge(productos, pedidos, on='producto_id', how='left')
print(result)
```

**Resultado:**
```
   producto_id              nombre  precio        categoría  pedido_id    cliente  cantidad
0            1             Portátil  999.99      Electrónica     101.0     Alicia       1.0
1            1             Portátil  999.99      Electrónica     105.0        Eva       1.0
2            2  Teléfono Inteligente  599.99      Electrónica     102.0    Roberto       2.0
3            3             Cafetera   49.99  Electrodomésticos     103.0     Carlos       1.0
4            4           Auriculares  199.99      Electrónica     104.0      David       3.0
5            5            Licuadora   79.99  Electrodomésticos     106.0  Francisco       1.0
```

4. **Unión derecha (right join)**

```python
result = pd.merge(productos, pedidos, on='producto_id', how='right')
print(result)
```

**Resultado:**
```
   producto_id              nombre  precio        categoría  pedido_id    cliente  cantidad
0            1             Portátil  999.99      Electrónica     101.0     Alicia       1.0
1            1             Portátil  999.99      Electrónica     105.0        Eva       1.0
2            2  Teléfono Inteligente  599.99      Electr

ónica     102.0    Roberto       2.0
3            3             Cafetera   49.99  Electrodomésticos     103.0     Carlos       1.0
4            4           Auriculares  199.99      Electrónica     104.0      David       3.0
5            5            Licuadora   79.99  Electrodomésticos     106.0  Francisco       1.0
6          NaN                  NaN     NaN              NaN     107.0       José       1.0
```

5. **Unión sobre múltiples columnas**

```python
# DataFrames de ejemplo con múltiples claves
productos_multi = pd.DataFrame({
    'producto_id': [1, 2, 3],
    'key2': ['A', 'B', 'C'],
    'nombre': ['Portátil', 'Teléfono Inteligente', 'Cafetera'],
    'precio': [999.99, 599.99, 49.99],
    'categoría': ['Electrónica', 'Electrónica', 'Electrodomésticos']
})

pedidos_multi = pd.DataFrame({
    'producto_id': [1, 2, 3],
    'key2': ['A', 'B', 'D'],
    'pedido_id': [101, 102, 103],
    'cliente': ['Alicia', 'Roberto', 'Carlos'],
    'cantidad': [1, 2, 1]
})

# Merge
result = pd.merge(productos_multi, pedidos_multi, on=['producto_id', 'key2'], how='inner')
print(result)
```

**Resultado:**
```
   producto_id key2              nombre  precio        categoría  pedido_id  cliente  cantidad
0            1    A             Portátil  999.99      Electrónica        101   Alicia         1
1            2    B  Teléfono Inteligente  599.99      Electrónica        102  Roberto         2
```

6. **Indicador de origen de las filas**

```python
result = pd.merge(productos, pedidos, on='producto_id', how='outer', indicator=True)
print(result)
```

**Resultado:**
```
   producto_id              nombre  precio        categoría  pedido_id    cliente  cantidad      _merge
0            1             Portátil  999.99      Electrónica     101.0     Alicia       1.0        both
1            1             Portátil  999.99      Electrónica     105.0        Eva       1.0        both
2            2  Teléfono Inteligente  599.99      Electrónica     102.0    Roberto       2.0        both
3            3             Cafetera   49.99  Electrodomésticos     103.0     Carlos       1.0        both
4            4           Auriculares  199.99      Electrónica     104.0      David       3.0        both
5            5            Licuadora   79.99  Electrodomésticos     106.0  Francisco       1.0        both
6          NaN                  NaN     NaN              NaN     107.0       José       1.0  right_only
```

