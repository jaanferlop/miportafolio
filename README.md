# Mi Portafolio Web Interactivo

Portafolio personal de **Jaime Andrés Fernández López**, estudiante de Ingeniería de Software y auditor profesional. Actividad integradora de la Unidad 1 – Lenguaje de Programación para la Web.

## Tecnologías
- HTML5 semántico
- CSS3 (Flexbox, Grid, variables, mobile-first con 3 breakpoints)
- JavaScript vanilla (DOM, eventos, `localStorage`)
- Git y GitHub Pages

## Funcionalidades
- Menú hamburguesa responsive
- Carga dinámica de proyectos desde un array de objetos
- Validación de formulario en tiempo real (envío simulado)
- Tema claro/oscuro persistente
- Animaciones de aparición al hacer scroll

## Estructura
```
mi-portafolio/
├── index.html
├── css/ (reset, variables, layout, components)
├── js/  (main, form-handler, animations)
└── assets/ (images, icons)
```

## Ejecución local
1. Clona el repositorio.
2. Abre `index.html` en el navegador, o ejecuta `python3 -m http.server` y visita `http://localhost:8000`.

## Capturas de pantalla
### Escritorio
![Versión escritorio](assets/images/captura-escritorio.png)

### Móvil
![Versión móvil](assets/images/captura-movil.png)

**Sitio en vivo:** https://jaanferlop.github.io/miportafolio/

---

# Entregables Unidad 1 – Mi Portafolio Web Interactivo

## Entregable 1.1 – Requerimientos

### Requerimientos funcionales
Convención: `RF` identifica los requerimientos funcionales del sistema.

- `RF-01`: El sitio debe mostrar una sección de presentación personal con nombre, carrera y perfil profesional.
- `RF-02`: El sitio debe listar mínimo 3 proyectos, cada uno con título, descripción, tecnologías, imagen y enlace.
- `RF-03`: Los proyectos deben cargarse dinámicamente desde un arreglo de objetos en JavaScript.
- `RF-04`: El sitio debe incluir un formulario de contacto (nombre, correo, asunto y mensaje) con envío simulado.
- `RF-05`: El formulario debe validar los campos en tiempo real y mostrar mensajes de error claros.
- `RF-06`: El menú de navegación debe convertirse en menú hamburguesa en pantallas móviles.
- `RF-07`: El usuario debe poder alternar entre tema claro y oscuro, y el sitio debe recordar su elección.

### Requerimientos no funcionales
Convención: `RNF` identifica los requerimientos no funcionales, relacionados con calidad, mantenibilidad, accesibilidad y operación del proyecto.

- `RNF-01` **Responsividad:** el diseño debe adaptarse a móvil (<768 px), tablet (≥768 px) y escritorio (≥1024 px).
- `RNF-02` **Accesibilidad:** imágenes con texto alternativo, campos con `label` asociado, enlace "saltar al contenido" y atributos ARIA en el menú.
- `RNF-03` **Mantenibilidad:** estilos con variables CSS y código separado en archivos por responsabilidad.
- `RNF-04` **Compatibilidad:** debe funcionar en las versiones actuales de Chrome y Firefox sin librerías externas.
- `RNF-05` **Rendimiento:** sitio estático, imágenes ligeras y sin dependencias de JavaScript de terceros.
- `RNF-06` **Disponibilidad:** desplegado en GitHub Pages con URL pública.
- `RNF-07` **Usabilidad:** respeta la preferencia de "reducir movimiento" del sistema y mantiene contraste suficiente entre texto y fondo.

## Entregable 1.2 – Wireframe de baja fidelidad

### Escritorio
```
+--------------------------------------------------------------+
| JF.      Inicio  Sobre mí  Proyectos  Contacto          [🌙] |  <- header / nav
+--------------------------------------------------------------+
|   ¡Bienvenido a mi espacio!                                  |
|   Jaime Andrés Fernández López                               |
|   [Ver proyectos]  [Contáctame]                              |  <- hero
+--------------------------------------------------------------+
|  SOBRE MÍ                                                    |
|   ( JF )     Texto de presentación...                        |
|              [HTML5][CSS3][JS][Git][Auditoría]               |
+--------------------------------------------------------------+
|  PROYECTOS                                                   |
|  +----------+   +----------+   +----------+                  |
|  |  imagen  |   |  imagen  |   |  imagen  |   <- JS genera   |
|  |  título  |   |  título  |   |  título  |      las tarjetas|
|  |  [Ver]   |   |  [Ver]   |   |  [Ver]   |                  |
|  +----------+   +----------+   +----------+                  |
+--------------------------------------------------------------+
|  CONTACTO                                                    |
|  Nombre [__________]  <- validación en tiempo real (JS)      |
|  Correo [__________]                                         |
|  Asunto [ v ]                                                |
|  Mensaje [_________]                                         |
|  [Enviar]                                                    |
+--------------------------------------------------------------+
|  © 2026 Jaime Andrés Fernández López                         |
+--------------------------------------------------------------+
```

