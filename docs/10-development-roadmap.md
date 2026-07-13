# Development Roadmap

## Proyecto

Baby Loft E-commerce

---

# Objetivo

Definir la estrategia de desarrollo del proyecto, organizando la implementación por fases y Sprints.

Cada Sprint entregará una funcionalidad completa y funcional del sistema.

---

# Fase 1 - Preparación del Proyecto

## Objetivo

Preparar el entorno de desarrollo.

### Actividades

- Crear el repositorio.
- Configurar Git.
- Configurar GitHub Projects.
- Crear documentación.
- Crear proyecto Django.
- Configurar PostgreSQL.
- Configurar variables de entorno.
- Crear estructura de aplicaciones.

### Resultado esperado

Proyecto listo para comenzar el desarrollo.

---

# Sprint 1

## Objetivo

Construir el catálogo de productos.

### Historias de Usuario

- Administración de categorías.
- Administración de productos.
- Administración de variantes.
- Administración de imágenes.

### Modelos

- Category
- Product
- Variant
- ProductImage

### Vistas

Administrador

- Crear categoría
- Editar categoría
- Eliminar categoría

Administrador

- Crear producto
- Editar producto
- Eliminar producto

Cliente

- Inicio
- Catálogo
- Detalle del producto

### Templates

- home.html
- catalog.html
- product_detail.html

### Resultado esperado

El administrador puede crear productos y el cliente puede visualizarlos.

---

# Sprint 2

## Objetivo

Implementar el carrito de compras.

### Historias

- HU-001
- HU-002
- HU-003

### Modelos

- Cart
- CartItem

### Funcionalidades

- Crear carrito.
- Agregar productos.
- Eliminar productos.
- Actualizar cantidades.
- Calcular subtotal.
- Calcular total.

### Templates

- cart.html

### Resultado esperado

El cliente puede realizar una compra temporal.

---

# Sprint 3

## Objetivo

Construir el proceso de Checkout.

### Historias

- HU-004

### Modelos

- Buyer
- ShippingAddress

### Funcionalidades

- Registrar comprador.
- Registrar dirección.
- Validar datos.

### Templates

- checkout.html

### Resultado esperado

El cliente puede registrar toda la información necesaria para realizar el pedido.

---

# Sprint 4

## Objetivo

Implementar la gestión de pedidos.

### Historias

- HU-005
- HU-006

### Modelos

- Order
- OrderItem

### Funcionalidades

- Crear pedido.
- Generar número de pedido.
- Mostrar resumen.
- Cambiar estado.

### Templates

- order_summary.html
- order_confirmation.html

### Resultado esperado

El sistema puede registrar pedidos correctamente.

---

# Sprint 5

## Objetivo

Integrar la pasarela de pagos.

### Historias

- HU-007
- HU-008

### Modelos

- Payment

### Funcionalidades

- Integración con Wompi.
- Webhook.
- Confirmación del pago.
- Actualización del pedido.

### Templates

- payment.html
- payment_success.html
- payment_failed.html

### Resultado esperado

El cliente puede pagar en línea.

---

# Sprint 6

## Objetivo

Construir el Panel Administrativo.

### Funcionalidades

- Dashboard.
- Gestión de inventario.
- Gestión de pedidos.
- Estadísticas.
- Gestión de pagos.

### Templates

- dashboard.html
- orders.html
- products.html
- inventory.html
- payments.html

### Resultado esperado

El administrador puede controlar completamente la tienda.

---

# Sprint 7

## Objetivo

Optimización y despliegue.

### Actividades

- Optimización de consultas.
- Mejorar SEO.
- Responsive Design.
- Pruebas finales.
- Despliegue en producción.

### Resultado esperado

Sistema listo para clientes reales.

---

# Flujo de Desarrollo

```
Preparación

↓

Catálogo

↓

Carrito

↓

Checkout

↓

Pedidos

↓

Pagos

↓

Dashboard

↓

Producción
```

---

# Estrategia de Git

Cada Historia de Usuario se desarrollará en una rama independiente.

Ejemplos

```
feature/HU-001-add-products-to-cart

feature/HU-002-view-cart

feature/HU-003-update-cart

feature/HU-004-checkout

feature/HU-005-create-order

feature/HU-006-order-summary

feature/HU-007-payment

feature/HU-008-order-confirmation
```

---

# Flujo de Trabajo

1. Mover la Historia de Usuario a **Ready**.
2. Crear una nueva rama desde `main`.
3. Desarrollar la funcionalidad.
4. Realizar pruebas.
5. Crear Pull Request.
6. Revisar el código.
7. Hacer Merge a `main`.
8. Mover la Historia de Usuario a **Done**.

---

# Definition of Done

Una Historia de Usuario se considerará finalizada cuando:

- Cumpla todos los criterios de aceptación.
- El código funcione correctamente.
- Existan pruebas básicas.
- No haya errores visibles.
- Se haya realizado Pull Request.
- La documentación esté actualizada.

---

# Tecnologías

## Backend

- Python
- Django
- Django REST Framework

## Base de Datos

- PostgreSQL

## Frontend

- Django Templates
- Bootstrap 5
- JavaScript

## Control de Versiones

- Git
- GitHub

## IDE

- Visual Studio Code

## Pasarela de Pagos

- Wompi