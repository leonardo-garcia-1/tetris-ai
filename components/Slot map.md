# Slot map

> [!ABSTRACT]
> El Slot map es un componente que representa visualmente la distribución de posiciones dentro de una estantería o espacio físico, permitiendo al usuario identificar y seleccionar posiciones dentro de una grilla. Resuelve la necesidad de orientar al operario en contextos de gestión de almacén o punto de venta.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=224-2015) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=5-349) |

Componente en librería
Specs
Permite visualizar la organización de elementos dentro de un espacio determinado.

---

## Identidad del componente

| Campo | Valor |
|-------|-------|
| Nombre canónico | Slot map |
| Aliases permitidos | `SlotMap`, `slot-map` |
| Categoría | Visualización de espacio físico |
| Dominio | Gestión de almacén / Punto de venta |
| Owner | Tetris |
| Status de madurez | Componente en librería |
| Fecha de última revisión | — |

---

## Descripción general

El Slot map es un componente que representa visualmente la distribución de posiciones dentro de una estantería o espacio físico. Cada celda (slot) puede encontrarse en distintos estados —vacía, activa, deshabilitada o lista— y refleja de manera fiel la estructura real de la estantería que representa.

Se utiliza principalmente en contextos de gestión de almacén o punto de venta, donde el usuario necesita identificar y seleccionar posiciones dentro de una grilla de estanterías, tanto en dispositivos de escritorio como en dispositivos handheld.

---

## Usos habituales

- Cuando se necesita representar visualmente la disposición de productos dentro de una estantería.
- Para que el usuario identifique y seleccione una posición específica dentro de un slot.
- Para reflejar el estado actual de cada posición en tiempo real (ocupada, disponible, activa).

### Contexto de composición

El Slot map se usa típicamente como elemento central de una pantalla de selección de posición. Puede estar acompañado de:
- Un encabezado que identifique la estantería o sección.
- Controles de navegación entre estanterías cuando hay más de una.
- Un indicador o resumen de la posición activa seleccionada.

No tiene dependencias estructurales obligatorias: puede funcionar como componente standalone dentro de un layout de pantalla completa o dentro de un modal/panel lateral.

---

## Cuándo elegir otra opción

- Usar **Highlight** cuando la estantería tiene muchos espacios y una representación fiel del mapa resultaría demasiado densa o difícil de leer. En esos casos, señalar la posición de forma más abstracta es suficiente para guiar al usuario.
- Usar los **símbolos de capability sorting** cuando el contexto del producto lo requiere (ej. flujos de sorting por capacidad), donde la posición se comunica mediante símbolos en lugar de una grilla de slots.

---

## Anatomía

| # | Parte | Obligatoriedad | Función | Token / prop relacionado |
|---|-------|---------------|---------|--------------------------|
| 1 | **Structure** | Obligatorio | Estructura base que define las columnas laterales y la franja inferior del componente. | `color/surface/tertiary`, `border/radius/l` |
| 2 | **Rows** | Opcional (cantidad variable) | Filas de posiciones; su cantidad varía según la estantería representada. | `spacing/6xs` (gap), `spacing/4xs` (padding horizontal) |
| 3 | **Positions** | Obligatorio (mínimo 1) | Celdas individuales que representan cada slot. Pueden estar en estado Ready, Disabled, Active o Empty. | `color/surface/secondary`, `color/brand/fill`, `border/radius/xs` |

---

## Variantes *

### Desktop vertical shelve
Representa posiciones dentro de estanterías verticales para devices Desktop.

### Desktop horizontal shelve
Representa posiciones dentro de estanterías horizontales.

### Handheld vertical shelve
Representa posiciones dentro de estanterías verticales para devices Handheld.

### Combinaciones de propiedades

| Device | Direction | Variante soportada |
|--------|-----------|-------------------|
| Desktop | Vertical | ✓ Desktop vertical shelve |
| Desktop | Horizontal | ✓ Desktop horizontal shelve |
| Handheld | Vertical | ✓ Handheld vertical shelve |
| Handheld | Horizontal | — No definida. Usar Handheld vertical shelve como fallback. |

