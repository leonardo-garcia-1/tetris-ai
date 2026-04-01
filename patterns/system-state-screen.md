
# **System state screen**

| | |
|---|---|
| **Owner** | Tetris |
| **Status** | WIP |
| **Última revisión** | Marzo 2026 |
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=23847-1012) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=1953-209) |

> [!ABSTRACT]
> El System state screen es el preset de pantalla completa que compone el componente `System state` dentro del entorno Desktop o Handheld. Comunica un estado de excepción del sistema (vacío, error, advertencia, información) que interrumpe el flujo operativo normal.

> **Ver documentación completa del componente:** [System state](../components/system-state.md) — cubre anatomía, tokens, variantes por dispositivo y presentación, templates y accesibilidad.

---

## Descripción general

El System state screen es la composición de pantalla completa del componente `System state`. En **Desktop** se presenta como un card blanco flotante sobre fondo oscuro, con bottom navigation siempre visible. En **Handheld** ocupa la pantalla directamente con fondo blanco y header de navegación.

Existe también la variante **Drawer**: el System state se presenta dentro del componente `Drawer` cuando el estado es contextual a una subtarea, sin abandonar el contexto de la pantalla padre.

---

## Cuándo usar este preset vs el Drawer

| Situación | Usar |
|---|---|
| El estado de excepción afecta la pantalla completa y bloquea el flujo | **System state screen (Full screen)** |
| El estado de excepción es contextual a una sección o subtarea | **System state en Drawer** |
| El error o estado no bloquea el flujo | `Snackbar` |

---

## Variantes

### Por dispositivo

| Variante | Dimensiones | Layout |
|---|---|---|
| **Desktop** | `1920×1080px` | Card blanco flotante sobre fondo `#1c1c2b`. Bottom navigation siempre visible. Ícono `160px`. |
| **Handheld** | `360×640px` | Fondo blanco directo. Header con navegación. Ícono `80px`. |

### Por presentación

| Variante | Descripción |
|---|---|
| **Full screen** | Ocupa toda la pantalla. Para estados críticos que bloquean el flujo. |
| **Drawer** | El System state se muestra dentro del componente `Drawer`. Para estados secundarios sin abandono del contexto padre. |

### Por template

| Template | Icono | Uso típico |
|---|---|---|
| **Empty** | Cactus | Sin resultados o contenido disponible |
| **Error** | Advertencia | Error inesperado del sistema |
| **Caution** | Alerta | Advertencia antes de continuar |
| **Informative** | Información | Mensaje del sistema sin carácter de error |

### Por tipo de acción

| Tipo | Descripción |
|---|---|
| **Buttons** | Botón primario (obligatorio) + botón secundario opcional |
| **Touchless** | Acción sin toque físico. Solo Handheld. |

---

## Propiedades

Comparte todas las propiedades del componente `System state`. Ver [propiedades completas](../components/system-state.md#propiedades).

| Propiedad | Tipo | Default | Descripción |
|---|---|---|---|
| `device` | `"Desktop"` / `"Handheld"` | `"Desktop"` | Variante de dispositivo. |
| `presentation` | `"Full screen"` / `"Drawer"` | `"Full screen"` | Modo de presentación. |
| `actionType` | `"Buttons"` / `"Touchless"` | `"Buttons"` | Tipo de acción. |
| `buttonSecondary` | `boolean` | `false` | Botón secundario adicional. |

---

## Comportamiento

- **Desktop Full screen**: card blanco flotante sobre fondo `#1c1c2b`. Bottom navigation siempre presente con botones en estado deshabilitado y botón Exit activo.
- **Handheld Full screen**: pantalla blanca con Header y botón de retroceso. Botón de acción al pie.
- **Drawer (ambos dispositivos)**: el componente `Drawer` provee el contenedor. El header del Drawer reemplaza al header nativo. En Desktop el Drawer se abre desde la derecha (`948px` de ancho); en Handheld cubre la parte inferior de la pantalla (`500px` de alto mínimo).
- En el Drawer Handheld, la presentación puede ser con fondo completo (cubre toda la pantalla) o parcial (ocupa desde `140px` desde la parte superior hacia abajo).

---

## Ejemplos

### Estado vacío en Handheld (template Empty)

Variante **Handheld Full screen**, template **Empty**. La pantalla tiene fondo blanco con el header de navegación en la parte superior (solo flecha de retroceso). El ícono de cactus centrado verticalmente comunica la ausencia de contenido disponible. Debajo, el título "Sorry, there's nothing here" y la descripción "Try again later" orientan al rep sobre qué pasó. El botón azul primario "Retry" al pie ofrece la única acción disponible para reintentar la operación.

### Error inesperado en Desktop (template Error)

Variante **Desktop Full screen**, template **Error**. El card blanco flota sobre el fondo oscuro (`#1c1c2b`) y concentra toda la atención del rep en el error. El ícono de alerta (círculo con signo de exclamación) comunica el tipo de excepción sin color semántico adicional. El título "Unexpected error" y la descripción "Try again later" son directos y no técnicos. El botón "Go back" debajo del título permite al rep salir del estado. La bottom navigation en la parte inferior queda visible pero con los tres botones de acción deshabilitados — solo el botón de salida (logout) permanece activo.

---

## Recomendaciones

### ✅ Do
- Usar **Full screen** cuando el estado bloquea completamente el flujo y requiere atención total del rep.
- Usar **Drawer** cuando el estado es contextual a una sección parcial de la pantalla.
- Incluir siempre una acción de salida clara ("Volver", "Reintentar", "Continuar").

### ❌ Don't
- No usar este preset para errores menores o validaciones — usar `Snackbar`.
- No omitir la acción: el rep siempre debe tener una salida del estado.
- No usar Touchless en Desktop.
- No usar Full screen para estados secundarios que no bloquean el flujo.

---

## Componentes relacionados

- **[System state](../components/system-state.md)**: componente interno con anatomía, tokens y accesibilidad completos.
- **Drawer**: componente contenedor para la presentación en panel.
- **Screen template**: preset base Desktop sobre el que se compone este preset.
- **Feedback screen**: preset alternativo para resultados de operaciones recientes.
- **Snackbar**: para notificaciones no bloqueantes.