### Móvil
```
+----------------+
| JF.   [🌙] [≡] |  <- botón hamburguesa (JS)
+----------------+
| Hero           |
| Sobre mí       |
| Proyectos      |
|  (1 columna)   |
| Contacto       |
| Footer         |
+----------------+
```

### Puntos de interacción con JavaScript
1. Botón hamburguesa: abre y cierra el menú.
2. Botón de tema: cambia entre claro y oscuro.
3. Tarjetas de proyectos: se crean desde un arreglo.
4. Formulario: valida mientras se escribe y simula el envío.
5. Animaciones: los bloques aparecen al hacer scroll.

## Entregable 2.1 – Arquitectura de archivos y justificación

```
mi-portafolio/
├── index.html
├── css/
│   ├── reset.css
│   ├── variables.css
│   ├── layout.css
│   └── components.css
├── js/
│   ├── main.js
│   ├── form-handler.js
│   └── animations.js
├── assets/
│   ├── images/
│   └── icons/
└── README.md
```

### ¿Por qué separar el CSS en varios archivos?
- **Una responsabilidad por archivo.** `reset.css` iguala el punto de partida entre navegadores, `variables.css` concentra colores y medidas, `layout.css` define la distribución de la página y `components.css` define botones, tarjetas e inputs.
- **Mantenimiento más fácil.** Para cambiar la paleta solo se edita `variables.css`, y el resto del sitio se actualiza solo.
- **Orden de la cascada.** Se cargan de lo general a lo específico (reset, variables, layout, componentes), lo que reduce conflictos de especificidad.
- **Trabajo en equipo.** Varias personas pueden editar archivos distintos sin generar conflictos en Git.

### ¿Por qué modularizar el JavaScript?
- **Separación de responsabilidades.** `main.js` coordina el sitio, `form-handler.js` se ocupa solo del formulario y `animations.js` solo de los efectos visuales.
- **Depuración sencilla.** Si falla el formulario, se sabe en qué archivo buscar.
- **Reutilización.** Cada módulo puede llevarse a otro proyecto sin arrastrar el resto.
- **Legibilidad.** Archivos cortos son más fáciles de leer, comentar y evaluar que un solo archivo largo.

### Relación con el modelo cliente-servidor
Todo el sitio es estático. El navegador (cliente) pide los archivos a GitHub Pages (servidor), recibe HTML, CSS y JS, y los ejecuta localmente. No hay lógica de servidor todavía: el formulario simula el envío. En la Unidad 2 se podrá reemplazar esa simulación por una llamada a un backend.

## Entregable 2.2 – Guía de estilos

### Paleta de colores
| Uso | Color | Variable CSS |
|---|---|---|
| Primario (azul oscuro) | `#0b2545` | `--color-primario` |
| Primario secundario | `#13315c` | `--color-primario-claro` |
| Acento (azul medio) | `#3e7cb1` | `--color-acento` |
| Fondo (blanco) | `#ffffff` | `--color-fondo` |
| Fondo alterno | `#f1f5fa` | `--color-fondo-alt` |
| Texto | `#1b2a41` | `--color-texto` |
| Error | `#c0392b` | `--color-error` |
| Éxito | `#1e8449` | `--color-ok` |

El tema oscuro redefine estas mismas variables bajo `[data-theme="dark"]`, sin duplicar estilos.

### Tipografías (2 familias)
- **Poppins** (600 y 700): títulos y logo. Variable `--fuente-titulos`.
- **Inter** (400 y 500): texto general. Variable `--fuente-texto`.

### Componentes reutilizables
| Componente | Clase | Descripción |
|---|---|---|
| Botón | `.btn`, `.btn-outline` | Fondo azul, esquinas redondeadas, se eleva al pasar el cursor. |
| Tarjeta | `.proyecto-card` | Imagen, título, descripción, etiquetas y botón. Sube al pasar el cursor. |
| Etiqueta | `.skills li`, `.tecnologias span` | Cápsula con fondo claro y borde sutil. |
| Campo de formulario | `.field` | Etiqueta, input y mensaje de error. Borde rojo si es inválido y verde si es válido. |

## Historial de commits
Ver el historial completo con `git log --oneline` o en la pestaña *Commits* del repositorio.

## Autor y licencia
Jaime Andrés Fernández López · Licencia MIT
