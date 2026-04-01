
# **Counter**

> [!ABSTRACT]
> El Counter es un componente utilizado para indicar cantidades o información específica destacable, mostrando una cantidad numérica asociada a un elemento del sistema con alta legibilidad y jerarquía. Resuelve la necesidad de comunicar unidades parciales o totales en flujos operativos como packing o picking.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=7320-1749) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=5-344) |

## El counter es un componente utilizado para indicar cantidades o información específica destacable.

![][image79]

## **Descripción general**

Es un componente que permite mostrar una cantidad numérica asociada a un elemento del sistema. Se utiliza para indicar unidades parciales o totales. Prioriza claridad visual, alta legibilidad y jerarquía.

### Usos habituales

* Para indicar la cantidad de unidades escaneadas dentro de una tarea o flujo sistémico operativo (totes, cajas, productos, etc.)

## **Anatomía**

**![][image80]**

**1\. Label**  
**2\. Value**  
**3\. Total value** (Opcional)

**Devices**

![][image81]

### Desktop

Muestra una jerarquía destacable para pantallas grandes.

### Handheld

Indica una cantidad parcial o total en el tercio inferior de la pantalla.

## **Ejemplos** 

**Packing**

![][image82]

## **Recomendaciones**

![][image83]   ![][image84]

**✓ Do:** Usar counter para elementos de escaneo rápido. Ej. unidades, posiciones.

✗ **Don’t:** No usar counter para otro parámetro que no sea unidad, puede generar confusión.

![][image85]    ![][image86]

✗ **Don’t:** Evitar palabras largas, el componente debe ser un destacado para algo relacionado con un máximo de 4 caracteres.

✗ **Don’t:** No modificar los tamaños de encabezados preestablecidos ni los colores.

![][image87]

✗ **Don’t:** No usar para información que no sea numérica.

## **Accesibilidad**

Esta sección incluye solo las consideraciones esenciales de accesibilidad que están implementadas en los componentes de Tetris, como por ejemplo el uso de roles y etiquetas que facilitan comprender el propósito de los componentes cuando son interpretados por lectores de pantalla, así como la navegación por teclas o gestos que garantizan una interacción inclusiva. 

Para conocer más en detalle sobre tecnologías asistivas, te recomendamos visitar la [guia de accesibilidad digital.](https://sites.google.com/mercadolibre.com/accesibilidad-digital/tecnolog%C3%ADas-asistivas)

Para saber más sobre cómo hacer un hand off accesible te recomendamos visitar la documentación de [Accesibility notes.](https://andes.mercadolibre.com/924dc6ec5/p/770b77-accessibility-notes) 

### Roles y etiquetado

![][image88]

#### Teclado

| Tecla | Detalle |
| :---- | :---- |
| Tab | Ej: Permite alcanzar el componente y ponerlo en foco |

