# Aplicación 1 — Explorador de arquitectura y flujo de Django

Proyecto didáctico **mínimo** para observar cómo funciona Django internamente desde que llega una URL hasta que se renderiza un template.

---

## Requisitos previos

- Python 3.10+ instalado
- Terminal (PowerShell/CMD en Windows, o terminal en Linux/macOS)

Verifica tu instalación:

```bash
python --version
pip --version
````

> En Linux/macOS puede ser `python3` en vez de `python`.

---

## 1) Crear carpeta del proyecto y entrar

```bash
mkdir explorador_django
cd explorador_django
```

---

## 2) Crear y activar entorno virtual (venv)

### Windows (PowerShell)

```bash
python -m venv venv
.\venv\Scripts\Activate.ps1
```

Si PowerShell bloquea la activación por políticas, ejecuta (una vez) como administrador:

```bash
Set-ExecutionPolicy RemoteSigned
```

Luego vuelve a activar:

```bash
.\venv\Scripts\Activate.ps1
```

### Windows (CMD)

```bash
python -m venv venv
venv\Scripts\activate.bat
```

### Linux / macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

Verifica que estás dentro del entorno virtual:

```bash
python -c "import sys; print(sys.executable)"
```

---

## 3) Instalar Django

Actualiza pip e instala Django:

```bash
python -m pip install --upgrade pip
pip install django
```

Verifica versión de Django:

```bash
python -m django --version
```

---

## 4) Crear el proyecto Django

Dentro de la carpeta `explorador_django/` (la que creaste con `mkdir`), ejecuta:

```bash
django-admin startproject explorador_django .
```

> El punto `.` es importante: crea el proyecto **en la carpeta actual**.

Comprueba que existe `manage.py`:

```bash
dir
```

En Linux/macOS:

```bash
ls
```

Deberías ver `manage.py` y la carpeta `explorador_django/`.

---

## 5) Crear la aplicación

Crea la app del curso:

```bash
python manage.py startapp arquitectura
```

---

## 6) Primera migración (tablas base de Django)

Ejecuta migraciones iniciales:

```bash
python manage.py migrate
```

---

## 7) Editar archivos del proyecto (los que “tocamos”)

Ahora debes **modificar/crear** los siguientes archivos (según lo que ya te entregué antes):

* `explorador_django/settings.py` (agregar `arquitectura` y templates DIRS)
* `explorador_django/urls.py` (incluir rutas de la app)
* `arquitectura/urls.py` (crear archivo)
* `arquitectura/views.py` (editar)
* `arquitectura/models.py` (editar, modelo `Nota`)
* `templates/base.html` (crear)
* `templates/arquitectura/home.html` (crear)
* `templates/arquitectura/flujo.html` (crear)
* `templates/arquitectura/mvc.html` (crear)

---

## 8) Crear carpetas de templates

Crea estas carpetas:

### Windows (PowerShell / CMD)

```bash
mkdir templates
mkdir templates\arquitectura
```

### Linux / macOS

```bash
mkdir -p templates/arquitectura
```

---

## 9) Crear migraciones de tu modelo (Nota)

Después de editar `arquitectura/models.py` con el modelo `Nota`, ejecuta:

```bash
python manage.py makemigrations arquitectura
```

Luego aplica:

```bash
python manage.py migrate
```

---

## 10) (Opcional) Crear superusuario para entrar al admin

Si vas a usar `/admin`:

```bash
python manage.py createsuperuser
```

Te pedirá:

* usuario
* email (opcional)
* contraseña

---

## 11) Levantar el servidor

```bash
python manage.py runserver
```

Abre en el navegador:

* `http://127.0.0.1:8000/` → Inicio
* `http://127.0.0.1:8000/flujo/` → Flujo URL → View → Template
* `http://127.0.0.1:8000/mvc/` → MTV mínimo (Model/Template/View)
* `http://127.0.0.1:8000/admin/` → Admin (si creaste superusuario)

Para detener el servidor:

* `CTRL + C`

---

## 12) (Opcional) Guardar dependencias del proyecto

Para dejar el proyecto reproducible:

```bash
pip freeze > requirements.txt
```

---

## 13) Salir del entorno virtual

```bash
deactivate
```

---

## Checklist rápido (para la clase)

```bash
mkdir explorador_django
cd explorador_django
python -m venv venv
# activar venv según SO
pip install django
django-admin startproject explorador_django .
python manage.py startapp arquitectura
python manage.py migrate
# editar/crear archivos del proyecto
python manage.py makemigrations arquitectura
python manage.py migrate
python manage.py runserver
```

---

## Solución rápida de errores comunes

### `python` no encontrado / versión incorrecta

* En Linux/macOS usa `python3`.
* Asegúrate de tener Python agregado al PATH.

### No se activó el entorno virtual

Verifica el ejecutable:

```bash
python -c "import sys; print(sys.executable)"
```

### “No module named django”

Instala Django dentro del venv:

```bash
pip install django
```

### Cambios en templates no se ven

* Revisa que exista `templates/`
* Revisa que `settings.py` tenga `DIRS: [BASE_DIR / "templates"]`
* Reinicia el servidor con `CTRL + C` y `python manage.py runserver`
