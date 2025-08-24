# Proyecto CRUD con Django REST Framework

Este es un proyecto personal de un CRUD utilizando **Django** y **Django REST Framework (DRF)** para exponer una API, con soporte para **CORS** y documentación automática con **CoreAPI**.

---

## Tecnologías utilizadas
- **Python**: `python --version`
- **Node.js**: `node --version`
- **Django**
- **Django REST Framework**
- **Django CORS Headers**
- **CoreAPI**

---

## Instalación y configuración

### 1. Crear entorno virtual
```bash
pip install virtualenv
python -m venv venv
````

Activar el entorno virtual:

* En **Windows**:

  ```bash
  .\venv\Scripts\activate
  ```
* En **Linux/MacOS**:

  ```bash
  source venv/bin/activate
  ```

Selecciona este entorno virtual como **Python Interpreter** en tu editor.

---

### 2. Instalar dependencias

```bash
pip install django
pip install djangorestframework
pip install django-cors-headers
pip install coreapi
```

---

### 3. Crear proyecto y aplicación

```bash
django-admin startproject django-crud-api
cd django-crud-api
python manage.py startapp tasks
```

Agregar la aplicación al archivo **`settings.py`** en `INSTALLED_APPS`:

```python
INSTALLED_APPS = [
    ...
    "tasks",
    "rest_framework",
    "corsheaders",
]
```

---

### 4. Configuración de CORS

En **`settings.py`**, agregar el middleware:

```python
MIDDLEWARE = [
    "corsheaders.middleware.CorsMiddleware",
    "django.middleware.common.CommonMiddleware",
    ...
]
```

Y al final del archivo:

```python
CORS_ALLOWED_ORIGINS = [
    # Ejemplo: "http://localhost:3000",
]
```

---

### 5. Migraciones y base de datos

Ejecutar migraciones iniciales:

```bash
python manage.py migrate
```

Si creas modelos en la aplicación **tasks**:

```bash
python manage.py makemigrations tasks
python manage.py migrate tasks
```

---

### 6. Superusuario

Para acceder al panel de administración:

```bash
python manage.py createsuperuser
```

Registrar modelos en **`tasks/admin.py`**:

```python
from django.contrib import admin
from .models import Task

admin.site.register(Task)
```

---

### 7. Estructura de la API

* **Modelos** → Representan las tablas en la base de datos.
* **Serializadores** → Transforman datos de Python a JSON y viceversa.
* **Vistas** → Controlan las operaciones (crear, listar, actualizar, eliminar).
* **Rutas** → Definen las URLs de acceso a las vistas.

---

### 8. Documentación automática

Agregar en **`settings.py`**:

```python
REST_FRAMEWORK = {
    "DEFAULT_SCHEMA_CLASS": "rest_framework.schemas.coreapi.AutoSchema",
}
```

---

### 9. Ejecutar servidor

```bash
python manage.py runserver
```

Accede a la aplicación en:
[http://127.0.0.1:8000](http://127.0.0.1:8000)

---

## 📖 Endpoints esperados (ejemplo)

| Método | Endpoint     | Descripción              |
| ------ | ------------ | ------------------------ |
| GET    | /tasks/      | Listar todas las tareas  |
| POST   | /tasks/      | Crear una nueva tarea    |
| GET    | /tasks/{id}/ | Obtener una tarea por ID |
| PUT    | /tasks/{id}/ | Actualizar una tarea     |
| DELETE | /tasks/{id}/ | Eliminar una tarea       |

---

## Notas

* Usar `rest_framework` para crear APIs más rápidas.
* `corsheaders` permite que el frontend (ej: React, Vue) consuma la API.
* `coreapi` habilita la documentación interactiva.

---
