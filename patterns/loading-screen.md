# **Loading screen**

| | |
|---|---|
| **Owner** | Tetris |
| **Status** | WIP |
| **Última revisión** | Marzo 2026 |
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=23847-1021) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=5-356) |

> [!ABSTRACT]
> El Loading screen es un preset de pantalla completa para Handheld que indica al rep que el sistema está procesando una operación. Bloquea la interacción durante la espera y comunica visualmente el progreso mediante una animación de spinner. La pantalla es de solo lectura — el rep no puede interactuar hasta que la carga termine.

---

## Descripción general

El Loading screen cubre la pantalla completa mientras el sistema realiza una operación en segundo plano (carga de datos, procesamiento de un escaneo, transición entre flujos). Centra la atención del rep en el estado de espera e impide cualquier interacción accidental durante el proceso.

La animación tiene una secuencia de estados: inicia con el arco girando sobre fondo claro, transiciona a fondo oscuro al completarse la carga y opcionalmente muestra un texto descriptivo al finalizar.

---

## Usos habituales

- Indicar que el sistema está cargando datos antes de mostrar el contenido de la siguiente pantalla.
- Cubrir la pantalla durante transiciones entre flujos operativos.
- Comunicar que un escaneo o acción del rep está siendo procesada.

---

## Cuándo elegir alternativas

- Usar `Progress bar` para indicar avance de un proceso dentro de una pantalla, sin bloquear la interfaz completa.
- Usar `System state` (template Error) cuando la operación falla y el rep necesita una acción de salida.
- Usar `Feedback screen` para comunicar el resultado final de la operación una vez completada.

---

## Anatomía

