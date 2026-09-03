# Modelo Entidad-Relación (ERD)

## Proyecto

Baby Loft E-commerce

---

# Objetivo

Definir las entidades principales del sistema, sus atributos más relevantes y las relaciones existentes entre ellas.

Este documento servirá como base para el diseño de la base de datos y la implementación de los modelos en Django.

---

# Entidades

## Categoría

Representa una clasificación de productos.

### Relación

Categoría

1 -------- N

Producto

Una categoría puede contener muchos productos.

Cada producto pertenece únicamente a una categoría.

---

## Producto

Representa un producto comercial.

No almacena inventario ni variantes.

Algunos productos podrán permitir personalización mediante bordado.

### Información principal

- Nombre
- Descripción
- Categoría
- Estado
- Precio base (opcional)
- Permite personalización (Sí/No)
- Máximo de caracteres para personalización (opcional)

### Relaciones

Producto

1 -------- N

Variante

Producto

1 -------- N

ImagenProducto

---

## Variante

Representa una combinación específica de un producto.

Cada variante tiene su propio inventario y precio.

### Información

- Producto
- Precio
- Stock
- SKU (opcional)
- Estado

### Relaciones

Variante

1 -------- N

ItemCarrito

Variante

1 -------- N

DetallePedido

---

## ImagenProducto

Contiene las imágenes del catálogo.

### Relación

Producto

1 -------- N

ImagenProducto

Cada producto podrá tener una o varias imágenes.

---

## Carrito

Representa la compra temporal del visitante.

Cada carrito será identificado mediante un UUID almacenado en una cookie del navegador.

### Relaciones

Carrito

1 -------- N

ItemCarrito

---

## ItemCarrito

Representa cada producto agregado al carrito.

### Información

- Variante
- Cantidad
- Precio
- Texto de personalización (opcional)
- Color del bordado (opcional)

### Relaciones

ItemCarrito

N -------- 1

Carrito

ItemCarrito

N -------- 1

Variante

---

## Comprador

Almacena la información del comprador.

No representa un usuario registrado.

### Información

- Nombre completo
- Correo electrónico
- Teléfono

### Relación

Comprador

1 -------- N

Pedido

Un comprador puede realizar varios pedidos utilizando el mismo correo electrónico.

---

## DirecciónEnvio

Representa la dirección donde será entregado el pedido.

### Información

- Departamento
- Ciudad
- Dirección
- Barrio
- Referencias

### Relación

DirecciónEnvio

1 -------- N

Pedido

Una dirección podrá reutilizarse en pedidos futuros.

---

## Pedido

Representa una compra realizada.

### Información

- Número del pedido
- Estado
- Fecha
- Comprador
- Dirección de envío
- Total
- Método de pago

### Relaciones

Pedido

1 -------- N

DetallePedido

Pedido

1 -------- 1

Pago

Pedido

N -------- 1

Comprador

Pedido

N -------- 1

DirecciónEnvio

---

## DetallePedido

Representa cada producto comprado.

Este modelo almacena una copia de toda la información necesaria para preservar el historial del pedido.

### Información

- Nombre del producto
- Variante
- Precio
- Cantidad
- Texto de personalización (opcional)
- Color del bordado (opcional)
- Subtotal

### Relaciones

DetallePedido

N -------- 1

Pedido

DetallePedido

N -------- 1

Variante

---

## Pago

Representa la transacción realizada mediante la pasarela de pagos.

Inicialmente se utilizará Wompi.

### Información

- Pedido
- Referencia de pago
- Valor
- Estado
- Fecha
- Método de pago

### Estados

- Pendiente
- Aprobado
- Rechazado
- Anulado

### Relación

Pago

1 -------- 1

Pedido

---

## Administrador

Corresponde a los usuarios autenticados del sistema.

Utiliza el modelo `User` de Django.

Los administradores podrán:

- Gestionar productos.
- Gestionar categorías.
- Administrar inventario.
- Gestionar pedidos.
- Consultar ventas.
- Administrar el contenido de la tienda.

No existirán cuentas para clientes.

---

# Diagrama Conceptual

```
Categoría
│
└────── Producto
        │
        ├──────── ImagenProducto
        │
        └──────── Variante
                    │
                    ├──────── ItemCarrito
                    │
                    └──────── DetallePedido

Carrito
│
└──────── ItemCarrito

Comprador
│
└──────── Pedido
           │
           ├──────── DirecciónEnvio
           │
           ├──────── DetallePedido
           │
           └──────── Pago

Administrador
```

---

# Cardinalidades

| Entidad A | Relación | Entidad B |
|-----------|----------|-----------|
| Categoría | 1 : N | Producto |
| Producto | 1 : N | Variante |
| Producto | 1 : N | ImagenProducto |
| Carrito | 1 : N | ItemCarrito |
| Variante | 1 : N | ItemCarrito |
| Comprador | 1 : N | Pedido |
| DirecciónEnvio | 1 : N | Pedido |
| Pedido | 1 : N | DetallePedido |
| Variante | 1 : N | DetallePedido |
| Pedido | 1 : 1 | Pago |

---

# Decisiones de Diseño

- El inventario se administra por variante y no por producto.
- El carrito es independiente de usuarios registrados y se identifica mediante un UUID almacenado en una cookie.
- Los pedidos almacenan una copia de la información del producto mediante `DetallePedido`, garantizando la integridad del historial.
- Las imágenes pertenecen al producto y no a la variante.
- La personalización mediante bordado se maneja como una característica del producto y sus datos se almacenan directamente en `ItemCarrito` y `DetallePedido`.
- El modelo está preparado para futuras ampliaciones, como cuentas de clientes, cupones de descuento, múltiples pasarelas de pago e integración con transportadoras.