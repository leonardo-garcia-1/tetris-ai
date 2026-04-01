
# **System state**

> [!ABSTRACT]
> El System state es una pantalla completa o panel que comunica al usuario un estado del sistema que interrumpe el flujo normal de la operación: estado vacío, error inesperado, éxito u otras condiciones. Centra la atención del usuario en el mensaje y ofrece una acción de salida o reintento.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=17263-27775) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=1953-209) |

| | |
|---|---|
| **Owner** | Tetris |
| **Status** | Stable |
| **Última revisión** | Noviembre 2025 |
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=17263-27775) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=1953-209) |

El System state es una pantalla completa o panel que comunica al usuario un estado del sistema que interrumpe el flujo normal de la operación: estado vacío, error inesperado, éxito u otras condiciones. Centra la atención del usuario en el mensaje y ofrece una acción de salida o reintento.

---

## Descripción general

El System state ocupa toda la pantalla disponible (o un drawer) y presenta un ícono, un título, una descripción y una acción. Está diseñado para estados de excepción —no para flujos habituales— y se adapta a Desktop y Handheld con layouts y tokens diferentes. El fondo oscuro del entorno Desktop contrasta con el contenido en card blanco, mientras que en Handheld el fondo es blanco directo.

---

## Usos habituales

- Comunicar un estado vacío: sin resultados, sin contenido disponible (ej. "Sorry, there's nothing here").
- Mostrar un error inesperado del sistema con opción de reintento (ej. "Unexpected error / Try again later").
- Confirmar el éxito de una operación crítica que requiere atención completa del usuario.
- Informar una condición de sistema que impide continuar el flujo (mantenimiento, sin conexión, etc.).

---

## Cuándo elegir alternativas

- Usar `Snackbar` para errores o confirmaciones no bloqueantes que no interrumpen el flujo.
- Usar `Drawer` directamente si el estado secundario no requiere comunicar un estado de sistema, sino mostrar contenido adicional.
- Usar `Highlight` para estados informativos de menor jerarquía dentro de una pantalla.

---

## Anatomía

### Desktop (full screen)

1. **Fondo**: capa oscura (`color/background/inverse` `#1c1c2b`) que envuelve toda la pantalla.
2. **Main content card**: contenedor blanco redondeado (`border/radius` `16px`) que ocupa el área central.
3. **Icon**: ícono representativo del estado. Tamaño `160px`. Centrado en el card.
4. **Title**: título del estado. Máximo 2 líneas. Tipografía `Heading/large` (88px, Semibold).
5. **Description**: descripción complementaria. Máximo 1 línea. Tipografía `Body/large` (32px, Regular).
6. **Action**: botón primario (obligatorio). Botón secundario opcional. Alineados al fondo del card.
7. **Bottom navigation**: barra de navegación inferior del entorno Desktop, siempre visible.

### Handheld (full screen)

1. **Header**: barra superior con botón de retroceso (flecha izquierda).
2. **Icon**: ícono representativo del estado. Tamaño `80px`. Centrado verticalmente.
3. **Title**: máximo 2 líneas. Tipografía `Heading/small` (32px, Semibold).
4. **Description**: máximo 1 línea. Tipografía `Body/medium` (20px, Regular).
5. **Action**: botón primario al pie. Botón secundario opcional, o variante Touchless.

### Drawer (Desktop y Handheld)

El System state puede presentarse dentro de un Drawer cuando el estado es contextual a una tarea parcial. Mantiene la misma estructura interna (icon + title + description + action) pero el contenedor es el componente `Drawer` en lugar de pantalla completa.

---

## Variantes

### Por dispositivo

**Desktop**
Pantalla `1920×1080px`. Fondo `#1c1c2b`. Content card blanco con padding `160px` horizontal, `80px` vertical. Bottom navigation siempre visible. Botones de `96px` de alto.

**Handheld**
Pantalla `360×640px`. Fondo blanco. Padding `24px`. Header con navegación de retroceso. Botones de `72px` de alto.

