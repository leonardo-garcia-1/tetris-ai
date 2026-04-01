<!--
nombre: Icon
owner: Tetris
madurez: stable
aliases: —
fecha-revisión: 2026-03-31
figma-library: https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=2769-11284
figma-specs: —
-->

# Icon

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=2769-11284) |

> [!ABSTRACT]
> Wrapper de tamaño que estandariza la escala de los íconos del sistema. Define el contenedor; el ícono final proviene de la librería de assets de Tetris.

---

## Descripción general

Icon es un componente estructural que no dibuja un ícono por sí mismo: define el tamaño del contenedor y recibe el ícono como slot intercambiable. Los íconos reales viven en una librería de assets separada (Tetris Icons) y se insertan dentro de este componente.

El sistema ofrece 7 tamaños fijos que cubren todos los contextos de uso, desde íconos inline en texto (2XS = 24px) hasta íconos ilustrativos de gran escala (2XL = 160px).

### Usos habituales

- Para insertar cualquier ícono de la librería Tetris con el tamaño correcto del sistema.
- Como contenedor estandarizado dentro de otros componentes que necesitan un ícono (Button icon, List, Badge, Content).
- Para íconos ilustrativos de gran escala en pantallas de estado o instrucción (tamaños L, XL, 2XL).

### Cuándo elegir otra opción

- Si necesitás un botón con ícono, usá [Button icon](#) — ya incluye el contenedor, los estados interactivos y la accesibilidad.
- Si el ícono es parte de un componente existente (Badge, List, Content), usalo dentro de ese componente directamente sin envolver con Icon adicional.

---

## Anatomía

1. **Container:** contenedor cuadrado con radio de borde circular (`border/radius/circle` = 9999px). Define el área del ícono.
2. **Icon (slot):** ícono insertado desde la librería de assets de Tetris. En diseño, si no se asigna un ícono, el componente muestra un Placeholder Image como referencia visual — el Placeholder no debe usarse en producción.

---

## Variantes

El Icon tiene 7 tamaños. El contenedor y el ícono interno siempre tienen el mismo tamaño.

| Tamaño | Dimensión | Uso típico |
| :----- | :-------- | :--------- |
| `2XS` | 24×24px | Íconos inline, contextos muy compactos |
| `XS` | 32×32px | Íconos en componentes compactos (Badge) |
| `S` | 48×48px | Íconos en botones y listas (Button icon, List) |
| `M` | 64×64px | Íconos de soporte en contenido secundario |
| `L` | 80×80px | Íconos ilustrativos en drawers o cards |
| `XL` | 120×120px | Íconos ilustrativos en pantallas de estado |
| `2XL` | 160×160px | Íconos ilustrativos de máximo peso visual |

---

## Propiedades

### Size

Única propiedad del componente. Define el tamaño del container y del ícono interno. Default: `2XS`.

### Icon (slot)

El ícono a mostrar, insertado desde la librería Tetris Icons. Si no se provee, el componente muestra un Placeholder Image en diseño.

---

## Comportamiento

- El componente no tiene estados interactivos propios. Los estados de interacción (Hover, Pressed, Disabled) son responsabilidad del componente contenedor.
- El container siempre es cuadrado. El ícono interno ocupa el 100% del container.
- El color del ícono se controla mediante el token `color/icon/primary` (`#2f2f46`) por defecto, y puede ser sobreescrito por el componente contenedor según contexto.
- Los íconos disponibles están definidos en la librería Tetris Icons. `[ABIERTO]` — agregar link cuando esté disponible.

---

## Ejemplos

Icon es un contenedor: su apariencia final depende del ícono que se inserta. Los ejemplos significativos viven en los componentes que lo usan (Button icon, List, Content, Badge). En todos los casos, la elección del tamaño sigue la tabla de variantes: el contexto de uso determina el tamaño correcto.

---

## Recomendaciones

**✓ Do:** Usar siempre íconos de la librería Tetris Icons. No importar íconos externos sin coordinarlo con el equipo Tetris.

**✓ Do:** Elegir el tamaño según el contexto de uso. Para acciones compactas usar `S` o `XS`; para ilustraciones en pantallas de estado usar `L`, `XL` o `2XL`.

✗ **Don't:** No usar el Placeholder Image en producción. Es solo una referencia visual para diseño.

✗ **Don't:** No redimensionar el container manualmente. El tamaño siempre debe venir de las variantes del sistema.

---

## Componentes relacionados

- **Button icon** — usa Icon internamente para mostrar la acción.
- **List** — usa Icon en sus variantes con ícono lateral.
- **Content** — usa Icon como elemento ilustrativo en variantes Instruction y Scan.
- **Badge** — usa Icon en su variante de solo ícono.

---

## Accesibilidad

### Roles y etiquetado

Icon es decorativo por defecto. En todos los casos donde esté acompañado de texto que describa su función, debe marcarse con `aria-hidden="true"`.

Si se usa de forma aislada (sin texto visible que lo describa), el componente contenedor debe proveer un `aria-label` descriptivo. Icon no gestiona etiquetas accesibles por sí mismo.

### Navegación

Icon no recibe foco de teclado ni responde a gestos directos. No es interactivo.

#### Teclado

| Tecla | Detalle |
| :---- | :------ |
| — | Icon no recibe foco por teclado. |

#### Gestos

| Gesto | Detalle |
| :---- | :------ |
| — | Icon no responde a gestos directos. |

### Consideraciones de diseño

- Asegurar que el ícono elegido sea semánticamente coherente con la acción o contenido que representa.
- En contextos de solo ícono (sin texto), siempre coordinar con el componente contenedor para que provea el `aria-label` correspondiente.

---

## Especificaciones técnicas

| Elemento en Figma | Nombre en código | Tipo | Token resuelto | Notas |
| :---------------- | :--------------- | :--- | :------------- | :---- |
| Container / border-radius | border-radius | dimension | `border/radius/circle` → 9999px | Container circular |
| Icon color (default) | color | color | `color/icon/primary` → `#2f2f46` | — |
| Size 2XS | width / height | dimension | — → 24×24px | Default |
| Size XS | width / height | dimension | — → 32×32px | — |
| Size S | width / height | dimension | — → 48×48px | — |
| Size M | width / height | dimension | — → 64×64px | — |
| Size L | width / height | dimension | — → 80×80px | — |
| Size XL | width / height | dimension | — → 120×120px | — |
| Size 2XL | width / height | dimension | — → 160×160px | — |

---

## API del componente

### Props

| Prop | Tipo | Default | Requerido | Descripción |
| :--- | :--- | :------ | :-------- | :---------- |
| `size` | `"2XS" \| "XS" \| "S" \| "M" \| "L" \| "XL" \| "2XL"` | `"2XS"` | No | Tamaño del container y del ícono interno |
| `icon` | `ReactNode` | `null` | No | Ícono a mostrar. Si es null, muestra Placeholder Image en diseño |

### Estado de implementación

| Plataforma | Estado | Notas |
| :--------- | :----- | :---- |
| iOS | `[ABIERTO]` | — |
| Android | `[ABIERTO]` | — |

---

## Decisiones de diseño

- **El componente solo define el tamaño, no el ícono:** los íconos viven en una librería de assets separada. Esto permite actualizar el set de íconos sin tocar el componente. `[HECHO]`
- **Set de íconos disponibles:** documentado en la librería Tetris Icons. `[ABIERTO]` — agregar link cuando esté disponible.
