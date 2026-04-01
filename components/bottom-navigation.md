
# **Bottom navigation**

> [!ABSTRACT]
> El Bottom navigation presenta acciones fijas que acompañan a flujos Desktop o Tablet, mostrando las acciones principales siempre visibles durante la tarea del usuario. Resuelve la necesidad de acceso rápido a acciones clave sin interrumpir el flujo operativo.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=234-3725) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=5-340) |

## Este componente presenta acciones fijas que acompañan a flujos Desktop o Tablet.

![][image22]

## **Descripción general**

El bottom navigation es exclusivo para devices Desktop y optimizado para pantallas touch. Muestra acciones principales que siempre quedan fijas durante el flujo o tarea a realizar por la persona usuaria.

### Usos habituales

* Por ejemplo, para realizar la acción de revisar la orden anterior, para reportar un problema, para digitar un código de manera manual y no mediante un scan, entre otras.  
* Si la cantidad de acciones no entra dentro del máximo permitido (3 botones), el tercer botón servirá como “Más acciones” para abrir un drawer que contenga la totalidad de acciones disponibles (las que no aparezcan en el bottom nav no serán consideradas como principales, sino secundarias).

## **Anatomía**

*![][image23]*

**A. Button navigation**  
1\. Container  
2\. Icon  
3\. Label  
4\. Badge (Optional)

**B. Button icon**  
1\. Container  
2\. Icon

## **Propiedades**

**States**  
Los botones del componente de Bottom navigation tiene distintos estados de interacción que reflejan tanto su disponibilidad como su comportamiento dentro de la interfaz.

**![][image24]**

### 

| Estado | Detalle |
| :---- | :---- |
| 1\. [Idle](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?node-id=234-3592&t=xaVIDrvJCzfZ5K10-4) | El componente está en reposo, sin interacción ni foco. |
| 2\. [Pressed](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?node-id=679-12850&t=xaVIDrvJCzfZ5K10-4) | Se activa todo el tiempo que el usuario clickee o tapee sobre el área del botón. |
| 3\. [Disabled](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?node-id=234-3625&t=xaVIDrvJCzfZ5K10-4) | El componente no es interactivo ni recibe foco. Se recomienda usarlo solo cuando la acción no está disponible para la persona usuaria y debe entenderse como tal. |

###  

## **Recomendaciones**

![][image25]       ![][image26]

**✓ Do:** Reforzar la acción del botón con iconos y mantener la cantidad propuesta.

✗ **Don’t:** No utilizar íconos que generen confusión o conflicto con la acción a realizar, ni alterar el orden de lectura de los botones.

![][image27]       ![][image28]

**✓ Do:** Si hay menos de 3 acciones, utilizar los botones que no tengan acción en disabled, manteniendo los anchos predefinidos.

✗ **Don’t:** No eliminar ni añadir botones. Mantener la cantidad definida por el componente.

## **Accesibilidad**

Esta sección incluye solo las consideraciones esenciales de accesibilidad que están implementadas en los componentes de Andes, como por ejemplo el uso de roles y etiquetas que facilitan comprender el propósito de los componentes cuando son interpretados por lectores de pantalla, así como la navegación por teclas o gestos que garantizan una interacción inclusiva. 

Para conocer más en detalle sobre tecnologías asistivas, te recomendamos visitar la [guia de accesibilidad digital.](https://sites.google.com/mercadolibre.com/accesibilidad-digital/tecnolog%C3%ADas-asistivas)

Para saber más sobre como hacer un hand off accesible te recomendamos visitar la documentación de [Accesibility notes.](https://andes.mercadolibre.com/924dc6ec5/p/770b77-accessibility-notes) 

### Roles y etiquetado

El **Bottom navigation** tiene botones en fila posicionados debajo del container principal de un flujo Desktop o Tablet y presenta un máximo de 3 acciones principales.  
Los lectores de pantalla anuncian la **etiqueta** del componente y su **estado** actual.  
En **Tetris**, se anuncian las etiquetas pertinentes de los botones que presentan acciones del flujo, siempre siendo el último botón el de “Salir de flujo”,  permitiendo que las tecnologías de asistencia lean el texto junto con la función del control.

![][image29]

### Navegación

La navegación de las interfaces por medio de tecnologías asistidas, se realizan de manera convencional en todos los casos, siguiendo un orden de lectura de izquierda a derecha y de arriba hacia abajo, ya sea que se navegue mediante gestos (para mobile) o mediante teclado (para desktop).

![][image30]

#### Teclado

| Tecla | Detalle |
| :---- | :---- |
| Tab | Permite alcanzar el componente y ponerlo en foco. También permite avanzar entre los botones del Bottom Navigation. |
| Shift \+ Tab | Permite navegar en dirección contraria a la que se navega solo con tab. |
| Space (x2) | Permite accionar el componente. |

