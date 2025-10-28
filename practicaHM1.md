¡Excelente! Aquí tienes una guía paso a paso y fácil de seguir para que los estudiantes de preparatoria creen un proyecto básico en Django en una computadora con Windows. 🚀
💻 Paso 1: Configuración Inicial (Instalar Python y Pip)
Django funciona con Python, así que es lo primero que necesitamos.
1.	Descargar Python: Ve al sitio web oficial de Python y descarga el instalador más reciente para Windows (asegúrate de que sea la versión 3.x).
2.	Instalar Python: Ejecuta el instalador. MUY IMPORTANTE: Marca la casilla que dice "Add Python X.X to PATH" al inicio del instalador. Esto es crucial para que todo funcione fácilmente desde la línea de comandos. Luego, haz clic en "Install Now".
________________________________________
🐍 Paso 2: Crear el Entorno Virtual (Virtual Environment)
Un entorno virtual es un espacio aislado para tu proyecto. Esto evita conflictos entre las dependencias de diferentes proyectos.
1.	Abrir la Terminal/CMD: Presiona la tecla Windows y escribe cmd (o "Símbolo del sistema").
2.	Crear una Carpeta para el Proyecto: Usa los siguientes comandos para crear una carpeta y entrar en ella. Sustituye MiProyectoDjango por el nombre que quieras darle a la carpeta principal de tu proyecto.
Bash
mkdir MiProyectoDjango
cd MiProyectoDjango
3.	Crear el Entorno Virtual: Ejecuta este comando dentro de la carpeta:
Bash
python -m venv venv
Esto crea una carpeta llamada venv que contiene todo lo necesario para el entorno virtual.
4.	Activar el Entorno Virtual: Para comenzar a usarlo, activa el entorno:
Bash
venv\Scripts\activate
Si lo hiciste correctamente, verás (venv) al inicio de la línea de comandos. ¡Estás dentro del entorno!
________________________________________
✨ Paso 3: Instalar Django
Ahora, instala el framework Django dentro de tu entorno virtual.
1.	Instalar Django: Usa el gestor de paquetes de Python, pip:
Bash
pip install django
Esto descarga e instala Django y todas sus dependencias.
________________________________________
🏗️ Paso 4: Crear el Proyecto Django
Un proyecto Django es el contenedor de la configuración y de una o más aplicaciones.
1.	Crear el Proyecto: Dentro de la carpeta MiProyectoDjango y con el entorno activado, ejecuta (sustituye configuracion_sitio por el nombre que quieras darle a la configuración de tu proyecto, se recomienda que sea diferente al nombre de la carpeta principal):
Bash
django-admin startproject configuracion_sitio .
El punto (.) al final es importante; le dice a Django que cree los archivos de configuración dentro de la carpeta actual.
2.	Estructura de Carpetas (Deberías ver):
3.	MiProyectoDjango/  <-- Carpeta principal
4.	├── venv/
5.	├── manage.py       <-- Archivo principal de comandos
6.	└── configuracion_sitio/
7.	    └── (archivos de configuración)
________________________________________
🏃 Paso 5: Ejecutar el Servidor de Desarrollo
¡Es hora de ver que todo funciona!
1.	Ejecutar el Servidor: Usa el archivo manage.py para iniciar el servidor de prueba:
Bash
python manage.py runserver
2.	Abrir el Navegador: El servidor se iniciará. Abre tu navegador y escribe la siguiente dirección:
3.	http://127.0.0.1:8000/
4.	Resultado Esperado: Deberías ver una página de bienvenida que dice "The install worked successfully! Congratulations!" con un cohete. 🚀
5.	Detener el Servidor: Vuelve a la terminal y presiona Ctrl + C para detener el servidor.
________________________________________
🧩 Paso 6: Crear una Aplicación (La Lógica de tu Sitio)
En Django, una aplicación es un módulo que hace algo específico (por ejemplo, una aplicación de blog, una de usuarios, etc.).
1.	Crear la Aplicación: Detén el servidor (si está corriendo) y ejecuta (sustituye app_principal por el nombre de tu aplicación, por ejemplo blog o paginas):
Bash
python manage.py startapp app_principal
Ahora tendrás una nueva carpeta llamada app_principal/ dentro de MiProyectoDjango.
2.	Registrar la Aplicación: Abre el archivo configuracion_sitio/settings.py y busca la sección INSTALLED_APPS. Agrega el nombre de tu aplicación:
Python
# configuracion_sitio/settings.py
# ...
INSTALLED_APPS = [
    # ... otras apps ...
    'app_principal',  # <--- ¡Añade esta línea!
]
________________________________________
📝 Paso 7: Crear tu Primera Página (Hello World)
Vamos a configurar la aplicación para que muestre un simple mensaje.
A. Definir la Vista (Lógica)
La Vista (views.py) es la función que maneja la solicitud web y devuelve una respuesta.
1.	Abrir app_principal/views.py y reemplaza su contenido con esto:
Python
from django.shortcuts import render
from django.http import HttpResponse # Importamos HttpResponse

def hello_world(request):
    # Esta función devuelve una respuesta simple de texto
    return HttpResponse("<h1>¡Hola, estudiantes! Este es mi primer proyecto Django.</h1>")
B. Mapear la URL (Dirección)
Necesitamos decirle a Django qué URL (dirección) debe ejecutar la función hello_world.
1.	Crear el Archivo de URLs de la Aplicación: Dentro de la carpeta app_principal/, crea un nuevo archivo llamado urls.py.
2.	Pegar el Siguiente Código en el Nuevo app_principal/urls.py:
Python
from django.urls import path
from . import views # Importamos las vistas (funciones) de la aplicación

urlpatterns = [
    # Cuando la URL esté vacía (''), llama a la función views.hello_world
    path('', views.hello_world, name='inicio'),
]
C. Conectar las URLs de la Aplicación al Proyecto
El proyecto principal necesita saber dónde buscar las URLs de la aplicación.
1.	Abrir el Archivo de URLs del Proyecto: configuracion_sitio/urls.py
2.	Importar include y Conectar la Aplicación: Edita este archivo para que se vea así:
Python
from django.contrib import admin
from django.urls import path, include # <--- Importar 'include'

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('app_principal.urls')), # <--- ¡Añadir esta línea!
]
Esto le dice al proyecto: "Para la URL vacía (''), busca las rutas en el archivo app_principal.urls".
________________________________________
🎉 Paso 8: Ver el Resultado Final
1.	Ejecutar el Servidor:
Bash
python manage.py runserver
2.	Ver tu Página: Ve a http://127.0.0.1:8000/ en tu navegador. ¡Deberías ver tu mensaje personalizado!
¡Felicidades, has creado y configurado un proyecto básico de Django!
________________________________________
¿Te gustaría que te muestre cómo usar plantillas (templates) en Django para que puedas crear una página HTML más compleja en lugar de solo mostrar texto?