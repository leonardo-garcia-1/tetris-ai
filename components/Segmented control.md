# Segmented control

> [!ABSTRACT]
> El Segmented control agrupa pocas opciones concretas y permite seleccionar una de ellas de forma rápida y excluyente. Se utiliza para alternar entre vistas, filtros o modos dentro de una misma pantalla, tanto en Desktop como Handheld.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=19230-972) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=2656-657) |

| Campo | Valor |
|---|---|
| **Categoría** | Selección / Filtro |
| **Plataformas** | Desktop · Handheld |
| **Status** | Estable |
| **Última revisión** | 6 de marzo de 2026 |

**Descripción breve**: Agrupa pocas opciones concretas y permite seleccionar una de ellas de forma rápida y excluyente.

---

## Descripción general

El Segmented control es un componente que agrupa un conjunto acotado de opciones mutuamente excluyentes, permitiendo al usuario seleccionar una sola de forma rápida y directa. Funciona como un selector visual donde una opción permanece activa en todo momento.

Se utiliza en contextos donde el usuario necesita alternar entre vistas, filtros o modos dentro de una misma pantalla, tanto en dispositivos Desktop como Handheld.

---

## Usos habituales

- Cuando se necesita alternar entre dos o más vistas relacionadas dentro de una misma pantalla (ej. lista / grilla, cámara frontal / trasera).
- Para filtrar contenido por categorías mutuamente excluyentes sin navegar a otra pantalla.
- Para que el usuario elija un modo de operación de forma persistente durante la sesión.

---

## Cuándo elegir alternativas

- Usar `Switch` cuando la acción es binaria (activar/desactivar) y tiene efecto inmediato, sin necesidad de elegir entre múltiples opciones etiquetadas.

---

## Anatomía

1. **Container**: Marco exterior del componente. En tipo Idle tiene fondo blanco (`color/background/primary`) y borde (`color/border/primary`). En tipo Inverse tiene fondo oscuro (`color/interactive/fill/quiet-inverse/default`).
2. **Active segment button**: Botón seleccionado actualmente. Resaltado con fondo contrastante y texto con `color/text/primary` (Idle) o `color/text/inverse` (Inverse).
3. **Inactive segment button**: Botón no seleccionado. Sin fondo especial, texto con `color/text/primary` (Idle) o `color/text/inverse` (Inverse).

---

## Variantes

### Idle
El container tiene fondo blanco con borde sutil. El botón activo se destaca con fondo oscuro (`color/interactive/fill/quiet-inverse/default` — `#454768`) y texto en blanco. Se usa sobre fondos claros.

### Inverse
El container tiene fondo oscuro (`color/interactive/fill/quiet-inverse/default` — `#454768`). El botón activo se destaca con fondo blanco (`color/background/primary`) y texto en `color/text/primary`. Se usa sobre fondos oscuros o imágenes.

**Combinaciones válidas e inválidas:**

| Combinación | Válida | Nota |
|---|---|---|
| Idle sobre fondo claro | ✅ | Uso estándar |
| Inverse sobre fondo oscuro o imagen | ✅ | Uso estándar |
| Idle sobre fondo oscuro | ❌ | El container se pierde en el fondo |
| Inverse sobre fondo claro | ❌ | El container contrasta de forma no prevista |
| Mezclar Idle e Inverse en la misma pantalla | ❌ | Rompe la consistencia visual |

---

## Propiedades

| Propiedad | Valores | Descripción |
|-----------|---------|-------------|
| `type` | `Idle` / `Inverse` | Define la apariencia según el fondo sobre el que se coloca el componente |
| `showButton3` | `true` / `false` | Controla la visibilidad del tercer segmento |
| `showButton4` | `true` / `false` | Controla la visibilidad del cuarto segmento |

### Tokens de diseño

| Token | Valor | Uso |
|-------|-------|-----|
| `Segmented control/size/height` | `80px` (Desktop) / `48px` (Handheld) | Altura del componente |
| `Segmented control/spacing/padding` | `24px` (Desktop) / `16px` (Handheld) | Padding horizontal interno de cada botón |
| `Segmented control/spacing/padding-borda` | `8px` (Desktop) / `4px` (Handheld) | Padding interno del container |
| `Segmented control/border radius/frame` | `16px` (Desktop) / `12px` (Handheld) | Border radius del container |
| `Segmented control/border radius/button` | `12px` (Desktop) / `8px` (Handheld) | Border radius de cada botón |
| `color/background/primary` | `#ffffff` | Fondo del botón activo (tipo Idle) y container (tipo Idle) |
| `color/interactive/fill/quiet-inverse/default` | `#454768` | Fondo del botón activo (tipo Idle) y container (tipo Inverse) |
| `color/border/primary` | `#bdbfd6` | Borde del container en tipo Idle |
| `color/text/primary` | `#1c1c2b` | Texto del botón activo en tipo Idle e inactivos en tipo Idle |
| `color/text/inverse` | `#ffffff` | Texto del botón activo en tipo Idle e inactivos en tipo Inverse |

