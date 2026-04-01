
# **Screen template**

| | |
|---|---|
| **Owner** | Tetris |
| **Status** | WIP |
| **Última revisión** | Marzo 2026 |
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=23847-1010) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=5-354) |

> [!ABSTRACT]
> El Screen template es el preset base de Desktop que establece la disposición de los elementos estructurales de una pantalla: header, área de contenido principal y bottom navigation. Es la base sobre la que se construyen todos los presets de Desktop.

---

## Descripción general

El Screen template define el esqueleto común de las pantallas Desktop de Tetris: fondo oscuro, header opcional con texto de tarea e información contextual, un área de contenido central configurable mediante slot y una bottom navigation opcional con botones de acción. No es un preset de experiencia concreta sino la estructura sobre la que se componen el resto de pantallas Desktop.

---

## Usos habituales

- Como base estructural para cualquier pantalla Desktop que siga el patrón estándar de Tetris.
- Para componer experiencias con header de tarea + contenido personalizado + bottom navigation.
- Para definir el layout de pantallas de picking, stowing, preparación de estación u otras tareas operativas que requieran la estructura canónica Desktop.

---

## Cuándo elegir alternativas

- Usar `Feedback screen` cuando el objetivo de la pantalla es comunicar el resultado de una operación completada.
- Usar `System state screen` cuando la pantalla comunica un estado de excepción del sistema.
- Para presets de Handheld, los elementos estructurales son distintos — ver los presets específicos (`Container screen`, `Product screen`, etc.).

---

## Anatomía

1. **Header** _(opcional)_: barra superior oscura con el texto de la tarea principal (`Main task text`) alineado a la izquierda. A la derecha puede incluir una fila de información contextual con hasta 3 pares Label/Info separados por divisores verticales. Fondo `color/background/inverse`.
2. **Container**: área de contenido principal. Fondo `color/surface/primary` (blanco). Crece con `flex: 1` para ocupar todo el espacio disponible entre header y bottom navigation. Contiene un **Slot** configurable donde se inserta el componente o contenido de cada pantalla.
3. **Bottom navigation** _(opcional)_: barra inferior oscura con hasta 3 botones de acción configurables + un botón de salida fijo (logout). Altura `96px`, fondo `color/background/inverse`.

---

## Variantes

El Screen template no tiene variantes de tipo distintas — su configuración se controla mediante las propiedades de visibilidad del header y la bottom navigation. Los distintos presets Desktop (Feedback screen, Container screen...) son especializaciones de esta estructura base.

---

## Propiedades

| Propiedad | Tipo | Default | Descripción |
|---|---|---|---|
| `header` | `boolean` | `true` | Muestra u oculta el header con el texto de tarea e información contextual. |
| `bottomNavigation` | `boolean` | `true` | Muestra u oculta la bottom navigation. |
| `mainTaskText` | `string` | `"Main task text"` | Texto de la tarea en el header. |
| `information2` | `boolean` | `true` | Muestra el segundo par Label/Info en el header. |
| `information3` | `boolean` | `true` | Muestra el tercer par Label/Info en el header. |
| `information4` | `boolean` | `false` | Muestra un cuarto par Label/Info en el header. |

### Design tokens

| Token | Valor resuelto | Descripción |
|---|---|---|
| `device/breakpoints/width` | `1920px` | Ancho Desktop |
| `device/breakpoints/height` | `1080px` | Alto Desktop |
| `color/background/inverse` | `#1c1c2b` | Fondo general, header y bottom navigation |
| `color/surface/primary` | `#ffffff` | Fondo del container de contenido |
| `color/text/inverse` | `#ffffff` | Texto del header (task text e información) |
| `color/interactive/fill/quiet-inverse/default` | `#454768` | Fondo de botones de la bottom navigation |
| `color/white-alpha/100` | `#ffffff` | Divisores entre pares de información en el header |
| `border/radius/m` | `16px` | Radio del botón de salida |
| `border/radius/circle` | `9999px` | Radio del ícono del botón de salida |
| `spacing/padding/m` | `40px` | Padding general de la pantalla |
| `spacing/gap/xl` | `40px` | Gap vertical entre header, container y bottom navigation |
| `spacing/gap/m` | `24px` | Gap horizontal entre botones de la bottom navigation |
| `spacing/gap/s` | `16px` | Gap interno del slot placeholder |
| `spacing/4xs` | `16px` | Padding del container |
| `spacing/s` | `40px` | Padding horizontal de los botones de la bottom navigation |
| `typograph/body/font-size/large` | `32px` | Texto de información en el header |
| `typograph/body/line-height/large` | `40px` | Line-height del texto de información |

---

## Comportamiento

