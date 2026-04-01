
# **Haptics**

| | |
|---|---|
| **Owner** | Tetris |
| **Status** | WIP |
| **Última revisión** | Marzo 2026 |
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=23847-1014) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=1312-5224) |

> [!ABSTRACT]
> Haptics es una capa de overlay que se superpone sobre la pantalla activa para indicar al rep qué gesto físico debe realizar en el dispositivo. No es una pantalla de estado ni de contenido: es una señal de interacción que guía la acción táctil del rep mediante animación visual + instrucción textual.

---

## Descripción general

El overlay de Haptics cubre la pantalla con un fondo semitransparente oscuro (`backdrop-blur` + `rgba(47,47,70,0.7)`) y muestra una animación que representa el gesto esperado (press, scroll, press and hold) junto a una instrucción textual. En Desktop, Haptics también contempla una alerta flotante crítica (`Alert Boxi`) para notificaciones urgentes del sistema.

El componente no bloquea la interacción de forma permanente — aparece durante el momento en que el rep debe ejecutar el gesto y desaparece una vez completado.

---

## Usos habituales

- Indicar al rep que debe **presionar** un botón o elemento en pantalla.
- Indicar al rep que debe **hacer scroll** para continuar.
- Indicar que el sistema está **escuchando** con el micrófono activo (Voice).
- Mostrar una alerta crítica de sistema en Desktop que requiere atención inmediata (**Alert Boxi**).
- Guiar el gesto de **press and hold** sobre un elemento específico de la pantalla.

---

## Cuándo elegir alternativas

- Usar `Touchless` para indicar que el rep debe escanear un código — no requiere gesto táctil.
- Usar `System state` para errores o excepciones que interrumpen completamente el flujo.
- Usar `Snackbar` para notificaciones no críticas que no requieren gesto del rep.

---

## Anatomía

### Handheld — Press / Scroll

El overlay cubre toda la pantalla Handheld. Contiene:

1. **Image**: representación visual animada del gesto (ícono o ilustración que muestra el movimiento). Centrada en la pantalla.
2. **Description**: instrucción textual que describe la acción esperada. Tipografía `Body/small/default` (24px, Regular). Color `color/text/inverse` (blanco). Alineada a la derecha del área de animación.

### Handheld — Microphone (Voice)

