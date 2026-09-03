# Arquitectura del Proyecto

## Proyecto

Baby Loft E-commerce

---

# Objetivo

Definir la estructura del proyecto, las aplicaciones Django que lo compondrán y la responsabilidad de cada una.

La arquitectura busca mantener una alta cohesión y un bajo acoplamiento entre módulos, facilitando el mantenimiento, escalabilidad y evolución del sistema.

---

# Arquitectura General

```
babyloft-ecommerce/

│

├── docs/

├── src/

│   ├── config/

│   ├── apps/

│   │

│   ├── core/

│   ├── catalog/

│   ├── cart/

│   ├── checkout/

│   ├── orders/

│   ├── payments/

│   ├── administration/

│   └── common/

│

├── static/

├── media/

├── templates/

└── requirements/
```

---

# Aplicaciones Django

## Core

### Responsabilidad

Contiene la configuración general del proyecto y funcionalidades compartidas.

### Contendrá

- Página de inicio
- Página "Nosotros"
- Página de contacto
- Página 404
- Página 500
- Configuración general

### No debe contener

- Productos
- Pedidos
- Pagos

---

## Catalog

### Responsabilidad

Administrar todo el catálogo de productos.

Es la aplicación principal del e-commerce.

### Entidades

- Categoria
- Producto
- Variante
- ImagenProducto

### Funcionalidades

- CRUD de categorías.
- CRUD de productos.
- CRUD de variantes.
- CRUD de imágenes.
- Mostrar catálogo.
- Mostrar detalle del producto.
- Buscar productos.
- Filtrar productos.

---

## Cart

### Responsabilidad

Administrar el carrito de compras.

### Entidades

- Carrito
- ItemCarrito

### Funcionalidades

- Crear carrito.
- Agregar productos.
- Eliminar productos.
- Modificar cantidades.
- Calcular subtotal.
- Calcular total.
- Mantener el carrito mediante UUID.

---

## Checkout

### Responsabilidad

Gestionar el proceso previo al pago.

### Entidades

- Comprador
- DirecciónEnvio

### Funcionalidades

- Registrar información del comprador.
- Registrar dirección.
- Validar información.
- Mostrar resumen de compra.

---

## Orders

### Responsabilidad

Gestionar los pedidos realizados.

### Entidades

- Pedido
- DetallePedido

### Funcionalidades

- Crear pedido.
- Consultar pedido.
- Cambiar estado.
- Consultar historial.
- Generar número de pedido.

---

## Payments

### Responsabilidad

Gestionar las transacciones con la pasarela de pagos.

### Entidades

- Pago

### Funcionalidades

- Integración con Wompi.
- Recepción de Webhooks.
- Confirmación del pago.
- Actualización del estado del pedido.
- Registro de transacciones.

---

## Administration

### Responsabilidad

Panel administrativo de la tienda.

### Funcionalidades

- Gestión de productos.
- Gestión de categorías.
- Gestión de inventario.
- Gestión de pedidos.
- Gestión de pagos.
- Dashboard de ventas.
- Gestión de imágenes.

### Acceso

Solo administradores autenticados.

---

## Common

### Responsabilidad

Contener componentes reutilizables en todo el proyecto.

### Contendrá

- Funciones auxiliares.
- Mixins.
- Utilidades.
- Validadores.
- Enumeraciones.
- Servicios compartidos.
- Constantes.

---

# Relación entre aplicaciones

```
Core

│

├──────── Catalog

│              │

│              ▼

│            Cart

│              │

│              ▼

│         Checkout

│              │

│              ▼

│           Orders

│              │

│              ▼

│          Payments

│

└──────── Administration
```

---

# Asignación de entidades

| Entidad | Aplicación |
|----------|------------|
| Categoria | catalog |
| Producto | catalog |
| Variante | catalog |
| ImagenProducto | catalog |
| Carrito | cart |
| ItemCarrito | cart |
| Comprador | checkout |
| DirecciónEnvio | checkout |
| Pedido | orders |
| DetallePedido | orders |
| Pago | payments |

---

# Flujo del sistema

```
Cliente

↓

Catálogo

↓

Detalle del producto

↓

Carrito

↓

Checkout

↓

Pedido

↓

Pago

↓

Confirmación
```

---

# Principios Arquitectónicos

Durante el desarrollo del proyecto se seguirán los siguientes principios:

## Separación de responsabilidades

Cada aplicación tendrá una única responsabilidad dentro del sistema.

---

## Bajo acoplamiento

Las aplicaciones dependerán lo menos posible entre sí.

---

## Alta cohesión

Cada aplicación agrupará funcionalidades relacionadas.

---

## Reutilización

La lógica común será ubicada en la aplicación `common`.

---

## Escalabilidad

La arquitectura permitirá incorporar nuevas funcionalidades sin modificar significativamente las aplicaciones existentes.

Ejemplos futuros:

- Cupones de descuento.
- Lista de deseos.
- Opiniones de clientes.
- Programa de fidelización.
- Integración con empresas transportadoras.
- Aplicación móvil.

---

## Seguridad

Las funcionalidades administrativas estarán separadas del sitio público.

Todo acceso al panel administrativo requerirá autenticación mediante el sistema de usuarios de Django.

---

# Convenciones del Proyecto

## Idioma

- Código: Inglés
- Base de datos: Inglés
- Interfaces: Español

Ejemplo

Clase

```
Product
```

Tabla

```
product
```

Vista

```
product_detail.html
```

Texto mostrado al usuario

```
Agregar al carrito
```

---

## Organización del código

Cada aplicación mantendrá la siguiente estructura:

```
app/

├── admin.py

├── apps.py

├── models.py

├── views.py

├── urls.py

├── forms.py

├── services.py

├── tests/

├── templates/

├── static/

└── migrations/
```

---

# Beneficios de la Arquitectura

- Fácil mantenimiento.
- Código organizado.
- Escalable.
- Preparado para crecimiento.
- Facilita pruebas unitarias.
- Facilita el trabajo colaborativo.
- Sigue las buenas prácticas recomendadas para proyectos Django de mediana y gran escala.


docs/
│
├── 01-product-vision.md
├── 02-functional-requirements.md
├── 03-non-functional-requirements.md
├── 04-domain-model.md
├── 05-er-diagram.md
├── 06-project-architecture.md
├── 07-data-dictionary.md
├── 08-use-cases.md
├── 09-wireframes.md
├── 10-development-roadmap.md
├── 11-deployment.md
└── README.md