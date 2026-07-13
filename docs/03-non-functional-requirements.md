# Requisitos No Funcionales

### Rendimiento 

RNF-001

El tiempo de respuesta promedio no deberá superar los 2 segundos para operaciones comunes.

RNF-002

El catálogo deberá soportar al menos 500 productos sin degradación perceptible.

### Seguridad 

RNF-003

Toda la aplicación utilizará HTTPS en producción.

RNF-004

Las contraseñas de los administradores estarán cifradas mediante los mecanismos de Django.

RNF-005

El sistema estará protegido contra CSRF, XSS y SQL Injection mediante las protecciones nativas de Django.

### Disponibilidad

RNF-006

El sistema deberá estar disponible el 99% del tiempo en producción.

### Usabilidad

RNF-007

El sitio deberá ser responsive.

RNF-008

El proceso de compra deberá completarse sin crear una cuenta.

RNF-009

La navegación deberá ser intuitiva y consistente.

### Mantenibilidad

RNF-010

El código seguirá la guía PEP 8.

RNF-011

El proyecto estará organizado por aplicaciones Django.

RNF-012

Toda funcionalidad nueva deberá implementarse mediante una rama independiente y un Pull Request.

### Compatibilidad

RNF-013

El sistema será compatible con Chrome, Edge, Firefox y Safari en sus versiones recientes.