---

## Estados

| Estado | Aplica a | Detalle |
|--------|----------|---------|
| Selected | Segmento activo | Fondo contrastante y texto resaltado. Solo puede haber un segmento seleccionado a la vez. No es posible deseleccionar sin seleccionar otro. |
| Idle | Segmentos inactivos | Sin fondo especial. Texto con `color/text/primary` (tipo Idle) o `color/text/inverse` (tipo Inverse). |
| Focus | Componente | Estado de foco de teclado sobre el componente completo. La navegación interna entre segmentos se realiza con flechas; no con Tab. El anillo de foco debe cumplir WCAG 2.4.7. |
| Hover | Segmento (Desktop) | No está definido como estado en la librería Figma. El comportamiento visual de hover queda a cargo de la implementación de cada plataforma. |
| Disabled | Componente o segmento | No está definido en la librería actual. Si se requiere, debe acordarse como extensión del componente. |

> **Reglas de combinación**: Selected y Idle son mutuamente excluyentes por segmento. Siempre debe haber exactamente un segmento en estado Selected.

---

## Comportamiento

- El componente admite entre **2 y 4 opciones**. No puede usarse con menos de 2 ni más de 4 segmentos.
- El **ancho de los botones debe ser consistente** dentro de un mismo componente, pero el conjunto puede ajustarse en su ancho total según la cantidad de caracteres de las etiquetas.
- El componente tiene **tamaños preestablecidos para Desktop y Handheld**: Desktop usa altura de 80px y tipografía Body/small (24px); Handheld usa altura de 48px y tipografía reducida (16px).
- La selección es **mutuamente excluyente**: al seleccionar un segmento, el anterior se deselecciona automáticamente.
- El ancho del componente es flexible y se adapta al contenedor, distribuyendo el espacio equitativamente entre los botones.
- **Edge case — etiqueta larga**: Si una etiqueta supera el espacio disponible, el texto se trunca con elipsis (`text-ellipsis`). Se recomienda limitar las etiquetas a 2–3 palabras para evitar truncamiento. No se permite el quiebre de línea dentro de un segmento.
- **Edge case — contenedor muy angosto**: En pantallas pequeñas o contenedores restringidos, el componente mantiene el mínimo de ancho necesario para ser legible; si no cabe, debe reconsiderarse el uso del componente.

---

## Ejemplos

### Types — Idle e Inverse
El componente tiene dos variantes según el fondo sobre el que se coloca. En **Idle**, el container tiene fondo blanco con borde sutil y el segmento activo se destaca con fondo oscuro (`#454768`) y texto blanco. En **Inverse**, el container tiene fondo oscuro (`#454768`) y el segmento activo se invierte mostrando fondo blanco con texto en `color/text/primary`.

### Device sizes — Desktop y Handheld
El componente tiene tamaños preestablecidos según el dispositivo. La versión **Desktop** tiene una altura de 80px con tipografía más grande. La versión **Handheld** tiene 48px de altura con tipografía reducida. En ambos casos los botones distribuyen el espacio equitativamente dentro del container.

### States — Selected e Idle
Muestra los dos estados del segmento en contexto de tipo Inverse (container oscuro). El estado **Selected** destaca el botón activo con fondo blanco contrastante. El estado **Idle** corresponde a los segmentos no seleccionados: sin fondo especial, texto sobre el color del container.

### Settings — Opciones variables
El componente permite entre 2 y 4 segmentos. El ancho de cada botón es consistente dentro de un mismo componente, pero el ancho total del conjunto se adapta según la longitud de las etiquetas. Se muestran dos instancias con 4 segmentos: una con etiquetas largas ("Button 1", "Button 2"…) y otra con etiquetas cortas ("B1", "B2"…), demostrando que el componente se contrae cuando el contenido es más breve.

### Caso de uso — Handheld (pantalla de escaneo)
Segmented control de tipo Idle con 2 segmentos ubicado en la parte superior de una pantalla de escaneo móvil. Permite al usuario alternar entre dos modos de visualización del producto. El primer segmento está seleccionado por defecto. Debajo aparece la imagen y datos del artículo escaneado.

### Caso de uso — Desktop (selección de fuente de cámara)
Segmented control de tipo Inverse con 3 segmentos ("Webcam 1", "Webcam 2", "Celular") posicionado en la esquina superior derecha sobre una vista de cámara. Permite cambiar la fuente de video activa en una estación de escaneo. El tipo Inverse garantiza legibilidad sobre el fondo oscuro de la imagen de cámara.

---

## Recomendaciones

