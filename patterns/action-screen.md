
# **Action screen**

| | |
|---|---|
| **Owner** | Tetris |
| **Status** | Stable |
| **Última revisión** | Marzo 2026 |
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=13993-3040) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=1295-9380) |

> [!ABSTRACT]
> El Action screen es un preset de pantalla completa para Handheld que presenta un contenido visual (imagen o componente custom) junto a un título, subtítulo y dos botones de acción. Estructura flujos de confirmación o inicio de tarea donde el usuario debe elegir entre dos opciones.

---

## Descripción general

El Action screen combina una zona de contenido flexible (imagen o slot) con un bloque de texto y una barra de acción fija al pie. El área de contenido crece para ocupar todo el espacio disponible entre el header y los botones, adaptándose a distintas alturas de pantalla dentro del rango Handheld (530–640px). Es un preset: no es un componente atómico sino una pantalla lista para usar con slots configurables.

---

## Usos habituales

- Presentar una acción principal al usuario con contexto visual antes de ejecutarla (ej. mostrar foto del producto antes de confirmar).
- Pantalla de inicio de tarea con ilustración y dos opciones de navegación.
- Confirmación de operación con imagen de referencia + botón primario de confirmación y secundario de cancelación.

---

## Cuándo elegir alternativas

- Usar `System state` cuando el contenido comunica un estado de excepción (error, vacío, éxito) en lugar de una acción.
- Usar `Scan screen` cuando el flujo principal es la captura de un código por cámara.
- Usar `Drawer` cuando la acción es secundaria y no requiere pantalla completa.

---

## Anatomía

1. **Header** _(opcional)_: barra superior con ícono de menú (hamburger) en la esquina derecha. Fondo `color/surface/primary`.
2. **Content area**: zona flexible que ocupa todo el espacio disponible entre el header y el footer. Padding top `32px`, horizontal `24px`, bottom `20px`.
3. **Main content**: el contenido visual + texto. Varía según el `type`:
   - **Image**: imagen a pantalla flexible (`border-radius` `8px`) + bloque de texto debajo.
   - **Slot**: área de contenido personalizable + bloque de texto debajo.
4. **Title**: título de la acción. Tipografía `Heading/small` (32px, Semibold).
5. **Subtitle** _(opcional)_: descripción breve. Tipografía `Body/medium` (20px, Regular).
6. **Action footer**: zona fija al pie con dos botones apilados verticalmente. Fondo blanco, padding `24px`.
7. **Botón primario**: acción principal. Fondo `#4850e5`, texto blanco, altura `72px`.
8. **Botón secundario**: acción alternativa o cancelación. Fondo `#e0e9ff`, texto `#4850e5`, altura `72px`.

---

## Variantes

### Image
El área de contenido muestra una imagen que escala para ocupar todo el espacio flexible. Ideal cuando hay un visual de producto, persona o contexto que acompaña la acción.

### Slot
El área de contenido es un slot vacío donde se puede insertar cualquier componente local. Indicado cuando el contenido no es una imagen simple sino un componente más complejo (ej. mapa, cámara, componente de escaneo).

---

## Propiedades

| Propiedad | Tipo | Default | Descripción |
|---|---|---|---|
| `type` | `"Image"` / `"Slot"` | `"Image"` | Define el tipo de contenido visual en el área principal. |
| `header` | `boolean` | `true` | Muestra u oculta el header con el ícono de menú. |
| `titleText` | `string` | `"Title"` | Texto del título. |
| `showSubtitle` | `boolean` | `true` | Muestra u oculta el subtítulo. |
| `subtitleText` | `string` | `"Subtitle"` | Texto del subtítulo. |

### Design tokens del componente

| Token | Valor resuelto | Descripción |
|---|---|---|
| `device/breakpoints/width` | `360px` | Ancho base Handheld |
| `device/breakpoints/height` | `640px` | Alto base Handheld |
| `color/background/primary` | `#ffffff` | Fondo general y footer |
| `color/surface/primary` | `#ffffff` | Fondo del header |
| `color/text/primary` | `#1c1c2b` | Color del título |
| `color/text/secondary` | `#5a5a7c` | Color del subtítulo |
| `color/text/inverse` | `#ffffff` | Texto del botón primario |
| `color/interactive/fill/loud/default` | `#4850e5` | Fondo del botón primario |
| `color/interactive/fill/quiet/default` | `#e0e9ff` | Fondo del botón secundario |
| `color/interactive/text/default` | `#4850e5` | Texto del botón secundario |
| `border/radius/m` | `16px` | Radio de los botones |
| `border/radius/xs` | `8px` | Radio de la imagen (type Image) |
| `border/radius/circle` | `9999px` | Radio del botón de header |
| `spacing/padding/s` | `32px` | Padding top del área de contenido |
| `spacing/padding/xs` | `24px` | Padding horizontal del contenido y footer |
| `spacing/padding/2xs` | `20px` | Padding bottom del área de contenido |
| `spacing/gap/xl` | `40px` | Gap entre imagen y bloque de texto |
| `spacing/gap/s` | `16px` | Gap entre botones |
| `spacing/gap/xs` | `8px` | Gap entre título y subtítulo |
| `typograph/heading/font-size/small` | `32px` | Tamaño de fuente del título |
| `typograph/heading/line-height/small` | `36px` | Line-height del título |
| `typograph/body/font-size/medium` | `20px` | Tamaño de fuente del subtítulo |
| `typograph/body/line-height/medium` | `28px` | Line-height del subtítulo |
| `typograph/label/font-size/medium` | `20px` | Tamaño de fuente de los botones |

