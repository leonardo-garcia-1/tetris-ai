
# **Textfield**

> [!ABSTRACT]
> El Textfield es el componente de entrada de texto del sistema que permite al usuario ingresar información libre en una línea o en un área de texto multilinea. Resuelve la necesidad de capturar texto libre con soporte para estados de validación, error, carga y limpieza.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=6888-131) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=1047-2513) |

| | |
|---|---|
| **Owner** | Tetris |
| **Status** | Stable |
| **Última revisión** | Marzo 2026 |

El Textfield es el componente de entrada de texto del sistema. Permite al usuario ingresar información libre en una línea o en un área de texto multilinea, con soporte para estados de validación, error, carga y limpieza.

---

## Descripción general

El Textfield agrupa el campo de entrada, su etiqueta, texto de ayuda y estados visuales en un único componente. Está disponible en dos tipos: **Single line** para entradas cortas y **Text area** para contenido extenso. El componente cubre todos los estados del ciclo de vida de un campo de formulario: desde el reposo hasta la validación o el error.

---

## Usos habituales

- Para capturar texto libre del usuario: nombres, cantidades, descripciones, búsquedas.
- En formularios de operación donde se necesita validación visual inmediata (error, loading, validated).
- Cuando el contenido a ingresar es extenso y requiere múltiples líneas (Text area).

---

## Cuándo elegir alternativas

- Usar `Num pad` cuando la entrada es exclusivamente numérica y se necesita un teclado dedicado.
- Usar `Dropdown` cuando las opciones son predefinidas y el usuario debe elegir entre ellas.
- Usar `Input stepper` cuando el valor numérico se incrementa o decrementa en pasos fijos.

---

## Anatomía

### Single line

1. **Label** _(opcional)_: etiqueta descriptiva del campo. Se oculta en estado Disabled con color deshabilitado.
2. **Container**: contenedor con borde redondeado. El grosor y color del borde varía según el estado.
3. **Placeholder / Input text**: texto de guía cuando el campo está vacío; texto ingresado cuando tiene contenido.
4. **Suffix** _(opcional)_: texto fijo al final del campo (ej. `cm`, `kg`). Visible en estados Idle, Pressed y Active.
5. **Icono de estado** _(según estado)_: spinner en Loading, check en Validated, botón X en Clear.
6. **Helper text** _(opcional)_: texto auxiliar debajo del campo. En Error incluye ícono de advertencia y texto en rojo.

### Text area

1. **Label** _(opcional)_: igual que Single line.
2. **Container**: contenedor de mayor altura, mínimo 192px.
3. **Placeholder / Input text**: texto multilinea.
4. **Scroll bar**: barra de desplazamiento interna cuando el contenido supera la altura del container.
5. **Helper text** _(opcional)_: igual que Single line.
6. **Counter** _(opcional)_: contador de caracteres (ej. `0/100`) alineado a la derecha del helper text.

---

## Variantes

### Single line
Campo de una sola línea. Altura fija de `96px`. Incluye estados exclusivos: Clear, Loading y Validated.

### Text area
Área de texto multilinea. Altura mínima `192px`. Incluye contador de caracteres y scroll bar interno. No tiene estados Clear, Loading ni Validated.

---

## Propiedades

| Propiedad | Tipo | Default | Descripción |
|---|---|---|---|
| `type` | `"Single line"` / `"Text area"` | `"Single line"` | Define si el campo es de una línea o multilinea. |
| `state` | ver tabla de estados | `"Idle"` | Estado visual del componente. |
| `showLabel` | `boolean` | `true` | Muestra u oculta la etiqueta superior. |
| `labelText` | `string` | `"Label"` | Texto de la etiqueta. |
| `helperText` | `boolean` | `true` | Muestra u oculta el texto de ayuda inferior. |
| `suffix` | `boolean` | `false` | Muestra texto fijo al final del campo (ej. `cm`). Solo Single line. |
| `counter` | `boolean` | `true` | Muestra el contador de caracteres. Solo Text area. |
| `clear` | `boolean` | `false` | Habilita el botón de limpieza en estado Clear. Solo Single line. |

### Design tokens del componente

| Token | Valor resuelto | Descripción |
|---|---|---|
| `border/radius/m` | `16px` | Radio del container |
| `border/width/m` | `2px` | Borde en Idle, Filled, Error, Loading, Validated |
| `border/width/l` | `3px` | Borde en Active, Pressed, Clear |
| `color/interactive/border/default` | `#bdbfd6` | Borde en Idle y Filled |
| `color/interactive/border/active` | `#4850e5` | Borde en Active |
| `color/selected/border/hover` | `#353ac5` | Borde en Pressed y Clear |
| `color/feedback/border/negative-loud` | `#da0b38` | Borde en Error |
| `color/fill/disabled` | `#dedfed` | Fondo del container en Disabled |
| `color/text/primary` | `#1c1c2b` | Color del texto ingresado |
| `color/text/placeholder` | `#737396` | Color del placeholder |
| `color/text/disabled` | `#9ca0bf` | Color del texto en Disabled |
| `color/text/secondary` | `#5a5a7c` | Color del helper text en Idle |
| `color/feedback/text/negative-loud` | `#7e0620` | Color del helper text en Error |
| `color/icon/disabled` | `#bdbfd6` | Color de la scroll bar en Text area |
| `spacing/gap/s` | `16px` | Gap entre elementos del componente |
| `spacing/padding/xs` | `24px` | Padding horizontal del container |
| `spacing/padding/3xs` | `16px` | Padding derecho en estado Clear |
| `spacing/gap/xs` | `8px` | Gap entre ícono y texto en helper de Error |
| `typograph/label/font-size/medium` | `28px` | Tamaño de fuente del label |
| `typograph/label/font-size/large` | `32px` | Tamaño de fuente del input text |
| `typograph/label/font-size/small` | `24px` | Tamaño de fuente del helper text y counter |