### Por presentación

**Full screen**: ocupa toda la pantalla disponible. Uso habitual para estados de sistema críticos.

**Drawer**: el System state se muestra dentro del componente `Drawer`. Usado cuando el estado corresponde a una subtarea sin abandonar el contexto de la pantalla padre.

### Por tipo de acción

**Buttons**: botón primario (obligatorio) + botón secundario opcional.

**Touchless**: acción sin interacción física. Disponible en Handheld para contextos donde el usuario no puede tocar la pantalla.

---

## Propiedades

| Propiedad | Tipo | Descripción |
|---|---|---|
| `device` | `"Desktop"` / `"Handheld"` | Variante de dispositivo. Controla layout, tipografías, tamaños y padding. |
| `presentation` | `"Full screen"` / `"Drawer"` | Define si el componente ocupa toda la pantalla o se presenta en un drawer. |
| `actionType` | `"Buttons"` / `"Touchless"` | Tipo de acción disponible para el usuario. |
| `buttonSecondary` | `boolean` | Muestra u oculta el botón secundario. Solo aplica cuando `actionType = "Buttons"`. |
| `icon` | `node` | Ícono que representa el estado del sistema. |
| `title` | `string` | Texto del título. Máximo 2 líneas. |
| `description` | `string` | Texto descriptivo. Máximo 1 línea. |

### Design tokens del componente

| Token | Valor resuelto | Descripción |
|---|---|---|
| `color/background/inverse` | `#1c1c2b` | Fondo oscuro del entorno Desktop |
| `color/background/primary` | `#ffffff` | Fondo del card / pantalla Handheld |
| `color/surface/primary` | `#ffffff` | Header en Handheld |
| `color/text/primary` | `#1c1c2b` | Color del título |
| `color/text/secondary` | `#5a5a7c` | Color de la descripción |
| `color/text/inverse` | `#ffffff` | Texto de botón primario |
| `color/interactive/fill/loud/default` | `#4850e5` | Fondo botón primario |
| `color/interactive/fill/quiet/default` | `#e0e9ff` | Fondo botón secundario |
| `color/interactive/text/default` | `#4850e5` | Texto botón secundario |
| `color/interactive/fill/quiet-inverse/disabled` | `#2f2f46` | Botones de nav deshabilitados (Desktop) |
| `color/interactive/fill/quiet-inverse/default` | `#454768` | Botón Exit en bottom nav (Desktop) |
| `border/radius/m` | `16px` | Radio del card y de los botones |
| `system-state/icon/width` | `160px` (Desktop) / `80px` (Handheld) | Ancho del ícono |
| `system-state/icon/height` | `160px` (Desktop) / `80px` (Handheld) | Alto del ícono |
| `system-state/spacing/between-elements` | `40px` (Desktop) / `24px` (Handheld) | Gap entre ícono y bloque de texto |
| `system-state/spacing/between-text` | `32px` (Desktop) / `12px` (Handheld) | Gap entre título y descripción |
| `system-state/spacing/padding` | `24px` (Handheld) | Padding interno del área de estado |
| `spacing/padding/2xl` | `80px` | Padding vertical del card (Desktop) |
| `spacing/5xl` | `160px` | Padding horizontal del card (Desktop) |
| `typograph/heading/font-size/large` | `88px` | Título en Desktop |
| `typograph/heading/font-size/small` | `32px` | Título en Handheld |
| `typograph/body/font-size/large` | `32px` | Descripción en Desktop |
| `typograph/body/font-size/medium` | `20px` | Descripción en Handheld |

---

## Estados / Templates disponibles

| Template | Descripción |
|---|---|
| **Empty** | Estado vacío. Sin resultados o sin contenido disponible. Ej: "Sorry, there's nothing here / Try again later". Ícono de cactus. |
| **Error** | Error inesperado del sistema. Ej: "Unexpected error / Try again later". Ícono de advertencia. |
| **Caution** | Advertencia que requiere atención del usuario antes de continuar. |
| **Informative** | Mensaje informativo del sistema sin carácter de error. |

