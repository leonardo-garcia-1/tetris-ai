# Touchless

> [!ABSTRACT]
> El Touchless es un componente de acción que permite realizar acciones a través de un scan en lugar de un tap, anclado en el extremo inferior de una pantalla o drawer. Resuelve la necesidad de interacción sin contacto en contextos operativos donde el toque directo es impráctico (ej. usuarios con guantes).

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=26492-25960) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=4694-2084) |

| Campo | Valor |
|-------|-------|
| Nombre canónico | `Touchless` |
| Aliases permitidos | — |
| Categoría | Acción / CTA |
| Dominio | Operaciones en campo |
| Status | Componente en librería · Specs |
| Owner | Tetris |
| Madurez | Stable |
| Última revisión | — |

Permite realizar acciones a través de un scan en lugar de un tap.

---

## Descripción general

El Touchless es un componente de acción que se ancla en el extremo inferior de una pantalla o drawer, invitando al usuario a escanear un código (QR u otro) en lugar de interactuar táctilmente. Combina un ícono animado de scan con un texto de instrucción corto y direccional. Tiene versiones adaptadas para Desktop y Handheld.

---

## Usos habituales

- Para reemplazar un botón cuando el contexto operativo hace que el toque sea impráctico: personas usuarias con guantes, dispositivos de mano en movimiento, o entornos donde el scan es el gesto más natural y confiable disponible.
- En pantallas donde el diseño requiere un CTA explícito pero se prioriza el scan como mecanismo de acción sobre el tap.

---

## Cuándo elegir otra opción

- Usar `Button` cuando el usuario no lleva guantes y puede interactuar táctilmente sin fricción, o cuando no existe un código en el entorno que tenga sentido escanear para ejecutar la acción.
- Usar `Button` cuando la acción requiere una confirmación intencional explícita (ej. confirmar un error, aceptar una advertencia) que no debe delegarse a un gesto físico automático como el scan.
- Usar `Button Icon` cuando la acción es secundaria, compacta o contextual dentro de la pantalla, y no necesita ocupar el espacio estructural del extremo inferior.
- Usar `Bottom Navigation` cuando el extremo inferior de la pantalla está destinado a la navegación entre secciones de la aplicación, no a disparar una acción puntual del flujo.
- Usar `Button Icon Shape` cuando la acción es icónica, contextual y se ubica fuera del extremo inferior de la pantalla (ej. menús o acciones auxiliares en la esquina superior derecha), sin requerir el espacio estructural de una CTA principal.

---

## Anatomía

**A. Touchless**

| # | Parte | Obligatoriedad | Función |
|---|-------|---------------|---------|
| 1 | **Scan icon** | Obligatoria | Ícono animado que representa el área de escaneo. Indica visualmente que el dispositivo está en modo lectura. Decorativo: no transmite información semántica adicional al texto. |
| 2 | **Instruction text** | Obligatoria | Texto corto y direccional que describe la acción que debe realizar el usuario para avanzar. Es la única parte que comunica la instrucción a lectores de pantalla. |

---

## Variantes

| Variante | Plataforma | Padding horizontal | Padding vertical | Tamaño ícono | Gap ícono-texto | Tipografía |
|----------|-----------|-------------------|-----------------|-------------|-----------------|------------|
| Desktop | Desktop | `64px` | `40px` | `48×48px` | `24px` (`spacing/2xs`) | Label/large · 32px |
| Handheld | Handheld | `24px` | `24px` | `48×48px` | `16px` (`spacing/4xs`) | Body/medium · 20px |

**Combinaciones permitidas:** cada variante es exclusiva de su plataforma; no se combinan entre sí.

**Fallback:** si la plataforma no está definida en el contexto, usar la variante Handheld como base.

---

## Propiedades

| Propiedad | Valores | Descripción |
|-----------|---------|-------------|
| `instructionText` | `string` · default `"Scan instruction description"` | Texto de instrucción que acompaña al ícono de scan. Debe ser concreto, corto y direccional. |

### Design tokens del componente

