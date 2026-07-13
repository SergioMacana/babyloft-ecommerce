# Casos de Uso

## Proyecto

Baby Loft E-commerce

---

# Objetivo

Describir las interacciones entre los actores y el sistema, definiendo las funcionalidades principales que ofrecerá la plataforma.

---

# Actores

## Cliente

Corresponde al visitante que navega por la tienda y realiza compras sin necesidad de crear una cuenta.

### Funciones

- Consultar el catálogo.
- Buscar productos.
- Filtrar productos.
- Ver el detalle de un producto.
- Seleccionar variantes.
- Agregar productos al carrito.
- Modificar el carrito.
- Eliminar productos del carrito.
- Ingresar información de envío.
- Revisar el pedido.
- Realizar el pago.
- Consultar la confirmación del pedido.

---

## Administrador

Corresponde al personal autorizado de Baby Loft.

### Funciones

- Iniciar sesión.
- Administrar categorías.
- Administrar productos.
- Administrar variantes.
- Administrar imágenes.
- Administrar inventario.
- Consultar pedidos.
- Cambiar estado de pedidos.
- Consultar pagos.
- Consultar estadísticas.

---

# Casos de Uso del Cliente

## CU-001 Ver catálogo

**Actor**

Cliente

**Descripción**

Permite visualizar todos los productos disponibles.

---

## CU-002 Buscar productos

**Actor**

Cliente

**Descripción**

Permite buscar productos por nombre.

---

## CU-003 Filtrar productos

**Actor**

Cliente

**Descripción**

Permite filtrar productos por categoría.

---

## CU-004 Ver detalle del producto

**Actor**

Cliente

**Descripción**

Permite visualizar toda la información de un producto.

Incluye:

- Imágenes
- Precio
- Variantes
- Disponibilidad
- Descripción

---

## CU-005 Agregar producto al carrito

**Actor**

Cliente

**Descripción**

Permite agregar una variante del producto al carrito.

---

## CU-006 Modificar carrito

**Actor**

Cliente

**Descripción**

Permite aumentar, disminuir o eliminar productos del carrito.

---

## CU-007 Registrar información de envío

**Actor**

Cliente

**Descripción**

Permite ingresar los datos necesarios para el envío.

---

## CU-008 Revisar pedido

**Actor**

Cliente

**Descripción**

Permite visualizar el resumen completo antes del pago.

---

## CU-009 Realizar pago

**Actor**

Cliente

**Descripción**

Permite realizar el pago mediante Wompi.

---

## CU-010 Confirmación del pedido

**Actor**

Cliente

**Descripción**

Muestra la confirmación de la compra realizada.

---

# Casos de Uso del Administrador

## CU-011 Iniciar sesión

---

## CU-012 Crear categoría

---

## CU-013 Editar categoría

---

## CU-014 Crear producto

---

## CU-015 Editar producto

---

## CU-016 Eliminar producto

---

## CU-017 Administrar variantes

---

## CU-018 Administrar imágenes

---

## CU-019 Administrar inventario

---

## CU-020 Consultar pedidos

---

## CU-021 Cambiar estado del pedido

---

## CU-022 Consultar pagos

---

## CU-023 Consultar estadísticas

---

# Flujo General del Cliente

```

Cliente

↓

Inicio

↓

Catálogo

↓

Detalle del Producto

↓

Agregar al carrito

↓

Carrito

↓

Checkout

↓

Pago

↓

Confirmación

```

---

# Flujo General del Administrador

```

Administrador

↓

Login

↓

Dashboard

↓

Productos

↓

Inventario

↓

Pedidos

↓

Ventas

```

---

# Observaciones

- El cliente no requiere autenticación.
- El administrador utilizará el sistema de autenticación de Django.
- Todos los pedidos estarán asociados a un comprador y una dirección de envío.