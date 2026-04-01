
# **Transit screen**

| | |
|---|---|
| **Owner** | Tetris |
| **Nombre anterior** | Direction screen |
| **Status** | WIP |
| **Última revisión** | Marzo 2026 |
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=23847-1020) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=3158-17891) |

> [!ABSTRACT]
> El Transit screen es un preset de pantalla completa para Handheld que orienta al rep hacia dónde debe desplazarse dentro del depósito. Muestra únicamente el nivel macro de la dirección (los primeros campos), no los niveles micro que el rep necesitará buscar visualmente una vez llegue al lugar.

---

## Descripción general

El Transit screen pone el foco en los datos de tránsito: la información que el rep necesita para iniciar su desplazamiento, nada más. Está compuesto por una instrucción, hasta tres bloques de dirección jerarquizados y un mecanismo de avance (timeout, escaneo o botón).

La regla de diseño central: **¿Qué parte de la dirección necesita realmente el rep para saber hasta dónde debe ir?** Todo lo demás (nivel, bin, MU dentro de una posición) corresponde a una pantalla posterior de búsqueda visual, no al Transit screen.

La pantalla tiene fondo oscuro para maximizar la legibilidad de los datos de dirección mientras el rep se desplaza.

---

## Usos habituales

- Indicar al rep hacia qué rua, módulo o área debe dirigirse antes de iniciar la búsqueda de la posición exacta.
- Comunicar el destino de desplazamiento en flujos de picking, stowing o traslado de contenedores.
- Mostrar la transición entre dos puntos de la operación con información de nivel macro.

---

## Cuándo elegir alternativas

- Usar `Container screen` cuando el rep ya llegó al lugar y necesita identificar la posición, tote o MU exacta (nivel micro).
- Usar `Action screen` cuando el flujo requiere una decisión explícita antes de iniciar el desplazamiento.
- Usar `Feedback screen` para comunicar el resultado de una operación ya completada.

---

## Anatomía

1. **Header**: componente estándar con menú secundario. No incluye título — la instrucción de pantalla se ubica en el área de título debajo del header.
2. **Instrucción (Title)**: texto de la instrucción de desplazamiento. Tipografía `Display/large`. Es la dirección en forma de frase (ej. "Vá para a nova linha", "Transit instruction").
3. **Direcciones**: hasta 3 bloques de información de dirección agrupados por relevancia. Cada bloque tiene un `label` pequeño (ej. "rua", "módulo") y un `value` grande. El bloque principal ocupa todo el ancho; los bloques secundarios se distribuyen en una fila horizontal.
   - **Tip de agrupación**: datos relacionados deben unificarse en un solo bloque. En lugar de "Área MZ" + "Piso 1" en bloques separados, usar "Área MZ-1" en un bloque único. Simplifica el consumo visual.
4. **Acción**: mecanismo de avance al siguiente paso. Puede ser timeout automático, escaneo (Touchless) o botón explícito.
5. **Progress bar**: barra de progreso al pie de la pantalla. Indica la posición dentro del flujo de tarea.

---

## Variantes

### Por tipo de dirección

| Tipo | Descripción |
|---|---|
| **Multi** | Muestra múltiples campos de dirección jerarquizados: un bloque principal (value grande) y hasta dos bloques secundarios en fila. Para contextos donde el rep necesita más de un dato para orientarse. |
| **Single (Dirija)** | Un único valor de dirección dominante a pantalla completa. Para casos donde un solo dato es suficiente para guiar el desplazamiento. |

### Por estado del área

| Estado | Descripción |
|---|---|
| **Active on** | El área de destino está activa y tiene actividad. |
| **Active off** | El área de destino no tiene actividad o está vacía. Los bloques de valores pueden mostrarse como vacíos o deshabilitados. |

### Por tipo de acción

| Tipo | Descripción |
|---|---|
| **Timeout** | La pantalla avanza automáticamente después de un período de espera. El Touchless (escaneo) está disponible si el rep quiere avanzar antes. |
| **Button** | El rep debe confirmar el desplazamiento tocando un botón explícito en la parte inferior. |

---

## Propiedades

| Propiedad | Tipo | Default | Descripción |
|---|---|---|---|
| `type` | `"Multi"` / `"Single"` | `"Multi"` | Define si se muestran múltiples bloques de dirección o uno solo dominante. |
| `naveStatus` | `"Active on"` / `"Active off"` | `"Active on"` | Estado del área de destino. |
| `bottomElementType` | `"Timeout"` / `"Button"` | `"Timeout"` | Mecanismo de avance. |
| `instructionText` | `string` | `"Transit instruction"` | Texto de la instrucción de desplazamiento. |

### Design tokens

| Token | Valor resuelto | Descripción |
|---|---|---|
| `device/breakpoints/width` | `360px` | Ancho base Handheld |
| `device/breakpoints/height` | `640px` | Alto base Handheld |
| `color/background/inverse` | `#1c1c2b` | Fondo oscuro general de la pantalla |
| `color/text/inverse` | `#ffffff` | Color del texto principal sobre fondo oscuro |
| `color/text/secondary` (inverse) | — | Labels de dirección (ej. "rua", "módulo") |

