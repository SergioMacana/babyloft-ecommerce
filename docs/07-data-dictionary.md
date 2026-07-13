# Diccionario de Datos

## Proyecto

Baby Loft E-commerce

---

# Objetivo

Definir cada una de las entidades del sistema junto con sus atributos, tipos de datos y restricciones.

Este documento servirá como guía para la implementación de los modelos de Django.

---

# Categoria

| Campo | Tipo Django | Restricciones | Descripción |
|---------|------------|---------------|-------------|
| id | BigAutoField | PK | Identificador |
| name | CharField(100) | Unique | Nombre de la categoría |
| slug | SlugField | Unique | URL amigable |
| description | TextField | Blank | Descripción |
| is_active | BooleanField | Default=True | Estado |
| created_at | DateTimeField | Auto Now Add | Fecha creación |
| updated_at | DateTimeField | Auto Now | Fecha actualización |

---

# Producto

| Campo | Tipo Django | Restricciones | Descripción |
|---------|------------|---------------|-------------|
| id | BigAutoField | PK | Identificador |
| category | ForeignKey(Category) | CASCADE | Categoría |
| name | CharField(150) | Required | Nombre |
| slug | SlugField | Unique | URL |
| description | TextField | Blank | Descripción |
| allows_customization | BooleanField | Default=False | Permite bordado |
| customization_max_length | PositiveSmallIntegerField | Null=True | Máximo caracteres |
| is_active | BooleanField | Default=True | Estado |
| created_at | DateTimeField | Auto Now Add | Fecha |
| updated_at | DateTimeField | Auto Now | Fecha |

---

# Variante

| Campo | Tipo Django | Restricciones |
|---------|------------|---------------|
| id | BigAutoField | PK |
| product | ForeignKey(Product) | CASCADE |
| sku | CharField(50) | Unique |
| price | DecimalField(10,2) | Required |
| stock | PositiveIntegerField | Default=0 |
| is_active | BooleanField | Default=True |

---

# ImagenProducto

| Campo | Tipo Django |
|---------|------------|
| id | BigAutoField |
| product | ForeignKey(Product) |
| image | ImageField |
| alt_text | CharField(150) |
| is_primary | BooleanField |

---

# Carrito

| Campo | Tipo Django |
|---------|------------|
| id | UUIDField |
| created_at | DateTimeField |
| updated_at | DateTimeField |

---

# ItemCarrito

| Campo | Tipo Django |
|---------|------------|
| id | BigAutoField |
| cart | ForeignKey(Cart) |
| variant | ForeignKey(Variant) |
| quantity | PositiveIntegerField |
| unit_price | DecimalField(10,2) |
| personalization_text | CharField(20) |
| embroidery_color | CharField(30) |

---

# Comprador

| Campo | Tipo Django |
|---------|------------|
| id | BigAutoField |
| full_name | CharField(150) |
| email | EmailField |
| phone | CharField(20) |

---

# DirecciónEnvio

| Campo | Tipo Django |
|---------|------------|
| id | BigAutoField |
| buyer | ForeignKey(Buyer) |
| department | CharField(100) |
| city | CharField(100) |
| address | CharField(200) |
| neighborhood | CharField(100) |
| references | TextField |

---

# Pedido

| Campo | Tipo Django |
|---------|------------|
| id | BigAutoField |
| order_number | CharField(20) |
| buyer | ForeignKey(Buyer) |
| shipping_address | ForeignKey(ShippingAddress) |
| total | DecimalField(10,2) |
| status | CharField(30) |
| payment_method | CharField(30) |
| created_at | DateTimeField |

---

# DetallePedido

| Campo | Tipo Django |
|---------|------------|
| id | BigAutoField |
| order | ForeignKey(Order) |
| variant | ForeignKey(Variant) |
| product_name | CharField(150) |
| quantity | PositiveIntegerField |
| unit_price | DecimalField(10,2) |
| subtotal | DecimalField(10,2) |
| personalization_text | CharField(20) |
| embroidery_color | CharField(30) |

---

# Pago

| Campo | Tipo Django |
|---------|------------|
| id | BigAutoField |
| order | OneToOneField(Order) |
| provider | CharField(30) |
| reference | CharField(100) |
| amount | DecimalField(10,2) |
| status | CharField(30) |
| transaction_date | DateTimeField |

---

# Convenciones

## Todos los modelos tendrán

- created_at
- updated_at

excepto los modelos históricos.

## Todos los nombres de tablas estarán en singular.

## Todo el código estará en inglés.

## La interfaz será completamente en español.