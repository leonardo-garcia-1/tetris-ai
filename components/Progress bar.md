# Progress bar

> [!ABSTRACT]
> Las barras de progreso comunican visualmente el avance de una operación en curso, ofreciendo retroalimentación clara y continua al usuario. Es un componente de solo visualización, disponible en dos variantes de color (Idle e Inverse) para fondos claros y oscuros.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=7753-18152) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=1571-1691) |

Las barras de progreso comunican visualmente el avance de una operación en curso, ofreciendo retroalimentación clara y continua al usuario.

---

## Identidad del componente

| Campo | Valor |
|-------|-------|
| Nombre canónico | `Progress bar` |
| Alias permitidos | barra de progreso |
| Categoría | Retroalimentación / Feedback |
| Dominio | Interacción — estados de proceso |
| Propósito | Indicar visualmente el porcentaje de avance de un proceso en curso |
| Owner | Tetris |
| Estado de madurez | Estable |
| Fecha de creación | 04 de febrero de 2025 |
| Fecha de última revisión | — |
| Plataformas | Desktop · Handheld |

---

## Descripción general

El Progress bar es un componente de retroalimentación visual que indica el porcentaje de avance de un proceso. Se compone de una pista de fondo y una barra de relleno cuyo ancho representa el progreso actual. Es un componente de solo visualización, sin interacción directa del usuario. Está disponible en dos variantes de color (Idle e Inverse) y adapta su altura según el dispositivo (Desktop y Handheld).

---

## Usos habituales

- Para mantener una pantalla activa mientras el usuario realiza una acción o se desplaza hacia una zona indicada, indicando visualmente el tiempo o avance restante.
- Como mecanismo de transición automática: al completarse el progreso, la aplicación avanza a la pantalla siguiente sin intervención del usuario.
- Para comunicar el avance de procesos en curso que requieren espera, ofreciendo retroalimentación continua sobre el estado de la operación.

---

## Cuándo elegir otra opción

- Si el sistema no puede conocer el estado real del proceso pero la persona usuaria sí puede observarlo, es preferible no usar el Progress bar como disparador automático. En ese caso, se recomienda pedirle al usuario que confirme la acción cuando esté listo, por ejemplo mediante un botón (Button) de confirmación o un escaneo (Touchless).

---

## Anatomía

1. **Progress space**: Área rellena que representa el avance actual del proceso. Su ancho se calcula proporcionalmente al valor de progreso.
2. **Empty space**: Pista de fondo que representa el total del recorrido disponible. Siempre ocupa el ancho completo del contenedor.

---

## Variantes

### Idle
Variante estándar para fondos claros. Pista en color `color/surface/secondary` y barra de relleno en `color/interactive/fill/loud/default`.

### Inverse
Variante para fondos oscuros o de color. Pista en color `color/interactive/fill/quiet-inverse/default` y barra de relleno en `color/icon/inverse` (blanco).

---

## Propiedades

| Propiedad | Valores | Descripción |
|-----------|---------|-------------|
| `type` | `"Idle"` / `"Inverse"` · default `"Idle"` | Variante de color. Define los tokens de color aplicados a la pista y a la barra de relleno. |

### Design tokens del componente

| Token | Valor resuelto | Descripción |
|-------|---------------|-------------|
| `Progress bar/size/height` | `8px` | Altura de la barra en Desktop |
| `border/radius/circle` | `9999px` | Radio de borde de la barra y la pista (fully rounded) |
| `color/surface/secondary` | `#ededf7` | Color de la pista en variante Idle |
| `color/interactive/fill/loud/default` | `#4850e5` | Color del relleno en variante Idle |
| `color/interactive/fill/quiet-inverse/default` | `#454768` | Color de la pista en variante Inverse |
| `color/icon/inverse` | `#ffffff` | Color del relleno en variante Inverse |

### Mapeamiento técnico

| Elemento de diseño (Figma) | Nombre en código | Tipo | Notas |
|----------------------------|-----------------|------|-------|
| `Progress bar` | `ProgressBar` | Componente | Confirmado en Figma |
| Propiedad `type = Idle` | `type="Idle"` | Prop | Variante para fondos claros. Default. |
| Propiedad `type = Inverse` | `type="Inverse"` | Prop | Variante para fondos oscuros |
| `Progress space` | `value` / `progress` | Prop numérica (0–100) | Controla el ancho de la barra de relleno |
| Altura Desktop (`8px`) | aplicada vía token | Token / CSS var | `Progress bar/size/height` |
| Altura Handheld (`4px`) | aplicada vía token | Token / CSS var | `[ABIERTO]` — valor 4px confirmado, nombre del token pendiente |

> **Storybook / referencia técnica:** `[ABIERTO]` — completar con URL o nombre del story

> **Eventos:** El componente es de solo lectura y no emite eventos propios. El valor de progreso es recibido como prop desde el sistema o flujo que lo controla.

---

## Estados

El Progress bar es un componente de visualización sin estados interactivos propios. Su apariencia depende exclusivamente del valor de progreso recibido (de 0 % a 100 %) y de la variante de color (`type`) configurada.

---

## Comportamiento

