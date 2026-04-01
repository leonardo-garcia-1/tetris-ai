
# **Status screen**

| | |
|---|---|
| **Owner** | Tetris |
| **Status** | WIP |
| **Última revisión** | Marzo 2026 |
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=21620-1455) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=1297-6287) |

> [!ABSTRACT]
> El Status screen es un preset de pantalla completa para Handheld que muestra el estado actual de la tarea del rep: qué posición o acción fue completada recientemente, información contextual asociada y un slot configurable para contenido adicional. Es una pantalla de monitoreo, no de interacción activa.

---

## Descripción general

El Status screen combina un header con el estado de la tarea (título, subtítulo y hora), una tarjeta de última acción y un área de slot flexible. El fondo secundario (#ededf7) diferencia visualmente esta pantalla de las pantallas de acción (blancas) y de las de tránsito (oscuras). Un botón chevron al pie permite expandir o revelar más información.

---

## Usos habituales

- Mostrar al rep la última posición visitada o acción completada (ej. "Arrived at BL-0-000-000-00-00").
- Comunicar el estado general de la tarea en curso (título + subtítulo en el header).
- Presentar contexto adicional en el slot mientras el rep espera la siguiente instrucción.

---

## Cuándo elegir alternativas

- Usar `Feedback screen` cuando el objetivo es comunicar el resultado final de una operación completa (no el estado en curso).
- Usar `Container screen` cuando el rep necesita identificar una posición o contenedor específico para actuar.
- Usar `System state` cuando hay una excepción del sistema que interrumpe el flujo.

---

## Anatomía

1. **Header**: zona superior con padding `24px`. Contiene:
   - **Title**: texto del estado de tarea. Tipografía `Body/large/strong` (24px, Semibold). Color `color/text/primary`.
   - **Subtitle**: descripción de segundo nivel. Tipografía `Body/small/default` (16px, Regular). Color `color/text/secondary`.
   - **Hour**: ícono de reloj + hora actual. Tipografía `Label/small/emphasis` (16px, Medium). Alineado a la derecha del header.
2. **Last action card**: tarjeta blanca (`color/background/primary`) con radio `12px` y padding `20px`. Muestra:
   - **Última acción**: texto de la acción completada (ej. dirección visitada). Tipografía `Body/medium/emphasis` (20px, Medium). Color `color/text/primary`.
   - **Information** _(opcional)_: etiqueta de información contextual adicional. Tipografía `Body/small/default` (16px, Regular). Color `color/text/secondary`.
3. **Slot**: área flexible configurable. Mínimo `240px` de alto. Radio `16px`. Ocupa todo el espacio disponible entre la tarjeta y el botón inferior. En diseño muestra un placeholder violeta — en producción se reemplaza por el componente real.
4. **Bottom button (chevron up)**: botón circular de `56px` centrado al pie. Permite expandir o navegar hacia más información.

---

## Variantes

### Con slot
La pantalla muestra la Last action card en la parte superior y el slot ocupa el resto del espacio disponible. Para contextos donde hay contenido adicional relevante que mostrar mientras el rep espera.

### Sin slot (`slot = false`)
Solo se muestra la Last action card. El espacio restante queda vacío. Para contextos donde la última acción es suficiente como información de estado.

### Con information
La Last action card muestra un texto de información adicional debajo de la última acción (`information = true`).

### Sin information
La Last action card muestra solo el texto de la última acción, sin etiqueta secundaria.

---

## Propiedades

| Propiedad | Tipo | Default | Descripción |
|---|---|---|---|
| `slot` | `boolean` | `true` | Muestra u oculta el área de slot. |
| `information` | `boolean` | `true` | Muestra u oculta la etiqueta de información en la Last action card. |
| `informationLabel` | `string` | `"Information"` | Texto de la etiqueta de información contextual. |
| `lastAction` | `string` | `"Arrived at BL-0-000-000-00-00"` | Texto de la última acción completada. |
| `changeSlot` | `node` | `null` | Componente personalizado para reemplazar el slot placeholder. |

### Design tokens

| Token | Valor resuelto | Descripción |
|---|---|---|
| `device/breakpoints/width` | `360px` | Ancho base Handheld |
| `device/breakpoints/height` | `640px` | Alto base Handheld |
| `color/background/secondary` | `#ededf7` | Fondo general de la pantalla |
| `color/background/primary` | `#ffffff` | Fondo de la Last action card |
| `color/text/primary` | `#1c1c2b` | Título del header y texto de última acción |
| `color/text/secondary` | `#5a5a7c` | Subtítulo, hora e information label |
| `border/radius/s` | `12px` | Radio de la Last action card |
| `border/radius/m` | `16px` | Radio del slot |
| `border/radius/circle` | `9999px` | Radio del botón inferior |
| `spacing/padding/xs` | `24px` | Padding del header y horizontal de cards |
| `spacing/padding/2xs` | `20px` | Padding de la Last action card |
| `spacing/padding/3xs` | `16px` | Padding top del área de cards |
| `spacing/6xs` | `8px` | Padding bottom del área de cards |
| `spacing/gap/m` | `24px` | Gap entre Last action card, slot y bottom |
| `spacing/gap/s` | `16px` | Gap interno del área de content y action content |
| `spacing/gap/xs` | `8px` | Gap entre elementos del header y entre título/subtítulo |
| `button-icon/structure/spacing/padding` | `12px` | Padding interno del botón chevron |
| `typograph/body/font-size/large` | `24px` | Título del header |
| `typograph/body/line-height/large` | `32px` | Line-height título |
| `typograph/body/font-size/small` | `16px` | Subtítulo, hora e information label |
| `typograph/body/line-height/small` | `24px` | Line-height subtítulo/information |
| `typograph/body/font-size/medium` | `20px` | Texto de última acción |
| `typograph/body/line-height/medium` | `28px` | Line-height última acción |
| `typograph/label/font-size/small` | `16px` | Texto de hora |
| `typograph/label/line-height/small` | `16px` | Line-height hora |

---

## Comportamiento

- **Dimensiones**: `360×640px` (min-width `320px`, min-height `530px`, max `640×640px`). Rango Handheld.
- **Fondo**: `color/background/secondary` (#ededf7) — fondo secundario diferenciador de las pantallas de acción.
- **Header**: altura fija con padding `24px`. El título y subtítulo crecen a la izquierda; la hora queda anclada a la derecha.
- **Cards area**: crece con `flex: 1` para ocupar todo el espacio disponible entre header y borde inferior. Contiene `Content` (flex-1) + `Bottom`.
- **Content**: flex-1, gap `16px`. La Last action card es de altura fija; el Slot ocupa el resto con `flex: 1`.
- **Slot**: mínimo `240px` de alto. Si `slot = false`, el Content solo contiene la Last action card.
- **Bottom button**: centrado al pie del área de cards (`align-items: center`, `justify-content: end`). Botón circle de `56px` (mín) a `88px` (máx) con ícono chevron up de `32px`.
- La pantalla es de solo lectura: no requiere una acción del rep para avanzar. El chevron up puede expander información o abrir un panel secundario.

---

## Ejemplos

---

## Recomendaciones

### ✅ Do
- Usar el texto de `lastAction` en lenguaje claro y orientado a la acción completada (ej. "Arrived at BL-0-000-000-00-00").
- Usar el slot para mostrar información relevante del contexto actual (ej. mapa, lista de próximas posiciones).
- Usar `information` para agregar contexto sin sobrecargar el texto de la última acción.

### ❌ Don't
- No usar este preset para comunicar el resultado final de una tarea — usar `Feedback screen`.
- No usar este preset en Desktop — es exclusivo de Handheld.
- No reemplazar el botón chevron por otro tipo de interacción — su función es expandir, no confirmar.
- No sobrecargar el `lastAction` con múltiples datos — debe ser una línea descriptiva y clara.

---

## Componentes relacionados

- **Feedback screen**: preset para comunicar el resultado final de una operación.
- **Container screen**: preset para identificación de posición o contenedor activo.
- **Transit screen**: preset para desplazamiento hacia una dirección.
- **System state**: preset para excepciones del sistema que interrumpen el flujo.
- **Button icon**: componente de botón circular usado en el bottom (chevron up).

---

## Accesibilidad

### Roles y etiquetado

La pantalla debe tener un `<main>` como contenedor principal. El título del header debe implementarse con `<h1>`. La hora (`12:34`) debe incluir un `aria-label` descriptivo (ej. `aria-label="Hora actual: 12:34"`) para que el ícono de reloj no sea el único indicador. El texto de `lastAction` debe ser legible por lector de pantalla en su totalidad — no truncar semánticamente.

### Navegación

Orden de lectura: header (título → subtítulo → hora) → Last action card (acción → information) → contenido del slot → botón chevron.

### Interacciones con teclado

| Tecla | Función |
|---|---|
| Tab | Navegar al botón chevron |
| Enter / Space | Activar el botón chevron (expandir/navegar) |

### Gestos

| Gesto | Función |
|---|---|
| Tap en chevron | Expandir información o abrir panel secundario |

### Consideraciones de diseño

- El fondo secundario (#ededf7) con texto `color/text/primary` (#1c1c2b) cumple WCAG AA.
- El texto `color/text/secondary` (#5a5a7c) sobre fondo blanco de la Last action card debe verificarse — a 16px (texto pequeño) puede estar en el límite de contraste WCAG AA.
- El botón chevron de `56px` mínimo garantiza área de toque suficiente para uso con guantes.
