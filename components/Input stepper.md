# Input stepper

> [!ABSTRACT]
> El Input stepper es un componente de entrada que permite ajustar un valor numérico dentro de un rango predefinido mediante botones de incremento (+) y decremento (−). Resuelve la necesidad de registrar cantidades específicas en flujos operativos de forma rápida y controlada.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=1-1594) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=5-345) |

## Descripción general

El Input stepper permite incrementar y reducir un valor numérico dentro de un rango predefinido.

Componente de entrada que permite ajustar un valor numérico dentro de un rango predefinido mediante botones de incremento (+) y decremento (−).
Opcionalmente, el valor también puede modificarse mediante introducción manual con teclado numérico. En esta modalidad, el valor se muestra en color azul y subrayado para indicar que es interactivo y puede tocarse (tap) para editarlo.

## Usos habituales / Cuándo elegir alternativas

### Usos habituales

Registrar cantidades específicas de unidades involucradas en flujos determinados de la operación (por ejemplo, productos dañados, embalajes faltantes, cajas ingresadas, totes llenos).

### Cuándo elegir otra opción

Si necesitás mostrar un valor fijo, o valores totales sobre valores parciales, recomendamos usar el Counter.
Para destaques de valores u otros datos no numéricos, usar Highlight.

## Anatomía

Estructura del componente.

**A. Input stepper**

| # | Elemento | Descripción |
|---|----------|-------------|
| 1 | Label (Opcional) | Texto descriptivo que indica qué cantidad se está ajustando |
| 2 | Value | Valor numérico actual del stepper |
| 3 | Controler | Par de botones (añadir / quitar) para incrementar o decrementar el valor |

## Variantes

### Default

Variante estándar con botones de incremento (+) y decremento (−). El valor numérico se muestra en negro.

### Editable

El valor numérico se muestra en color azul y subrayado, indicando que es interactivo. La persona usuaria puede tocarlo (tap) para editarlo directamente mediante el teclado numérico.

*`(inferido — requiere validación)`*

## Propiedades

### Props del componente

| Propiedad | Tipo | Valor por defecto | Descripción |
|-----------|------|-------------------|-------------|
| `label` | `boolean` | `true` | Muestra u oculta el label |
| `labelText` | `string` | `"Label"` | Texto del label |
| `state` | `"Default" \| "Min Limit" \| "Max Limit" \| "Disabled"` | `"Default"` | Estado del componente |

### Tokens de diseño

| Token | Valor | Descripción |
|-------|-------|-------------|
| `Input stepper/structure/size/width` | `600px` | Ancho total del componente |
| `Input stepper/structure/size/height` | `272px` | Alto total del componente |
| `Input stepper/structure/button/width` | `160px` | Ancho de los botones de control |
| `Input stepper/structure/button/height` | `120px` | Alto de los botones de control |
| `Input stepper/structure/button/border-radius` | `24px` | Radio de borde de los botones |
| `Input stepper/structure/spacing/gap` | `40px` | Separación entre label y control |
| `color/interactive/fill/quiet/default` | `#e0e9ff` | Fondo de botones en estado activo |
| `color/fill/disabled` | `#dedfed` | Fondo de botones en estado deshabilitado o en límite |
| `color/text/primary` | `#1c1c2b` | Color del valor numérico y label activo |
| `color/text/disabled` | `#9ca0bf` | Color del label en estado Disabled |
| `color/interactive/icon/default-accent` | `#4850e5` | Color de los iconos en estado activo |
| `color/icon/disabled-on-fill` | `#737396` | Color de los iconos en estado deshabilitado |

## Estados

El componente Input stepper tiene 4 comportamientos.