---

## Comportamiento

- **Dimensiones**: ancho `360px` (min `320px`, max `640px`), alto `640px` (min `530px`, max `640px`). Se adapta al rango Handheld.
- **Content area**: crece con `flex: 1` para ocupar todo el espacio entre header y footer. La imagen o slot se expande para llenar esa zona.
- **Image**: escala con `object-cover` para llenar el área sin distorsión.
- **Slot**: muestra un placeholder visual (fondo violeta translúcido con patrón) en modo diseño. En producción se reemplaza por el componente real.
- **Footer**: siempre fijo al pie. Los dos botones son obligatorios — el preset no admite un solo botón.
- **Header**: cuando `header = false`, el contenido sube hasta el borde superior de la pantalla.
- El título y subtítulo se ubican **debajo** del área de contenido visual, nunca superpuestos.

---

## Ejemplos

### Consolidación de totes

Pantalla de inicio de tarea que usa el type **Image** con una ilustración 3D de totes amarillos apilados en fila. El título explica la acción requerida y los dos botones ofrecen confirmar o cancelar.

| Propiedad | Valor |
|---|---|
| `type` | `Image` |
| `header` | `false` |
| `titleText` | `"Deja los totes en fila para consolidar"` |
| `showSubtitle` | `false` |

**Cuándo usarlo:** flujos de preparación o consolidación de pedidos donde se necesita instruir al operario con un visual claro antes de que ejecute la tarea.

---

## Recomendaciones

### ✅ Do
- Usar imágenes de alta resolución y con buena legibilidad para el type Image.
- Mantener el título en 1–2 líneas máximo.
- Usar el botón primario para la acción positiva y el secundario para cancelar o volver.
- Usar el Slot cuando el contenido principal es dinámico o compuesto.

### ❌ Don't
- No omitir ninguno de los dos botones — el preset requiere siempre una acción primaria y una secundaria.
- No usar este preset en Desktop — es exclusivo de Handheld.
- No poner texto crítico dentro de la imagen, puede quedar tapado por el recorte.
- No usar el Action screen para estados de error o vacío — usar `System state`.

---

## Componentes relacionados

- **System state**: preset para estados de excepción del sistema.
- **Scan screen**: preset para flujos de escaneo con cámara.
- **Button**: componente de acción usado en el footer.
- **Header**: componente de encabezado usado opcionalmente.
- **Drawer**: alternativa cuando la acción no requiere pantalla completa.

---

## Accesibilidad

### Roles y etiquetado

La pantalla debe tener un `<main>` como contenedor principal. El título debe implementarse con `<h1>`.

La imagen (type Image) debe incluir un `alt` descriptivo del contenido visual cuando aporte contexto relevante a la acción. Si es puramente decorativa, usar `alt=""`.

### Navegación

Orden de lectura: header → imagen/slot → título → subtítulo → botón primario → botón secundario.

### Interacciones con teclado

| Tecla | Función |
|---|---|
| Tab | Navegar entre botones y header |
| Enter / Space | Activar el botón enfocado |

### Gestos

| Gesto | Función |
|---|---|
| Tap en botón primario | Ejecutar acción principal |
| Tap en botón secundario | Ejecutar acción alternativa o cancelar |
| Tap en menú (header) | Abrir menú de navegación |

### Consideraciones de diseño

- El botón primario (`#4850e5`) sobre fondo blanco cumple WCAG AA en el área del footer.
- El texto del botón secundario (`#4850e5`) sobre `#e0e9ff` debe verificarse en contexto — puede estar cerca del límite de contraste WCAG AA para texto normal.
- Los botones de `72px` de alto garantizan un área de toque suficiente para uso con guantes o en condiciones de operación.
