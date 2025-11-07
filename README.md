#  Agente IA Text-to-SQL para Gestión de Inventario (Flask + MySQL)

Este proyecto desarrolla un **Agente Inteligente** capaz de convertir consultas en **Lenguaje Natural (Español)** en sentencias **SQL válidas** para la gestión y consulta de un sistema de inventario. El sistema está construido con un servidor web **Flask**, utiliza la API de **Groq** como motor de traducción y se conecta a una base de datos **MySQL**.

##  Características Principales

* **Traducción IA:** Uso de la API de Groq (modelo Llama-3.1) para una traducción rápida y precisa de NL a SQL (incluyendo `SELECT`, `INSERT`, `UPDATE`, `DELETE`).
* **Interfaz Web Moderna:** Aplicación web con un diseño limpio y funcional  que permite al usuario interactuar con la base de datos sin escribir código.
* **Base de Datos MySQL:** Orientado al esquema de gestión de inventario (`tienda_inventario`).
* **Seguridad:** Implementación de lógica de validación para prevenir la ejecución de consultas peligrosas (`DROP`, `TRUNCATE`).

## ⚙️ Esquema de Base de Datos

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
