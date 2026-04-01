# Carousel

> [!ABSTRACT]
> El Carousel permite mostrar múltiples elementos de forma secuencial, recorriendo diferentes vistas sin abandonar el flujo principal. Es ideal para mostrar múltiples imágenes en tamaño grande, como galerías de fotos de producto.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=15772-11828&t=QPYbw6d2Xji0v5Le-1) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=2657-4857&m=dev) |

Permite mostrar múltiples elementos de forma secuencial.

| Campo | Valor |
|-------|-------|
| **Nombre canónico** | Carousel |
| **Categoría** | Navegación / Contenido |
| **Status de madurez** | Estable |
| **Owner** | Tetris |

---

## Descripción general

El Carousel permite recorrer diferentes vistas de manera secuencial sin abandonar el flujo principal, invita a la persona usuaria a descubrir contenido adicional en un mismo espacio.
Es ideal para mostrar múltiples imágenes en tamaño grande.

---

## Usos habituales

- Cuando se quiere dar acceso a diferentes fotos de un mismo producto.
- Para galerías de imágenes o contenido multimedia con navegación controlada por el usuario.

---

## Anatomía

Está definido esencialmente por un slot que aloja el contenido a mostrar y, de forma opcional, controles de navegación. El slot que acepta imágenes es el elemento central e irremplazable del componente; los controles de navegación son elementos complementarios que refuerzan la exploración y orientan a la persona usuaria dentro de la secuencia.

1. **Slot**: Acepta cualquier contenido visual; contiene la vista o imagen a mostrar. Es el único elemento obligatorio del componente.
2. **Navigation controls** _(opcional)_: agrupan los elementos que permiten navegación manual. Su presencia es configurable.
3. **Chevron**: botones accionables para avanzar a la vista siguiente o retroceder a la anterior. Se posicionan bajo el slot, en los bordes laterales.
4. **View indicator**: indica cuántas vistas componen el Carousel y cuál está activa en ese momento.

---

## Variantes

El Carousel tiene una sola variante, pero admite dos opciones de uso que determinan si los controles de navegación están presentes o no.

### Simple (sin Navigation controls)

No incluye Navigation controls. Se utiliza cuando se necesita mostrar una única imagen a pantalla completa, sin necesidad de navegación.

### Con Navigation controls

Incluye chevrons y view indicator. Es la opción recomendada cuando el Carousel contiene múltiples vistas y la persona usuaria necesita orientarse y navegar libremente entre ellas. Uso habitual: galería de fotos de producto en pantalla de detalle (PDP).

---

## Propiedades

### Navigation controls

Propiedad booleana que determina si los controles de navegación (chevrons y view indicator) son visibles. Cuando está desactivada, el componente depende de gestos para avanzar entre vistas. El componente no posee propiedad de autoplay.

### Items

Slot múltiple que acepta las vistas a mostrar. La cantidad de ítems determina el estado del view indicator. Los chevrones de los extremos pueden estar deshabilitados ya que el componente no permite navegación en loop.

---

## Estados

### Dot states

| Estado | Detalle |
|--------|---------|
| **Active on** | El punto indica la vista que se está mostrando en ese momento. |
| **Active off** | El punto representa una vista restante de la secuencia. |

### Chevron states

| Estado | Detalle |
|--------|---------|
| **Default** | Disponible para navegar. |
| **Disabled** | Se aplica al chevron izquierdo cuando se está en la primera vista —inhabilitando la navegación hacia atrás— y al chevron derecho cuando se está en la última —inhabilitando la navegación hacia adelante. |

### Estados de interacción (Navigation controls)

| Estado | Detalle |
|--------|---------|
| **Hover** | Se activa al pasar el cursor sobre el área interactiva. Proporciona retroalimentación visual sutil para indicar interactividad en experiencias desktop. |
| **Active** | Aparece mientras el usuario hace clic o tap sobre el componente. Refuerza que la acción fue reconocida mediante un cambio visual más notorio que Hover. |
| **Disabled** | Indica que el componente no está disponible. No responde a interacción y presenta un contraste reducido para señalar su inactividad. |

---

## Comportamiento

### Navegación

La persona usuaria puede navegar entre vistas de tres formas: mediante los chevrons (clic/tap), mediante gestos de swipe horizontal (en dispositivos táctiles) y mediante las teclas de flecha del teclado cuando el componente está en foco. Cada acción de navegación avanza o retrocede una vista a la vez.

### View indicator

Se actualiza automáticamente con cada cambio de vista, independientemente del método de navegación usado. El punto activo refleja la posición de la vista visible dentro de la secuencia total.

### Responsividad

El Carousel ocupa el alto y ancho del drawer que lo aloja. El slot se adapta rellenando el espacio. Los chevrons mantienen su tamaño y posición relativa sobre el slot en todos los breakpoints.

### Áreas activas

Los chevrons son las únicas áreas interactivas permanentes del componente. En dispositivos táctiles, toda la superficie del slot responde al gesto de swipe horizontal. El view indicator no es interactivo.

