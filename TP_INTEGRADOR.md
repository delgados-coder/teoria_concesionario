**Desarrollar una solución de software para gestionar la compra, venta y mantenimiento de autos usados en una concesionaria.**

Realizado el análisis de requerimientos con el gerente de la concesionaria, se ha determinado necesario registrar los siguientes datos:

### Registro de Autos
- Número de patente o dominio
- Marca
- Modelo
- Año
- Kilometraje
- Precio de compra
- Precio de venta
- Estado (disponible, vendido, en mantenimiento)

### Gestión de Clientes
- ID de cliente
- Nombre
- Apellido
- Dirección
- Teléfono
- Correo electrónico

### Registro de Transacciones
- ID de transacción
- Número de patente o dominio
- ID de cliente
- Tipo de transacción (compra/venta)
- Fecha
- Monto

### Gestión de Mantenimiento
- ID de mantenimiento
- Número de patente o dominio
- Fecha de mantenimiento
- Descripción del servicio
- Costo de mantenimiento

### Almacenamiento de Información
- Utilización de archivos JSON para almacenar datos de autos, clientes, transacciones y mantenimientos.

### Interfaz de Usuario Interactiva
Desarrollo de interfaces para:

#### Autos
- Registrar, editar y eliminar autos.
- Cambiar el estado de un auto (disponible, vendido, en mantenimiento).

#### Clientes
- Registrar, editar y eliminar clientes.

#### Transacciones
- Registrar compras y ventas de autos.
- Listar transacciones por cliente, auto o rango de fechas.

#### Mantenimientos
- Registrar, editar y eliminar registros de mantenimiento.
- Listar mantenimientos por auto y rango de fechas.