- **Dimensiones**: `1920×1080px` fijo (fullscreen Desktop). Definido por `device/breakpoints/width` y `device/breakpoints/height`.
- **Fondo general**: `color/background/inverse` (#1c1c2b). Crea el contraste visual entre el fondo oscuro y el área de contenido blanca.
- **Header**: fijo al tope. Contiene la tarea principal y hasta 3 (o 4) pares de información contextual con divisores de `1px × 36px`. Cuando `header = false`, el container sube hasta el borde superior.
- **Container**: crece con `flex: 1` para llenar el espacio disponible. El `.Slot` interior (mínimo `240px`) recibe el componente o layout específico de cada pantalla.
- **Bottom navigation**: 3 botones de ancho flexible (mínimo `208px`, crecen con `flex: 1`) + botón de salida fijo de `162px`. Todos con altura `96px` y fondo `color/interactive/fill/quiet-inverse/default` (#454768). El botón de salida tiene radio `16px` y muestra el ícono de logout de `24px`. Cuando `bottomNavigation = false`, el container se extiende hasta el borde inferior.
- El Screen template es exclusivamente Desktop — para Handheld, usar los presets específicos.

---

## Ejemplos

### Preparación de estación de trabajo con slot map

El header muestra la tarea principal "Prepare a estação de trabalho" en texto blanco sobre fondo oscuro. El container central ocupa todo el espacio disponible entre el header y la bottom navigation: a la izquierda del slot se muestra un ícono de tote, el título "Coloque o tote na posição indicada" y la instrucción secundaria "Aperte o botão luminoso para confirmar"; a la derecha, un slot map con una grilla de posiciones donde la celda "3-2" aparece resaltada en amarillo indicando la posición activa donde el rep debe depositar el tote. La bottom navigation al pie mantiene el fondo oscuro: el primer botón muestra "Problema no botão" como acción disponible, los dos siguientes están vacíos/deshabilitados, y el botón de salida (logout) permanece activo en la esquina derecha.

---

## Recomendaciones

### ✅ Do
- Usar el header para comunicar la tarea principal que el rep debe ejecutar en esa pantalla.
- Aprovechar los pares Label/Info del header para mostrar contexto operativo relevante (ej. estación de trabajo, turno, unidad de negocio).
- Insertar en el slot el componente o preset que resuelve la experiencia concreta de esa pantalla.
- Usar la bottom navigation con los botones necesarios para el flujo — pueden quedar hasta 3 activos.

### ❌ Don't
- No usar el Screen template directamente en Handheld — es exclusivo de Desktop (1920×1080px).
- No dejar el slot sin contenido en producción — el placeholder es solo para diseño.
- No agregar más de 4 pares Label/Info en el header — más información compite visualmente con el texto de tarea.
- No modificar el fondo general ni los colores estructurales fuera de los tokens definidos.

---

## Componentes relacionados

- **Header**: componente de encabezado con tarea e información contextual.
- **Content** (Flex): componente de contenedor flexible usado como área principal.
- **Bottom navigation**: componente de barra de navegación inferior con botones de acción.
- **Feedback screen**: preset Desktop especializado en comunicar resultados de operación.
- **System state screen**: preset Desktop para estados de excepción del sistema.
- **Container screen**: preset Handheld para identificación de posición o contenedor.

---

## Accesibilidad

Los criterios de accesibilidad específicos se encuentran en las especificaciones de cada componente constitutivo (Header, Content, Bottom navigation).

### Roles y etiquetado

La pantalla debe tener un `<main>` como contenedor principal para el área de contenido. El texto de la tarea principal en el header debe implementarse con un elemento semántico de encabezado (`<h1>`) para que los lectores de pantalla puedan navegar directamente a él. Los botones de la bottom navigation deben tener etiquetas accesibles (`aria-label`) claras que describan su acción.

### Navegación

Orden de lectura: header (tarea + información contextual) → contenido del slot → botones de bottom navigation → botón de salida.

### Interacciones con teclado

| Tecla | Función |
|---|---|
| Tab | Navegar entre elementos interactivos del header, slot y bottom navigation |
| Enter / Space | Activar el botón enfocado |

### Gestos

| Gesto | Función |
|---|---|
| Tap en botón de nav | Ejecutar acción de navegación |
| Tap en botón de salida | Salir de la tarea actual |

### Consideraciones de diseño

- El texto blanco del header (`color/text/inverse`) sobre fondo `#1c1c2b` cumple WCAG AA para texto de 32px (texto grande).
- Los botones de la bottom navigation tienen `96px` de alto — suficiente área de toque para uso en condiciones operativas.
- El botón de salida de `162px × 96px` garantiza un área mínima cómoda para el ícono de logout de `24px`.
