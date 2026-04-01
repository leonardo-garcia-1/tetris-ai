
# **Flex**

> [!ABSTRACT]
> Flex es un componente estructural de layout que permite componer pantallas dividiendo el espacio disponible en uno, dos o tres slots horizontales intercambiables. Resuelve la necesidad de construir vistas completas de forma modular, insertando cualquier componente en cada slot de forma flexible.

## Permite componer pantallas insertando componentes en cada slot de forma flexible.

![][image111]

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=224-2014) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=5063-49587) |

## **Descripción general**

Flex es un componente estructural de layout que divide el espacio disponible en uno, dos o tres slots horizontales intercambiables. Cada slot acepta cualquier componente como contenido, lo que permite construir vistas completas de forma modular. El componente gestiona automáticamente el espaciado entre slots según el tipo de distribución seleccionado.

### Usos habituales

* Cuando se necesita dividir el contenido de una pantalla en columnas de igual o distinto tamaño  
* Para componer vistas con múltiples áreas de contenido independiente  
* Para prototipar layouts antes de definir el contenido final de cada sección

## **Anatomía**

El componente de Flex no posee anatomía, ya que se adapta a los espacios en los que esté contenido y al componente seleccionado por el usuario.  
   

## **Variantes** 

![][image112]

### 1 Slot

Un único slot que ocupa todo el ancho del contenedor. Sin gap lateral. Ideal para contenido que requiere máximo espacio horizontal.

### 2 Slots

Dos slots de igual tamaño.

### 3 Slots

Tres slots de igual tamaño. Distribución simétrica 33/33/33.

### 1 slot / 2 slots

Distribución asimétrica: slot izquierdo más amplio (sin restricción de ancho) y slot derecho más estrecho.

### 2 slots / 1 slot

Distribución asimétrica inversa: slot izquierdo más estrecho y slot derecho más amplio.

## **Ejemplos**

Flex es un componente estructural: su función es distribuir el espacio en slots, no mostrar contenido propio. Los ejemplos son infinitos porque dependen de qué componentes se insertan en cada slot. En lugar de ejemplos fijos, se describen los patrones de uso más habituales:

- **1 slot:** contenido que necesita el ancho completo de la pantalla. Ej: Product card, Slot map, System state.
- **2 slots:** dos áreas de igual peso visual. Ej: Product card a la izquierda + Highlight a la derecha.
- **3 slots:** tres áreas de igual tamaño. Ej: tres contadores o tres indicadores de estado en paralelo.
- **1 slot / 2 slots (asimétrico):** área principal a la izquierda con información secundaria compacta a la derecha. Ej: descripción del producto + cantidad.
- **2 slots / 1 slot (asimétrico inverso):** inverso del anterior. Ej: imagen del producto + datos de identificación.

---

## **Recomendaciones**

**✓ Do:** Ordenar la historia de los slots y su información/componentes de izquierda a derecha.

\! **Attention:** En caso de traer componentes externos a los predefinidos, asegurar que se utilicen las definiciones y tokens propios de Tetris.

✗ **Don’t:** No modificar tamaños de ancho, alto o propiedades de los marcos (Fill, Hug, etc.)

---

## Especificaciones técnicas

Flex es un componente puramente estructural. No define colores, tipografías ni bordes propios — hereda todo de los componentes que se insertan en sus slots. Los únicos valores que define son los de layout:

| Elemento en Figma | Nombre en código | Tipo | Token resuelto | Notas |
| :--- | :--- | :--- | :--- | :--- |
| Gap entre slots | gap | spacing | `spacing/gap/m` → `24px` | Aplica entre slots en variantes de 2 y 3 slots |
| Slot (fondo placeholder) | slot-bg | color | `color/surface/secondary` → `#ededf7` | Solo en diseño/prototipo. En producción el slot no tiene fondo propio |
| Contenedor | flex | layout | `flex: 1 0 0` | Cada slot crece para ocupar el espacio disponible en distribución simétrica |

---

## **Accesibilidad**

Flex es un componente estructural de layout sin semántica propia. No tiene rol, no recibe foco y no es anunciado por lectores de pantalla. La accesibilidad es responsabilidad de los componentes que se insertan en cada slot.

### Roles y etiquetado

El contenedor Flex no requiere rol ni `aria-label`. Cada componente insertado en sus slots es responsable de exponer su propia semántica accesible.

### Navegación

El foco y la navegación siguen el orden de lectura de los componentes insertados: de izquierda a derecha y de arriba hacia abajo, respetando el orden visual de los slots.

#### Teclado

| Tecla | Detalle |
| :---- | :---- |
| — | Flex no recibe foco. La navegación opera a nivel de los componentes dentro de cada slot. |

#### Gestos

| Gestos | Detalle |
| :---- | :---- |
| — | Flex no responde a gestos directos. Los gestos son gestionados por los componentes internos. |