### Cantidad de ítems

No existe un límite técnico en la cantidad de vistas, pero se recomienda un rango de 2 a 5 ítems para mantener la utilidad del componente. Con más de 5 ítems, la orientación dentro de la secuencia se vuelve difícil y el componente pierde efectividad.

---

## Ejemplos

### Galería de producto

Carousel con variante *Con Navigation controls* utilizado en la página de detalle de producto para mostrar múltiples ángulos de un mismo artículo. El view indicator en posición overlay permite conocer la cantidad total de imágenes sin desplazar la vista.

### Ampliación de imágenes de producto en Drawer

> Los productos que aparecen en los ejemplos son ilustrativos. En producción, las imágenes son levantadas dinámicamente por el sistema según el ítem seleccionado.

El Carousel se abre dentro de un Drawer al tocar el Button icon de zoom en la Product card. Muestra los distintos ángulos del mismo producto en secuencia: vista principal, laterales, detalles de materiales y vistas combinadas. El view indicator (dots) refleja la posición activa dentro de la galería y los chevrones permiten avanzar o retroceder entre ángulos. El chevron izquierdo aparece deshabilitado en la primera vista y el chevron derecho en la última, ya que el componente no navega en loop. El botón de cierre (×) se ubica en la esquina superior derecha del Drawer y permite volver a la pantalla anterior sin perder el contexto.

---

## Recomendaciones

✓ **Do:** Usar el Carousel para mostrar múltiples imágenes de un mismo objeto o producto. La secuencialidad tiene sentido cuando las vistas comparten un hilo conductor claro.

✗ **Don't:** Usar el Carousel para agrupar contenidos no relacionados entre sí. Si cada vista es un concepto independiente, considerar Tabs o una estructura de lista como alternativa.

---

✓ **Do:** Mantener el número de ítems entre 2 y 5. El view indicator pierde legibilidad y utilidad cuando la secuencia supera ese rango.

✗ **Don't:** Incluir información crítica únicamente dentro de un Carousel. Una parte importante de las personas usuarias no interactúa con la navegación y solo verá la primera vista.

---

## Componentes relacionados

- **Drawer**: el Carousel va siempre dentro de un Drawer.
- **Product card**: el Carousel va siempre asociado a una Product card. La Product card contiene un Button icon (opcional) que abre el Drawer con el Carousel.

---

## Accesibilidad

Esta sección incluye solo las consideraciones esenciales de accesibilidad que están implementadas en los componentes de Tetris: el uso de roles y etiquetas que facilitan comprender el propósito de los componentes cuando son interpretados por lectores de pantalla, así como la navegación por teclas o gestos que garantizan una interacción inclusiva.

Para conocer más en detalle sobre tecnologías asistivas, se recomienda visitar la guía de accesibilidad digital. Para saber más sobre cómo hacer un handoff accesible, visitar la documentación de Accessibility notes.

### Roles y etiquetado

El Carousel debe implementarse como una región con `role="region"` y un `aria-label` descriptivo (ej. `"Carrusel de productos"`). Cada Slide debe tener `role="group"` con `aria-label` que indique su posición (ej. `"Ítem 1 de 5"`).

Si el carrusel tiene autoplay, debe incluirse `aria-live="off"` por defecto y activarse solo bajo demanda. El botón de pausa debe ser el primer elemento enfocable del componente.

### Navegación

El foco sigue el orden visual: botón Previous → slides → botón Next → indicadores (si son interactivos). Los dots o indicadores no interactivos deben marcarse con `aria-hidden="true"`. Tab debe poder salir del componente hacia el siguiente elemento de la página.

### Teclado

| Tecla | Función |
|-------|---------|
| `Tab` | Enfocar el componente; navegar entre controles interactivos |
| `←` | Retroceder al ítem anterior |
| `→` | Avanzar al ítem siguiente |
| `Space` / `Enter` | Activar el botón enfocado |

### Gestos

| Gesto | Detalle |
|-------|---------|
| Deslizar izquierda | Avanzar al ítem siguiente |
| Deslizar derecha | Retroceder al ítem anterior |
| Tap sobre botón | Activar navegación |

### Mensajes y feedback no visual

- El cambio de ítem activo debe anunciarse a lectores de pantalla mediante `aria-live="polite"` o actualizando el `aria-label` del contenedor.
- El estado disabled de los botones debe comunicarse mediante `aria-disabled="true"`.
- El estado del autoplay (reproduciendo / pausado) debe comunicarse mediante `aria-label` dinámico en el botón de pausa.

### Consideraciones de diseño

- Contraste mínimo **WCAG 2.2, nivel AA** para los controles de navegación sobre cualquier fondo.
- Si hay autoplay, mecanismo visible para pausarlo (**WCAG 2.1 — 2.2.2**).
- Área táctil mínima de **44×44 px** en botones para dispositivos móviles (**WCAG 2.5.5**).
- La animación de transición debe respetar `prefers-reduced-motion`.
