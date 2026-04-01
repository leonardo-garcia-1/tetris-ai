
# **Button**

> [!ABSTRACT]
> Los botones permiten realizar las acciones principales y secundarias de una pantalla, o en otros componentes como modal y cards. Es el componente principal de acción del sistema: dispara acciones concretas, prioriza tareas, activa procesos y ofrece retroalimentación visual sobre el estado de una acción.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=376-5364) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=5-339) |

## Los botones permiten realizar las acciones principales y secundarias de una pantalla, o en otros componentes como modal y cards.

![][image31]

## **Descripción general**

Es el componente principal de acción. Su función principal es disparar acciones concretas dentro de una interfaz. Ayuda a priorizar tareas, activar procesos y ofrecer retroalimentación visual sobre el estado de una acción.

Se utiliza para facilitar decisiones rápidas y avanzar dentro de una secuencia lógica, capturando la atención de la persona usuaria cuando es necesario.

### Usos habituales

* **Confirmar o enviar datos:** guardar cambios en un formulario, enviar un mensaje, confirmar un pago.  
* **Avanzar en un flujo:** continuar con un registro paso a paso, pasar al siguiente nivel de configuración.  
* **Acción principal en un bloque de contenido:** comprar ahora, suscribirse en una landing.

## **Anatomía**

*![][image32]*

*Los títulos de anatomía en inglés.*

**1\. Container:**  el container define la superficie interactiva del Button, delimitando el área donde la persona usuaria puede hacer clic o tap, y comunica su estado.  
**2\. Label:**  label es el texto del Button y el elemento más importante de su anatomía. Siempre debe ser corto, en verbo y explícito.                                                                                                                                          

## **Propiedades**

### Sizes

Button cuenta con 2 tamaños:

* **Compact**: Menor tamaño, ideal para áreas con poco espacio.

* **Full-width**: Mayor tamaño o área de interacción. Máx. 2 buttons por linea.  
* 

![][image33]

### Hierarchy

La jerarquía determina el peso visual del Button en relación con su entorno y ayuda a guiar la atención de la persona usuaria según la prioridad de la acción. Este sistema ofrece tres niveles:

* **Loud**: máximo peso visual. Se utiliza para acciones principales.

* **Quiet**: menor contraste y énfasis. Apropiado para acciones secundarias que deben estar disponibles sin competir visualmente.

![][image34]

### 

### States

Los estados ofrecen retroalimentación sobre disponibilidad e interactividad.

**Loud**

*![][image35]*

| Estado | Detalle |
| :---- | :---- |
| 1\. Idle | Estado predeterminado del componente sin interacción del usuario. Representa su apariencia por defecto. |
| 2\. Pressed | Indica cuando el componente está siendo presionado por el usuario. |
| 3\. Active | Aparece mientras el usuario hace click o tap sobre el componente. Refuerza que la acción fue reconocida mediante un cambio visual más notorio que Hover. |
| 4\. Loading | Este estado indica que una operación está en curso pero su duración o progreso no pueden estimarse. A diferencia del estado determinate, este se comunica mediante una animación continua o cíclica, sin indicar porcentaje de avance. |
| 5\. Disabled | Indica que el componente no está disponible. No responde a interacción y presenta un contraste reducido para señalar su inactividad. |

**Quiet**

**![][image36]**

| Estado | Detalle |
| :---- | :---- |
| 1\. Idle | Estado predeterminado del componente sin interacción del usuario. Representa su apariencia por defecto. |
| 2\. Pressed | Indica cuando el componente está siendo presionado por el usuario. |
| 3\. Active | Aparece mientras el usuario hace click o tap sobre el componente. Refuerza que la acción fue reconocida mediante un cambio visual más notorio que Hover. |
| 4\. Loading | Este estado indica que una operación está en curso pero su duración o progreso no pueden estimarse. A diferencia del estado determinate, este se comunica mediante una animación continua o cíclica, sin indicar porcentaje de avance. |
| 5\. Disabled | Indica que el componente no está disponible. No responde a interacción y presenta un contraste reducido para señalar su inactividad. |

### Devices

Button está disponible para 2 devices:

* **Desktop**: para pantallas de mayor tamaño.

* **Handheld**: para devices mobile y de pantallas más pequeñas y portables.

## **Ejemplos** 

**Botones full-width primario y secundario dentro de Drawer**

![][image37]

**Botón compact secundario dentro de Drawer**

![][image38]

**Botones primario y secundario en Handheld**

![][image39]

## **Recomendaciones**

     

**✓ Do:** Usar Buttons para acciones directas y claras, escribiendo etiquetas cortas y objetivas.

**✓ Do:** Usar diferentes jerarquías de Buttons en conjunto para diferenciar los tipos de acción.

**✓ Do:** Apilar hasta tres Buttons con una acción primaria y dos acciones secundarias.

✗ **Don’t:** No deshabilitar el botón sin una explicación para el usuario.

**✓ Do:** Al ordenar verticalmente, mantener el ancho y ubicar en la parte inferior de la pantalla.

✗ **Don’t:** No usar dos Buttons juntos con diferente ancho ni desalinear con la parte inferior de la pantalla.

✗ **Don’t:** No cambiar el color o poner el texto en mayúsculas. La etiqueta debe tener solo la primera letra en mayúscula.

✗ **Don’t:** No usar labels grandes sin necesidad.

## **Accesibilidad**

Esta sección incluye solo las consideraciones esenciales de accesibilidad que están implementadas en los componentes de Tetris, como por ejemplo el uso de roles y etiquetas que facilitan comprender el propósito de los componentes cuando son interpretados por lectores de pantalla, así como la navegación por teclas o gestos que garantizan una interacción inclusiva.

Para conocer más en detalle sobre tecnologías asistivas, te recomendamos visitar la [guia de accesibilidad digital.](https://sites.google.com/mercadolibre.com/accesibilidad-digital/tecnolog%C3%ADas-asistivas)

Para saber más sobre cómo hacer un hand off accesible te recomendamos visitar la documentación de [Accesibility notes.](https://andes.mercadolibre.com/924dc6ec5/p/770b77-accessibility-notes)

### Roles y etiquetado

En Tetris, el Button siempre tiene su label visible, por lo que no necesita una etiqueta para nombrarlo.

![][image40]

### Navegación

La navegación de las interfaces por medio de tecnologías asistidas, se realizan de manera convencional en todos los casos, siguiendo un orden de lectura de izquierda a derecha y de arriba hacia abajo, ya sea que se navegue mediante gestos (para mobile) o mediante teclado (para desktop).

#### Teclado

| Tecla | Detalle |
| :---- | :---- |
| Tab | Permite alcanzar el componente y ponerlo en foco |
| Space | Permite accionar el componente. |

#### Gestos

| Gestos | Detalle |
| :---- | :---- |
| Swipe hacia la derecha | Permite navegar dentro de la interfaz, alcanzando el componente y poniéndolo en foco. |
| Swipe hacia la izquierda | Permite navegar hacia atrás en los elementos de la interfaz. |
| Doble tap | Permite accionar el componente. |

![][image41]

