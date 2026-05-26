# Django Cinema App

![Django](https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Jazzmin](https://img.shields.io/badge/Admin-Jazzmin-purple?style=for-the-badge)

Sistema desarrollado para la administración de complejos cinematográficos, automatización de carteleras, reserva dinámica de asientos y control de pedidos de dulcería. Desarrollado sobre **Django 5.2**, cuenta con un ecosistema automatizado que genera comprobantes en formato PDF con códigos QR únicos por boleto al confirmar la orden de forma directa, los cuales se envían por correo electrónico (SMTP) y quedan disponibles para su descarga inmediata desde la plataforma web.

---

## Arquitectura y Características del Sistema

### Diseño de Base de Datos y Lógica de Negocio
* **Arquitectura Multi-sucursal (`Cinema`):** Soporte nativo para el control, localización y operación de múltiples complejos cinematográficos en paralelo.
* **Layouts Matriciales de Salas (`Auditorium` & `Seat`):** Generación e inicialización automatizada de estructuras de asientos por sala, utilizando restricciones y validadores estrictos (`MinValueValidator` y `MaxValueValidator`).
* **Integridad Transaccional y Anti-Sobreventa (`Ticket`):** Implementación de restricciones únicas a nivel base de datos mediante `unique_together = (('showtime', 'seat'),)` para mitigar de forma absoluta la colisión o duplicidad de boletos vendidos para una misma función.
* **Módulo de Dulcería y Gestión de Combos (`SnackItem`):** Catálogo dinámico de productos y consumibles integrados con control estricto de disponibilidad y categorías.
* **Flujo de Confirmación Directa de Órdenes (`Order`):** Flujo ágil que unifica la reserva de boletos y snacks en una sola transacción sin necesidad de pasarelas externas. Al confirmar la compra, el sistema procesa el pedido en una transacción ACID, calcula los totales y actualiza los estados al instante.
* **Generación de Tickets en PDF y Códigos QR Dinámicos (`Ticket.qr_code`):** Integración con motores de renderizado de documentos y servicios SMTP. Al confirmar la orden, el sistema genera de manera automatizada un archivo PDF formal (comprobante de entrada) con el desglose de la orden, los asientos asignados y un código QR escaneable. Está disponible para descargalo directamente en la web.
* **Sistema de Fidelización (`Customer`):** Extensión del modelo `User` nativo de Django para la automatización, acumulación y cálculo de puntos de lealtad (`loyalty_pts`) por cada orden confirmada.

### Administración Avanzada (Backoffice)
* Interfaz administrativa, optimizada y completamente responsive mediante la integración de **Jazzmin Theme** (Bootstrap 4 & AdminLTE 3).
* **Ingeniería de Compatibilidad de Base de Datos:** Implementación de overrides en el ORM de Django para omitir las restricciones estrictas de versiones y la sentencia `RETURNING` en motores MariaDB legados (entornos de desarrollo locales como XAMPP 10.4). Esto garantiza inserciones en lote (*bulk operations*) limpias y eficientes sin bloqueos de hilos ni fallos en base de datos.

---

## Demostración Visual

### Funcionamiento de la Plataforma en Tiempo Real
A continuación se muestra una demostración del flujo interactivo del sistema, incluyendo la navegación por el panel de administración **Jazzmin**, la gestión del inventario de salas, dulcería y el flujo del cliente:

<video src="https://github.com/user-attachments/assets/0b11145a-c22b-4339-93f1-e95115fd33a1" controls autoplay loop muted width="100%"></video>

---

### Comprobantes e Interfaces del Sistema

| Comprobante PDF de Entrada (Con QR) | Backoffice Administrativo (Jazzmin) |
| :---: | :---: |
| ![Ticket PDF Generado](https://github.com/user-attachments/assets/fdd7f344-f934-4c01-a2a9-5afaeaf77e16) | ![Panel de Control Administrativo](https://github.com/user-attachments/assets/f7e6f3e6-f4f0-4b66-8a43-d8084296e5aa) |


| Flujo de Experiencia del Cliente |
| :---: |
| **Cartelera de Películas**<br><img src="https://github.com/user-attachments/assets/f93e018e-d51d-4f88-be8a-aae30187cf1f" width="31%"/> &nbsp;&nbsp; **Selección de Asientos**<br><img src="https://github.com/user-attachments/assets/3749f884-fdd1-4f39-9fc3-da2e6ac0a626" width="31%"/> &nbsp;&nbsp; **Catálogo de Dulcería**<br><img src="https://github.com/user-attachments/assets/2327c77d-dd99-4f0d-9e7c-da120c4d553e" width="31%"/> |

## Stack Tecnológico

* **Framework Principal:** Django 5.2+
* **Lenguaje de Programación:** Python 3.x
* **Motor de Base de Datos:** MySQL / MariaDB (Optimizado para XAMPP)
* **UI de Administración:** Jazzmin Admin Theme
* **Comunicaciones:** SMTP Client con soporte TLS (Notificaciones automatizadas vía Gmail con backend personalizado).

---

## Instalación y Configuración Local

Siga estos pasos para clonar, configurar e inicializar el entorno de desarrollo:

### 1. Clonar el repositorio y preparar entorno
```bash
git clone [https://github.com/tu-usuario/django-cinema-app.git](https://github.com/tu-usuario/django-cinema-app.git)
cd django-cinema-app
