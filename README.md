# Gridfinity 30 · generador de STL

Generador web de **bases, clips y cajas Gridfinity de paso 30 mm**, pensado para imprimir en una cama de 256 × 256 mm (Bambu Lab P2S) sin soportes. Todo se calcula en tu navegador con WebAssembly: no se sube ni se envía nada a ningún servidor.

**Web:** https://serverheaven.github.io/gridfinity-generator/

## Qué hace

- Reparte la base de un cajón en placas que caben en la cama y genera sus STL.
- Une las placas con **clips tipo corbatín** (un único STL de clip, se imprimen varios).
- Genera cajas de cualquier planta (1×1 … 4×4 o a medida) y altura (1U … 40U), sin muescas para dedos.
- Valores por defecto: cajón de **292 × 520 mm**, cama de 256 mm, rejilla de 30 mm → 9 × 17 celdas, 6 placas y 21 clips. Son medidas de referencia: cámbialas por las de tu cajón.
- Descarga cada pieza en STL o todo junto en un ZIP, con las cantidades por pieza y una estimación del filamento.

## Modos

| Modo | Para qué sirve |
|---|---|
| **Básico** | Medidas del cajón, cama de la impresora, reparto en placas y cajas por casillas (planta × altura). |
| **Avanzado** | Todas las cotas editables: perfil de la base, clips, pies de caja, pared, suelo, holguras, densidad del filamento… «Restablecer» vuelve a los valores originales. |

## Vistas

- **Cajón montado:** todas las bases con los clips y las cajas elegidas, en 3D. Gira arrastrando, acerca con la rueda. Hay vistas Iso, Arriba y Abajo (los clips se ven desde abajo).
- **Pieza:** una pieza suelta con sus medidas, volumen y si cabe en la cama.
- **Plano:** esquema del troceado con las placas y los clips.

## Cajas una a una

En la sección **«Cajas del cajón»** eliges cajas individuales, mezclando plantas y alturas. En la vista **«Mi composición»**:

- se colocan solas sobre la rejilla, o fijas su posición con *col / fila*;
- **arrastra una caja** con el ratón para moverla por la rejilla (no se solapa ni sale del cajón);
- *Girar* la gira 90°;
- sus STL se generan y entran en el ZIP con la cantidad que hayas puesto.

## Configuraciones

Puedes guardar varias configuraciones con nombre (se guardan en el navegador), y **Exportar / Importar** un JSON para llevarlas a otro equipo o navegador. Incluyen las cotas, las cantidades y la composición de cajas.

## Pantallas

El diseño se adapta al ancho: en monitores ultraancho (≥ 1500 px) pasa a tres columnas (controles, visor 3D grande, piezas).

## Imprimir sin soportes

- Las esquinas de las cajas llevan un plano a 45° bajo el relieve, así no hay voladizos.
- Quedan algunos puentes cortos (huecos entre pies y ranuras de los clips) que un laminador normal resuelve sin soportes.
- Ajustes de partida: capa 0,20 mm, 3 perímetros, relleno 15 %; clips con 4 perímetros y 100 % de relleno. Revisa la primera impresión antes de lanzar el lote entero.

## Estructura del repositorio

```
index.html      Versión 2 (la que publica GitHub Pages)
v1/index.html   Versión 1, conservada aparte
.nojekyll       Evita que Pages procese los archivos
```

Cada HTML es autosuficiente: incluye el motor de geometría ([manifold-3d](https://github.com/elalish/manifold), licencia Apache-2.0) y no necesita compilar nada. Solo carga las tipografías de Google Fonts; sin conexión usa las del sistema.

## Uso local

Abre `index.html` con doble clic. Las descargas funcionan directamente.

## Estado

La geometría coincide con el diseño original de Fusion (volúmenes con menos de 0,05 % de diferencia) y todas las piezas salen cerradas y válidas. Falta validar el ajuste real en un cajón y la impresión de los puentes cortos.

## Publicar tu propia copia en GitHub Pages

1. Sube estos archivos a la rama `main` de tu repositorio.
2. Settings → Pages → *Deploy from a branch* → `main` / `(root)`.
3. En un minuto estará en `https://TU_USUARIO.github.io/NOMBRE_DEL_REPOSITORIO/`.
