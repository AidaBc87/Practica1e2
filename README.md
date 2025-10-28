# Practica1-curso-django-estatal
primera practica django response
¡Claro! A continuación, te presento un **material didáctico paso a paso**, pensado especialmente para **estudiantes de preparatoria** que están empezando con **Django**. El contenido está explicado de forma clara, sencilla y ordenada, siguiendo las instrucciones que solicitaste, basado en el conocimiento proporcionado y adaptado a nivel **principiante**.

---

# 🎓 **Aplicación: Explicación de las vistas y URLs de Django**  
**Curso: Introducción a Django (Backend Web)**  
**Nivel: Principiante**  
**Dirigido a: Estudiantes de preparatoria**

---

## 🔧 **1. Procedimiento para acceder a la terminal de Windows**

1. Presiona la tecla **Windows** del teclado.
2. Escribe: **"Símbolo del sistema"** o **"cmd"**.
3. Haz clic en **"Símbolo del sistema"** o presiona **Enter**.
4. Se abrirá una ventana negra llamada **CMD (Command Prompt)**. Aquí puedes escribir comandos.

> ✅ Consejo: Puedes escribir `cls` y dar Enter para limpiar la pantalla.

---

## 📁 **2. Procedimiento para crear carpeta de trabajo “practica1”**

En la terminal (cmd), escribe:

```bash
mkdir practica1
```

Esto crea una carpeta llamada **practica1** en la ubicación actual (por ejemplo, en `C:\Users\TuNombre`).

> ✅ Para ver que se creó: escribe `dir` y verás la lista de carpetas y archivos.

---

## 💻 **3. Procedimiento desde terminal CMD para abrir VS Code**

Primero, asegúrate de tener **Visual Studio Code (VS Code)** instalado.

En la terminal, entra a la carpeta:

```bash
cd practica1
```

Luego escribe:

```bash
code .
```

Esto abre **VS Code** con la carpeta `practica1` como carpeta de trabajo.

> ✅ Si no funciona, descarga VS Code desde: https://code.visualstudio.com/

---

## 🐍 **4. Desde terminal verificar la instalación de Python**

Escribe en la terminal:

```bash
python --version
```

o

```bash
py --version
```

Deberías ver algo como:

```
Python 3.10.6
```

> ✅ Si no aparece, debes instalar Python desde: https://www.python.org/downloads/

---

## 🌐 **5. Procedimiento para crear un entorno virtual**

Un entorno virtual es como una "cajita" donde instalas solo lo que necesitas para tu proyecto.

En la terminal (dentro de `practica1`), escribe:

```bash
python -m venv env
```

Esto crea una carpeta llamada **env** que será tu entorno virtual.

---

## 🔌 **6. Procedimiento para activar el entorno virtual**

En Windows, escribe:

```bash
env\Scripts\activate
```

Verás que en la terminal aparece `(env)` al inicio:

```
(env) C:\...\practica1>
```

> ✅ Esto significa que el entorno está activo.

---

## 🧠 **7. Procedimiento para seleccionar intérprete de Python en VS Code**

1. Abre VS Code.
2. Presiona **Ctrl + Shift + P** (para abrir el menú de comandos).
3. Escribe: **"Python: Select Interpreter"** y selecciónalo.
4. Elige el que diga algo como:
   ```
   ./env/Scripts/python.exe
   ```
5. Listo, ahora VS Code usa el Python de tu entorno virtual.

---

## 📦 **8. Procedimiento para instalar Django**

Con el entorno virtual activado, escribe:

```bash
pip install django
```

Este comando descarga e instala Django.

> ✅ Espera a que termine (puede tardar un momento).

---

## 📏 **9. Procedimiento para ver la versión de Django**

Escribe:

```bash
django-admin --version
```

Verás algo como:

```
4.2.3
```

> ✅ Esto confirma que Django se instaló correctamente.

---

## ❓ **10. Procedimiento para ver comandos de Django**

Escribe:

```bash
django-admin help
```

Te mostrará todos los comandos disponibles, como `startproject`, `startapp`, etc.

---

## 🛠️ **11. Procedimiento para crear proyecto “backend_servidor” sin duplicar carpeta**

