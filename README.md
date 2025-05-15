# Bookstore - Plataforma de Compra y Venta de Libros

## Descripción

**Bookstore** es una aplicación web desarrollada con Flask que permite a los usuarios registrarse, publicar libros para vender y comprar libros de otros usuarios. La aplicación incluye gestión de catálogo, sistema de autenticación, procesamiento de pagos, opciones de envío y funcionalidades administrativas.

## Características

- **Autenticación de usuarios**: Registro, inicio de sesión y cierre de sesión  
- **Gestión de catálogo**: Ver, añadir, editar y eliminar libros  
- **Compra de libros**: Selección de cantidad, procesamiento de pagos y opciones de envío  
- **Panel de administración**: Gestión de usuarios y estadísticas  
- **Base de datos MySQL**: Almacenamiento seguro y escalable  

## Requisitos

- Python 3.10 o superior  
- Docker y Docker Compose (opcional para despliegue)  
- MySQL Server (configurado a través de RDS de AWS)  
- Navegador web moderno  

## Instalación y Configuración

### Opción 1: Instalación Local

1. Clona el repositorio:
```bash
git clone https://github.com/Juanstevan1/Bookstore-proyecto2
cd bookstore
```

2. Instala las dependencias
```
pip install -r requirements.txt
```
3. Configura la base de datos
   
   - La configuración de la base de datos se encuentra en config.py
   - Asegúrate de que la base de datos MySQL esté accesible

4. Inicializa la base de datos:

  ```
flask shell
>>> from extensions import db
>>> db.create_all()
>>> exit()
  ```

5. Ejecutar la aplicación

  ```
  python app.py
  ```

6. Accede a la aplicación en tu navegador:

```
http://localhost:5000
```

### Opción 2: Despliegue con Docker

1. Clona el repositorio:
   
 ```
git clone <url-del-repositorio>
cd bookstore
```

2. Construye y ejecuta los contenedores con Docker Compose:

```
docker-compose up -d
```

3. Accede a la aplicación en tu navegador:

```
http://localhost:5000
```

### Estructura del Proyecto
```
bookstore/
│
├── app.py # Punto de entrada de la aplicación
├── config.py # Configuración de la aplicación
├── docker-compose.yml # Configuración de Docker Compose
├── Dockerfile # Configuración de Docker
├── extensions.py # Extensiones de Flask
├── requirements.txt # Dependencias de Python
│
├── controllers/ # Controladores por funcionalidad
│ ├── admin_controller.py
│ ├── auth_controller.py
│ ├── book_controller.py
│ ├── delivery_controller.py
│ ├── payment_controller.py
│ └── purchase_controller.py
│
├── models/ # Modelos de la base de datos
│ ├── book.py
│ ├── delivery.py
│ ├── delivery_assignment.py
│ ├── payment.py
│ ├── purchase.py
│ └── user.py
│
└── templates/ # Plantillas HTML
├── add_book.html
├── base.html
├── catalog.html
├── delivery_options.html
├── edit_book.html
├── home.html
├── list_users.html
├── login.html
├── my_books.html
├── payment.html
└── register.html
```

### Configuración de la Base de Datos

1. La aplicación utiliza una base de datos MySQL alojada en AWS RDS. La configuración de conexión se encuentra en config.py:
```
pythonSQLALCHEMY_DATABASE_URI = 'mysql+pymysql://bookstore_user:bookstore_pass@bookstore-db.cr6oemqg45kn.us-east-1.rds.amazonaws.com:3306/bookstore'
```

### Notas Importantes

1. Al iniciar la aplicación por primera vez, se crean automáticamente las tablas en la base de datos y se inicializan los proveedores de entrega.
2. Asegúrate de tener las credenciales correctas para la base de datos.
3. En entornos de producción, deberías cambiar la clave secreta en config.py y deshabilitar el modo de depuración.
4. La aplicación está diseñada para ser ejecutada en un entorno controlado y seguro.
5. La implementación del Objetivo 3 se entregó con un avance del 85%, se logró implementar la gran mayoría de las características propuestas para este objetivo. Sin embargo, una porción menor quedó pendiente de ser finalizada.