1. **Spinner**: área de animación de `160×160px`. Compuesta por:
   - **Shape**: círculo de fondo. En el estado inicial (`color/surface/secondary` #ededf7). Transiciona a oscuro (`color/interactive/icon/default` #1c1c2b) al completarse la carga.
   - **Icon**: ícono representativo de `80×80px` centrado dentro del shape.
   - **Loading arc**: arco SVG que gira alrededor del shape indicando actividad.
2. **Description** _(opcional)_: texto descriptivo bajo el spinner. Aparece al finalizar la carga. Tipografía `Label/medium/strong` (28px, Semibold). Color `color/text/primary`.

---

## Variantes

### Por estado de la animación

La animación sigue una secuencia de 4 estados internos que se transicionan automáticamente:

| Estado | Descripción |
|---|---|
| **Loading** | Arco girando, fondo del shape claro (#ededf7). Sin label visible. Estado de espera activa. |
| **Finished loading** | Carga completada. Label aparece con fade-in. Fondo del shape aún claro. |
| **Transition to black** | El fondo del shape transiciona de claro a oscuro (#1c1c2b). Indica finalización inminente. |
| **Finished loading (dark)** | Estado final. Fondo oscuro. Label completamente visible. |

### Por label

| Variante | Descripción |
|---|---|
| **Con description** | Muestra un texto descriptivo al completarse la carga (`label = true`). |
| **Sin description** | Solo animación, sin texto (`label = false`). Para transiciones rápidas sin mensaje. |

---

## Propiedades

| Propiedad | Tipo | Default | Descripción |
|---|---|---|---|
| `label` | `boolean` | `true` | Muestra u oculta el texto de descripción bajo el spinner. |
| `labelText` | `string` | `"Label description"` | Texto descriptivo que aparece al completarse la carga. |

### Design tokens

| Token | Valor resuelto | Descripción |
|---|---|---|
| `device/breakpoints/width` | `360px` | Ancho base Handheld |
| `device/breakpoints/height` | `640px` | Alto base Handheld |
| `color/background/primary` | `#ffffff` | Fondo de la pantalla |
| `color/surface/secondary` | `#ededf7` | Fondo del shape en estado Loading |
| `color/interactive/icon/default` | `#1c1c2b` | Fondo del shape en estado final |
| `color/text/primary` | `#1c1c2b` | Color del texto de description |
| `border/radius/circle` | `9999px` | Radio del shape circular |
| `spacing/gap/m` | `24px` | Gap entre spinner y label |
| `spacing/padding/xs` | `24px` | Padding horizontal de la pantalla |
| `font/weight/semibold` | `600` | Peso de la fuente del label |
| `font/line-height/400` | `28px` | Line-height del label |

---

## Comportamiento

- **Dimensiones**: `360×640px` (min-width `320px`, min-height `530px`, max `640×640px`). Rango Handheld.
- **Fondo**: `color/background/primary` (#ffffff) — blanco durante todo el estado de carga.
- **Spinner**: centrado vertical y horizontalmente. El arco gira indefinidamente en el estado Loading.
- **Transición de color**: el Shape cambia de `color/surface/secondary` a `color/interactive/icon/default` cuando la operación se completa, señalando visualmente el fin de la espera.
- **Label**: en el estado Loading está presente en el DOM pero con `opacity: 0`. Al completarse la carga hace fade-in. Si `label = false`, no se renderiza.
- La pantalla no tiene elementos interactivos — el rep no puede hacer nada hasta que la carga finalice.
- La transición a la siguiente pantalla ocurre automáticamente al completarse la operación del sistema.

---

## Ejemplos

### Carga de ruta en flujo de picking

Variante **con description**. La pantalla muestra el spinner centrado verticalmente sobre fondo blanco: el shape circular en estado de carga (`color/surface/secondary` #ededf7) contiene el ícono de ruta en su interior, y el arco de carga gira en la parte inferior del círculo indicando actividad. Debajo del spinner, el texto "Creando la mejor ruta..." informa al rep qué está procesando el sistema. No hay elementos interactivos — el rep espera hasta que el sistema termine de calcular la ruta y navegue automáticamente a la siguiente pantalla.

---

## Recomendaciones

### ✅ Do
- Usar siempre que el rep deba esperar más de ~1 segundo para que el sistema procese una acción.
- Agregar un `labelText` descriptivo cuando la espera es larga o el resultado es importante (ej. "Procesando escaneo…").
- Permitir que la transición de color indique el fin de la carga antes de navegar a la siguiente pantalla.

### ❌ Don't
- No usar para transiciones instantáneas — si el proceso tarda menos de ~500ms, preferir una transición directa.
- No agregar botones ni interacciones a esta pantalla — el rep no debe poder escapar durante la carga.
- No usar en Desktop — es exclusivo de Handheld.
- No omitir la transición a la siguiente pantalla: la pantalla de loading siempre debe resolverse en otra pantalla.

---

## Componentes relacionados

- **Progress bar**: indicador de progreso no bloqueante, dentro de una pantalla de acción.
- **Feedback screen**: preset para comunicar el resultado final de la operación completada.
- **System state**: preset para errores o excepciones que interrumpen el flujo.
- **Transit screen**: preset de transición entre puntos de la operación (con datos de dirección).

---

## Accesibilidad

### Roles y etiquetado

El contenedor principal debe tener `role="status"` y `aria-live="polite"` para que los lectores de pantalla anuncien el estado de carga sin interrumpir. El ícono del spinner debe marcarse como decorativo (`aria-hidden="true"`).

Si se muestra el `labelText`, debe ser legible por lector de pantalla y describir la operación en curso (ej. `"Cargando datos de la operación"`).

### Navegación

No hay elementos interactivos — ningún elemento debe recibir foco durante el estado de carga. El foco no debe quedar atrapado en esta pantalla.

### Consideraciones de diseño

- El fondo blanco con el texto `color/text/primary` (#1c1c2b) cumple WCAG AA en todos los tamaños.
- La transición de color del shape es puramente decorativa — no transmite información crítica por sí sola. El `aria-live` region debe comunicar el cambio de estado semánticamente.
- El spinner de `160px` es suficientemente grande para ser visible en condiciones de baja atención del rep (en movimiento, con guantes).