Para evitar carpetas duplicadas, usa un punto al final:

```bash
django-admin startproject backend_servidor .
```

> ✅ El punto (`.`) significa "aquí", así el proyecto se crea dentro de `practica1` sin crear una carpeta extra.

---

## ▶️ **12. Procedimiento para ejecutar el servidor Django**

Escribe:

```bash
python manage.py runserver
```

Verás un mensaje como:

```
Starting development server at http://127.0.0.1:8000/
```

> ✅ Presiona **Ctrl + C** para detenerlo después.

---

## 🌍 **13. Procedimiento para cambiar idioma a es-mx en settings.py**

1. Abre en VS Code el archivo:
   ```
   backend_servidor/settings.py
   ```
2. Busca la línea:
   ```python
   LANGUAGE_CODE = 'en-us'
   ```
3. Cámbiala a:
   ```python
   LANGUAGE_CODE = 'es-mx'
   ```
4. También busca:
   ```python
   USE_TZ = True
   ```
   Y justo arriba, asegúrate de tener:
   ```python
   USE_I18N = True
   ```

> ✅ Esto cambia el idioma de la interfaz a español (México).

---

## ⏹️ **14. Parar servidor**

En la terminal, mientras el servidor está corriendo, presiona:

```
Ctrl + C
```

Y luego escribe `y` y da Enter si te lo pide.

---

## 🧩 **15. Procedimiento para crear la aplicación “app_peticiones”**

Dentro de la carpeta `practica1`, con el entorno activado, escribe:

```bash
python manage.py startapp app_peticiones
```

Esto crea una carpeta llamada **app_peticiones** con los archivos necesarios.

---

## 📥 **16. Procedimiento para registrar app_peticiones en backend_servidor**

Abre el archivo:

```
backend_servidor/settings.py
```

Busca la lista `INSTALLED_APPS` y agrega `'app_peticiones'`:

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'app_peticiones',  # ← Aquí agregas tu app
]
```

> ✅ Así Django sabe que existe tu aplicación.

---

## 🔗 **17. Procedimiento para incluir la ruta de app_peticiones en urls.py de backend_servidor**

Abre:

```
backend_servidor/urls.py
```

Agrega `include` en la importación:

```python
from django.contrib import admin
from django.urls import path, include  # ← incluye "include"
```

Luego, en `urlpatterns`, agrega:

```python
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('app_peticiones.urls')),  # ← nueva línea
]
```

> ✅ Esto conecta las URLs de tu app con el proyecto principal.

---

## ⚙️ **18. Realizar configuraciones en settings.py y urls.py de backend_servidor**

Ya hiciste ambas:
- En `settings.py`: agregaste `'app_peticiones'` a `INSTALLED_APPS`.
- En `urls.py`: agregaste `include('app_peticiones.urls')`.

✅ ¡Listo! El proyecto está configurado.

---

## 💬 **19. En views.py de app_peticiones agregar función `inicio`**

Abre el archivo:

```
app_peticiones/views.py
```

Agrega este código:

```python
from django.http import HttpResponse

def inicio(request):
    return HttpResponse("Hola 20 curso de Django")
```

> ✅ Esta función devuelve un mensaje cuando alguien entra a la página.

---

## 📎 **20. Crear el archivo urls.py en app_peticiones con la ruta “inicio”**

1. Dentro de la carpeta `app_peticiones`, crea un archivo nuevo llamado `urls.py`.
2. Escribe dentro:

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.inicio, name='inicio'),
]
```

> ✅ Esto dice: cuando entren a la página principal, muestra la función `inicio`.

---

## ▶️ **30. Ejecutar servidor**

En la terminal (con el entorno activado):

```bash
python manage.py runserver
```

---

## 🌐 **31. Procedimiento para ver la página de inicio en el navegador**

1. Abre tu navegador (Chrome, Firefox, etc.).
2. Escribe en la barra de direcciones:

```
http://127.0.0.1:8000
```

3. Deberás ver:

```
Hola 20 curso de Django
```

✅ ¡Tu primera página en Django!

---

## 🔍 **32. Procedimiento para inspeccionar página**

1. En el navegador, presiona **F12** o **clic derecho → Inspeccionar**.
2. Verás el código HTML (aunque solo sea texto plano por ahora).
3. Puedes ver la consola, red, etc.

