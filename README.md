#  Agente IA Text-to-SQL para Gestión de Inventario (Flask + MySQL)

Este proyecto desarrolla un **Agente Inteligente** capaz de convertir consultas en **Lenguaje Natural (Español)** en sentencias **SQL válidas** para la gestión y consulta de un sistema de inventario. El sistema está construido con un servidor web **Flask**, utiliza la API de **Groq** como motor de traducción y se conecta a una base de datos **MySQL**.

##  Características Principales

* **Traducción IA:** Uso de la API de Groq (modelo Llama-3.1) para una traducción rápida y precisa de NL a SQL (incluyendo `SELECT`, `INSERT`, `UPDATE`, `DELETE`).
* **Interfaz Web Moderna:** Aplicación web con un diseño limpio y funcional  que permite al usuario interactuar con la base de datos sin escribir código.
* **Base de Datos MySQL:** Orientado al esquema de gestión de inventario (`tienda_inventario`).
* **Seguridad:** Implementación de lógica de validación para prevenir la ejecución de consultas peligrosas (`DROP`, `TRUNCATE`).

##  Esquema de Base de Datos

El agente interactúa con el esquema `tienda_inventario`, compuesto por las siguientes tablas principales:

| Tabla | Descripción | Campos Clave (PK) |
| :--- | :--- | :--- |
| **productos** | Catálogo principal del inventario con stock y precios. | `id`, `nombre`, `categoria`, `precio`, `stock` |
| **ventas** | Registro de transacciones históricas. | `id`, `producto_id`, `cantidad`, `fecha` |

---

##  Funcionalidades Demostrables

El agente puede manejar las siguientes operaciones de gestión de inventario:

| Categoría | Ejemplos de Prompt al Agente | Sentencia SQL Esperada |
| :--- | :--- | :--- |
| **Consultas** | "Muestra el stock actual de la Laptop Pro" | `SELECT stock FROM productos WHERE nombre = 'Laptop Pro';` |
| **Agregación** | "¿Cuál es el precio promedio de los productos de Electrónica?" | `SELECT AVG(precio) FROM productos WHERE categoria = 'Electrónica';` |
| **Inserción** | "Añadir un producto llamado 'Libreta' en Oficina con 50 unidades en stock." | `INSERT INTO productos...` |
| **Modificación** | "Actualizar stock de 'Laptop Pro' a 20 unidades." | `UPDATE productos SET stock = 20...` |

---

##  Instalación y Configuración

### 1. Requisitos

* Python 3.x
* Servidor **MySQL** activo.
* Una clave API de **Groq** (disponible en [link text](https://groq.com/)).

### 2. Estructura del Proyecto
Agente_SQL_Final/ ├── venv/ ├── templates/ │ └── index.html # Interfaz de usuario (Frontend) ├── static/ │ └── style.css # Archivo de estilos CSS └── app.py # Servidor Flask, Lógica y Conexión a BD

### 3. Configuración de Entorno (Implícita en app.py)

Asegúrate de configurar tus credenciales dentro del archivo `app.py`:

```python
# Reemplaza con tus credenciales y clave Groq
GROQ_API_KEY = "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"
    "database": "tienda_inventario",
    "user": "root",
    "password": "1234" 
}
# 1. Crear entorno virtual (si no existe)
python -m venv venv 

# 2. Activar entorno virtual
# En Windows:
venv\Scripts\activate
# En Linux/macOS:
source venv/bin/activate

# 3. Instalar librerías
pip install Flask mysql-connector-python groq
Ejecución del Agente
Asegúrate de que tu servidor MySQL esté encendido y que la base de datos tienda_inventario exista.

Bash

python app.py