### ✅ Do

- Usar etiquetas cortas y claras en cada segmento para facilitar la lectura rápida.
- Mantener el mismo tipo (Idle o Inverse) consistente dentro de una misma pantalla.
- Usar entre 2 y 4 opciones. Para más opciones, considerar un componente diferente.
- Asegurarse de que siempre haya una opción seleccionada por defecto al cargar la pantalla.

### ❌ Don't

- No usar el Segmented control como navegación principal entre pantallas distintas; para eso usar tabs o navegación.
- No mezclar opciones con longitudes de texto muy dispares que rompan la equidad visual entre botones.
- No usar más de 4 opciones; la legibilidad y el espacio disponible se degradan.

---

## Mapeamiento técnico

### Props del componente (Figma → código)

| Prop Figma | Tipo | Valores | Descripción |
|---|---|---|---|
| `type` | `enum` | `Idle` / `Inverse` | Variante visual del componente |
| `showButton3` | `boolean` | `true` / `false` | Muestra u oculta el tercer segmento |
| `showButton4` | `boolean` | `true` / `false` | Muestra u oculta el cuarto segmento |
| `label` (por botón) | `string` | texto libre | Etiqueta visible de cada segmento |

### Eventos esperados

| Evento | Descripción |
|---|---|
| `onChange(index)` | Se dispara al seleccionar un segmento. Retorna el índice (0-based) del segmento activo. |

### Dependencias

El componente no depende de otros componentes de la librería. Es una unidad atómica de selección.

### Nombre en librería Figma

`Segmented control` — nodo ID: `19230:972` (Tetris Library 2.0)

---

## Criterios de aceptación

- [ ] Siempre hay exactamente un segmento seleccionado (nunca cero, nunca dos).
- [ ] Al seleccionar un segmento, el anterior se deselecciona inmediatamente.
- [ ] El componente admite entre 2 y 4 segmentos; fuera de ese rango no debe renderizarse.
- [ ] Los botones distribuyen el espacio de forma equitativa; ninguno es más ancho que otro.
- [ ] El tipo Idle se usa sobre fondos claros; el tipo Inverse, sobre fondos oscuros o imágenes.
- [ ] El contraste del texto activo sobre su fondo supera 4.5:1 (WCAG AA).
- [ ] El componente es navegable por teclado: Tab para foco, flechas para selección interna.
- [ ] En Handheld, el área de toque de cada segmento es de al menos 44×44px.
- [ ] Hay una opción preseleccionada por defecto al cargar la pantalla.
- [ ] El texto truncado con elipsis es visible y no se corta dentro del botón.

---

## Componentes relacionados

- **Switch**: alternativa cuando la elección es estrictamente binaria (on/off) y no requiere mostrar etiquetas de opción. Usar Segmented control cuando hay 2 o más opciones con labels visibles; usar Switch cuando alcanza con un toggle sin contexto adicional.

---

## Accesibilidad

### Roles y etiquetado

El componente debe implementarse con `role="group"` en el container y cada botón con `role="radio"` dentro de un `radiogroup`, o bien como botones con `aria-pressed`. El botón activo debe tener `aria-checked="true"` (si se usa el patrón radio) o `aria-pressed="true"`.

Se recomienda incluir un `aria-label` descriptivo en el container que indique el propósito del grupo (ej. `aria-label="Tipo de vista"`).

### Navegación

La lectura sigue el orden de izquierda a derecha. El foco se mueve entre segmentos con las teclas de flecha. El componente completo recibe foco como una unidad y la navegación interna es mediante flechas.

### Interacciones con teclado

| Tecla | Función |
|-------|---------|
| Tab | Enfocar el componente |
| Flecha derecha / Flecha abajo | Mover al siguiente segmento y seleccionarlo |
| Flecha izquierda / Flecha arriba | Mover al segmento anterior y seleccionarlo |
| Space / Enter | Activar el segmento enfocado |

> Las flechas de dirección también seleccionan el segmento al navegar.

### Gestos

| Gesto | Función |
|-------|---------|
| Tap | Seleccionar el segmento tocado |
| Swipe derecha / izquierda | Navegar entre segmentos (según implementación) |

### Consideraciones de diseño

- El contraste entre el texto del botón activo y su fondo debe cumplir **WCAG 2.1 AA** (relación mínima 4.5:1 para texto normal).
- En tipo Idle: texto blanco (`#ffffff`) sobre `#454768` — relación ~5.8:1 ✓
- En tipo Inverse: texto `#1c1c2b` sobre `#ffffff` — relación ~17.7:1 ✓
- El área de toque de cada segmento debe ser suficientemente grande en Handheld (mínimo 44×44px recomendado por WCAG 2.5.5).
- Siempre debe haber una opción preseleccionada para que el estado inicial sea claro para lectores de pantalla.
