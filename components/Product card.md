# Product card

> [!ABSTRACT]
> El Product card es un patrón que muestra la información de un elemento específico uniendo su imagen con su información referente: código identificador, descripción y badges informativos. Resuelve la necesidad de identificar visualmente un producto escaneado o seleccionado de forma compacta en pantallas de operación.

| | |
|---|---|
| **Owner** | Tetris |
| **Status** | Stable |
| **Última revisión** | Noviembre 2025 |

El pattern Product card muestra la información de un elemento específico, uniendo su imagen con su información referente.

---

## Descripción general

El Product card es un patrón que presenta la información de un ítem de forma visual y compacta: imagen del producto, código identificador, descripción y badges informativos. Está disponible en dos versiones de dispositivo (Desktop y Handheld) y soporta estados de contenido vacío y placeholder para cubrir los flujos de carga o escaneo previo.

---

## Usos habituales

- Cuando se necesita identificar un producto escaneado o seleccionado, mostrando su código, descripción e imagen de forma unificada.
- Para presentar los datos principales de un ítem (código identificador, descripción y etiquetas de clasificación) en pantallas de operación o gestión de inventario.
- Como punto de confirmación visual antes de ejecutar una acción sobre un producto específico.

---

## Cuándo elegir alternativas

- Usar `List` cuando necesitás mostrar múltiples productos al mismo tiempo. El Product card está pensado para destacar un único ítem a la vez.

---

## Anatomía

1. **Image**: Área de imagen del producto. Ocupa la mayor parte del card.
2. **Border** _(opcional)_: Contorno del contenedor de imagen. Se puede ocultar.
3. **Badge** _(opcional)_: Etiqueta superpuesta sobre la imagen, con fondo semitransparente. Indica información contextual del producto.
4. **Code**: Texto de código identificador del producto. Tipografía Semibold de alta jerarquía.
5. **Product description**: Texto descriptivo del producto. Tipografía Regular, color secundario.
6. **Zoom icon** _(opcional)_: Ícono de expansión ubicado sobre la imagen. Permite ampliar la imagen o abrir un carousel.

---

## Variantes

### Desktop
Card de mayor tamaño destinado a pantallas grandes. El código del producto se muestra en tipografía de encabezado, la descripción ocupa el ancho completo y los badges se disponen en fila.

### Handheld
Card compacto para dispositivos de mano. Código y descripción en tipografías más pequeñas, alineados al centro. Badge superpuesto sobre la imagen de menor altura.

---

## Propiedades

| Propiedad | Tipo | Default | Descripción |
|-----------|------|---------|-------------|
| `device` | `"Desktop"` / `"Handheld"` | `"Desktop"` | Variante de dispositivo. Controla tamaños, tipografías y espaciados. |
| `product` | `"Empty"` / `"Placeholder"` / `string` | `"Empty"` | Estado de contenido del card. `Empty` muestra imagen vacía; `Placeholder` muestra ícono de espera previo al escaneo. |
| `productDescription` | `string` | `"Product description"` | Texto de descripción del producto. Slot de contenido libre. |
| `showBorder` | `boolean` | `true` | Muestra u oculta el borde del contenedor de imagen. |
| `badgeProduct` | `boolean` | `true` | Muestra u oculta el badge superpuesto sobre la imagen (Desktop). |
| `badgeHandheld` | `boolean` | `true` | Muestra u oculta el badge superpuesto sobre la imagen (Handheld). |
| `buttonIcon` | `boolean` | `false` | Muestra u oculta el ícono de zoom/expansión sobre la imagen. Disponible en Handheld. |
| `showBadge` | `boolean` | `true` | Muestra u oculta el bloque de badge pills en la sección de texto (Desktop). |
| `badge2` | `boolean` | `true` | Muestra u oculta el segundo badge pill en la fila de badges (Desktop). |

### Design tokens del componente

| Token | Valor resuelto | Descripción |
|-------|---------------|-------------|
| `Product card/spacing/between-image` | `40px` | Espacio entre el contenedor de imagen y el bloque de texto |
| `Product card/spacing/between-text` | `24px` | Espacio entre elementos de texto |
| `Product card/spacing/between-badges` | `20px` | Espacio entre badge pills |
| `Product card/text/font-size` | `48px` | Tamaño de fuente del código de producto |
| `Product card/text/line-height` | `56px` | Interlineado del código de producto |
| `border/radius/m` | `16px` | Radio de borde del card y del contenedor de imagen |
| `border/radius/xs` | `8px` | Radio de borde de la imagen interior |
| `border/radius/s` | `12px` | Radio de borde del badge superpuesto |
| `border/width/s` | `1px` | Grosor del borde del contenedor de imagen |
| `color/surface/primary` | `#ffffff` | Fondo del card |
| `color/interactive/border/default` | `#bdbfd6` | Color del borde del contenedor de imagen |
| `color/background/overlay` | `rgba(47, 47, 70, 0.70)` | Fondo del badge superpuesto sobre la imagen |
| `color/text/primary` | `#1c1c2b` | Color del código de producto |
| `color/text/secondary` | `#5a5a7c` | Color de la descripción del producto |
| `color/text/inverse` | `#ffffff` | Color del texto sobre el badge de imagen |
| `Device/spacing/padding` | `80px` | Padding interno del card en Desktop |
| `spacing/padding/xs` | `24px` | Padding interno del card en Handheld |

---

## Estados