| Token | Valor resuelto | Descripción |
|-------|---------------|-------------|
| `Touchless/size/padding-vertical` | `40px` (Desktop) / `24px` (Handheld) | Padding vertical del componente |
| `Drawer/structure/spacing/padding` | `64px` (Desktop) / `24px` (Handheld) | Padding horizontal del componente |
| `border/width/m` | `2px` | Grosor del borde superior separador |
| `color/border/disabled` | `#dedfed` | Color del borde superior separador |
| `spacing/2xs` | `24px` | Espacio entre el ícono de scan y el texto de instrucción |
| `color/text/primary` | `#1c1c2b` | Color del texto de instrucción |

---

## Estado

El Touchless es un componente de invitación a la acción sin estados interactivos propios. Su apariencia es fija; el cambio de estado (de espera a éxito o error) es gestionado por la pantalla o flujo que lo contiene.

---

## Comportamiento

- El componente se posiciona **siempre en el extremo inferior** de la pantalla o drawer que lo contiene.
- Un borde superior de `2px` (`color/border/disabled`) lo separa visualmente del contenido que lo precede.
- El ícono de scan es animado, reforzando la acción esperada del usuario.
- El texto de instrucción se muestra en una sola línea con truncamiento (`text-overflow: ellipsis`) si supera el ancho disponible.
- **Desktop**: padding horizontal `64px`, padding vertical `40px`, ícono `48×48px`.
- **Handheld**: padding horizontal `24px`, padding vertical `24px`, ícono `48×48px`, gap `16px`, tipografía Body/medium 20px.
- El componente ocupa el ancho completo del contenedor padre.

### Orden de foco y lectura

El componente no forma parte del flujo de foco de teclado. Los lectores de pantalla anuncian únicamente el `instructionText`; el ícono es ignorado (`aria-hidden="true"`).

### Edge cases

| Situación | Comportamiento esperado |
|-----------|------------------------|
| `instructionText` vacío | No renderizar el componente o mostrar el texto default `"Scan instruction description"`. |
| Texto demasiado largo para una línea | Truncar con ellipsis. No hacer wrapping a segunda línea. |
| Contenedor padre muy angosto | El componente se adapta al ancho disponible; el texto se trunca antes que el ícono. |
| `prefers-reduced-motion: reduce` | El ícono de scan se muestra en estado estático; no hay animación. |
| Scan no reconocido / código inválido | El componente no gestiona este estado: la pantalla o flujo contenedor es responsable del feedback de error. |

---

## Ejemplos

### Packing drawer desktop

El Touchless aparece anclado al extremo inferior de un drawer en pantalla Desktop. El operario tiene guantes y debe confirmar el empaque de un ítem escaneando el código del tote. El componente reemplaza el botón "Confirmar" con la instrucción _"Scan the tote to confirm packing"_.

### Picking handheld

En un flujo de picking desde un dispositivo de mano, el Touchless ocupa el extremo inferior de la pantalla con la variante Handheld. El operario debe escanear el producto en la ubicación para validar el pick. El componente muestra la instrucción _"Scan the item to confirm pick"_ con padding compacto acorde al dispositivo.

### Feedback screen desktop

El Touchless aparece dentro de una pantalla de feedback en Desktop, invitando al usuario a escanear para continuar al siguiente paso del flujo después de recibir una confirmación del sistema. El componente se mantiene en el extremo inferior, separado del contenido informativo mediante el borde superior.

---

## Recomendaciones

✓ **Do**: Usar un call to action concreto, corto y direccional para el usuario.
✗ **Don't**: No usar texto complejo para la acción que va a realizar el usuario.

---

✓ **Do**: Usar íconos de scan sugeridos en el sistema (preferred).
✗ **Don't**: No usar íconos diferentes a los de scan.

---

✗ **Don't**: No posicionar el componente en otra área que no sea el extremo inferior.

---

## Componentes relacionados

- Feedback screen

---

## Mapping técnico

| Elemento | Figma | Código | Storybook |
|----------|-------|--------|-----------|
| Componente Desktop | node-id `1424:18455` | `<Touchless />` | `[ABIERTO]` |
| Componente Handheld | node-id `26492:25960` | `<Touchless />` | `[ABIERTO]` |

> **Nota para IT:** Desktop y Handheld son componentes separados en Figma, no variantes de una misma prop. La diferenciación de plataforma se resuelve a nivel de implementación.

### Props y eventos

| Nombre | Tipo | Default | Descripción |
|--------|------|---------|-------------|
| `instructionText` | `string` | `"Scan instruction description"` | Texto de instrucción visible y leído por lectores de pantalla. |

