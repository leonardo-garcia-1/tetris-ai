
# **Feedback screen**

| | |
|---|---|
| **Owner** | Tetris |
| **Status** | WIP |
| **Última revisión** | Marzo 2026 |
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=23847-1011) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=4214-341) |

> [!ABSTRACT]
> El Feedback screen es un preset de pantalla completa que comunica el resultado de una operación al rep (operador). Presenta un ícono de feedback, un título, una descripción y un slot configurable para contenido adicional. Disponible en Desktop y Handheld.

---

## Descripción general

El Feedback screen combina una zona de feedback visual (ícono con color semántico) con un bloque de texto y un slot de contenido flexible. Su propósito es cerrar el ciclo de una tarea: confirmar que algo salió bien, advertir de un problema o comunicar un estado neutral. No requiere una acción obligatoria del rep — puede avanzar mediante escaneo (Touchless).

La pantalla se adapta a cada dispositivo: en **Desktop** el feedback icon aparece como una franja lateral izquierda, el contenido ocupa el área central y el Touchless se ubica a la derecha. En **Handheld** el ícono está en la parte superior, el contenido en el centro y el Touchless en la parte inferior.

---

## Usos habituales

- Confirmar que una operación se completó exitosamente (ej. producto escaneado correctamente).
- Comunicar un error o resultado negativo antes de reintentar o redirigir al rep.
- Presentar un estado intermedio o advertencia dentro de un flujo de tarea.
- Cerrar un paso del flujo con información contextual adicional en el slot (ej. detalle del producto, siguiente destino).

---

## Cuándo elegir alternativas

- Usar `System state` cuando el feedback no está ligado a una acción reciente sino a un estado del sistema (sin conexión, vacío, error de carga).
- Usar `Action screen` cuando el objetivo de la pantalla es presentar una decisión entre dos opciones, no confirmar un resultado.
- Usar `Status screen` cuando el rep necesita monitorear el progreso de un proceso en curso.

---

## Anatomía

### Desktop

1. **Header** _(opcional)_: barra superior oscura con texto de tarea principal y fila de información contextual (hasta 3 pares Label/Info con divisores). Fondo `color/background/inverse`.
2. **Feedback strip**: franja lateral izquierda de `256px` de ancho. Fondo semántico según el tipo de feedback. Contiene el ícono centrado.
3. **Ícono**: círculo de `128px` con el símbolo del resultado (check, cruz, alerta). Fondo semántico loud.
4. **Main content**: área central flexible. Contiene título, descripción y slot.
5. **Título**: texto principal del resultado. Tipografía `Heading/large` (88px, Semibold). Color `color/text/primary`.
6. **Descripción**: texto secundario explicativo. Tipografía `Body/large/emphasis` (32px, Medium). Color `color/text/tertiary`.
7. **Slot**: área flexible para contenido adicional personalizable. Mínimo `240px` de alto.
8. **Touchless**: columna derecha de `442px` separada por borde izquierdo. Contiene ícono de escaneo animado e instrucción de texto.
9. **Bottom navigation**: barra inferior con hasta 3 botones de acción + botón de salida (logout). Fondo `color/background/inverse`.

### Handheld

1. **Feedback strip**: franja superior de `176px` de alto, ancho completo. Fondo semántico según el tipo.
2. **Ícono**: círculo de `80px` con el símbolo del resultado. Fondo semántico loud.
3. **Título**: texto principal. Tipografía `Heading/small` (32px, Semibold). Color `color/text/primary`.
4. **Descripción**: texto secundario. Tipografía `Body/medium/default` (20px, Regular). Color `color/text/secondary`.
5. **Slot**: área flexible para contenido adicional. Máximo `208px` de alto.
6. **Touchless**: zona de acción fija al pie. Contiene ícono de escaneo + instrucción. Separada por borde superior.

---

## Variantes

### Por tipo de feedback

El color de la franja y del ícono cambia según el resultado comunicado:

