# Snackbar

> [!ABSTRACT]
> El Snackbar es un componente de feedback temporal que informa al usuario sobre el resultado de una acción o proceso, apareciendo de forma automática sin requerir interacción y ocultándose tras un período de tiempo definido. Resuelve la necesidad de comunicar mensajes breves de confirmación, advertencia o error sin interrumpir el flujo principal.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?node-id=13627-18713) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=5-350) |

| Campo | Valor |
|-------|-------|
| **Nombre canónico** | Snackbar |
| **Alias interno** | Toast |
| **Categoría** | Feedback |
| **Status** | Stable |
| **Owner** | Tetris |
| **Última revisión** | — |
| **Figma** | [Component-Specs → Snackbar](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=5-350) |

`Componente en librería`

**Specs**

Componente de feedback temporal que informa al usuario sobre el resultado de una acción o proceso. Aparece de forma automática, sin requerir interacción, y se oculta tras un período de tiempo definido.

---

## Descripción general

El Snackbar es un componente de retroalimentación que comunica mensajes breves relacionados al estado de una operación. Puede ser temporal (se cierra solo) o accionable (requiere respuesta del usuario). Soporta cuatro tipos de feedback según la naturaleza del mensaje: positivo, advertencia, negativo e informativo. Incluye un ícono identificador, texto de título opcional, descripción, área de acción y barra de progreso.

---

## Usos habituales

- Cuando se necesita confirmar el resultado de una acción del usuario (ej: "Producto agregado al carrito").
- Para notificar errores o advertencias no bloqueantes que no interrumpen el flujo.
- Para comunicar el estado de un proceso en segundo plano.

---

## Cuándo elegir otra opción

Usar una **Feedback Screen** cuando el mensaje requiere interrumpir el flujo del usuario para comunicar un estado o resultado que necesita mayor atención o comprensión.

---

## Anatomía

_Los títulos de anatomía en inglés._

1. **Icon**: Ícono de feedback que refuerza visualmente el tipo de mensaje.
2. **Title** _(opcional)_: Título corto que resume el mensaje principal.
3. **Description**: Texto principal del mensaje. Puede ser de una o múltiples líneas.
4. **Action** _(opcional)_: Texto accionable que permite al usuario ejecutar una acción relacionada.
5. **Progress Bar** _(opcional)_: Indicador visual del tiempo restante antes de que el componente se cierre automáticamente.

---

## Variantes *