---

## Estados

| Estado | Disponible en | Detalle |
|---|---|---|
| **Idle** | Single line, Text area | Estado por defecto. Borde gris `2px`. Muestra placeholder. |
| **Active** | Single line, Text area | Campo enfocado, usuario escribiendo. Borde azul `3px`. Cursor de tipeo visible. |
| **Pressed** | Single line, Text area | Presionado antes del foco. Borde azul oscuro `3px`. |
| **Filled** | Single line, Text area | Con contenido ingresado, sin foco. Borde gris `2px`. |
| **Clear** | Single line | Con contenido y botón X activo. Borde azul oscuro `3px`. |
| **Loading** | Single line | Procesando validación. Borde gris `2px`, spinner a la derecha. |
| **Validated** | Single line | Validación exitosa. Borde gris `2px`, ícono de check a la derecha. |
| **Error** | Single line, Text area | Error de validación. Borde rojo `2px`. Helper text en rojo con ícono. |
| **Disabled** | Single line, Text area | No disponible. Fondo gris `#dedfed`, sin borde, textos en gris claro. |

---

## Comportamiento

- **Single line**: altura fija `96px`. El texto se trunca con ellipsis si supera el ancho del campo.
- **Text area**: altura mínima `192px`. El contenido crece verticalmente; la scroll bar aparece cuando supera el área visible.
- **Clear**: el botón X aparece solo cuando `state = "Clear"` y `clear = true`. Al activarse limpia el contenido del campo.
- **Loading**: el spinner ocupa el espacio del ícono de estado. El campo no es editable en este estado.
- **Validated**: el check reemplaza al spinner una vez completada la validación exitosa.
- **Error**: el helper text cambia a `color/feedback/text/negative-loud` y agrega ícono de advertencia a la izquierda.
- **Suffix**: texto estático (`cm`, `kg`, etc.) alineado a la derecha del input. Visible en Idle, Pressed y Active.
- **Counter** (Text area): muestra `0/100` alineado a la derecha del helper text. Se actualiza en tiempo real.

---

## Ejemplos

> Los valores de ejemplo son ilustrativos. En producción el contenido es ingresado por el operario o cargado por el sistema.

### Ingreso de cantidad manual

![][example-quantity]

En un flujo de picking donde el operario debe ingresar una cantidad diferente a la sugerida, el Textfield Single line aparece dentro de un Drawer con label "Cantidad" y helper text indicando el rango válido. Al escribir, el campo pasa al estado Active; al confirmar, al estado Validated si el valor es correcto, o Error si está fuera del rango.

### Reporte de problema con descripción

![][example-report]

En el formulario de reporte de problema, el Textfield Text area permite al operario escribir una descripción libre del inconveniente. El contador de caracteres (`0/280`) se actualiza en tiempo real. El helper text indica el límite máximo.

---

## Recomendaciones

### ✅ Do
- Usar `showLabel` siempre que el contexto no sea obvio. El label reduce la carga cognitiva.
- Usar el helper text para indicar el formato esperado (ej. "Máximo 100 caracteres").
- Usar el estado Error con un mensaje claro y accionable.
- Usar Text area solo cuando el contenido esperado sea genuinamente largo (más de una línea).

### ❌ Don't
- No usar Textfield para entradas numéricas con rango acotado — preferir `Input stepper` o `Num pad`.
- No ocultar el label en campos dentro de formularios complejos.
- No usar el estado Loading de forma indefinida sin feedback adicional.
- No usar suffix para texto que cambia dinámicamente — el suffix es siempre estático.

---

## Componentes relacionados

- **Num pad**: alternativa para entradas exclusivamente numéricas.
- **Input stepper**: para valores numéricos incrementales.
- **Dropdown**: para selección entre opciones predefinidas.

---

## Accesibilidad

### Roles y etiquetado

Implementar con `<input type="text">` (Single line) o `<textarea>` (Text area). El label debe asociarse mediante `for` / `id` o `aria-label`.

En estado Error, el helper text debe referenciarse con `aria-describedby` para que los lectores de pantalla lo anuncien junto al campo.

### Navegación

Orden de lectura: label → campo → helper text / counter.

### Interacciones con teclado

| Tecla | Función |
|---|---|
| Tab | Enfocar el campo |
| Escape | Cancelar edición (según contexto del formulario) |
| Enter | Confirmar en Single line (según contexto del formulario) |

### Consideraciones de diseño

- El contraste del placeholder (`#737396` sobre blanco) debe verificarse en contexto — puede estar por debajo del umbral WCAG AA para texto normal.
- El texto de error (`#7e0620`) sobre fondo blanco cumple contraste WCAG AA.
- En estado Disabled, asegurar `disabled` o `aria-disabled="true"` para que el campo no reciba foco.