---

## Comportamiento

- El componente ocupa el **100% del área disponible** (`size-full`), ya sea la pantalla completa o el interior de un Drawer.
- El contenido (icon + text) se centra **verticalmente** en el espacio disponible entre el header y la zona de acción.
- En **Desktop**, el Main content card está flotando sobre el fondo oscuro con `border-radius: 16px` y `overflow: clip`.
- La **bottom navigation** de Desktop siempre está presente y los botones de navegación se muestran en estado deshabilitado (`color/interactive/fill/quiet-inverse/disabled`).
- El botón **Exit** en la bottom nav de Desktop usa el ícono Logout y permite salir del estado del sistema.
- En **Drawer**, el System state hereda el comportamiento de apertura/cierre del componente `Drawer`. El header del Drawer reemplaza al header nativo del System state.
- El **título** admite máximo 2 líneas antes de truncarse. La **descripción** admite máximo 1 línea.

---

## Ejemplos

> Los textos que aparecen en los ejemplos son ilustrativos. En producción, título y descripción son configurados por el flujo que llama al componente según el tipo de estado.

### Error inesperado en Desktop

![][example-error-desktop]

Durante un flujo de packing en Desktop, un error de conectividad interrumpe la operación. El System state ocupa toda la pantalla con fondo oscuro y muestra el ícono de advertencia, el título "Unexpected error" y la descripción "Try again later". El botón "Try again" en el card blanco permite al operario reintentar sin abandonar el flujo.

### Estado vacío en Handheld

![][example-empty-handheld]

En un flujo de picking en Handheld, la lista de productos asignados está vacía. El System state muestra el ícono de cactus, el título "Nothing here" y la descripción "There are no items assigned". El botón "Go back" lleva al operario a la pantalla anterior.

---

## Recomendaciones

### ✅ Do
- Usar un ícono que represente claramente el tipo de estado (error, vacío, éxito).
- Redactar el título en términos comprensibles para el usuario operativo, no técnicos.
- Incluir siempre una acción clara: "Try again", "Go back", "Refresh".
- Usar el template Empty para listas o contenidos que pueden estar vacíos legítimamente.

### ❌ Don't
- No usar System state para errores menores o validaciones de formulario — usar `Snackbar` o el estado Error del componente correspondiente.
- No omitir la acción: el usuario siempre debe tener una salida.
- No incluir más de 2 botones simultáneamente.
- No usar la variante Touchless en Desktop — solo aplica a Handheld.

---

## Componentes relacionados

- **Snackbar**: para errores o confirmaciones no bloqueantes.
- **Drawer**: contenedor alternativo para System state contextual.
- **Button**: componente de acción usado internamente.
- **Header**: componente de encabezado usado en la variante Handheld.
- **Bottom navigation**: barra inferior del entorno Desktop, siempre presente.

---

## Accesibilidad

### Roles y etiquetado

La pantalla de System state debe implementarse con un rol `main` o `region` con `aria-label` descriptivo del estado (ej. `aria-label="Error del sistema"`).

El título debe implementarse como `<h1>` para que los lectores de pantalla identifiquen el contexto de la pantalla.

### Navegación

Orden de lectura: header/navegación → ícono (decorativo) → título → descripción → acción.

El ícono debe marcarse como decorativo (`aria-hidden="true"`) ya que el texto lo describe.

### Interacciones con teclado

| Tecla | Función |
|---|---|
| Tab | Navegar entre elementos interactivos (botones) |
| Enter / Space | Activar la acción seleccionada |

### Consideraciones de diseño

- El contraste de texto en el card blanco cumple WCAG AA en todos los tokens definidos.
- El texto del botón primario (`color/text/inverse` `#ffffff`) sobre `color/interactive/fill/loud/default` (`#4850e5`) cumple WCAG AA grande.
- En Handheld, asegurar que el botón de acción sea alcanzable con el pulgar (zona inferior de pantalla).
