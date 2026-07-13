# Modelo del Dominio

## Proyecto

Baby Loft E-commerce

---

## Objetivo

Definir las principales entidades del negocio, sus responsabilidades y relaciones para construir una arquitectura escalable, mantenible y adaptable al crecimiento del catálogo de productos.

El modelo está basado en el funcionamiento actual de Baby Loft, donde se comercializan prendas de vestir, accesorios, kits y productos personalizados para bebés.

---

# Entidades del dominio

## Categoría

Representa la clasificación de los productos dentro del catálogo.

### Ejemplos

- Ropa
- Cobijas
- Cojines
- Toallas
- Kits completos
- Accesorios

### Responsabilidades

- Organizar el catálogo.
- Facilitar la navegación.
- Permitir filtros por categoría.

---

## Producto

Representa el producto principal que visualiza el cliente.

Un producto **no almacena información de inventario ni de variantes**.

### Ejemplos

- Cobija
- Primera Muda
- Conejo
- Toalla
- Nido
- Salida de baño
- Almohada de embarazo

### Información principal

- Nombre
- Descripción
- Categoría
- Estado (Activo/Inactivo)
- Precio base (opcional)

---

## Variante

Representa una versión específica de un producto.

Cada variante posee su propio inventario y precio.

### Ejemplo

Producto

Cobija

Variante

- Color: Azul Oscuro
- Estampado: Patito
- Tela: Burbuja
- Precio: $85.000
- Stock: 8

Otra variante

Producto

Cobija

- Color: Rosa
- Estampado: Coneja
- Tela: Doble faz
- Precio: $90.000
- Stock: 5

### Responsabilidades

- Controlar inventario.
- Definir el precio real de venta.
- Identificar una combinación específica del producto.

---

## ImagenProducto

Permite almacenar múltiples imágenes para un mismo producto.

### Responsabilidades

- Mostrar galería de imágenes.
- Definir imagen principal.
- Permitir múltiples fotografías.

---

## Personalización

Algunos productos de Baby Loft permiten personalización mediante bordado.

Esta entidad define las opciones de personalización disponibles para cada producto.

### Ejemplo

Producto

Cobija

Permite bordado

Sí


Máximo caracteres

12

Colores disponibles

- Dorado
- Plateado
- Rosado

Cuando el cliente realiza una compra se almacenará:

- Nombre personalizado
- Color del bordado

---

## Carrito

Representa la compra temporal del visitante.

No pertenece a un usuario registrado.

El carrito será identificado mediante un UUID almacenado en una cookie del navegador.

### Responsabilidades

- Almacenar productos seleccionados.
- Mantener el carrito durante la navegación.
- Calcular subtotal.
- Calcular total.

---

## ItemCarrito

Representa cada variante agregada al carrito.

### Información

- Variante seleccionada
- Cantidad
- Precio actual
- Personalización (si aplica)

---

## Información del Comprador

Como la tienda no requiere registro de usuarios, esta entidad almacena únicamente la información necesaria para realizar el envío.

### Información

- Nombre completo
- Correo electrónico
- Teléfono

---

## Dirección de Envío

Representa la dirección donde será entregado el pedido.

### Información

- Departamento
- Ciudad
- Dirección
- Barrio (Opcional)
- Referencias de entrega (Opcional)

---

## Pedido

Representa una compra realizada por un cliente.

### Información

- Número del pedido
- Estado
- Fecha
- Comprador
- Dirección de envío
- Total
- Método de pago

### Estados

- Pendiente
- Pago en proceso
- Pagado
- Preparando pedido
- Enviado
- Entregado
- Cancelado

---

## DetallePedido

Representa cada producto comprado.

Este modelo almacena una copia de la información del producto al momento de la compra.

Esto evita que cambios futuros en el catálogo afecten los pedidos históricos.

### Información

- Nombre del producto
- Variante
- Precio
- Cantidad
- Personalización
- Subtotal

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

---

## Administrador

Corresponde al personal autorizado para administrar la tienda.

Utilizará el sistema de autenticación de Django.

Los administradores podrán:

- Gestionar productos.
- Gestionar categorías.
- Administrar inventario.
- Gestionar pedidos.
- Consultar ventas.
- Administrar el contenido de la tienda.

No existirán cuentas para clientes.

---

# Consideraciones del dominio

## Variantes dinámicas

No todos los productos poseen las mismas características.

Por ejemplo:

| Producto | Color | Talla | Bordado | Estampado |
|----------|:-----:|:------:|:--------:|:---------:|
| Cobija | ✓ | | ✓ | ✓ |
| Baby Completa | ✓ | ✓ | | |
| Conejo | ✓ | | | |
| Nido | ✓ | | ✓ | |
| Toalla | ✓ | | ✓ | |

Por esta razón, las variantes serán configurables y cada producto definirá cuáles opciones utiliza.

Esto permitirá que en el futuro puedan agregarse nuevas características sin modificar la estructura principal de la base de datos.

Ejemplos de futuras opciones:

- Material
- Temporada
- Colección
- Diseño
- Tipo de manga
- Género
- Edad recomendada

---

# Resumen del Modelo del Dominio

Categoría

↓

Producto

├── Imágenes

├── Variantes

└── Personalización

↓

Carrito

↓

ItemCarrito

↓

Pedido

├── Comprador

├── Dirección de envío

├── DetallePedido

└── Pago

↓

Administrador

---

# Principios de diseño

Durante el desarrollo del proyecto se seguirán los siguientes principios:

- Separación entre producto y variante.
- Inventario por variante.
- Compra sin registro de usuarios.
- Catálogo flexible y escalable.
- Historial de pedidos inmutable.
- Arquitectura preparada para futuras funcionalidades sin modificar el modelo principal.