- **Desktop**: altura `8px`.
- **Handheld**: altura `4px`.
- El componente adapta su altura al dispositivo manteniendo el mismo sistema de tokens; el ancho siempre ocupa el 100 % del contenedor padre.
- La barra de relleno (`Progress space`) se posiciona en el extremo izquierdo y su ancho aumenta de izquierda a derecha conforme avanza el proceso.
- El componente fue creado como multidevice desde su versión inicial (04 de febrero de 2025).

---

## Ejemplos

### Transit screen
El Progress bar se usa en la pantalla de tránsito para indicar el tiempo restante de una acción en curso (por ejemplo, esperar a que el usuario llegue a una zona o complete un desplazamiento). Al alcanzar el 100 %, la aplicación avanza automáticamente a la pantalla siguiente. Se usa la variante según el fondo de la pantalla de tránsito correspondiente.

### Snack bar
El Progress bar puede acompañar a un Snack bar para representar el tiempo de vida restante del mensaje antes de que se cierre automáticamente. En este contexto refuerza la retroalimentación temporal del componente sin requerir interacción del usuario.

---

## Recomendaciones

### ✅ Do
- Usar el Progress bar cuando el sistema conoce con precisión el tiempo o porcentaje restante del proceso.
- Usar la variante Inverse sobre fondos oscuros o de color para garantizar contraste y legibilidad.
- Asegurarse de que la animación de avance sea continua y fluida, reflejando el progreso real del proceso en tiempo real.
- Usar el componente a lo ancho completo del contenedor disponible para maximizar la legibilidad del progreso.

### ❌ Don't
- No usar el Progress bar para procesos indeterminados donde no se conoce el tiempo de finalización; en ese caso usar un indicador de carga (spinner o skeleton).
- No detener la barra en un valor fijo sin que el proceso haya concluido; esto genera confusión y desconfianza en el usuario.
- No usar el Progress bar como único mecanismo de confirmación cuando el proceso depende de una acción física del usuario fuera del sistema.
- No forzar colores o alturas fuera de los tokens definidos por el sistema; respetar las variantes Idle/Inverse y los tamaños Desktop/Handheld.

---

## Evidencias y validación

### Criterios de aceite

| Criterio | Verificación |
|----------|-------------|
| La barra refleja el valor de progreso real del proceso en tiempo real | Visual / funcional |
| La variante Idle se muestra correctamente sobre fondos claros | Visual |
| La variante Inverse se muestra correctamente sobre fondos oscuros | Visual |
| La altura es `8px` en Desktop y `4px` en Handheld | Inspección CSS / token |
| El ancho ocupa el 100 % del contenedor padre | Visual / funcional |
| El relleno avanza de izquierda a derecha | Visual |
| El componente no responde a interacciones de teclado o gesto | Funcional |
| `role="progressbar"` con `aria-valuenow`, `aria-valuemin`, `aria-valuemax` están presentes | Inspección de accesibilidad |
| Contraste de colores cumple WCAG 2.2 AA | Herramienta de contraste |

### Pruebas de regresión sugeridas

- Verificar que un cambio en el token `color/interactive/fill/loud/default` actualiza el relleno en variante Idle.
- Verificar que la altura no varía al cambiar la variante de color.
- Verificar que un valor `0` muestra la barra vacía y un valor `100` la muestra completa.
- Verificar que el componente no genera scroll horizontal al ocupar el 100 % del contenedor.

---

## Componentes relacionados

- Transit screen
- Snack bar

---

## Accesibilidad

Esta sección incluye solo las consideraciones esenciales de accesibilidad que están implementadas en los componentes de Tetris, como por ejemplo el uso de roles y etiquetas que facilitan comprender el propósito de los componentes cuando son interpretados por lectores de pantalla, así como la navegación por teclas o gestos que garantizan una interacción inclusiva.

Para conocer más en detalle sobre tecnologías asistivas, te recomendamos visitar la guía de accesibilidad digital.

Para saber más sobre cómo hacer un hand off accesible te recomendamos visitar la documentación de Accessibility notes.

### Roles y etiquetado

El componente Progress bar debe incluir un elemento de texto accesible (equivalente al componente `TextOnly` con ícono informativo) que comunique el estado del progreso a lectores de pantalla, ya que la barra es un elemento puramente visual. Se recomienda usar `role="progressbar"` con los atributos `aria-valuenow`, `aria-valuemin` y `aria-valuemax` para exponer el valor actual.

### Navegación

El Progress bar no forma parte del orden de foco del teclado por ser un elemento de solo visualización. La información de progreso debe estar disponible en el contexto textual de la pantalla.

### Teclado

| Tecla | Detalle |
|-------|---------|
| — | Sin interacción directa. Componente de solo lectura. |

### Gestos

| Gesto | Detalle |
|-------|---------|
| — | Sin interacción directa. Componente de solo lectura. |

### Consideraciones de diseño

- El componente cumple con los criterios de contraste mínimo de **WCAG 2.2** en niveles **NORMAL AA** y **GRANDE AA**.
- En la variante Inverse, el relleno blanco (`#ffffff`) sobre pista oscura (`#454768`) debe verificarse en el contexto real de uso para garantizar contraste suficiente.
- La altura reducida en Handheld (`4px`) puede dificultar la percepción del componente para usuarios con baja visión; considerar complementar siempre con texto de porcentaje o descripción del estado.