1. **Icon microphone + wave animation**: ícono de micrófono con una animación de onda sonora (barras verticales animadas). Fondo `color/interactive/fill/quiet/default` (#e0e9ff). Pill redondeada de `16px` de radio.
2. **Description**: instrucción textual.

### Handheld — Press and hold

1. **Element to be pressed**: el elemento target visible bajo el overlay (recibe highlight visual).
2. **Animation**: animación de press ripple de `72×72px` posicionada sobre el elemento. Ciclo de 4 frames.
3. **Description**: instrucción textual de la acción.

### Desktop — Alert Boxi

Overlay sobre pantalla Desktop (1920×1080px). No cubre toda la pantalla:

1. **Alert box**: tarjeta flotante en la esquina inferior derecha. Contiene:
   - **Icon**: animación de ícono de alerta crítica.
   - **Title**: pregunta de confirmación (ej. "¿Sigues ahí?"). Tipografía `Body/medium`.
   - **Description**: texto complementario.
2. **Border glow**: borde rojo con blur (`color/feedback/border/negative-loud` #da0b38, blur 12px) que rodea toda la pantalla. Señala criticidad máxima.

---

## Variantes

| Tipo | Dispositivo | Descripción |
|---|---|---|
| **Press** | Handheld | Overlay con animación de press. Guía al rep a presionar un elemento. |
| **Scroll** | Handheld | Overlay con animación de scroll. Guía al rep a desplazarse. |
| **Voice** | Handheld | Overlay con ícono de micrófono y onda sonora. Indica escucha activa. |
| **Press and hold** | Handheld | Overlay con highlight del elemento target y animación de press sostenido. |
| **Alert Boxi** | Desktop | Alerta crítica flotante con borde glow rojo. No cubre toda la pantalla. |

---

## Propiedades

| Propiedad | Tipo | Default | Descripción |
|---|---|---|---|
| `type` | `"Press"` / `"Scroll"` / `"Voice"` / `"Press and hold"` / `"Alert Boxi"` | `"Press"` | Define el tipo de interacción haptic a comunicar. |
| `instructionText` | `string` | `"Haptics instruction"` | Texto de la instrucción visible al rep. |

### Design tokens

| Token | Valor resuelto | Descripción |
|---|---|---|
| `color/background/overlay` | `rgba(47,47,70,0.7)` | Fondo semitransparente del overlay Handheld |
| `color/text/inverse` | `#ffffff` | Color del texto de instrucción sobre overlay oscuro |
| `color/interactive/fill/quiet/default` | `#e0e9ff` | Fondo del pill de micrófono (Voice) |
| `color/interactive/icon/default-accent` | `#4850e5` | Color de las barras de onda sonora (Voice) |
| `color/feedback/border/negative-loud` | `#da0b38` | Color del borde glow de alerta (Alert Boxi) |
| `border/radius/circle` | `9999px` | Radio del pill de micrófono |

---

## Comportamiento

- El overlay Handheld cubre `360×640px` con `backdrop-blur: 4px` y fondo `rgba(47,47,70,0.7)`. El contenido de la pantalla subyacente es visible pero difuminado.
- La **Animation** del Press se posiciona en `left: 24px, top: 88px` (debajo del header). El texto de instrucción se alinea a la derecha.
- El gesto de **Press and hold** anima en 4 frames de 72×72px sobre el elemento target. El overlay se retira automáticamente al completarse el gesto (~2 segundos de hold).
- El overlay de **Voice** aparece solo mientras el micrófono está activo. Desaparece cuando el sistema deja de escuchar.
- **Alert Boxi** no oscurece la pantalla completa — es un elemento flotante sobre el Screen template de Desktop. El borde glow rojo (`blur: 12px`) bordea toda la pantalla como señal de alerta crítica.
- La transición de entrada/salida del overlay se realiza con animación de opacidad.

---

## Ejemplos

### Alert Boxi sobre pantalla de scanning en Desktop

Variante **Alert Boxi**, dispositivo **Desktop**. El Screen template subyacente muestra una operación de picking en curso: el rep está escaneando unidades de un producto (zapatilla New Balance, código "ML: AELY23413") con el contador "2/3 unidades escaneadas" y la caja destino "C16" visible. El sistema detecta baja productividad y dispara la alerta de Boxi: un borde rojo con blur rodea toda la pantalla como señal de criticidad máxima, y en la esquina inferior derecha aparece una tarjeta flotante con el ícono animado de Boxi y el mensaje "¿Sigues ahí? Vuelve a la tarea y evita ociosidad." La pantalla subyacente permanece visible — el rep puede ver el contexto de la tarea y retomar sin necesidad de navegar. La bottom navigation queda accesible con las acciones del flujo activas.

---

## Recomendaciones

### ✅ Do
- Usar Haptics solo cuando el gesto del rep es necesario y no es obvio por el contexto de la pantalla.
- Mantener la instrucción textual breve y orientada a la acción (ej. "Presiona para confirmar", "Desliza para ver más").
- En Press and hold, asegurar que el elemento target sea claramente visible bajo el overlay.

### ❌ Don't
- No usar el overlay de Haptics como pantalla de carga o espera — usar `Loading screen`.
- No acumular instrucciones en el texto — una sola acción por Haptic.
- No usar Alert Boxi para notificaciones no críticas — reservar para alertas que requieren atención inmediata del rep.
- No usar la variante Voice en Desktop — es exclusiva de Handheld.

---

## Componentes relacionados

- **Touchless**: componente de acción para escaneo (no requiere gesto táctil en pantalla).
- **Press animation**: subcomponente de animación de 4 frames usado internamente en Press y Press and hold.
- **Header**: presente en la pantalla subyacente que el overlay cubre parcialmente.
- **Screen template**: base Desktop sobre la que se superpone Alert Boxi.
- **Snackbar**: alternativa no bloqueante para notificaciones de menor jerarquía.

---

## Accesibilidad

### Roles y etiquetado

El overlay debe tener `role="alert"` o `role="status"` según el tipo:
- **Press / Scroll / Voice / Press and hold**: `role="status"` con `aria-live="polite"` — la instrucción se anuncia sin interrumpir.
- **Alert Boxi**: `role="alert"` con `aria-live="assertive"` — la alerta se anuncia de inmediato por el lector de pantalla.

La instrucción textual debe ser accesible y legible por lector de pantalla.

### Consideraciones de diseño

- El fondo overlay `rgba(47,47,70,0.7)` con texto blanco cumple WCAG AA para cualquier tamaño de texto.
- El borde glow rojo de Alert Boxi es puramente visual — no debe ser el único indicador de criticidad. El título y la descripción deben comunicar el nivel de urgencia textualmente.
- Las animaciones de Press/Scroll deben respetar la preferencia de sistema `prefers-reduced-motion` — ofrecer una versión estática de la instrucción como fallback.
