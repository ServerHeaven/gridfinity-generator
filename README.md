# Gridfinity 30 · generador de STL / STL generator

**🌐 Abrir la web / Open the web app:**

| Idioma | Enlace |
|---|---|
| Español | https://serverheaven.github.io/gridfinity-generator/es/ |
| English | https://serverheaven.github.io/gridfinity-generator/en/ |

La portada https://serverheaven.github.io/gridfinity-generator/ elige el idioma según tu navegador (y recuerda el que elijas con el botón ES / EN).

---

## Español

Generador web de **bases, clips y cajas Gridfinity de paso 30 mm**, pensado para imprimir en una cama de 256 × 256 mm (Bambu Lab P2S) sin soportes. Todo se calcula en tu navegador con WebAssembly: no se sube ni se envía nada a ningún servidor.

### Qué hace

- Reparte la base de un cajón en placas que caben en la cama y genera sus STL.
- Une las placas con **clips tipo corbatín** (un único STL de clip, se imprimen varios).
- Genera cajas de cualquier planta (1×1 … 4×4 o a medida) y altura (1U … 40U), sin muescas para dedos.
- Valores por defecto: cajón de **292 × 520 mm**, cama de 256 mm, rejilla de 30 mm → 9 × 17 celdas, 6 placas y 21 clips. Son medidas de referencia: cámbialas por las de tu cajón.
- Descarga cada pieza en STL o todo junto en un ZIP, con cantidades por pieza.

### Modos

| Modo | Para qué sirve |
|---|---|
| **Básico** | Medidas del cajón, cama de la impresora, reparto en placas, cajas por casillas (planta × altura) y precios. |
| **Avanzado** | Todas las cotas editables: perfil de la base, clips, pies de caja, pared, suelo, holguras, y los parámetros de la estimación de tiempo y coste. «Restablecer» vuelve a los valores originales. |

### Vistas

- **Cajón montado:** todas las bases con los clips y las cajas elegidas, en 3D. Gira arrastrando el fondo, acerca con la rueda. Vistas Iso, Arriba y Abajo (los clips se ven desde abajo).
- **Pieza:** una pieza suelta con sus medidas, volumen y si cabe en la cama.
- **Plano:** esquema del troceado con las placas y los clips.

### Cajas una a una

En **«Cajas del cajón»** eliges cajas individuales, mezclando plantas y alturas. En la vista **«Mi composición»**:

- se colocan solas sobre la rejilla, o fijas su posición con *col / fila*;
- **arrastra una caja** con el ratón para moverla por la rejilla (no se solapa ni sale del cajón);
- *Girar* la gira 90°;
- si una caja **no cabe en la cama** de la impresora, el generador avisa (en el formulario, en la lista y en un mensaje) aunque te deja crearla.

### Tiempo y coste

Estimación orientativa (paredes + relleno, no un laminado real):

- **Filamento** en gramos, **tiempo de impresión**, **consumo eléctrico (kWh)**, número aproximado de **tandas de cama**, **coste** (filamento + electricidad) y tiempo y coste por pieza en la tabla.
- Por defecto: filamento a **11 €/kg**, electricidad a 0,20 €/kWh, impresora a 110 W de media. Cámbialos en la sección «Coste y tiempo».
- En «Avanzado» ajustas el caudal de impresión, la fracción real de material respecto al macizo, el tiempo extra por capa y la preparación por tanda.

### Configuraciones

Guarda varias configuraciones con nombre (en el navegador) y **Exportar / Importar** un JSON para llevarlas a otro equipo. Incluyen cotas, cantidades y composición de cajas.

### Pantallas

El diseño se adapta al ancho: en monitores ultraancho (≥ 1500 px) pasa a tres columnas (controles, visor 3D grande, piezas).

### Imprimir sin soportes

- Las esquinas de las cajas llevan un plano a 45° bajo el relieve, así no hay voladizos.
- Quedan algunos puentes cortos (huecos entre pies y ranuras de los clips) que un laminador normal resuelve sin soportes.
- Ajustes de partida: capa 0,20 mm, 3 perímetros, relleno 15 %; clips con 4 perímetros y 100 % de relleno. Revisa la primera impresión antes de lanzar el lote entero.

### Estado

La geometría coincide con el diseño original de Fusion (volúmenes con menos de 0,05 % de diferencia) y todas las piezas salen cerradas y válidas. Falta validar el ajuste real en un cajón, la impresión de los puentes cortos y contrastar la estimación de tiempo y coste con un laminado real.

---

## English

Web generator for **Gridfinity baseplates, clips and bins on a 30 mm pitch**, designed for a 256 × 256 mm bed (Bambu Lab P2S) and printing without supports. Everything runs in your browser (WebAssembly); nothing is uploaded anywhere.

**Highlights**

- Splits the drawer base into plates that fit the bed and joins them with bowtie clips (one clip STL, print several).
- Bins of any footprint (1×1 … 4×4 or custom) and height (1U … 40U), no finger notch.
- Default values: 292 × 520 mm drawer, 256 mm bed, 30 mm grid → 9 × 17 cells, 6 plates, 21 clips (reference values: change them to your drawer).
- **Basic** and **Advanced** modes, assembled-drawer 3D view, plan view, saved configurations (export/import JSON), quantities per part, ZIP + single STL downloads.
- Pick bins **one by one** and **drag them** around the grid in the 3D view; a warning appears when a bin does not fit the printer bed.
- Estimated **filament, print time, energy (kWh), cost** (filament at €11/kg + electricity) per part and in total. Rough model, not a real slicing.
- Responsive layout, including ultrawide monitors.

**Status:** geometry matches the original Fusion design (volumes within 0.05 %). Real drawer fit, printing of the short bridges and the time/cost estimate still need to be checked against real prints.

---

## Estructura / Repository layout

```
index.html        Portada: redirige a /es/ o /en/ según el navegador
es/index.html     Versión 2 en español
en/index.html     Version 2 in English
v1/index.html     Versión 1 (solo español), conservada aparte
.nojekyll         Evita que Pages procese los archivos
```

Cada HTML es autosuficiente: incluye el motor de geometría ([manifold-3d](https://github.com/elalish/manifold), Apache-2.0) y no necesita compilar nada. Solo carga las tipografías de Google Fonts; sin conexión usa las del sistema. / Each HTML is self-contained; it only loads Google Fonts and falls back to system fonts offline.

## Uso local / Local use

Abre `es/index.html` o `en/index.html` con doble clic. / Double-click `es/index.html` or `en/index.html`.

## Publicar tu propia copia / Publish your own copy

1. Sube estos archivos a la rama `main` de tu repositorio. / Push these files to `main`.
2. Settings → Pages → *Deploy from a branch* → `main` / `(root)`.
3. `https://TU_USUARIO.github.io/NOMBRE_DEL_REPOSITORIO/`
