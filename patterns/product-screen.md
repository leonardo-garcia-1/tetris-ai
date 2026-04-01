
# **Product screen**

| | |
|---|---|
| **Owner** | Tetris |
| **Status** | WIP |
| **Última revisión** | Marzo 2026 |
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=23847-1018) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=1297-4673) |

> [!ABSTRACT]
> El Product screen es un preset de pantalla completa para Handheld que presenta la información de un producto junto a la indicación de cantidad. Combina imagen, código, descripción y un contador para guiar al rep durante operaciones de picking, stowing o verificación de producto.

---

## Descripción general

El Product screen une tres componentes constitutivos — Header, Product card y Counter — en una pantalla lista para usar. El Product card ocupa la mayor parte del área visible: muestra la imagen del producto con un badge superpuesto opcional, el código y la descripción. El Counter en la parte inferior indica la cantidad asociada a la operación con un número de gran tamaño para lectura rápida.

Es un preset de Handheld: no está diseñado para Desktop.

---

## Usos habituales

- Mostrar el producto que el rep debe recoger o depositar, con la cantidad a manipular.
- Confirmar visualmente la identidad del producto antes de escanear o tomar una unidad.
- Presentar el código y descripción del producto junto al contador de unidades en un flujo de picking o verificación.

---

## Cuándo elegir alternativas

- Usar `Container screen` cuando el foco de la pantalla es la ubicación física (posición, tote, slot map) y no el producto en sí.
- Usar `Action screen` cuando se requiere presentar una decisión binaria (dos botones) con contenido visual flexible.
- Usar `Feedback screen` cuando el objetivo es comunicar el resultado de una operación ya completada.

---

## Anatomía

1. **Header**: barra superior con el texto de la tarea principal (`Main task text`) y un botón de ícono con el menú de hamburguesa en la esquina derecha. Fondo `color/surface/primary`.
2. **Product card**: zona flexible que ocupa todo el espacio disponible entre el header y el counter. Contiene:
   - **Imagen del producto**: área con borde y padding interior. La imagen escala con `object-contain`.
   - **Badge** _(opcional)_: etiqueta superpuesta sobre la imagen, pegada al borde inferior del contenedor. Fondo con blur y overlay oscuro semitransparente.
   - **Product code**: código del producto centrado, tipografía grande con letter-spacing positivo para facilitar lectura.
   - **Product description**: descripción breve centrada debajo del código.
3. **Counter**: zona fija al pie. Fondo `color/surface/secondary`. Muestra la cantidad como número de `128px`.

---

## Variantes

### Con badge
El badge se superpone sobre la imagen del producto, en la esquina inferior. Comunica una etiqueta adicional (ej. categoría, estado, indicador de picking). El fondo lleva blur y overlay para asegurar legibilidad sobre cualquier imagen.

### Sin badge
La imagen del producto se muestra sin etiqueta superpuesta. Para flujos donde el código y la descripción son suficientes para identificar el producto.

---

## Propiedades

| Propiedad | Tipo | Default | Descripción |
|---|---|---|---|
| `showBadge` | `boolean` | `true` | Muestra u oculta el badge superpuesto sobre la imagen. |
| `badgeText` | `string` | `"Label"` | Texto del badge. |
| `mainTaskText` | `string` | `"Main task text"` | Texto de la tarea en el header. |
| `productCode` | `string` | `"Product code"` | Código del producto (ej. `ML AELY12345`). |
| `productDescription` | `string` | `"Product description"` | Descripción del producto. |
| `counterValue` | `number` | `1` | Cantidad a mostrar en el counter. |

### Design tokens

| Token | Valor resuelto | Descripción |
|---|---|---|
| `device/breakpoints/width` | `360px` | Ancho base Handheld |
| `device/breakpoints/height` | `640px` | Alto base Handheld |
| `color/background/primary` | `#ffffff` | Fondo general de la pantalla |
| `color/surface/primary` | `#ffffff` | Fondo del header y product card |
| `color/surface/secondary` | `#ededf7` | Fondo del counter |
| `color/text/primary` | `#1c1c2b` | Product code y número del counter |
| `color/text/secondary` | `#5a5a7c` | Product description |
| `color/text/inverse` | `#ffffff` | Texto del badge |
| `color/background/overlay` | `rgba(47,47,70,0.7)` | Fondo del badge con overlay |
| `color/interactive/border/default` | `#bdbfd6` | Borde del contenedor de imagen |
| `border/radius/m` | `16px` | Radio del product card e imagen container |
| `border/radius/s` | `12px` | Radio del badge |
| `border/radius/xs` | `8px` | Radio de la imagen interior |
| `border/radius/circle` | `9999px` | Radio del botón de header |
| `border/width/s` | `1px` | Borde del contenedor de imagen |
| `device/spacing/padding` | `24px` | Padding del product card (top, horizontal) |
| `spacing/padding/xs` | `24px` | Padding horizontal del header y counter |
| `spacing/padding/2xs` | `20px` | Padding vertical del counter |
| `spacing/padding/3xs` | `16px` | Padding interior del contenedor de imagen |
| `spacing/padding/5xs` | `12px` | Padding top del header y padding del botón |
| `spacing/xs` | `32px` | Padding bottom del product card |
| `product-card/spacing/between-image` | `24px` | Gap entre imagen y bloque de texto |
| `product-card/spacing/between-text` | `16px` | Gap entre code y description |
| `typograph/body/font-size/medium` | `20px` | Header task text y product description |
| `typograph/body/line-height/medium` | `28px` | Line-height header y description |
| `typograph/heading/font-size/medium` | `32px` | Product code |
| `typograph/heading/line-height/medium` | `36px` | Line-height product code |

