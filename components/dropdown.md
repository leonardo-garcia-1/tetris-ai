
# **Dropdown**

> [!ABSTRACT]
> El Dropdown es un campo de entrada que permite al usuario desplegar una lista de opciones y seleccionar una. Resuelve la necesidad de capturar una selección de un conjunto de opciones predefinidas cuando el espacio es limitado y no conviene mostrar todas las opciones a la vez.

## Campo de entrada que permite al usuario desplegar opciones y seleccionar.

![][image105]

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=15679-938) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=5063-49586) |

## **Descripción general**

El Dropdown es un campo de entrada que, al interactuar con él, despliega una lista de opciones para que el usuario seleccione una. Combina un campo visible con un menú flotante (menu list) que puede ser scrollable o de altura fija, y soporta agrupación de opciones mediante títulos de sección.

### Usos habituales

* Cuando se necesita que el usuario seleccione una opción de una lista predefinida  
* Para formularios donde el espacio es limitado y no es conveniente mostrar todas las opciones a la vez


### Cuándo elegir otra opción

* Usar [Textfield]() cuando el usuario necesita ingresar texto libre en lugar de seleccionar de una lista

## **Anatomía**

*![][image106]*

**Dropdown**  
**1\. Label:** etiqueta descriptiva del campo. Máximo 1 línea.  
**2\. Placeholder / Input text:** texto de ayuda cuando no hay selección, o texto de la opción seleccionada cuando el estado es Filled.  
**3\. Chevron:** ícono indicador de acción desplegable. Rota 180° cuando el menú está abierto.  
**4\. Menu list:** contenedor flotante que aparece al activar el dropdown. Puede ser scrollable o non-scrollable.  
**5\. Title list (opcional):** encabezado de grupo dentro del menu list para categorizar opciones.  
**6\. Options:** ítems seleccionables dentro del menu list.  
**7\. Scroll bar:** barra de scroll visible cuando el menu list es scrollable y el contenido excede la altura visible.  
**8\. Groups:** separadores visuales que dividen las opciones en grupos temáticos dentro del menu list.   

                                                                                                                                      

## **Variantes**

![][image107]

### Scrollable

El menu list tiene scroll vertical cuando la cantidad de opciones excede el espacio visible. Se muestra una barra de scroll y un gradiente inferior indicando que hay más contenido.

### Non-scrolleable

El menu list muestra todas las opciones sin scroll. Adecuado cuando la lista es corta y cabe completamente en el espacio disponible.

## **Propiedades**  States 

![][image108]

| Estado | Detalle |
| :---- | :---- |
| 1\. Unselected | Apariencia por defecto sin interacción. |
| 2\. Pressed | Feedback visual al contacto del cursor/tap. |
| 3\. Active | El menú está desplegado. |
| 4\. Filled | Una opción ha sido seleccionada. |
| 5\. Disabled | Componente no disponible. |

## 

## Item states 

### ![][image109]

| Estado | Detalle |
| :---- | :---- |
| 1\. Idle | Apariencia por defecto sin interacción. |
| 2\. Hover | Cursor sobre el ítem. |
| 3\. Selected | Opción actualmente seleccionada. |
| 4\. Disabled | Componente no disponible. |

## 

## **Comportamiento**

Cuando excede el espacio visible dentro del menu, o para reducir el tamaño del mismo, se puede desplazar el contenido horizontalmente.

### ![][image110]

## **Ejemplos**

### Selección de motivo en formulario de reporte

![][example-report]

En una pantalla de reporte de problema, el Dropdown permite al operario seleccionar el motivo de la incidencia de una lista predefinida (ej. "Producto dañado", "Código incorrecto", "Unidades incorrectas"). La variante Scrollable se usa cuando la lista de motivos supera el espacio visible. Al seleccionar una opción, el campo pasa al estado Filled mostrando el valor elegido.

## **Recomendaciones**     

**✓ Do:** Utilizar alguna regla de orden lógico para facilitar la búsqueda. Puede ser orden alfabético, cronológico o de prioridad/similitud.

**✓ Do:** Usar para listas cortas y conocidas evitando demasiado scroll. Y agrupar por categorías para facilitar la búsqueda.

✗ **Don’t:** No usar Dropdown con listas largas sin orden aparente y difícil lectura. No cambiar el tamaño máximo del componente.

## Especificaciones técnicas

