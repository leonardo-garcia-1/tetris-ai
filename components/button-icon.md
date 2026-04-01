
# **Button icon**

> [!ABSTRACT]
> El Button icon es un botón que contiene únicamente un ícono, sin texto visible, diseñado para ejecutar acciones rápidas y sencillas con un solo toque optimizando el espacio en pantalla. Está pensado para acciones secundarias o utilitarias como editar, cerrar, agregar o abrir un menú contextual.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=7501-2614) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=1378-8847) |

## Permiten ejecutar acciones rápidas y sencillas con un solo toque, optimizando el espacio en pantalla.

![][image42]

## **Descripción general**

El **Button icon** es un botón que contiene únicamente un ícono, sin texto visible. Está diseñado para ejecutar acciones puntuales en interfaces con espacio reducido, donde un botón con etiqueta sería demasiado grande o visualmente pesado.

Es un componente de acción terciaria, ideal para acciones secundarias o utilitarias como editar, cerrar, agregar o abrir un menú contextual.

### Usos habituales

* Acciones de edición rápida (editar, eliminar, duplicar)  
* Botón para abrir menús contextuales o desplegables  
* Acciones de cierre o descarte  
* Controles de toolbar o barras de acción compactas


### Cuándo elegir otra opción

* Si la acción necesita ser explícita para el usuario ([Button]() con texto)  
* Si se requiere jerarquía visual clara entre acciones ([Button]() primary / secondary)

## **Anatomía**

*![][image43]*

**1\. Container:** Contenedor principal del botón.  
**2\. Icon:** Ícono perteneciente a la lib de Tetris.                                                                                                                                        

## **Propiedades**

### Sizes

Button icon cuenta con 2 tamaños:

* **Compact**: Menor tamaño, ideal para áreas con poco espacio.

* **Full-width**: Mayor tamaño o área de interacción. Máx. 2 buttons por linea.

![][image44]

### Hierarchy

La jerarquía determina el peso visual del Button en relación con su entorno y ayuda a guiar la atención de la persona usuaria según la prioridad de la acción. Este sistema ofrece tres niveles:

* **Loud**: máximo peso visual. Se utiliza para acciones principales.

* **Quiet**: menor contraste y énfasis. Apropiado para acciones secundarias que deben estar disponibles sin competir visualmente.

![][image45]

### 

### States

Los estados ofrecen retroalimentación sobre disponibilidad e interactividad.

**Loud**

*![][image46]*

| Estado | Detalle |
| :---- | :---- |
| 1\. Idle | Estado predeterminado del componente sin interacción del usuario. Representa su apariencia por defecto. |
| 2\. Pressed | Indica cuando el componente está siendo presionado por el usuario. |
| 3\. Active | Aparece mientras el usuario hace click o tap sobre el componente. Refuerza que la acción fue reconocida mediante un cambio visual más notorio que Hover. |
| 4\. Loading | Este estado indica que una operación está en curso pero su duración o progreso no pueden estimarse. A diferencia del estado determinate, este se comunica mediante una animación continua o cíclica, sin indicar porcentaje de avance. |
| 5\. Disabled | Indica que el componente no está disponible. No responde a interacción y presenta un contraste reducido para señalar su inactividad. |

**Quiet**

**![][image47]**

| Estado | Detalle |
| :---- | :---- |
| 1\. Idle | Estado predeterminado del componente sin interacción del usuario. Representa su apariencia por defecto. |
| 2\. Pressed | Indica cuando el componente está siendo presionado por el usuario. |
| 3\. Active | Aparece mientras el usuario hace click o tap sobre el componente. Refuerza que la acción fue reconocida mediante un cambio visual más notorio que Hover. |
| 4\. Loading | Este estado indica que una operación está en curso pero su duración o progreso no pueden estimarse. A diferencia del estado determinate, este se comunica mediante una animación continua o cíclica, sin indicar porcentaje de avance. |
| 5\. Disabled | Indica que el componente no está disponible. No responde a interacción y presenta un contraste reducido para señalar su inactividad. |

## **Ejemplos**

### Zoom sobre imagen de producto

![][example-zoom]

El Button icon con ícono de zoom se posiciona en la esquina superior derecha del contenedor de imagen de la Product card en Handheld. Al accionarlo, abre el Carousel dentro de un Drawer para que el operario pueda ver las imágenes del producto en detalle.

### Cierre de Drawer

![][example-close]

El Button icon con ícono de cierre (×) aparece en el header del Drawer para que el usuario pueda cerrar el panel y volver al flujo anterior sin ejecutar ninguna acción. Es el mecanismo de salida principal en todos los Drawers del sistema.

## **Recomendaciones**

![][image7]     ![][image8]

**✓ Do:** Usar los íconos disponibles en la librería de Tetris. En caso de requerir uno nuevo, notificar al equipo de Tetris.

**✓ Do:** Usar este botón en interfaces donde los usuarios ya conocen la función del ícono. Asegurar que el ícono sea semánticamente coherente con la acción.

✗ **Don’t:** No usar íconos sin una acción claramente asociada.

## **Accesibilidad**

Esta sección incluye solo las consideraciones esenciales de accesibilidad que están implementadas en los componentes de Tetris, como por ejemplo el uso de roles y etiquetas que facilitan comprender el propósito de los componentes cuando son interpretados por lectores de pantalla, así como la navegación por teclas o gestos que garantizan una interacción inclusiva. 

Para conocer más en detalle sobre tecnologías asistivas, te recomendamos visitar la [guia de accesibilidad digital.](https://sites.google.com/mercadolibre.com/accesibilidad-digital/tecnolog%C3%ADas-asistivas)

Para saber más sobre cómo hacer un hand off accesible te recomendamos visitar la documentación de [Accesibility notes.](https://andes.mercadolibre.com/924dc6ec5/p/770b77-accessibility-notes) 

### Roles y etiquetado

El Button icon tiene `role="button"`. Como no contiene texto visible, debe incluir siempre un `aria-label` que describa la acción que ejecuta (ej. `aria-label="Cerrar"`, `aria-label="Editar"`, `aria-label="Abrir menú"`). El ícono interno es decorativo y debe marcarse con `aria-hidden="true"`.

En estado Disabled, el botón debe tener `aria-disabled="true"` y no recibir foco.

### Navegación

La navegación sigue el orden de lectura de izquierda a derecha y de arriba hacia abajo.

#### Teclado

| Tecla | Detalle |
| :---- | :---- |
| Tab | Permite alcanzar el componente y ponerlo en foco |
| Space / Enter | Acciona el botón ejecutando la acción asociada |

#### Gestos

| Gestos | Detalle |
| :---- | :---- |
| Tap | Acciona el botón ejecutando la acción asociada |

