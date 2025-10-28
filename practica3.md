¡Claro\! Un ejercicio excelente después de la guía inicial es aprender a usar **plantillas (templates)**. Esto te permite crear páginas web completas en HTML, CSS y JavaScript, en lugar de solo devolver texto simple.

Aquí tienes el siguiente paso: **Crear una Plantilla HTML Básica**. 🎨

-----

## 🎨 Paso 9: Usar Plantillas (Templates) para HTML

En Django, una **Plantilla** es un archivo HTML que tiene marcadores especiales de Django.

### A. Crear la Carpeta de Plantillas

1.  **Crea una Carpeta:** Dentro de la carpeta de tu aplicación (`app_principal/`), crea una nueva carpeta llamada **`templates`**.

2.  **Crea una Subcarpeta:** Dentro de **`templates/`**, crea otra carpeta con el mismo nombre de tu aplicación, **`app_principal`**.

      * **Estructura de Carpetas (Deberías tener):**
        ```
        app_principal/
        ├── templates/
        │   └── app_principal/
        │       └── (aquí irá el archivo HTML)
        ├── views.py
        └── urls.py
        ```

### B. Crear el Archivo HTML de la Plantilla

1.  **Crear el Archivo:** Dentro de la carpeta `app_principal/templates/app_principal/`, crea un nuevo archivo llamado **`inicio.html`**.

2.  **Pegar el Siguiente Código en `inicio.html`:**

    ```html
    <!DOCTYPE html>
    <html lang="es">
    <head>
        <meta charset="UTF-8">
        <title>Mi Página Principal</title>
        <style>
            body { font-family: sans-serif; text-align: center; margin-top: 50px; background-color: #f4f4f9; }
            h1 { color: #007bff; }
            p { font-size: 1.2em; }
        </style>
    </head>
    <body>
        <h1>¡Bienvenido a la Web de Django!</h1>
        <p>Esta página fue creada usando una plantilla HTML.</p>
        <p>¡El siguiente paso es añadir una imagen!</p>
    </body>
    </html>
    ```

### C. Modificar la Vista para Usar la Plantilla

Ahora, cambia la función de la Vista para que cargue y muestre este archivo HTML en lugar del simple texto.

1.  **Abrir `app_principal/views.py`** y modificarlo:

    ```python
    from django.shortcuts import render # Importamos la función render

    # Esta función ahora usa render para cargar la plantilla
    def hello_world(request):
        # La función render busca 'app_principal/inicio.html'
        # en las carpetas de 'templates' que configuramos en el Paso 6.
        return render(request, 'app_principal/inicio.html') 
    ```

### D. Ver el Resultado

1.  **Ejecutar el Servidor:** Si lo detuviste, vuelve a la terminal y ejecuta:

    ```bash
    python manage.py runserver
    ```

2.  **Ver tu Página:** Ve a `http://127.0.0.1:8000/`.

    **Resultado Esperado:** Ahora verás una página con un **título grande, texto centrado y un fondo de color** gracias al código HTML y CSS de tu plantilla.

-----

**Siguiente Reto:** ¿Quieres aprender a usar la base de datos de Django para guardar información, como un listado de tareas? 💾