> ✅ Útil para depurar errores.

---

⏹️ **Parar servidor**: Presiona `Ctrl + C` en la terminal.

---

## 🧑‍💼 **33. En views.py agregar función `acerca_de_mi`**

En `app_peticiones/views.py`, agrega:

```python
def acerca_de_mi(request):
    datos = {
        'Nombre': 'Eliseo',
        'Edad': 60,
        'Trabajo': 'cbtis'
    }
    info = f"<h1>Acerca de mí</h1><p>Nombre: {datos['Nombre']}</p><p>Edad: {datos['Edad']}</p><p>Trabajo: {datos['Trabajo']}</p>"
    return HttpResponse(info)
```

> ✅ Envía un diccionario y muestra los datos en formato HTML.

---

## 🔗 **34. Agregar segunda ruta en urls.py de app_peticiones**

Abre `app_peticiones/urls.py` y agrega:

```python
path('acerca/', views.acerca_de_mi, name='acerca_de_mi'),
```

Queda así:

```python
urlpatterns = [
    path('', views.inicio, name='inicio'),
    path('acerca/', views.acerca_de_mi, name='acerca_de_mi'),
]
```

---

## ▶️ **35. Ejecutar servidor para ver "Acerca de mí"**

```bash
python manage.py runserver
```

---

## 🌐 **36. Inspeccionar página**

Ve a:

```
http://127.0.0.1:8000/acerca/
```

Verás los datos en formato bonito. Usa **F12** para inspeccionar el HTML.

---

## 👋 **37. En views.py agregar función `hola` con parámetro**

En `views.py`, agrega:

```python
def hola(request, primer_nombre):
    return HttpResponse(f"<h1>¡Hola, {primer_nombre}!</h1>")
```

---

## 🔗 **38. Agregar tercera ruta en urls.py**

En `app_peticiones/urls.py`, agrega:

```python
path('hola/<str:primer_nombre>/', views.hola, name='hola'),
```

> ✅ `<str:primer_nombre>` captura el nombre que escriban en la URL.

---

## ▶️ **39. Ejecutar servidor para ver "hola"**

```bash
python manage.py runserver
```

Abre en el navegador:

```
http://127.0.0.1:8000/hola/Juan
```

Verás: **¡Hola, Juan!**

Puedes cambiar "Juan" por cualquier nombre.

---

## ➕ **40. En views.py agregar función `calcula_suma`**

En `views.py`:

```python
def calcula_suma(request, num1, num2):
    resultado = num1 + num2
    return HttpResponse(f"<h1>La suma de {num1} + {num2} es {resultado}</h1>")
```

---

## 🔗 **41. Agregar cuarta ruta en urls.py**

```python
path('suma/<int:num1>/<int:num2>/', views.calcula_suma, name='calcula_suma'),
```

> ✅ `<int:num1>` y `<int:num2>` solo aceptan números enteros.

---

## ▶️ **42. Ejecutar servidor para ver calcula_suma**

```bash
python manage.py runserver
```

Abre en el navegador:

```
http://127.0.0.1:8000/suma/5/3
```

Verás:

```
La suma de 5 + 3 es 8
```

✅ ¡Funciona!

---

# 🎉 ¡Felicidades!

Has creado tu primera aplicación en Django con:

- Vistas que muestran mensajes.
- URLs que responden a diferentes direcciones.
- Funciones que reciben parámetros.
- Datos enviados desde el código.

---

📌 **Recursos útiles:**
- Documentación de Django: https://docs.djangoproject.com/
- Tutorial usado como base: [Building a Django CRUD Todo App](https://dev.to/aadarsh-nagrath/building-a-django-crud-todo-app-from-scratch-fe3)

---

👨‍🏫 **Profesor:** Eliseo  
📚 **Curso:** Desarrollo Web con Django  
📅 **Nivel:** 1° de Preparatoria (Introducción a Programación)

> ✅ Siguiente clase: Aprenderemos a usar **plantillas HTML** para hacer páginas más bonitas.

--- 

¿Quieres que te dé este material en formato PDF o Word para imprimirlo? Puedo ayudarte.