| Tipo | Strip background | Icon background | Uso |
|---|---|---|---|
| **Positive** | `color/feedback/fill/positive-quiet` (`#dbf0e2`) | `color/feedback/fill/positive-loud` (`#068943`) | Operación completada con éxito |
| **Negative** | `color/feedback/fill/negative-quiet` | `color/feedback/fill/negative-loud` | Error o resultado fallido |
| **Warning** | `color/feedback/fill/warning-quiet` | `color/feedback/fill/warning-loud` | Advertencia o resultado parcial |
| **Neutral** | `color/feedback/fill/neutral-quiet` | `color/feedback/fill/neutral-loud` | Información sin carga positiva/negativa |

### Por dispositivo

| Variante | Dimensiones | Layout del feedback |
|---|---|---|
| **Desktop** | `1920×1080px` | Franja lateral izquierda (`256px`), contenido central, Touchless derecha |
| **Handheld** | `360×640px` | Franja superior (`176px`), contenido central, Touchless inferior |

---

## Propiedades

| Propiedad | Tipo | Default | Descripción |
|---|---|---|---|
| `device` | `"Desktop"` / `"Handheld"` | `"Desktop"` | Dispositivo destino. Cambia el layout completo. |
| `feedbackType` | `"Positive"` / `"Negative"` / `"Warning"` / `"Neutral"` | `"Positive"` | Determina el color semántico de la franja e ícono. |
| `header` | `boolean` | `false` | Muestra u oculta el header con información de tarea. Solo Desktop. |
| `titleText` | `string` | `"Hey! I'm a feedback title"` | Texto del título del resultado. |
| `descriptionText` | `string` | `"Description"` | Texto descriptivo del resultado. |

### Design tokens

| Token | Valor resuelto | Descripción |
|---|---|---|
| `color/background/inverse` | `#1c1c2b` | Fondo Desktop y header |
| `color/background/primary` | `#ffffff` | Fondo Handheld |
| `color/surface/primary` | `#ffffff` | Fondo del card de contenido (Desktop) |
| `color/text/primary` | `#1c1c2b` | Color del título |
| `color/text/secondary` | `#5a5a7c` | Color de descripción (Handheld) |
| `color/text/tertiary` | `#737396` | Color de descripción (Desktop) |
| `color/text/inverse` | `#ffffff` | Texto del header Desktop |
| `color/feedback/fill/positive-quiet` | `#dbf0e2` | Fondo franja Positive |
| `color/feedback/fill/positive-loud` | `#068943` | Fondo ícono Positive |
| `color/border/disabled` | `#dedfed` | Borde separador del Touchless |
| `color/interactive/fill/quiet-inverse/disabled` | `#2f2f46` | Botones de nav deshabilitados (Desktop) |
| `color/interactive/fill/quiet-inverse/default` | `#454768` | Botón exit (Desktop) |
| `border/radius/m` | `16px` | Radio del card de contenido y botones |
| `border/radius/circle` | `9999px` | Radio del ícono de feedback |
| `border/width/m` | `2px` | Ancho del borde separador Touchless |
| `spacing/padding/2xl` | `80px` | Padding del main content (Desktop) |
| `spacing/padding/m` | `40px` | Padding top container (Handheld) y header Desktop |
| `spacing/padding/xs` | `24px` | Padding horizontal Handheld y del ícono |
| `spacing/gap/xl` | `40px` | Gap vertical layout Desktop |
| `spacing/gap/l` | `32px` | Gap entre título y descripción (Desktop) |
| `spacing/gap/m` | `24px` | Gap entre título y descripción (Handheld), gap bottom nav |
| `spacing/gap/2xl` | `48px` | Gap interno del Touchless (Desktop) |
| `typograph/heading/font-size/large` | `88px` | Título Desktop |
| `typograph/heading/line-height/large` | `92px` | Line-height título Desktop |
| `typograph/heading/font-size/small` | `32px` | Título Handheld |
| `typograph/heading/line-height/small` | `36px` | Line-height título Handheld |
| `typograph/body/font-size/large` | `32px` | Descripción Desktop |
| `typograph/body/line-height/large` | `40px` | Line-height descripción Desktop |
| `typograph/body/font-size/medium` | `20px` | Descripción Handheld |
| `typograph/body/line-height/medium` | `28px` | Line-height descripción Handheld |

---

## Comportamiento

