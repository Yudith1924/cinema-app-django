# Django Cinema App

![Django](https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![XAMPP](https://img.shields.io/badge/XAMPP-F37623?style=for-the-badge&logo=xampp&logoColor=white)
![Jazzmin](https://img.shields.io/badge/Admin-Jazzmin-purple?style=for-the-badge)

Sistema desarrollado para la administración de complejos cinematográficos, automatización de carteleras, reserva dinámica de asientos y control de pedidos de dulcería. Desarrollado sobre **Django 5.2**, cuenta con un ecosistema automatizado que genera comprobantes en formato PDF con códigos QR únicos por boleto al confirmar la orden de forma directa, los cuales se envían por correo electrónico (SMTP) y quedan disponibles para su descarga inmediata desde la plataforma web.

---

## Arquitectura y Características del Sistema

### Diseño de Base de Datos y Lógica de Negocio
* **Arquitectura Multi-sucursal (`Cinema`):** Soporte nativo para el control, localización y operación de múltiples complejos cinematográficos en paralelo.
* **Layouts Matriciales de Salas (`Auditorium` & `Seat`):** Generación e inicialización automatizada de estructuras de asientos por sala, utilizando restricciones y validadores estrictos.
* **Integridad Transaccional y Anti-Sobreventa (`Ticket`):** Implementación de restricciones únicas a nivel base de datos para mitigar de forma absoluta la duplicidad de boletos vendidos para una misma función.
* **Módulo de Dulcería y Gestión de Combos (`SnackItem`):** Catálogo dinámico de productos y consumibles integrados con control estricto de disponibilidad.
* **Flujo de Confirmación Directa de Órdenes (`Order`):** Flujo ágil que unifica la reserva de boletos y snacks en una sola transacción ACID.
* **Notificaciones Automatizadas por Correo (Servicio SMTP):** Envío automático de comprobantes detallando el resumen de la compra y confirmación de reserva.
* **Generación de Tickets en PDF y Códigos QR:** Confirmación visual y archivo PDF descargable con código QR dinámico generado exclusivamente en la interfaz web.
* **Sistema de Fidelización (`Customer`):** Extensión del modelo `User` nativo para la acumulación y cálculo de puntos de lealtad (`loyalty_pts`).

### Administración Avanzada (Backoffice)
* Interfaz administrativa optimizada y responsive mediante **Jazzmin Theme** (Bootstrap 4 & AdminLTE 3).
* **Ingeniería de Compatibilidad:** Overrides en el ORM para garantizar operaciones en lote (`bulk operations`) eficientes en entornos MariaDB/MySQL.

---

## Demostración Visual

### Funcionamiento de la Plataforma en Tiempo Real
<video src="https://github.com/user-attachments/assets/7b0a3b36-5b40-4aa2-a148-9430067685da" controls autoplay loop muted width="100%"></video>

### Comprobantes e Interfaces del Sistema

| Comprobante PDF (Con QR) | Back Administrativo (Jazzmin) |
| :---: | :---: |
| <img src="https://github.com/user-attachments/assets/fdd7f344-f934-4c01-a2a9-5afaeaf77e16" width="380" /> | <img src="https://github.com/user-attachments/assets/f7e6f3e6-f4f0-4b66-8a43-d8084296e5aa" width="480" /> |

| Cartelera | Snacks | Selección de Asientos |
| :---: | :---: | :---: |
| <img src="https://github.com/user-attachments/assets/f93e018e-d51d-4f88-be8a-aae30187cf1f" width="280"/> | <img src="https://github.com/user-attachments/assets/3749f884-fdd1-4f39-9fc3-da2e6ac0a626" width="280"/> | <img src="https://github.com/user-attachments/assets/2327c77d-dd99-4f0d-9e7c-da120c4d553e" width="280"/> |

---

## Instalación y Configuración Local

Sigue estos pasos para inicializar el entorno de desarrollo:

1. **Clonar el repositorio:**
```bash
   git clone [https://github.com/Yudith1924/django-cinema-app.git](https://github.com/Yudith1924/django-cinema-app.git)
   cd django-cinema-app

```

2. **Crear y activar entorno virtual:**
```bash
python -m venv venv
# En Windows:
venv\Scripts\activate

```


3. **Instalar dependencias:**
```bash
pip install -r requirements.txt

```


4. **Configurar base de datos y migraciones:**
* Crea tu base de datos en MySQL/MariaDB.
* Configura tus credenciales en `settings.py` (o mediante un archivo `.env`).


```bash
python manage.py makemigrations
python manage.py migrate

```


5. **Crear usuario administrador y ejecutar:**
```bash
python manage.py createsuperuser
python manage.py runserver

```



---

## Stack Tecnológico

* **Framework:** Django 5.2+
* **Lenguaje:** Python 3.x
* **Base de Datos:** MySQL / MariaDB
* **UI:** Jazzmin Admin Theme
* **Servicios:** SMTP Client (TLS)