| Estado | Detalle |
|--------|---------|
| **Standard** | Card con imagen y contenido de texto cargados. Muestra todos los elementos activos. |
| **Empty** | Card sin contenido de producto. La imagen queda vacía, el texto muestra los placeholders por defecto. |
| **Placeholder** | Estado de espera previo al escaneo o carga del producto. Muestra un ícono central y un mensaje indicativo en el área de imagen. |

---

## Comportamiento

- **Desktop**: ancho `598px`, alto `776px`, padding `80px` (`Device/spacing/padding`). Código en tipografía grande (`48px`), descripción a ancho completo, badges en fila horizontal.
- **Handheld**: ancho entre `360px` y `640px`, alto `470px`, padding `24px`. Código y descripción centrados, tipografías más compactas (`32px` código, `20px` descripción).
- El bloque de imagen (`Img container`) ocupa la parte superior y crece flexible hasta completar el espacio disponible.
- El badge superpuesto sobre la imagen (`Badge product`) usa `backdrop-blur` y fondo semitransparente, posicionado en la parte inferior del contenedor de imagen.
- El ícono de zoom (`Button Icon`) se posiciona en la esquina superior derecha del contenedor de imagen. Fue añadido en Handheld para cubrir los casos de ampliación o apertura de carousel.
- La variante Placeholder fue incorporada para cubrir el flujo previo al escaneo del producto.
- **Carga de imagen**: si la imagen del producto no está disponible, se recomienda usar el componente Skeleton (documentado por separado) para cubrir el estado de carga.

---

## Ejemplos

> Los productos que aparecen en los ejemplos son ilustrativos. En producción, los datos (imagen, código y descripción) son levantados dinámicamente por el sistema según el ítem escaneado o seleccionado.

### Confirmación de producto en Desktop

![][example-desktop]

En una pantalla de operación de almacén en Desktop, el Product card muestra el producto escaneado antes de ejecutar una acción sobre él (por ejemplo, confirmar recepción o asignar a un tote). El card ocupa una columna lateral o el centro de la pantalla. La imagen del producto es grande y clara, el código identificador aparece en tipografía de encabezado y los badges indican atributos de manipulación como "Frágil" o "Líquido".

### Identificación de producto en Handheld

![][example-handheld]

En un dispositivo de mano durante un flujo de picking o escaneo, el Product card aparece en versión compacta. El operario escanea el ítem y el card confirma visualmente que el producto es el correcto antes de continuar. Código y descripción aparecen centrados bajo la imagen. El badge superpuesto puede indicar una categoría o cantidad.

### Estado Placeholder previo al escaneo

![][example-placeholder]

Antes de que el operario escanee un producto, el card muestra el estado Placeholder: un ícono central sobre el área de imagen y un mensaje indicativo. Esto comunica que el sistema está en espera y listo para recibir el escaneo. Una vez escaneado, la transición al estado Standard ocurre automáticamente.

---

## Recomendaciones

### ✅ Do
- Usar imágenes con buena resolución, fondo limpio y blanco.
- Usar la tipografía preestablecida para el código. Asegurarse de que el código entre en una sola línea.
- Usar etiquetas sólo cuando corresponda, respetando las clasificaciones existentes.
- Usar mayúsculas dentro del componente Badge para las etiquetas.

### ❌ Don't
- No usar imágenes al corte, complejas o con fondo diferente a blanco.
- No modificar la variable tipográfica del código.
- No usar etiquetas si no están relacionadas con el contenido, ni sumar categorías aleatorias.
- Evitar usar minúsculas en el componente Badge para las etiquetas.

---

## Componentes relacionados _(opcional)_

- **Badge pill**: usado internamente para mostrar etiquetas de clasificación del producto en la sección de texto (Desktop) y como badge superpuesto sobre la imagen.
- **Skeleton**: recomendado para cubrir el estado de carga de la imagen del producto.
- **List**: alternativa cuando se necesita mostrar múltiples productos simultáneamente.

---

## Accesibilidad

### Roles y etiquetado

El campo de código del producto se implementa con rol de encabezado **`H1`** y un `aria-label` con el patrón:

```
"Código {EAN} del producto {name}"
```

Esto permite a los lectores de pantalla identificar el card y navegar entre cards mediante gestos de encabezado.

La imagen del producto debe marcarse como decorativa aplicando el patrón **Ignore Area** del sistema (`aria-hidden="true"`), ya que no aporta información adicional a la experiencia del lector de pantalla.

### Navegación

Orden de lectura de izquierda a derecha, de arriba hacia abajo: imagen → código → descripción → badges.

### Interacciones con teclado

| Tecla | Función |
|-------|---------|
| Tab | Enfocar el card o los elementos interactivos internos |
| Enter / Space | Activar el ícono de zoom si está visible |

### Gestos

| Gesto | Función |
|-------|---------|
| Tap | Seleccionar el card |
| Tap en zoom icon | Expandir imagen o abrir carousel |

### Consideraciones de diseño

- El componente cumple con los criterios de contraste mínimo de **WCAG 2.2** en niveles **NORMAL AA** y **GRANDE AA**.
- El texto sobre el badge de imagen (`color/text/inverse` `#ffffff`) sobre fondo `rgba(47,47,70,0.70)` debe verificarse en contexto real para garantizar contraste suficiente.
- El área de imagen debe incluir un `alt` descriptivo del contenido visual cuando la imagen aporte información relevante al usuario.

[example-desktop]: ./assets/product-card-example-desktop.png
[example-handheld]: ./assets/product-card-example-handheld.png
[example-placeholder]: ./assets/product-card-example-placeholder.png