| Elemento en Figma | Nombre en código | Tipo | Token resuelto | Notas |
| :--- | :--- | :--- | :--- | :--- |
| Contenedor del campo | container | border | `border/width/l` → `3px` (active) / `border/width/m` → `2px` (default) | Borde azul en estado Active |
| Contenedor del campo | container | border-color | `color/interactive/border/active` → `#4850e5` (active) / `color/interactive/border/default` → `#bdbfd6` (default) | |
| Contenedor del campo | container | border-radius | `border/radius/s` → `12px` | |
| Contenedor del campo | container | padding | `spacing/padding/xs` → `24px` | |
| Contenedor del campo | container | height | `96px` fijo | min-height y max-height |
| Placeholder / Input text | text | color | `color/text/placeholder` → `#737396` (vacío) / `color/text/primary` → `#1c1c2b` (filled) / `color/interactive/text/default` → `#4850e5` (selected) / `color/text/disabled` → `#9ca0bf` (disabled) | |
| Placeholder / Input text | text | font-size | `32px` | `typograph/label/font-size/large` |
| Placeholder / Input text | text | line-height | `typograph/label/line-height/large` → `32px` | |
| Label | label | font-size | `28px` | `typograph/label/font-size/medium` |
| Label | label | line-height | `typograph/label/line-height/medium` → `28px` | |
| Label | label | color | `color/text/primary` → `#1c1c2b` | |
| Gap entre label y container | gap | spacing | `dropdown/spacing/gap` → `16px` | |
| Menu list | menu | background | `color/background/primary` → `white` | |
| Menu list | menu | border-radius | `border/radius/m` → `16px` | `list/large/border/radius` |
| Menu list | menu | padding | `dropdown/spacing/padding` → `24px` | |
| Menu list | menu | shadow | `0px 2px 12px 0px rgba(0,0,0,0.14)` | |
| Option item | option | padding-horizontal | `dropdown/spacing/padding-item-list` → `12px` | |
| Option item | option | padding-vertical | `dropdown/spacing/padding` → `24px` | |
| Option item | option | min-height | `96px` | |
| Option item (hover) | option | background | `color/surface/secondary` → `#ededf7` | |
| Option item (selected) | option | background | `color/blue/100` → `#e0e9ff` | |
| Option item (selected) | option | text-color | `color/interactive/text/default` → `#4850e5` | |
| Option item (disabled) | option | text-color | `color/text/disabled` → `#9ca0bf` | |
| Option description | description | font-size | `28px` | |
| Option description | description | line-height | `typograph/body/line-height/medium` → `36px` | |
| Option description | description | color | `color/text/secondary` → `#5a5a7c` | |
| Gap entre líneas de option | between-lines | spacing | `dropdown/spacing/between-lines` → `8px` | |
| Chevron | icon | size | `32×32px` | Rota 180° cuando está abierto |
| Fill disabled | container | background | `color/fill/disabled` → `#dedfed` | Solo estado Disabled |

---

## **Accesibilidad**

Esta sección incluye solo las consideraciones esenciales de accesibilidad que están implementadas en los componentes de Tetris, como por ejemplo el uso de roles y etiquetas que facilitan comprender el propósito de los componentes cuando son interpretados por lectores de pantalla, así como la navegación por teclas o gestos que garantizan una interacción inclusiva. 

Para conocer más en detalle sobre tecnologías asistivas, te recomendamos visitar la [guia de accesibilidad digital.](https://sites.google.com/mercadolibre.com/accesibilidad-digital/tecnolog%C3%ADas-asistivas)

Para saber más sobre cómo hacer un hand off accesible te recomendamos visitar la documentación de [Accesibility notes.](https://andes.mercadolibre.com/924dc6ec5/p/770b77-accessibility-notes) 

### Roles y etiquetado

El Dropdown se interpreta como un campo de selección que permite elegir uno o varios valores de una lista desplegable. Debe contar siempre con un label claro que indique su propósito, ya sea visible o únicamente accesible para lectores de pantalla. El input del componente se anuncia como botón y comunica su estado (expandido o colapsado), permitiendo que los usuarios que utilizan tecnologías asistivas comprendan cuándo el menú está abierto o cerrado.

### Navegación

La navegación de las interfaces por medio de tecnologías asistidas, se realizan de manera convencional en todos los casos, siguiendo un orden de lectura de izquierda a derecha y de arriba hacia abajo, ya sea que se navegue mediante gestos (para mobile) o mediante teclado (para desktop).

#### Teclado

| Tecla | Detalle |
| :---- | :---- |
| Tab | Ej: Permite alcanzar el componente y ponerlo en foco |
| Space / Enter | Ej: Permite accionar el componente. |
| Flechas del teclado | Ej: Permite navegación interna entre los elementos del grupo. |

#### Gestos

| Gestos | Detalle |
| :---- | :---- |
| Swipe hacia la derecha | Ej: Permite navegar dentro del elemento/grupo hacia la derecha/izquierda. |
| Swipe hacia la izquierda | Ej: Permite navegar dentro del elemento/grupo hacia atrás. |
| Doble tap | Ej: Permite accionar el componente. |