**Fallback**: Cuando una combinación no tenga variante oficial definida, usar la variante del mismo Device con Direction Vertical y notificar al equipo de design system para evaluar la necesidad de nuevas variantes.

---

## Propiedades

| Propiedad | Valores | Descripción |
|-----------|---------|-------------|
| Device | `Desktop` \| `Handheld` | Determina el dispositivo al que se adapta el componente. |
| Type | `Shelves` | Indica la clase de estructura que representa. |
| Direction | `Vertical` \| `Horizontal` | Define la orientación del estante. |

### Tokens de diseño

| Token | Valor resuelto | Uso |
|-------|---------------|-----|
| `color/surface/secondary` | `#ededf7` | Fondo de posición en estado vacío / ready |
| `color/surface/tertiary` | `#dedfed` | Columnas laterales y franja base |
| `color/brand/fill` | `#ffe600` | Fondo de posición activa |
| `color/brand/text-on-fill` | `#1c1c2b` | Texto sobre posición activa |
| `border/radius/xs` | `8px` | Radio de esquinas de cada posición |
| `border/radius/l` | `24px` | Radio del contenedor de posiciones |
| `spacing/6xs` | `8px` | Gap entre posiciones |
| `spacing/4xs` | `16px` | Padding horizontal en filas de posiciones |
| `spacing/padding/s` | `32px` | Padding inferior del contenedor de posiciones |

---

## Position states

| Estado | Detalle visual | Comportamiento |
|--------|---------------|----------------|
| Ready | Fondo `color/surface/secondary` (`#ededf7`). Sin texto visible. | Posición disponible para selección. Responde a tap / click. |
| Active | Fondo `color/brand/fill` (`#ffe600`). Muestra código de posición (ej. `4-3`) con tipografía `Heading/small` en `color/brand/text-on-fill`. | Posición seleccionada. Solo puede haber una posición Active a la vez por componente. |
| Disabled | Diferenciación visual respecto a Ready (sin depender únicamente del color). Sin interacción habilitada. | No responde a tap / click. No puede transicionar a Active. |
| Empty | Distinguible visualmente de Ready. Sin código de posición. | Representa un slot físicamente vacío. No interactivo en la mayoría de contextos. |

### Estados combinables y excluyentes

- Solo puede existir **una posición Active** por instancia del componente.
- **Disabled** y **Active** son mutuamente excluyentes: una posición no puede estar en ambos estados simultáneamente.
- **Empty** y **Disabled** pueden coexistir conceptualmente (posición vacía y no disponible), pero la representación visual debe estar definida por el equipo de diseño si se necesita distinguirlos.

---

## Comportamiento

- El componente adapta su tamaño y disposición según el valor de la propiedad **Device** (`Desktop` / `Handheld`).
- La orientación (`Direction`) determina si las filas de posiciones se despliegan en sentido vertical u horizontal.
- La cantidad de **Rows** es opcional y configurable para reflejar la cantidad exacta de filas de la estantería real.
- La posición activa muestra un tooltip con el código de la posición (ej. `4-3`) sobre la celda, con fondo `color/brand/fill` y tipografía `Heading/small`.
- Las columnas laterales y la franja base actúan como referencias visuales de los límites de la estantería.

### Edge cases

- **Estantería con una sola fila**: el componente debe renderizarse correctamente con una única Row sin romper el layout.
- **Todas las posiciones Disabled**: el componente debe ser visible e informativo, nunca ocultarse. Considerar agregar un mensaje contextual fuera del componente para guiar al usuario.
- **Estantería muy larga (muchas filas / columnas)**: si el contenido supera el área visible, el componente habilita scroll vertical u horizontal. Verificar que el scroll no rompa la alineación de Structure.
- **Actualización en tiempo real de estados**: los estados pueden cambiar mientras el usuario interactúa. Si la posición Active cambia a Disabled por actualización del sistema, se debe deseleccionar automáticamente y notificar al usuario.

### Orden de foco y lectura

