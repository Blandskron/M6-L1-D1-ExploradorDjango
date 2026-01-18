# Actividad M6-L1 — Introducción a Django y su Ecosistema

## 1) ¿Qué es Django?

**¿Qué es Django?**  
Django es un framework web de alto nivel para Python que facilita construir aplicaciones web completas de forma ordenada y segura, integrando componentes comunes (enrutamiento, plantillas, ORM, autenticación, panel admin, etc.).

**¿Qué tipo de framework es Django?**  
Es un **framework web** (server-side) para construir aplicaciones web siguiendo un patrón de arquitectura tipo **MTV** (Model–Template–View), derivado del MVC.

**¿Qué tipo de aplicaciones permite construir?**  
Permite construir:
- Sitios web tradicionales (páginas con templates renderizados en servidor)
- Aplicaciones empresariales (intranets, ERPs, CRMs, paneles de administración)
- Backends para aplicaciones móviles (si se expone como API con herramientas del ecosistema)
- Portales con autenticación, permisos, gestión de usuarios, gestión de contenido, etc.

**3 ventajas de usar Django sobre Python puro para desarrollo web**
1. **Productividad**: trae muchas piezas listas (routing, templates, ORM, auth, admin), reduciendo código repetido.
2. **Seguridad integrada**: incluye mitigaciones comunes (por ejemplo, CSRF, manejo seguro de sesiones, validaciones).
3. **Estructura y mantenibilidad**: promueve organización por apps, configuración central, buenas prácticas y el principio DRY.

---

## 2) Entornos virtuales en Python

**¿Qué es un entorno virtual y para qué sirve?**  
Un entorno virtual (venv) es un “Python aislado” dentro de una carpeta del proyecto. Sirve para instalar dependencias **solo para ese proyecto**, sin afectar otros proyectos ni el Python global.

**Ventajas de crear un entorno virtual para un proyecto Django**
- **Aislamiento**: evita choques de dependencias entre proyectos.
- **Control de versiones**: puedes usar versiones específicas de Django/librerías por proyecto.
- **Reproducibilidad**: facilita que otra persona instale exactamente lo mismo.
- **Orden**: evita depender del “Python del sistema” con paquetes instalados globalmente.

**Explica en tus palabras qué hace este comando (no es necesario ejecutarlo)**  
`python -m venv venv`  
Crea una carpeta llamada `venv` con un entorno virtual: incluye un intérprete Python y herramientas (pip) aisladas para instalar librerías del proyecto.

---

## 3) Estructura y diseño de Django

**¿Qué es el patrón MVC y cómo se aplica en Django (MTV)?**  
MVC es un patrón que separa responsabilidades:
- **Model**: datos y reglas (acceso a DB)
- **View**: lógica que decide qué mostrar o hacer con la petición
- **Controller**: recibe la petición, decide qué vista se ejecuta y coordina el flujo

En Django se suele hablar de **MTV**:
- **Model**: modelos y ORM (datos)
- **Template**: la presentación (HTML con variables y tags)
- **View**: la lógica que maneja la petición y responde (similar a “controlador” en la práctica)

### Tabla comparativa MVC vs MTV

| Concepto tradicional (MVC) | Nombre en Django (MTV) | Función |
|---|---|---|
| Model | Model | Define datos y reglas. ORM y estructura de tablas. |
| View | Template | Presentación: renderiza el contenido (HTML) con contexto. |
| Controller | View (y URLconf) | Control del flujo: recibe request, ejecuta lógica y retorna response; el enrutamiento decide qué view se ejecuta. |

**¿Qué es el enrutador de Django y qué papel cumple?**  
El enrutador (URLconf) es el sistema que **mapea URLs a funciones/clases de vista**. Cuando llega una petición, Django evalúa las rutas definidas (`urls.py`) y decide qué vista ejecutar para producir la respuesta.

---

## 4) Principios del desarrollo con Django

**¿Qué significa DRY y cómo lo aplica Django?**  
DRY (“Don’t Repeat Yourself”) significa **no duplicar lógica** y mantener una sola fuente de verdad. Django lo aplica con:
- **Templates con herencia** (`base.html` + bloques)
- **Reutilización por apps**
- **Configuración centralizada** en `settings.py`
- **ORM** para evitar repetir SQL manual en múltiples lugares

**¿Qué significa que Django tenga una “estructura flexible y minimalista”?**  
Que el framework propone una estructura base clara (proyecto + apps), pero permite:
- dividir el sistema en módulos (apps) según necesidad
- organizar templates, urls, vistas, modelos en capas
- mantener un “mínimo” funcional y escalar agregando piezas sin romper la estructura

**¿Qué son los Templates en Django y qué rol cumplen en la renderización?**  
Los templates son archivos (normalmente HTML) que incluyen variables y etiquetas de Django Template Language. Su rol es **presentar** contenido dinámico: una vista prepara un “contexto” (diccionario) y el template lo renderiza para generar el HTML final que recibe el navegador.