### Positive
Comunica el éxito de una operación. Usa el token `--color/feedback/fill/positive-loud` (#068943).

### Warning
Comunica una advertencia o resultado que requiere atención. Usa el token `--color/feedback/fill/caution-loud` (#ec5809).

### Negative
Comunica un error o fallo en una operación. Usa el token `--color/feedback/fill/negative-loud` (#da0b38).

### Informative
Comunica información contextual neutral. Usa el token `--color/feedback/fill/informative-loud` (#454768).

### Combinaciones de propiedades

| `progressBar` | `action` | Válido | Modo resultante |
|---------------|----------|--------|-----------------|
| `true` | `false` | ✓ | Temporal — se cierra automáticamente |
| `false` | `true` | ✓ | Accionable — requiere interacción del usuario |
| `false` | `false` | ✓ | Solo lectura — sin cierre explícito |
| `true` | `true` | ✗ | Contradictorio — no usar |

> La propiedad `type` es independiente y puede combinarse con cualquier configuración válida de las anteriores.

---

## Propiedades

### Props del componente

| Propiedad | Valores | Descripción |
|-----------|---------|-------------|
| `type` | `Positive` \| `Caution` \| `Negative` \| `Informative` | Define el tipo de feedback y el color de fondo del componente. |
| `title` | `true` \| `false` | Muestra u oculta el título del mensaje. |
| `titleText` | string | Texto del título. Por defecto: `"Title"`. |
| `descriptionText` | string | Texto de la descripción del mensaje. Por defecto: `"This can be a single or multiline message."` |
| `action` | `true` \| `false` | Muestra u oculta el área de acción. |
| `actionText` | string | Texto del botón de acción. Por defecto: `"ACTION"`. |
| `progressBar` | `true` \| `false` | Muestra u oculta la barra de progreso de tiempo. |

### Design tokens de estructura

| Token | Valor resuelto | Descripción |
|-------|----------------|-------------|
| `--snackbar/structure/border/radius` | `16px` | Radio de borde del contenedor. |
| `--snackbar/structure/spacing/horizontal` | `32px` | Padding horizontal del contenedor. |
| `--snackbar/structure/spacing/top` | `40px` | Padding superior del área de contenido. |
| `--snackbar/structure/spacing/bottom` | `32px` | Padding inferior del área de contenido. |
| `--snackbar/structure/spacing/gap-default` | `32px` | Gap entre los elementos internos del Snackbar. |
| `--snackbar/structure/spacing/between-content` | `16px` | Gap entre el título y la descripción. |
| `--snackbar/text/line-height` | `36px` | Altura de línea del texto del Snackbar. |

### Design tokens de color por tipo

| Token | Valor resuelto | Tipo |
|-------|----------------|------|
| `--color/feedback/fill/positive-loud` | `#068943` | Positive |
| `--color/feedback/fill/caution-loud` | `#ec5809` | Warning |
| `--color/feedback/fill/negative-loud` | `#da0b38` | Negative |
| `--color/feedback/fill/informative-loud` | `#454768` | Informative |
| `--color/text/inverse` | `#FFFFFF` | Texto e ícono sobre fondo de color |
| `--color/icon/inverse` | `#FFFFFF` | Ícono de la barra de progreso |
| `--color/white-alpha/30` | `rgba(255,255,255,0.3)` | Fondo de la barra de progreso |

---

## Estados

El Snackbar no tiene estados de interacción propios (hover, pressed, focus) sobre su contenedor, ya que es un componente de notificación no interactivo. Sus modos de comportamiento son:

| Modo | Descripción | Props asociadas |
|------|-------------|-----------------|
| **Temporal** | Aparece automáticamente y se cierra solo tras 3–10 segundos según la longitud del mensaje. | `progressBar: true`, `action: false` |
| **Accionable** | Aparece automáticamente y requiere que el usuario ejecute o descarte la acción. Adquiere el foco al aparecer. | `progressBar: false`, `action: true` |
| **Solo lectura** | Aparece y persiste sin cierre automático ni acción explícita. | `progressBar: false`, `action: false` |

> El componente **Action** interno hereda los estados interactivos del componente Button.

---

## Comportamiento

### Posicionamiento

- **Sin Header activado (Desktop):** El Snackbar se posiciona con `24px` de separación respecto a los márgenes interiores del Container.
- **Con Header activado (Desktop):** El Snackbar se posiciona por encima del Header, quedando a `64px` del tope del margen superior del mismo.

### Dimensiones

| Plataforma | Ancho por defecto | Ancho mín. | Ancho máx. | Alto |
|------------|-------------------|------------|------------|------|
| Desktop / Tablet | `640px` | `560px` | `740px` | Variable según contenido |
| Handheld (mobile) | `312px` | — | — | `76px` |

### Aparición y cierre

- Aparece desde el borde superior del contenedor, superpuesto al contenido de la pantalla.
- **Temporal:** se cierra automáticamente. La Progress Bar indica el tiempo restante (mínimo 3s, máximo 10s).
- **Accionable:** se cierra al ejecutar la acción o al deslizar (Swipe to dismiss).
- No se deben mostrar múltiples Snackbars simultáneamente.

---

## Ejemplos

### Positive

Pantalla de picking mostrando un producto (Fone Apple AirPods Max, código XTUGE94902) con 3 unidades para recoger y un mapa de posiciones de estante con la posición 4-2 resaltada. El Snackbar aparece superpuesto en la esquina superior izquierda con fondo verde, título "Pronto!" y descripción "Você reportou um produto não encontrado.", con barra de progreso visible.

### Negative

Pantalla de escaneo de estación de trabajo con la instrucción "Escanele a estação de trabalho" e imagen de un producto (auriculares en caja amarilla con código de barras resaltado en rojo). El Snackbar aparece superpuesto en la esquina superior izquierda con fondo rojo, título "Chame a ajuda" y descripción "Um usuário já está logado nesta estação de trabalho.", con barra de progreso visible.

---

## Recomendaciones

✓ **Do:** Usar Progress bar cuando el Snackbar se cierra solo, y Action cuando debe ser cerrado por el usuario.

✗ **Don't:** No usar Progress bar y Action juntos, puede resultar contradictorio.

---

✓ **Do:** Usar contenido corto y conciso.

✗ **Don't:** Evitar textos largos, con información demasiado detallada o específica.

---

✓ **Do:** Usar para información específica y acotada.

✗ **Don't:** No superponer los Snackbar.

---

✗ **Don't:** No usar para comunicar información crítica y extensa.

---

## Mapeo técnico

| Artefacto | Referencia |
|-----------|------------|
| **Figma (specs)** | [Component-Specs → Snackbar](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=5-350) |
| **Figma (librería)** | [Tetris Library 2.0 → Snackbar](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?node-id=13627-18713) |
| **Storybook** | `[ABIERTO]` — completar con URL del story |
| **Nombre en código** | `[ABIERTO]` — completar con nombre en repo |

---

## Componentes relacionados

- Progress bar

---

## Accesibilidad

### Roles y etiquetado

**Temporal**
El Snackbar temporal se anuncia automáticamente a lectores de pantalla sin necesidad de intervención del usuario. Se oculta automáticamente después de un mínimo de **3 segundos** y un máximo de **10 segundos**, dependiendo de la longitud del mensaje. Implementar como región `aria-live`.

**Accionable**
El Snackbar accionable requiere una acción del usuario, que puede variar desde una confirmación de lectura hasta una acción más específica. Cuando aparece, adquiere el foco automáticamente y debe comportarse como un `dialog` modal en lo que respecta a accesibilidad. El rol del botón de acción debe ser `button`.

### Navegación

Cuando aparece el Snackbar, este recibe el foco automáticamente. No se alcanza mediante navegación por Tab desde otros elementos de la interfaz.

### Interacciones con teclado

| Tecla | Detalle |
|-------|---------|
| `Space` (×2) | Acciona el elemento del Snackbar |

### Gestos

| Gestos | Detalle |
|--------|---------|
| Deslizar (Swipe to dismiss) | Cierra el componente |

### Consideraciones de diseño

Este componente cumple con los criterios de contraste mínimo de **WCAG 2.2**, nivel **AA** para texto normal y texto grande. El fondo de color intenso con texto blanco (`#FFFFFF`) garantiza la legibilidad en todos los tipos (Positive, Warning, Negative, Informative).

---

## Evidencias y criterios de aceite

### Criterios de aceite

- [ ] El componente muestra correctamente los cuatro tipos (`Positive`, `Caution`, `Negative`, `Informative`) con sus colores correspondientes.
- [ ] La Progress Bar solo aparece cuando `progressBar: true` y `action: false`.
- [ ] El Action solo aparece cuando `action: true` y `progressBar: false`.
- [ ] En modo temporal, el componente se cierra automáticamente entre 3 y 10 segundos.
- [ ] En modo accionable, el componente adquiere el foco al aparecer.
- [ ] El componente es descartable con Swipe to dismiss en dispositivos táctiles.
- [ ] No se muestran dos Snackbars simultáneamente.
- [ ] El contraste texto/fondo supera el ratio mínimo WCAG AA en todos los tipos.
- [ ] El componente se anuncia correctamente via `aria-live` en modo temporal.
- [ ] El componente se comporta como `dialog` modal en modo accionable.

### Casos incorrectos de referencia

- Usar `progressBar: true` + `action: true` al mismo tiempo.
- Usar el Snackbar para mensajes críticos que requieren atención sostenida del usuario (usar Feedback Screen en su lugar).
- Apilar múltiples Snackbars visibles simultáneamente.
- Usar para contenido extenso o con información muy detallada.