- **Dimensiones Desktop**: `1920×1080px` fijo (fullscreen). Fondo `color/background/inverse`.
- **Dimensiones Handheld**: `360×640px` (min-width `320px`, max-width `640px`).
- **Feedback strip Desktop**: ancho fijo `256px`, alto flexible (ocupa toda la altura del card de contenido).
- **Feedback strip Handheld**: ancho completo, alto fijo `176px`.
- **Slot**: área flexible que crece con `flex: 1` para ocupar el espacio disponible entre la descripción y la zona de acción. En diseño muestra un placeholder con fondo violeta translúcido — en producción se reemplaza por el componente real.
- **Touchless Desktop**: columna derecha de `442px`, separada del contenido principal por un borde izquierdo de `2px`. Contiene ícono de escaneo animado e instrucción de texto centrados verticalmente.
- **Touchless Handheld**: zona fija al pie, separada por borde superior de `2px`. Fila horizontal con ícono de escaneo e instrucción.
- **Header Desktop**: cuando `header = true`, se agrega la barra superior con nombre de tarea e información contextual. No aplica a Handheld.
- **Bottom navigation Desktop**: barra inferior con hasta 3 botones configurables + botón de salida fijo (`162px`). Los botones pueden estar deshabilitados según el contexto del flujo.
- **Avance**: el rep avanza mediante escaneo (Touchless). No hay botón de confirmación explícito en la variante base.

---

## Ejemplos

---

## Recomendaciones

### ✅ Do
- Usar el tipo de feedback correcto según el resultado: Positive para éxito, Negative para error, Warning para advertencia.
- Mantener el título en 1–2 líneas orientado al resultado concreto (ej. "Producto escaneado" en lugar de "¡Listo!").
- Usar el slot para contenido que ayude al rep a contextualizar el resultado (ej. nombre del producto, destino siguiente).
- Usar el header Desktop cuando el rep necesita ver la tarea principal para orientarse en el flujo.

### ❌ Don't
- No usar este preset para estados del sistema no relacionados con una acción reciente — usar `System state`.
- No omitir la descripción cuando el título solo no es suficiente para entender el resultado.
- No usar el Feedback screen como pantalla de inicio de tarea — es para cierre o confirmación de paso.
- No mezclar colores semánticos: el tipo de feedback debe ser consistente con el resultado real de la operación.

---

## Componentes relacionados

- **Touchless**: componente de escaneo usado como mecanismo de avance.
- **Header**: componente de encabezado con información de tarea (Desktop).
- **Bottom navigation**: barra de navegación inferior (Desktop).
- **System state**: preset alternativo para estados del sistema (no ligados a acción reciente).
- **Action screen**: preset alternativo cuando el objetivo es presentar una decisión, no un resultado.

---

## Accesibilidad

### Roles y etiquetado

La pantalla debe tener un `<main>` como contenedor principal. El título debe implementarse con `<h1>`. El ícono de feedback debe incluir un `aria-label` o texto alternativo que describa el resultado (ej. "Operación exitosa", "Error en la operación") para que los lectores de pantalla comuniquen el estado sin depender únicamente del color.

### Navegación

Orden de lectura: header (si presente) → ícono de feedback → título → descripción → contenido del slot → Touchless / instrucción de escaneo → bottom navigation (Desktop).

### Interacciones con teclado

| Tecla | Función |
|---|---|
| Tab | Navegar entre elementos interactivos (botones de nav, Touchless) |
| Enter / Space | Activar el botón o acción enfocados |

### Gestos

| Gesto | Función |
|---|---|
| Tap en Touchless | Activar escaneo para avanzar |
| Tap en botón de nav | Ejecutar acción de navegación (Desktop) |

### Consideraciones de diseño

- El color del ícono no debe ser el único indicador del tipo de feedback — el ícono simbólico (check, cruz, alerta) y el texto deben reforzar el mensaje para usuarios con daltonismo.
- El contraste del título (`color/text/primary` sobre fondo blanco) cumple WCAG AA.
- El contraste de descripción Desktop (`color/text/tertiary` #737396 sobre blanco) debe verificarse en contexto — a 32px califica como texto grande bajo WCAG.
- Los botones del Bottom navigation Desktop tienen `96px` de alto, garantizando área de toque suficiente.
