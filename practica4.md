¡Claro\! El siguiente ejercicio fundamental en Django es **trabajar con la base de datos** para crear una aplicación funcional, como una lista de tareas (To-Do List). Esto involucra los conceptos de **Modelos** y el panel de **Administración** de Django. 💾

Aquí tienes el reto: **Crear un Modelo y Acceder al Panel de Administración.**

-----

## 💾 Paso 10: Configurar la Base de Datos

Django usa por defecto **SQLite**, que es una base de datos ligera que no requiere instalación adicional.

1.  **Ejecutar Migraciones:** Las *migraciones* son comandos que le dicen a Django que configure la base de datos con las tablas iniciales que necesita el *framework*.
    Asegúrate de estar en el directorio `MiProyectoDjango/` con el entorno virtual activado y ejecuta:
    ```bash
    python manage.py migrate
    ```
    *Verás muchos mensajes de `OK` a la derecha. Esto creó el archivo `db.sqlite3` en tu carpeta.*

-----

## 👤 Paso 11: Crear un Superusuario (Administrador)

Necesitas una cuenta para acceder al panel de administración de Django, donde podrás gestionar los datos de tu aplicación.

1.  **Crear Superusuario:** Ejecuta el siguiente comando y sigue las instrucciones (te pedirá un nombre de usuario, email y contraseña):

    ```bash
    python manage.py createsuperuser
    ```

      * **Recomendación:** Usa `admin` como nombre de usuario y una contraseña simple para este ejercicio.\*

2.  **Verificar el Panel de Administración:**

      * Ejecuta el servidor: `python manage.py runserver`
      * Abre tu navegador y ve a la dirección: `http://127.0.0.1:8000/admin/`
      * Ingresa con las credenciales que acabas de crear. ¡Verás el panel de administración de Django\!

-----

## 📋 Paso 12: Crear el Modelo (La Estructura de Datos)

Un **Modelo** es una clase de Python que representa una tabla en la base de datos. Definiremos la estructura para una Tarea.

1.  **Abrir `app_principal/models.py`** y pega el siguiente código:

    ```python
    from django.db import models

    # Definimos la tabla Tarea
    class Tarea(models.Model):
        # Campos de la tabla:
        
        # Un campo de texto corto, obligatorio
        titulo = models.CharField(max_length=200) 
        
        # Un campo booleano (verdadero/falso)
        completada = models.BooleanField(default=False) 
        
        # Método que define cómo se muestra el objeto en el Admin
        def __str__(self):
            return self.titulo
    ```

-----

## 🔄 Paso 13: Migrar el Nuevo Modelo

Cada vez que cambies el archivo `models.py`, debes decirle a Django que actualice la base de datos en dos pasos:

1.  **Crear la Migración:** Le dice a Django cómo actualizar la base de datos.

    ```bash
    python manage.py makemigrations app_principal
    ```

    *Verás un mensaje diciendo que se creó un archivo de migración.*

2.  **Aplicar la Migración:** Ejecuta los cambios en la base de datos real.

    ```bash
    python manage.py migrate
    ```

    *Verás un mensaje de `OK` en `app_principal`.*

-----

## 🛠️ Paso 14: Registrar el Modelo en el Panel de Administración

Para que puedas agregar y modificar tareas usando el panel que acabas de ver, debes registrar tu modelo.

1.  **Abrir `app_principal/admin.py`** y edítalo de esta manera:

    ```python
    from django.contrib import admin
    from .models import Tarea # Importa el modelo Tarea que creaste

    # Registra el modelo para que aparezca en el panel de administración
    admin.site.register(Tarea)
    ```

-----

## ✅ Paso 15: Probar y Agregar Datos

1.  **Ejecutar el Servidor:** `python manage.py runserver`
2.  **Acceder al Admin:** Ve a `http://127.0.0.1:8000/admin/` e inicia sesión.
3.  **Ver tu Modelo:** Ahora verás una sección llamada **App Principal** y dentro el enlace **Tareas**.
4.  **Agregar una Tarea:**
      * Haz clic en **"Añadir Tarea"** (o "Add Tarea").
      * Escribe un **título** (ej: "Estudiar Django").
      * Deja **Completada** sin marcar.
      * Haz clic en **"Guardar"**.
      * Repite y añade una segunda tarea, marcando esta vez **Completada**.

¡Felicidades\! Has creado tu primer modelo de base de datos y has gestionado datos usando el panel de administración de Django.

El siguiente paso sería **mostrar esas tareas en la página web** que creaste con la plantilla. ¿Quieres continuar?