El foco recorre las posiciones de izquierda a derecha y de arriba hacia abajo, respetando el orden visual de las filas. Structure y Rows no reciben foco directamente; el foco opera a nivel de Positions.

---

## Ejemplos

> Los datos que aparecen en los ejemplos (código de posición, producto, cantidad) son ilustrativos. En producción son levantados dinámicamente por el sistema según el ítem y la tarea asignada.

### Indicación de posición en flujo de picking

![][example-picking]

En una pantalla de picking Desktop, el Slot map aparece junto a la Product card y el contador de unidades. La grilla representa la estantería real y resalta en amarillo la posición donde el operario debe retirar el ítem (ej. `4-3`). El operario usa esta referencia visual para ubicarse físicamente en el espacio antes de escanear la posición para confirmar.

### Indicación de posición en preparación de estación de trabajo

![][example-workstation]

En una pantalla de preparación de estación Desktop, el Slot map muestra la posición donde el operario debe colocar el tote (ej. `3-2`). La grilla está acompañada de una instrucción textual y una acción de confirmación mediante botón luminoso físico. El componente comunica visualmente la ubicación exacta dentro de la estantería sin necesidad de descripción verbal adicional.

---

## Recomendaciones

### ✓ Do
- Usar el pattern para que refleje de manera fiel la estantería real que representa (orden y labels de los slots actuales).
- Recrear estantes a modo ilustrativo, utilizando las variables del componente, siempre y cuando se respete la cantidad y ubicaciones reales.
- Usar las variantes de posición para que el componente quede siempre adentro del slot.

### ✗ Don't
- No modificar pesos o tamaños tipográficos y colores dentro del pattern.
- No recrear una representación 100% fiel, generando inconsistencias.
- No usar las variantes de posición de manera que se salgan del slot.

---

## Mapeamiento técnico

> Los valores de nombre en código y Storybook deben completarse con referencia al repositorio de implementación.

| Elemento | Figma | Código | Notas |
|----------|-------|--------|-------|
| Componente principal | `Slot map` | `[ABIERTO]` — confirmar nombre en repo | — |
| Propiedad Device | `Device` | `device: 'desktop' \| 'handheld'` | |
| Propiedad Direction | `Direction` | `direction: 'vertical' \| 'horizontal'` | |
| Estado de posición | `state` en Position | `state: 'ready' \| 'active' \| 'disabled' \| 'empty'` | |
| Código de posición | Texto dentro de Position Active | `positionCode: string` | Ej: `"4-3"` |
| Cantidad de filas | Rows (opcional) | `rows: number` | Sin valor mínimo obligatorio |

### Props principales

| Prop | Tipo | Requerido | Descripción |
|------|------|-----------|-------------|
| `device` | `'desktop' \| 'handheld'` | Sí | Define la variante de dispositivo |
| `direction` | `'vertical' \| 'horizontal'` | Sí | Define la orientación del estante |
| `rows` | `number` | No | Cantidad de filas de posiciones |
| `positions` | `Position[]` | Sí | Array de posiciones con su estado y código |
| `onPositionSelect` | `(positionCode: string) => void` | No | Callback al seleccionar una posición |

### Eventos

| Evento | Descripción |
|--------|-------------|
| `onPositionSelect` | Se dispara al activar una posición (tap, click, Enter/Space). Recibe el código de la posición. |
| `onPositionFocus` | Se dispara al enfocar una posición por teclado o tab. |

### Restricciones técnicas

- No modificar tokens de color o tipografía directamente en el componente; los overrides deben hacerse a nivel de tema.
- No crear instancias de Position fuera del contexto del Slot map.
- La combinación `Handheld + Horizontal` no tiene variante oficial; no implementar sin aprobación del equipo de design system.

---

## Accesibilidad

### Roles y etiquetado
El Slot map debe marcarse como una región con `role="grid"` o `role="figure"` según el contexto de uso. Cada celda de posición debe tener un `aria-label` que describa su código y estado (ej. `aria-label="Posición 4-3, activa"`). El contenedor principal debe incluir un `aria-label` descriptivo del mapa completo.

### Atributos por estado