| Estado | Descripción | Token de color (botón activo) |
|--------|-------------|-------------------------------|
| **Idle / Default** | Estado inicial, sin interacción activa del usuario. Ambos botones activos. | `color/interactive/fill/quiet/default` (#e0e9ff) |
| **Min. Limit** | Restringe la acción si el valor es menor al mínimo definido. El botón de disminuir queda deshabilitado. | Botón remove: `color/fill/disabled` (#dedfed) |
| **Max. Limit** | Restringe la acción si el valor supera al máximo definido. El botón de aumentar queda deshabilitado. | Botón add: `color/fill/disabled` (#dedfed) |
| **Disabled** | Elemento inactivo, sin posibilidad de interacción. Ambos botones y el label deshabilitados. | `color/fill/disabled` (#dedfed) en ambos botones |

## Ejemplos

### Picking handheld

El Input stepper aplicado en un flujo de picking en dispositivo handheld. La persona usuaria ve la pregunta "¿Cuántas unidades guardaste?" y ajusta el valor numérico con los botones de incremento y decremento. En este caso el valor es 4 y el botón (+) aparece deshabilitado, indicando que se alcanzó el máximo permitido (estado Max Limit). La barra inferior solicita escanear el tote para confirmar la acción.

## Comportamiento

El componente tiene tamaños preestablecidos para Desktop y Handheld.

| Plataforma | Ancho | Alto |
|------------|-------|------|
| Desktop | 600px | 240px |
| Handheld | 312px | 132px |

## Recomendaciones

Como aplicar el componente haciendo el mejor uso.

| | Guía | Descripción |
|--|------|-------------|
| ✅ Do | Usar con cantidades ajustables | Usar el Input stepper cuando el usuario necesite ajustar cantidades fácilmente. |
| ❌ Don't | No usar para valores grandes | No usar el Input stepper cuando se requieran valores grandes (mayores a 99) o imprecisos. |
| ✅ Do | Incluir siempre un label | Usar el label para dar contexto. |
| ❌ Don't | No sobrecargar el label | No sobrecargar la label de información. |

## Componentes relacionados

- Button icon

## Accesibilidad

### Roles y etiquetado

| Atributo | Descripción |
|----------|-------------|
| **Role** | El componente debe tener `role="group"` o estar contenido en un `<fieldset>` para agrupar semánticamente los controles. Los botones de incremento y decremento deben usar `<button>`. |
| **aria-label** | Cada botón debe incluir `aria-label` descriptivo, por ejemplo: `aria-label="Aumentar cantidad"` y `aria-label="Disminuir cantidad"`. |
| **aria-disabled** | Cuando un botón está en estado Min Limit, Max Limit o Disabled, se debe añadir `aria-disabled="true"`. |
| **aria-live** | El valor numérico debe estar en una región `aria-live="polite"` para que los lectores de pantalla anuncien los cambios. |
| **Contraste** | El estado Disabled utiliza `color/text/disabled` (#9ca0bf) sobre fondo blanco. Verificar contraste mínimo 4.5:1 para texto (WCAG 2.1 AA). |
| **WCAG** | 1.4.3 Contraste mínimo (AA), 2.1.1 Teclado, 4.1.2 Nombre, rol, valor. |

### Navegación por teclado

| Tecla | Descripción |
|-------|-------------|
| `Tab` | Mueve el foco entre los botones de control y otros elementos de la página. |
| `Enter` / `Space` | Activa el botón enfocado (disminuir o aumentar). |

### Gestos

| Gesto | Descripción |
|-------|-------------|
| Tap | Activa el botón de disminuir o aumentar. |
| Tap sobre el valor | En la variante Editable, abre el teclado numérico para ingresar el valor manualmente. |

### Consideraciones de diseño

- **Estados deshabilitados:** cuando un botón está en estado Min Limit, Max Limit o Disabled, debe incluir `aria-disabled="true"`. El botón no debe recibir foco ni responder a eventos de teclado.
- **Foco visible:** el indicador de foco debe ser visible en todo momento en ambos botones (WCAG 2.1 AA — criterio 2.4.7).
- **Variante Editable:** el valor en azul y subrayado debe comunicar su interactividad también para personas usuarias que no perciben el color. Considerar un ícono o etiqueta complementaria.
- **Rango de valores:** el componente no es adecuado para valores mayores a 99. Asegurarse de que el rango predefinido sea claro y esté reflejado en los estados Min Limit y Max Limit.
