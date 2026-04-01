<!--
nombre: Numpad
owner: Tetris
madurez: stable
aliases: Num pad, teclado numérico
fecha-revisión: 2026-03-26
-->

# Num pad

> [!ABSTRACT]
> Permite ingresar valores numéricos mediante interacción táctil o cursor.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=1208-8415) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=4519-3474) |

## Descripción general

El Num pad es un componente que permite ingresar valores numéricos mediante interacción táctil o cursor. Está compuesto por un conjunto de botones numéricos (del 1 al 9) organizados en una cuadrícula flexible, adaptada a los dispositivos Desktop y Handheld del sistema Tetris DS.

Es especialmente útil en flujos donde se necesita guiar a la persona usuaria hacia una entrada numérica controlada, como el ingreso de una cantidad de unidades específica. Al reemplazar el teclado nativo del dispositivo, ofrece una experiencia más predecible y visualmente integrada al producto.

### Usos habituales

- Cuando se necesita que la persona usuaria ingrese un número de una cifra.
- Para flujos donde se quiere restringir la entrada a dígitos.
- Cuando el contexto requiere reemplazar el teclado nativo del dispositivo para ofrecer una experiencia más controlada.

### Cuándo elegir otra opción

- Si necesitás que la persona ingrese texto alfanumérico, usá [Text Field](#).
- Para entrada de números dentro de un rango definido mediante incremento o reducción usá [Input stepper](#) (también permite ingreso manual).

---

## Anatomía

El Num pad está definido esencialmente por una grilla de teclas numéricas. Las columnas se organizan dependiendo del espacio disponible dentro del contenedor, con un mínimo de 3 columnas.

1. **Button number:** tecla individual que representa un dígito del 1 al 9. Al accionarse, envía el valor correspondiente al input asociado. Tiene estados Idle y Pressed.

---

## Variantes

El Num pad tiene dos variantes según el dispositivo. No se combinan entre sí: cada variante es exclusiva de su plataforma.

### Desktop

Para pantallas grandes. Padding horizontal `80px`, padding superior `48px`, gap entre celdas `24px`. Ancho del contenedor entre `640px` y `1280px`. Las celdas tienen mayor espaciado y el componente ocupa más espacio vertical, adecuado para operaciones desde estaciones de trabajo fijas.

### Handheld

Para dispositivos de mano. Padding horizontal `24px`, padding superior `24px`, gap entre celdas `12px`. Ancho del contenedor entre `320px` y `640px`. Las celdas son más compactas, optimizadas para interacción táctil con una sola mano.

---

## Propiedades

### Visibilidad de botones

Cada botón del 2 al 9 puede mostrarse u ocultarse de forma independiente mediante su prop correspondiente. El botón "1" siempre está visible y no tiene prop asociada.

| Nombre | Detalle |
| :---- | :---- |
| `prop2` | Controla la visibilidad del botón "2". Default `true` |
| `prop3` | Controla la visibilidad del botón "3". Default `true` |
| `prop4` | Controla la visibilidad del botón "4". Default `true` |
| `prop5` | Controla la visibilidad del botón "5". Default `true` |
| `prop6` | Controla la visibilidad del botón "6". Default `true` |
| `prop7` | Controla la visibilidad del botón "7". Default `true` |
| `prop8` | Controla la visibilidad del botón "8". Default `true` |
| `prop9` | Controla la visibilidad del botón "9". Default `true` |

---

## Estados

| Estado | Diferencia visual | Combinable con | Excluye a |
| :---- | :---- | :---- | :---- |
| Idle | Estado predeterminado sin interacción. Fondo `#e0e9ff`, texto `#4850e5` | — | Pressed |
| Pressed | Activo mientras la persona hace click o tap. Refuerza que la acción fue reconocida. Fondo `#ccdaff`, texto `#353ac5` | — | Idle |

---

## Comportamiento

### Adaptación a dispositivo

- **Desktop:** ancho del contenedor entre `640px` y `1280px`. Padding horizontal `80px` (`Device/spacing/padding`), padding superior `48px` (`Num pad/spacing/padding-top`), gap entre celdas `24px`.
- **Handheld:** ancho del contenedor entre `320px` y `640px`. Padding horizontal `24px`, padding superior `24px`, gap entre celdas `12px`.

### Distribución de celdas

Las celdas se distribuyen en una cuadrícula flexible (`flex-wrap`), adaptándose al ancho disponible del contenedor. Cada celda tiene ancho mínimo `128px`, ancho máximo `168px` y altura fija `128px`.

### Entrada de datos

Cada tecla numérica envía su dígito correspondiente al input asociado externamente. El Num pad no gestiona ni almacena el valor ingresado: es responsabilidad del componente padre o del campo de entrada conectado manejar el estado del input.

### Borrado

La tecla Backspace elimina el último carácter ingresado. Si el input está vacío, la acción no tiene efecto.

### Relación con el input

El Num pad no incluye un campo de visualización propio. Siempre se compone junto a un input o display externo que muestre el valor que se está construyendo. El Num pad es el mecanismo de entrada; el campo de input es la representación del valor.

### Áreas activas

Cada tecla tiene su propia área de toque/click independiente. No existe un área activa global para el componente completo.

### Tamaño y responsividad

El componente no es fluido: su tamaño está determinado por la variante seleccionada (Desktop o Handheld). Corresponde al equipo de producto seleccionar la variante correcta según el breakpoint o el tipo de dispositivo donde se renderiza.

---

## Ejemplos

### Selección de cantidad en drawer

El Num pad se usa dentro de un drawer para que la persona usuaria ingrese una cantidad numérica. En este caso, el componente muestra solo los botones del 1 al 6 — `prop7`, `prop8` y `prop9` en `false` — adaptando las opciones disponibles al rango válido de la operación. El título del drawer orienta a la persona usuaria sobre el dato que debe ingresar.

![][example-units]

---

## Recomendaciones

![][rec-do-1]

> [!DO]
> Usar sólo la cantidad de números necesarios. En caso de tener un máximo, se pueden desactivar los sobrantes.

![][rec-dont-1]

> [!DONT]
> No usar botones de más ni modificarlos.

---

## Componentes relacionados

- Button
- Drawer
- Input stepper
- Text Field

---

## Especificaciones técnicas

| Elemento en Figma | Nombre en código | Tipo | Token resuelto | Notas |
| :---- | :---- | :---- | :---- | :---- |
| Cell height | height | dimension | `Num pad/size/cell-height` → `128px` | Altura fija de cada celda |
| Cell min-width | min-width | dimension | `Num pad/size/cell-min-width` → `128px` | — |
| Cell max-width | max-width | dimension | `Num pad/size/cell-max-width` → `168px` | — |
| Gap entre celdas | gap | dimension | `Num pad/spacing/gap-between-cells` → `24px` | Solo Desktop |
| Padding superior | padding-top | dimension | `Num pad/spacing/padding-top` → `48px` | Solo Desktop |
| Contenedor min-width | min-width | dimension | `Num pad/size/min-width` → `640px` | Solo Desktop |
| Contenedor max-width | max-width | dimension | `Num pad/size/max-width` → `1280px` | Solo Desktop |
| Padding horizontal | padding | dimension | `Device/spacing/padding` → `80px` | Solo Desktop |
| Border radius | border-radius | dimension | `border/radius/m` → `16px` | — |
| Background / Idle | background-color | color | `color/interactive/fill/quiet/default` → `#e0e9ff` | — |
| Texto / Idle | color | color | `color/interactive/text/default` → `#4850e5` | — |
| Background / Pressed | background-color | color | `color/interactive/fill/quiet/hover` → `#ccdaff` | — |
| Texto / Pressed | color | color | `color/interactive/text/hover` → `#353ac5` | — |

---

## Accesibilidad

*Esta sección incluye solo las consideraciones esenciales de accesibilidad para la persona usuaria.*

### Roles y etiquetado

El container del Num pad expone el rol `group` con un `aria-label` que identifica el propósito del componente: `aria-label="Teclado numérico"`. Esto permite que el lector de pantalla anuncie el contexto al ingresar al componente.

Cada tecla numérica tiene el rol `button` con un `aria-label` que describe su valor: por ejemplo, `aria-label="1"`, `aria-label="2"`, etc. La tecla Backspace tiene `aria-label="Borrar último dígito"` para comunicar claramente su función más allá del ícono.

### Navegación

La navegación se realiza siguiendo un orden de lectura de izquierda a derecha y de arriba hacia abajo, tanto mediante gestos (mobile) como mediante teclado (desktop).

#### Teclado

| Tecla | Descripción |
| :---- | :---- |
| Tab | Permite alcanzar el componente y desplazar el foco entre las teclas en orden de lectura |
| Space / Enter | Acciona la tecla en foco, enviando el dígito o ejecutando el borrado según corresponda |

*Las flechas del teclado no aplican para la navegación interna del Num pad: el foco se mueve entre teclas exclusivamente con Tab.*

#### Gestos

| Gesto | Descripción |
| :---- | :---- |
| Tap | Acciona la tecla correspondiente, enviando el dígito o ejecutando el borrado |

*Los gestos de swipe no aplican a este componente.*

### Consideraciones de diseño

- Asegurarse de que la tecla Backspace tenga siempre un `aria-label` textual descriptivo. El ícono solo no es suficiente para comunicar la acción a personas que usan lector de pantalla.
- Garantizar que el contraste de las teclas en estado Idle cumple con los requisitos mínimos de WCAG AA tanto sobre fondos claros como sobre fondos de color. Si el Num pad se usa sobre fondos complejos o de alto contraste, verificar que los estados Pressed siguen siendo distinguibles.
- El Num pad no anuncia automáticamente el valor acumulado en el input asociado. Es responsabilidad del campo de entrada conectado gestionar las notificaciones `aria-live` que mantengan informadas a las personas que usan tecnologías asistivas sobre el valor en construcción.

---

[example-units]: ./assets/example-units.png
[rec-do-1]: ./assets/rec-do-1.png
[rec-dont-1]: ./assets/rec-dont-1.png