---

## Comportamiento

- **Dimensiones**: `360×640px` (rango Handheld: min `320px` ancho, `530px` alto).
- **Fondo**: oscuro (`color/background/inverse`). Diseñado para lectura rápida en movimiento.
- **Header**: `68px` de alto. Sin título en el header — la instrucción aparece en el área de título debajo.
- **Instrucción**: área de `36px` de alto debajo del header (y=78). Tipografía Display/large.
- **Container de direcciones**: inicia en y=114, ocupa `498px` de alto. Box interior de `312×308px` con padding de `24px`. Contiene:
  - Bloque principal: label (20px) + value (72px de alto) — máximo legibilidad a distancia.
  - Fila secundaria: dos items de `154×144px` con label (20px) + value (56px de alto).
- **Hasta 3 bloques** de información de dirección. No más — la pantalla no debe convertirse en un listado de datos.
- **Touchless** (timeout): componente de escaneo de `95px` de alto en y=560.
- **Button**: botón de `96px` de alto en y=464 (mutuamente excluyente con Touchless en la mayoría de variantes).
- **Progress bar**: `4px` de alto, `312px` de ancho, con `24px` de padding horizontal. Siempre visible al pie.
- La pantalla **no tiene scroll** — toda la información debe caber en el alto disponible.

---

## Ejemplos

### Tránsito hacia una posición con 3 bloques de dirección y botón de confirmación

Variante **Multi** con acción **Button**. La pantalla muestra la instrucción "Dirigete hacia la posición indicada" en el área de título, seguida de tres bloques de dirección jerarquizados: el bloque principal ocupa todo el ancho con el valor de rua o área ("AB-1") en tipografía de gran tamaño, y debajo dos bloques secundarios en fila horizontal con los valores de módulo y posición ("000" / "000"). El rep confirma el desplazamiento tocando el botón blanco al pie de la pantalla. El fondo oscuro maximiza la legibilidad de los datos mientras el rep camina hacia la posición indicada.

---

## Recomendaciones

### ✅ Do
- Mostrar solo los campos de dirección que el rep necesita para iniciar el desplazamiento (nivel macro).
- Agrupar datos relacionados en un solo bloque (ej. "Área MZ-1" en lugar de "Área MZ" + "Piso 1" por separado).
- Destacar visualmente el campo que representa un cambio respecto a la pantalla anterior (ej. nueva rua).
- Limitar a 3 bloques de dirección máximo.

### ❌ Don't
- No mostrar niveles micro (nivel de bin, MU dentro de una posición) en el Transit screen — esos datos corresponden al `Container screen` o pantallas de búsqueda visual posterior.
- No usar más de 3 bloques de dirección — añade carga cognitiva al rep en movimiento.
- No omitir la instrucción — el rep necesita saber qué acción está realizando, no solo adónde va.
- No usar este preset en Desktop — es exclusivo de Handheld.

---

## Componentes relacionados

- **Header**: componente de encabezado con menú secundario (sin título).
- **Progress bar**: barra de progreso al pie, indica posición en el flujo.
- **Touchless**: componente de escaneo para avance por timeout/scan.
- **Button**: botón de confirmación para variante con acción explícita.
- **Container screen**: preset complementario para el nivel micro de la dirección (posición exacta, tote, slot map).
- **Action screen**: preset alternativo cuando el rep debe tomar una decisión antes de desplazarse.

---

## Accesibilidad

### Roles y etiquetado

La pantalla debe tener un `<main>` como contenedor principal. La instrucción de desplazamiento debe implementarse con `<h1>`. Cada bloque de dirección debe estar estructurado semánticamente: el `label` asociado al `value` mediante `aria-labelledby` o un elemento `<label>` semántico, para que los lectores de pantalla anuncien el contexto antes del valor numérico.

Los valores de dirección grandes (ej. "AB-1", "000") deben ser legibles por lector de pantalla sin depender solo de la escala visual.

### Navegación

Orden de lectura: header → instrucción → bloque principal de dirección → bloques secundarios → acción (Touchless o botón) → progress bar.

### Interacciones con teclado

| Tecla | Función |
|---|---|
| Tab | Navegar entre elementos interactivos (menú del header, botón de acción) |
| Enter / Space | Activar el botón enfocado |

### Gestos

| Gesto | Función |
|---|---|
| Tap en Touchless | Avanzar antes de que expire el timeout |
| Tap en botón | Confirmar desplazamiento (variante Button) |
| Tap en menú (header) | Abrir menú de navegación secundaria |

### Consideraciones de diseño

- El fondo oscuro (`#1c1c2b`) con texto blanco cumple WCAG AA para texto de cualquier tamaño.
- Los valores de dirección (72px y 56px de alto) son texto de muy gran tamaño: cumplen cualquier criterio de contraste WCAG incluso con valores intermedios.
- El progress bar de `4px` es puramente decorativo en términos de accesibilidad — no transmite información crítica por sí solo. Debe complementarse con texto o estado semántico si es necesario para la navegación por lector de pantalla.