| Estado | Atributo requerido |
|--------|--------------------|
| Ready | `aria-label="Posición {código}, disponible"` |
| Active | `aria-label="Posición {código}, activa"` · `aria-selected="true"` |
| Disabled | `aria-label="Posición {código}, no disponible"` · `aria-disabled="true"` |
| Empty | `aria-label="Posición {código}, vacía"` |

### Navegación
El orden de lectura sigue el flujo natural de izquierda a derecha, de arriba hacia abajo, recorriendo las filas de posiciones en secuencia.

### Teclado

| Tecla | Función |
|-------|---------|
| Tab | Enfocar el componente |
| Flechas (↑ ↓ ← →) | Navegar entre posiciones de la grilla |
| Enter / Space | Activar o seleccionar la posición enfocada |

### Gestos

| Gestos | Detalle |
|--------|---------|
| Tap | Seleccionar una posición |
| Scroll vertical / horizontal | Desplazarse por la grilla cuando el contenido supera el área visible |

### Feedback no visual

- Al seleccionar una posición, el lector de pantalla debe anunciar: `"Posición {código} seleccionada"`.
- Al desactivar una posición, anunciar: `"Posición {código} deseleccionada"`.
- Si una posición activa pasa a Disabled por actualización del sistema, anunciar: `"Posición {código} ya no está disponible"`.
- Las posiciones Disabled deben ser anunciadas como no interactivas; no deben recibir foco de teclado.

### Consideraciones de diseño
- Verificar que el contraste entre el fondo de posición activa (`color/brand/fill` `#ffe600`) y el texto (`color/brand/text-on-fill` `#1c1c2b`) cumpla con WCAG AA (4.5:1 para texto normal).
- Verificar el contraste de las posiciones en estado Disabled respecto al fondo, para garantizar su distinción sin depender únicamente del color.
- El componente debe ser legible en distintas densidades de grilla (pocas filas vs. muchas filas).

---

## Evidencias y validación

### Criterios de aceptación

- [ ] El componente renderiza correctamente en las 3 variantes documentadas (Desktop vertical, Desktop horizontal, Handheld vertical).
- [ ] Cada posición refleja correctamente su estado visual: Ready, Active, Disabled, Empty.
- [ ] Solo una posición puede estar Active simultáneamente.
- [ ] Al seleccionar una posición Ready, transiciona a Active y la anterior vuelve a Ready.
- [ ] Las posiciones Disabled no responden a interacción.
- [ ] El código de posición es visible y legible en estado Active.
- [ ] El componente funciona con scroll cuando el contenido supera el área visible.
- [ ] Todos los tokens de diseño documentados están aplicados correctamente.
- [ ] El componente es navegable por teclado (Tab + flechas + Enter/Space).
- [ ] Los atributos ARIA reflejan el estado actual de cada posición.

### Tests de regresión visual

- [ ] Snapshot visual de cada variante en estado base (todas las posiciones Ready).
- [ ] Snapshot con una posición Active por variante.
- [ ] Snapshot con posiciones Disabled y Empty presentes.
- [ ] Snapshot en breakpoint Desktop y Handheld.

### Tests de accesibilidad

- [ ] Test de contraste: Active position cumple WCAG AA (4.5:1).
- [ ] Test de contraste: Disabled position es distinguible sin depender solo del color.
- [ ] Test de teclado: navegación completa sin mouse.
- [ ] Test con lector de pantalla: los estados son anunciados correctamente.

### Casos correctos de uso

- Grilla de estantería con 3 filas × 5 posiciones, una posición Active con código `2-3`.
- Grilla en modo Horizontal Desktop con posiciones en estados mixtos (Ready, Disabled, Empty).

### Casos incorrectos de uso (contraejemplos)

- Usar el componente para representar una estructura que no sea una estantería física.
- Tener dos posiciones Active al mismo tiempo.
- Aplicar overrides de color directamente sobre las posiciones sin usar los tokens documentados.
- Usar Handheld + Horizontal sin aprobación del equipo de design system.

[example-picking]: ./assets/slot-map-example-picking.png
[example-workstation]: ./assets/slot-map-example-workstation.png
