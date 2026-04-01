<!--
nombre: Badge
owner: Tetris
madurez: stable
aliases: —
fecha-revisión: 2026-03-20
-->

# Badge

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=7501-2614) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=2657-4857) |

> [!ABSTRACT]
> Son pequeñas unidades de información que aparecen como complemento dentro de determinados componentes.

![][cover]

## Descripción general

El Badge es un elemento de etiquetado compacto y no interactivo que se usa para comunicar estados, categorías o cantidades de forma rápida y visualmente clara. Acompaña a otros elementos de la interfaz —como ítems de lista, títulos o tarjetas— para agregar contexto sin interrumpir el flujo de lectura. Su tamaño reducido y su carga semántica de color lo hacen especialmente útil en interfaces con alta densidad de información.

### Usos habituales

- Indicar el estado de un elemento (activo, inactivo, pendiente).
- Mostrar una categoría o etiqueta asociada a un contenido.
- Comunicar una cantidad o conteo de forma compacta (ej. notificaciones no leídas).

### Cuándo elegir otra opción

- Si el elemento requiere interacción del usuario, considerá usar [Button](#) o [Button icon](#) en su lugar.
- Si necesitás mostrar mensajes de error o alertas, usá [Snackbar](#).
- Si el contenido es extenso o necesita más jerarquía visual, considerá un componente de mayor peso.

## Anatomía

La anatomía del Badge varía según el tipo de contenido que muestra. Existen tres configuraciones posibles:

**Label**
1. **Container:** envuelve todos los elementos del Badge y define su forma y color de fondo.
2. **Icon:** ícono complementario al label. Opcional.

*El Label admite máximo 1 línea de texto.*

**Number**
1. **Value:** contenido numérico compacto dentro del container.

*El Value admite máximo 2 caracteres.*

**Icon**
1. **Icon:** único elemento visible, sin label ni value.

## Variantes

El Badge tiene una propiedad de **Hierarchy** con dos valores: Loud y Quiet. Ambos se combinan con las opciones de color semántico: Positive, Caution, Negative e Informative.

### Loud

Usa fondo de color sólido con contenido en blanco. Es la jerarquía de mayor peso visual y se usa cuando el Badge necesita destacarse claramente dentro del contexto.

### Quiet

Usa fondo tenue con texto e ícono en el color semántico correspondiente. Es la jerarquía de menor peso visual y se usa cuando el Badge debe informar sin competir con otros elementos de la interfaz.

## Propiedades

### Color

Define el tono semántico del Badge. Cada color comunica un significado específico y se combina con la propiedad Hierarchy (Loud / Quiet).

| Nombre | Detalle |
| :----- | :------ |
| Positive (green) | Éxito, activo, positivo |
| Caution (orange) | Advertencia, atención requerida |
| Negative (red) | Error, alerta crítica, negativo |
| Informative (grey) | Informativo, genérico |


## Estados

| Estado | Diferencia visual | Combinable con | Excluye a |
| :----- | :---------------- | :------------- | :-------- |
| Default | — | — | — |

*El Badge es un elemento no interactivo. No tiene estados de Hover, Focus, Pressed ni Disabled salvo que se indique lo contrario en Figma. (inferido — requiere validación)*

## Comportamiento

### Contenido

El label del Badge debe ser breve. Se recomienda no superar 2–3 palabras o un número. Si el contenido es demasiado largo, el texto puede truncarse con ellipsis según la implementación.

### Device sizes

El Badge tiene dos tamaños según el dispositivo: uno para Desktop y uno para Handheld. El tamaño no se elige como propiedad explícita sino que se adapta automáticamente al contexto de uso.

### Corners

Los bordes del Badge se modifican para adaptarse a la posición donde se ubica el componente. El radio de esquina puede variar según el contexto de anclaje.

### Alineación

El Badge se alinea de forma inline con el contenido al que acompaña. En listas o tablas, respeta la alineación vertical del elemento contenedor.

## Ejemplos

### Badge pill como etiqueta de atributo en lista de productos

![][example-product-list]

En una pantalla de escaneo de productos en Desktop, el Badge pill se usa para comunicar atributos especiales de manipulación directamente sobre el ítem de la lista. En este caso, las etiquetas "Frágil" y "Líquido" aparecen debajo del nombre del producto para alertar a la persona operaria antes de manipularlo. El uso de múltiples badges sobre un mismo ítem es válido cuando los atributos son independientes entre sí.

### Badge number en bottom navigation

![][example-bottom-nav]

En el contexto de una estación de trabajo de Desktop, el Badge number se usa sobre un ítem del [Bottom navigation](#) para indicar la cantidad de totes activos. El número "1" comunica de forma compacta que hay un tote en curso, sin interrumpir el flujo de la interfaz principal.

## Recomendaciones

![](./assets/do-01.png)

> [!DO]
> Usá el color semántico que corresponde al significado real del contenido: Positive para éxito, Negative para error, Caution para advertencia.

![](./assets/dont-01.png)

> [!DONT]
> No uses el Badge para comunicar información crítica solo a través del color. Complementá siempre con texto o ícono.

![](./assets/do-02.png)

> [!DO]
> Mantené el contenido breve: máximo 1 línea de texto o 2 caracteres numéricos.

![](./assets/dont-02.png)

> [!DONT]
> No uses el Badge como elemento interactivo ni le agregues comportamiento de tap o click. Para eso usá [Button](#) o [Button icon](#).

## Componentes relacionados

- Button
- Button icon
- Product card
- Snackbar

## Accesibilidad

*Esta sección incluye solo las consideraciones esenciales de accesibilidad para la persona usuaria.*

> [!WARNING]
> Este componente no cumple con los criterios de contraste mínimo de WCAG 2.2. Usarlo con conciencia del impacto en personas con baja visión o daltonismo.

### Criterios soportados

| Criterio | Nivel | Estándar | Estado |
| :------- | :---- | :------- | :----- |
| Labelling and roles | AA | WCAG 2.2.2 | ✅ Cumple |
| Navigation | AA | WCAG 2.2.2 | ✅ Cumple |
| Color contrast | — | WCAG 2.2 | ❌ No cumple |

### Roles y etiquetado

El Badge es un elemento no interactivo. No recibe foco ni tiene rol semántico propio. Si el contenido del Badge es relevante para la comprensión del contexto, debe estar disponible también como texto accesible en el componente que lo contiene.

### Navegación

El Badge no es navegable por teclado ni por gestos, ya que no es un elemento interactivo.

#### Teclado

| Tecla | Descripción |
| :---- | :---- |
| — | El Badge no recibe foco por teclado. |

#### Gestos

| Gesto | Descripción |
| :---- | :---- |
| — | El Badge no responde a gestos directos. |

### Consideraciones de diseño

- **Contraste:** los colores semánticos del Badge (especialmente en jerarquía Quiet) pueden no cumplir el ratio de contraste mínimo de 4.5:1 exigido por WCAG 2.2. No usar el Badge como único indicador de estado cuando el contraste sea insuficiente.
- **No usar solo color:** el significado semántico (Positive, Caution, Negative, Informative) no debe comunicarse únicamente a través del color. Complementar con texto o ícono cuando sea posible.

## Especificaciones técnicas

| Elemento en Figma | Nombre en código | Tipo | Token resuelto | Notas |
| :---------------- | :--------------- | :--- | :------------- | :---- |
| Background / Loud + Positive | background-color | color | `color/feedback/fill/positive-loud` → `color/green/500` | — |
| Background / Loud + Caution | background-color | color | `color/feedback/fill/caution-loud` → `color/orange/500` | — |
| Background / Loud + Negative | background-color | color | `color/feedback/fill/negative-loud` → `color/red/500` | — |
| Background / Loud + Informative | background-color | color | `color/feedback/fill/informative-loud` → `color/gray/700` | — |
| Background / Quiet + Positive | background-color | color | `color/feedback/fill/positive-quiet` → `color/green/100` | — |
| Background / Quiet + Caution | background-color | color | `color/feedback/fill/caution-quiet` → `color/orange/100` | — |
| Background / Quiet + Negative | background-color | color | `color/feedback/fill/negative-quiet` → `color/red/100` | — |
| Background / Quiet + Informative | background-color | color | `color/feedback/fill/informative-quiet` → `color/gray/200` | — |
| Text / Loud + Positive | color | color | `color/feedback/text/positive-loud` → `color/green/900` | — |
| Text / Loud + Caution | color | color | `color/feedback/text/caution-loud` → `color/orange/900` | — |
| Text / Loud + Negative | color | color | `color/feedback/text/negative-loud` → `color/red/900` | — |
| Text / Loud + Informative | color | color | `color/feedback/text/informative-loud` → `color/gray/900` | — |
| Text / Quiet + Positive | color | color | `color/feedback/text/positive-quiet` → `color/green/500` | — |
| Text / Quiet + Caution | color | color | `color/feedback/text/caution-quiet` → `color/orange/500` | — |
| Text / Quiet + Negative | color | color | `color/feedback/text/negative-quiet` → `color/red/500` | — |
| Text / Quiet + Informative | color | color | `color/feedback/text/informative-quiet` → `color/gray/700` | — |
| Border radius / Badge pill | border-radius | dimension | `Badge/structure/border/radius-in-pill` → `border/radius/l` = 24px | — |
| Padding horizontal | padding-inline | dimension | `Badge/structure/spacing/padding-horizontal` → `spacing/padding/2xs` = 20px | — |
| Gap (icon + label) | gap | dimension | `Badge/structure/spacing/gap` → `spacing/gap/xs` = 8px | — |
| Height / Badge pill | height | dimension | `Badge/structure/size/height-pill` = 48px | — |
| Height / Badge icon + number | height | dimension | `Badge/structure/size/height-icon-number` = 40px | — |
| Icon size / in pill | width / height | dimension | `Badge/structure/icon/in-pill` = 24px | — |

[cover]: ./assets/cover.png
[example-bottom-nav]: ./assets/example-bottom-nav.png
[example-product-list]: ./assets/example-product-list.png
