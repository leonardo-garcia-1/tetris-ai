
# **Switch**

> [!ABSTRACT]
> El Switch sirve para acompañar una acción o estado, dando la posibilidad de escoger entre prendido y apagado mediante un control deslizante. Resuelve la necesidad de alternar entre dos estados excluyentes de forma inmediata, sin confirmación adicional por parte del usuario.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=19230-1550) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=2642-960) |

## Este componente sirve para acompañar una acción o estado, dando la posibilidad de escoger entre prendido y apagado.

![][image199]

## **Descripción general**

El Switch se presenta como un control deslizante que cambia entre “activado” y “desactivado”.

Es ideal para situaciones donde la acción debe reflejarse de manera instantánea, sin confirmación adicional por parte de la persona usuaria. Ejemplos comunes incluyen encender o apagar el modo oscuro, habilitar o deshabilitar el sonido, o activar las notificaciones push.

A diferencia de Checkbox o Radio Button, el Switch siempre implica un cambio instantáneo en el sistema, por lo que su uso se limita a interacciones que no requieren validación posterior.

### Usos habituales

* Cuando la selección tenga un efecto inmediato en la interfaz.  
* Para alternar entre dos estados excluyentes, como encendido/apagado, mostrar/ocultar.   
* En configuraciones o preferencias donde no se requiere confirmación adicional.

## **Anatomía**

*![][image200]*

**1\. Label** (Opcional)  
**2\. Switch**                                                                                                                                          

## **Propiedades**

**States**  
El Switch tiene distintos estados de interacción que reflejan tanto su disponibilidad como su comportamiento dentro de la interfaz.

### **Selected states**  ![][image201]

**Unselected states**

### ![][image202]

### 

| Estado | Detalle |
| :---- | :---- |
| 1\. Idle | El componente está en reposo, sin interacción ni foco. |
| 2\. Pressed | Se activa todo el tiempo que el usuario clickee o tapee sobre el área del Switch. |
| 3\. Disabled | El componente no es interactivo ni recibe foco. Se recomienda usarlo solo cuando la acción no está disponible para la persona usuaria y debe entenderse como tal. |

### 

### **Label**

Texto que acompaña al Switch y describe su funcionalidad. Aunque puede ser opcional, por accesibilidad se recomienda siempre incluirlo

### ![][image203]  

## **Recomendaciones**

![][image204]     ![][image205]

**✓ Do:** Usar el Switch para acciones binarias, activar o desactivar una configuración específica. Con etiquetas claras, sintéticas y descriptivas.

✗ **Don’t:** No usar el Switch para acciones irreversibles o críticas.

![][image206]     ![][image207]

**✓ Do:** Usar frases cortas, que no ocupen más de dos líneas

✗ **Don’t:** No usar textos largos ni redundantes.

![][image208]     ![][image209]

**✓ Do:** Usar sobre fondo blanco.

✗ **Don’t:** No usar fondos diferentes al blanco, que dificulten el contraste.

![][image210]     ![][image211]

✗ **Don’t:** No modifica estructura, colores ni ícono.

✗ **Don’t:** No usar en reemplazo de checkboxes.

## **Accesibilidad**

Esta sección incluye solo las consideraciones esenciales de accesibilidad que están implementadas en los componentes de Andes, como por ejemplo el uso de roles y etiquetas que facilitan comprender el propósito de los componentes cuando son interpretados por lectores de pantalla, así como la navegación por teclas o gestos que garantizan una interacción inclusiva. 

Para conocer más en detalle sobre tecnologías asistivas, te recomendamos visitar la [guia de accesibilidad digital.](https://sites.google.com/mercadolibre.com/accesibilidad-digital/tecnolog%C3%ADas-asistivas)

Para saber más sobre como hacer un hand off accesible te recomendamos visitar la documentación de [Accesibility notes.](https://andes.mercadolibre.com/924dc6ec5/p/770b77-accessibility-notes) 

### Roles y etiquetado

El **Switch** es un control de dos estados: activado (on) y desactivado (off).  
Los lectores de pantalla anuncian la **etiqueta** del componente, el **rol** “switch” y su **estado** actual.  
En **Tetris**, tanto los Switches con etiqueta visible como aquellos con etiqueta oculta exponen esa misma etiqueta como **nombre accesible**, permitiendo que las tecnologías de asistencia lean el texto junto con la función del control.

![][image212]

### Navegación

La navegación de las interfaces por medio de tecnologías asistidas, se realizan de manera convencional en todos los casos, siguiendo un orden de lectura de izquierda a derecha y de arriba hacia abajo, ya sea que se navegue mediante gestos (para mobile) o mediante teclado (para desktop).

#### Teclado

| Tecla | Detalle |
| :---- | :---- |
| Tab | Permite alcanzar el componente y ponerlo en foco |
| Shift \+ Tab | Permite navegar en dirección contraria a la que se navega solo con tab. |
| Space  | Permite accionar el componente. |

#### Gestos

| Gestos | Detalle |
| :---- | :---- |
| Swipe hacia la derecha | Permite navegar entre Switches o dentro de un grupo hacia la derecha. |
| Swipe hacia la izquierda | Permite navegar entre Switches o dentro de un grupo hacia la derecha. |
| Doble tap | Ej: Permite accionar el componente. |

![][image213]

### Touch area

Tódos los elementos tapeables deben tener un mínimo de 80px de área para Desktop y 45 para Handheld. El área tapeable ocupará todo el ancho y el alto de los ítems de la lista.

![][image214]