### Resolución de tokens por plataforma

| Token | Desktop | Handheld |
|-------|---------|----------|
| `Touchless/size/padding-vertical` | `40px` | `24px` |
| `Drawer/structure/spacing/padding` | `64px` | `24px` |

---

## Evidencias y criterios de aceptación

### Criterios de aceptación

- [ ] El componente se renderiza siempre en el extremo inferior del contenedor padre.
- [ ] El borde superior de `2px` en `color/border/disabled` es visible y separa el contenente previo.
- [ ] El ícono de scan se anima correctamente en condiciones normales.
- [ ] Con `prefers-reduced-motion`, el ícono es estático y no hay animación.
- [ ] El `instructionText` se trunca con ellipsis si supera el ancho disponible; no hace wrapping.
- [ ] El ícono tiene `aria-hidden="true"` y no es anunciado por lectores de pantalla.
- [ ] El `instructionText` es anunciado por lectores de pantalla de forma completa.
- [ ] El componente no recibe foco de teclado.
- [ ] Los tokens de padding Desktop y Handheld se aplican correctamente según variante.
- [ ] El componente ocupa el 100% del ancho del contenedor padre.

### Contraejemplos (uso incorrecto)

- Usar `instructionText` con frases largas o instrucciones de múltiples pasos.
- Posicionar el componente en la zona central o superior de la pantalla.
- Usar un ícono que no sea de scan (ej. ícono de cámara genérica, ícono de QR estático sin indicación de acción).
- Usar el Touchless para confirmar acciones de alto riesgo que requieren intención explícita del usuario.

---

## Especificaciones técnicas

| Elemento en Figma | Nombre en código | Tipo | Token resuelto | Notas |
| :--- | :--- | :--- | :--- | :--- |
| Contenedor | container | border-top | `border/width/m` → `2px` | Separador superior del componente |
| Contenedor | container | border-color | `color/border/disabled` → `#dedfed` | |
| Contenedor | container | padding-horizontal | `drawer/structure/spacing/padding` → `64px` | Cuando está dentro de un Drawer |
| Contenedor | container | padding-vertical | `touchless/size/padding-vertical` → `40px` | |
| Scan icon | scan-asset | size | `48×48px` | Ícono animado de escaneo |
| Gap entre icon y texto | gap | spacing | `spacing/2xs` → `24px` | |
| Instruction text | text | font-size | `32px` | `typograph/label/font-size/large` |
| Instruction text | text | line-height | `typograph/label/line-height/large` → `32px` | |
| Instruction text | text | color | `color/text/primary` → `#1c1c2b` | |
| Instruction text | text | letter-spacing | `-0.32px` | |

---

## Accesibilidad

### Roles y etiquetado

El ícono de scan es un elemento decorativo y debe marcarse con `aria-hidden="true"` para que los lectores de pantalla lo ignoren. El texto de instrucción debe ser legible por lectores de pantalla sin necesidad de contexto adicional — por eso debe ser autoexplicativo y concreto.

### Navegación

El componente no recibe foco de teclado por defecto al ser una instrucción visual. Si se añade alguna acción interactiva en su interior, debe ser alcanzable mediante `Tab` y operable con `Enter` o `Space`.

### Interacciones con teclado

| Tecla | Función |
|-------|---------|
| — | Sin interacción de teclado. El componente espera una acción de escaneo físico. |

### Gestos

| Gesto | Función |
|-------|---------|
| Scan (cámara / lector) | Acción principal. Reemplaza el tap como método de interacción. |

### Feedback no visual

El componente no emite feedback propio. El resultado del scan (éxito, error, código no reconocido) es responsabilidad de la pantalla o flujo contenedor, que debe comunicarlo mediante roles `aria-live` o navegación a una nueva vista anunciada por el lector de pantalla.

### Consideraciones de diseño

- El texto de instrucción debe tener contraste suficiente sobre el fondo según WCAG 2.2 AA.
- La animación del ícono de scan debe respetar la preferencia del sistema `prefers-reduced-motion`: en ese caso, mostrar el ícono en estado estático.
- El tamaño del ícono (`48×48px` en Desktop) cumple con los mínimos de área táctil/visual recomendados.
