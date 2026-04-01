<!--
nombre: Highlight
owner: tetris
madurez: stable
aliases: —
fecha-revisión: 2026-03-25
-->

# Highlight

> [!ABSTRACT]
> Armado de texto que estandariza tamaños y estructuras de contenido. Puede alinearse a la izquierda, al centro y a la derecha.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=13971-4734) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=2943-29180) |

![][cover]

## Descripción general

El Highlight es un componente de presentación de datos que resalta visualmente un valor o cantidad de forma prominente. Su función principal es comunicar métricas o cifras clave de un vistazo. Está compuesto por un texto principal de gran tamaño y una etiqueta contextual opcional (label) ubicada sobre el valor, permitiendo describir qué representa la cifra mostrada.

### Usos habituales

- Mostrar un identificador o código alfanumérico corto de forma prominente (ej. "4A", "12B").
- Indicar una posición, piso, calle o módulo en pantallas de navegación o picking.
- Destacar una dirección o slot en una estantería de depósito.
- Indicar un empaque particular dentro de un flujo de Packing.

### Cuándo elegir otra opción

- Si necesitás mostrar valores numéricos que refieren a cantidades, usá [Counter](#). El Counter está diseñado específicamente para ese caso y ofrece la opción de mostrar un total y un parcial cambiante en una sola instancia.

## Anatomía

![][anatomy]

1. **Indicator label** *(opcional)*: etiqueta descriptiva ubicada encima del valor Highlight que contextualiza lo que representa. Máximo 1 línea. Se puede ocultar con la prop `indicatorLabel`.
2. **Highlight**: valor principal del componente. Texto de gran tamaño diseñado para concentrar la atención de la persona usuaria. Máximo 1 línea.

## Propiedades

### indicatorLabel

Controla si el Indicator label es visible. Cuando está desactivado, solo se muestra el valor Highlight.

| Nombre | Detalle |
| :---- | :---- |
| true *(default)* | El Indicator label es visible. |
| false | El Indicator label se oculta. |

### label

Texto del Indicator label. Define el contexto semántico del valor que se muestra. Si `indicatorLabel` es `false`, esta propiedad no tiene efecto visual.

### highlight

Valor principal que se muestra en gran tamaño. Se recomienda un máximo de 3 a 4 caracteres para preservar la legibilidad en ambos device sizes.

### alignment

Define la alineación horizontal del contenido del componente.

| Nombre | Detalle |
| :---- | :---- |
| Left | El contenido se alinea a la izquierda. |
| Center | El contenido se alinea al centro. |
| Right | El contenido se alinea a la derecha. |

## Estados

| Estado | Diferencia visual | Combinable con | Excluye a |
| :---- | :---- | :---- | :---- |
| Default | — | — | — |

*El Highlight es un elemento no interactivo. No tiene estados de Hover, Focus, Pressed ni Disabled.*

## Comportamiento

### Device sizes

El componente tiene tamaños tipográficos preestablecidos para dos contextos de uso. El tamaño no se elige como propiedad explícita sino que se adapta automáticamente al device.

- **Desktop**: versión de mayor escala, creada para que el valor destaque en pantallas grandes de estación de trabajo.
- **Handheld**: versión reducida, creada para visualización en pantallas pequeñas de dispositivos móviles.

### Alineación

El contenido del componente se organiza en columna vertical centrada. El gap entre el Indicator label y el valor Highlight es fijo, al igual que el padding interior del container.

## Ejemplos

### Highlight como indicador de dirección en pantalla de navegación

![][example-direction]

En una pantalla de navegación, el Highlight se usa para mostrar el número de calle y el módulo de destino de forma prominente. Cada instancia utiliza el Indicator label ("Calle", "Módulo") para contextualizar el valor numérico que le corresponde. Este patrón permite a la persona operaria capturar los dos datos de destino de un solo vistazo.

### Highlight en contexto de picking con posición y piso

![][example-picking]

En una pantalla de picking de producto, el Highlight presenta valores de posicionamiento como el piso, el pasillo o el slot de destino. El Indicator label identifica qué representa cada valor dentro del flujo de la tarea.

## Recomendaciones

![][do-01]

> [!DO]
> Usá el Indicator label para dar contexto al valor. Un código como "4A" sin label no comunica nada por sí solo; con un label como "Pasillo" el significado es inmediato.

![][dont-01]

> [!DONT]
> No uses el Highlight con palabras largas. El componente está diseñado para un máximo de 3 a 4 caracteres; textos más largos rompen la jerarquía visual.

![][dont-02]

> [!DONT]
> No uses el Highlight en contextos de cantidad. Para eso, usá [Counter](#).

## Componentes relacionados

- Counter
- Transit screen

## Accesibilidad

*Esta sección incluye solo las consideraciones esenciales de accesibilidad que están implementadas en los componentes de Tetris, como por ejemplo el uso de roles y etiquetas que facilitan comprender el propósito de los componentes cuando son interpretados por lectores de pantalla, así como la navegación por teclas o gestos que garantizan una interacción inclusiva.*

*Para conocer más en detalle sobre tecnologías asistivas, te recomendamos visitar la [guía de accesibilidad digital](#). Para saber más sobre cómo hacer un hand off accesible, visitá la documentación de [Accessibility notes](#).*

### Roles y etiquetado

El Highlight es un elemento de visualización no interactivo. No recibe foco ni tiene rol semántico propio. Si el valor mostrado en el Highlight es relevante para la comprensión del contexto —lo cual, en la mayoría de los casos, lo es— debe estar disponible también como texto accesible en el componente o pantalla que lo contiene.

El Indicator label actúa como etiqueta contextual del valor. Cuando se oculta (`indicatorLabel: false`), asegurate de que el valor del Highlight sea comprensible por sí solo o que el contexto de la pantalla lo provea de otra forma.

### Navegación

La navegación de las interfaces por medio de tecnologías asistidas se realiza de manera convencional, siguiendo un orden de lectura de izquierda a derecha y de arriba hacia abajo, ya sea mediante gestos (Handheld) o mediante teclado (Desktop).

El Highlight no es navegable directamente por teclado ni por gestos, ya que no es un elemento interactivo.

#### Teclado

| Tecla | Descripción |
| :---- | :---- |
| — | El Highlight no recibe foco por teclado. |

#### Gestos

| Gesto | Descripción |
| :---- | :---- |
| — | El Highlight no responde a gestos directos. |

### Consideraciones de diseño

- **Contraste del valor principal:** el Highlight usa `color/text/primary` (#1c1c2b) que garantiza contraste adecuado sobre fondo blanco. Este token cumple con WCAG 2.2 nivel AA.
- **Contraste del Indicator label:** usa `color/text/secondary` (#5a5a7c). Verificar el ratio de contraste en los contextos específicos de uso, especialmente sobre fondos no blancos.
- **Tamaño de texto:** tanto el valor principal (200px) como el Indicator label (32px) son de gran tamaño, lo que favorece la legibilidad en condiciones de uso operativo (distancia, iluminación variable, movimiento).
- **No usar el Highlight como única fuente de información crítica:** si el valor que muestra es esencial para completar una tarea, complementarlo con contexto adicional en la pantalla o mediante texto accesible programático.

## Especificaciones técnicas

| Elemento en Figma | Nombre en código | Tipo | Token resuelto | Notas |
| :---- | :---- | :---- | :---- | :---- |
| Highlight / color de texto | color | color | `color/text/primary` → #1c1c2b | — |
| Indicator label / color de texto | color | color | `color/text/secondary` → #5a5a7c | — |
| Highlight / font-size | font-size | typography | `Content/highlight/text/title/font-size` → 200px | — |
| Highlight / line-height | line-height | typography | `Content/highlight/text/title/line-height` → 192px | — |
| Highlight / letter-spacing | letter-spacing | typography | — → -8px | *(inferido — requiere validación)* |
| Indicator label / font-size | font-size | typography | `Content/highlight/text/label/font-size` → 32px | — |
| Indicator label / line-height | line-height | typography | `Content/highlight/text/label/line-height` → 32px | — |
| Indicator label / letter-spacing | letter-spacing | typography | — → -1px | *(inferido — requiere validación)* |
| Container / gap | gap | dimension | `Content/highlight/spacing/gap` → 40px | Entre Indicator label y Highlight |
| Container / padding | padding | dimension | `Content/highlight/spacing/padding` → 40px | Padding interior del container |

[cover]: ./assets/cover.png
[anatomy]: ./assets/anatomy.png
[example-direction]: ./assets/example-direction.png
[example-picking]: ./assets/example-picking.png
[do-01]: ./assets/do-01.png
[dont-01]: ./assets/dont-01.png
[dont-02]: ./assets/dont-02.png