---

## Comportamiento

- **Dimensiones**: ancho `360px` (min `320px`, max `640px`), alto `640px` (min `530px`, max `640px`). Rango Handheld.
- **Product card**: crece con `flex: 1` para ocupar todo el espacio disponible entre header y counter.
- **Imagen**: escala con `object-contain` para mostrar el producto completo sin recorte, independientemente del aspect ratio.
- **Badge**: posición absoluta en la esquina inferior del contenedor de imagen (`bottom: 8px`, `left/right: 8px`). Ancho completo del área interior. Blur de `12px` sobre el fondo de la imagen.
- **Product code**: centrado horizontalmente con letter-spacing positivo (`0.64px`) para facilitar la lectura rápida de códigos alfanuméricos.
- **Counter**: fijo al pie. El número de `128px` es el elemento más prominente de la zona inferior — diseñado para lectura a distancia y con guantes.
- La pantalla no tiene scroll: todo el contenido debe caber en la altura disponible (`530px`–`640px`).

---

## Ejemplos

### Picking de producto líquido con badge de atributo

Variante **con badge**. El header muestra la instrucción "Toma la unidad y escanéala" con el menú de hamburguesa a la derecha. El product card ocupa la mayor parte de la pantalla: la imagen de la Coca-Cola Sem Açúcar llena el contenedor con `object-contain`, y sobre el borde inferior de la imagen aparece el badge con el texto "Líquido" sobre fondo oscuro con blur, alertando al rep sobre el tipo de manipulación requerida antes de tomar el producto. Debajo de la imagen, el código "ML H7890" en tipografía grande y la descripción "Refrigerante Coca Cola Sem Açucar Lata 350ml (12 Latas)" identifican el ítem. El counter al pie muestra "1" sobre fondo secundario — la cantidad que el rep debe tomar en este paso del flujo.

---

## Recomendaciones

### ✅ Do
- Usar imágenes de producto de alta resolución con fondo neutro para maximizar la legibilidad del product card.
- Mantener el product code en una sola línea — es el identificador primario y debe ser completamente visible.
- Usar el badge cuando hay información contextual crítica que complementa la imagen (ej. categoría, indicador de estado).
- Asegurarse de que el contador refleje exactamente la cantidad que el rep debe manipular en ese paso del flujo.

### ❌ Don't
- No usar este preset en Desktop — es exclusivo de Handheld.
- No poner texto descriptivo largo en el product description — debe ser una línea legible a golpe de vista.
- No usar el badge para información no crítica — el overlay reduce la visibilidad de la imagen.
- No usar este preset cuando el foco de la pantalla es la ubicación física — usar `Container screen`.

---

## Componentes relacionados

- **Header**: componente de encabezado con tarea principal y menú.
- **Product card**: componente de tarjeta de producto con imagen, badge, código y descripción.
- **Counter**: componente de conteo (ex Highlight) con número de gran tamaño.
- **Container screen**: preset para identificación de posición o contenedor físico.
- **Action screen**: preset para decisión binaria con contenido visual.
- **Feedback screen**: preset para comunicar el resultado de una operación.

---

## Accesibilidad

Los criterios de accesibilidad específicos se encuentran en las especificaciones de cada componente constitutivo (Header, Product card, Counter).

### Roles y etiquetado

La pantalla debe tener un `<main>` como contenedor principal. La imagen del producto debe incluir un `alt` con el nombre o código del producto. El badge debe ser legible por lector de pantalla con su texto visible o un `aria-label` equivalente.

El product code debe implementarse como un encabezado (`<h1>` o `<h2>`) para que los lectores de pantalla puedan navegar directamente a él. El contador debe tener una etiqueta accesible que indique qué representa el número (ej. `aria-label="Cantidad: 1"`).

### Navegación

Orden de lectura: header → imagen del producto → badge (si presente) → product code → product description → counter.

### Interacciones con teclado

| Tecla | Función |
|---|---|
| Tab | Navegar entre elementos interactivos (botón de menú del header) |
| Enter / Space | Activar el botón enfocado |

### Gestos

| Gesto | Función |
|---|---|
| Tap en menú (header) | Abrir menú de navegación |

### Consideraciones de diseño

- El product code (`color/text/primary` sobre blanco) cumple WCAG AA.
- El badge usa texto blanco sobre overlay oscuro con blur — el contraste puede variar según la imagen subyacente. Verificar en contexto con imágenes de baja luminosidad.
- El número del counter (`128px`) es texto de gran tamaño: cumple criterios de texto grande bajo WCAG incluso con contraste moderado.
