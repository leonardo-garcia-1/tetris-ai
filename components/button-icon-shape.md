
# **Button icon shape**

> [!ABSTRACT]
> El Button icon shape permite realizar acciones primarias o secundarias en contextos con poco espacio, compuesto internamente por un ícono que representa una acción concreta. Resuelve la necesidad de mostrar acciones de forma compacta cuando el espacio en pantalla es reducido.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=7541-9675) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=1378-8848) |

## Este componente permite realizar acciones primarias o secundarias en contextos con poco espacio.

![][image48]

## **Descripción general**

Es un botón que está compuesto internamente por un icon que representa una acción concreta. 

### Usos habituales

* Para mostrar acciones primarias  en contextos con poco espacio (por ejemplo, salir del flujo en el que se encuentra el usuario, adicionar algún archivo informativo, etc.)   
* Para mostrar acciones secundarias en contexto con poco espacio


### Cuándo elegir otra opción

* Si necesitás representar una acción con texto y de manera menos abstracta que con un ícono, utilizá el Botón común.

## **Anatomía**

*![][image49]*

**1\. Frame:** Container  
**2\. Icon**                                                                                                                                          

### Hierarchy

![][image50]

**Loud**: el mayor nivel de jerarquía. Utiliza el color de acento del sistema y se reserva para la acción principal de la pantalla.

**Quiet**: se utiliza para acciones de importancia intermedia.

### 

### **Sizes**

El componente cuenta con 2 tamaños.

![][image51]

**Compact**  
Menor tamaño, ideal para áreas con poco espacio.

**Full-width**  
Mayor tamaño o área de interacción. Máx. 2 Buttons por linea.

### **States**

Permiten identificar qué tipo de interacciones ofrece el Button icon shape en un determinado momento.

**Loud**  
Usados en contextos de mayor relevancia.

### ![][image52]

| Estado | Detalle |
| :---- | :---- |
| 1\. Idle | Estado predeterminado del componente sin interacción del usuario. Representa su apariencia por defecto. |
| 2\. Pressed | Se activa todo el tiempo que el usuario clickee o tapee sobre el área del Button icon shape. |
| 3\. Active | Se muestra luego de que el usuario hace click o tap sobre el componente. Refuerza que la acción fue reconocida mediante un cambio visual más notorio. |
| 4\. Loading | Aparece un indicador de carga (spinner) dentro del campo mientras finaliza una acción en segundo plano. Este estado se activa, por ejemplo, al validar datos contra un servicio externo. |
| 5\. Disabled | Indica que el componente no está disponible. No responde a interacción y presenta un contraste reducido para señalar su inactividad. |

**Quiet**  
Usados en contextos de menor relevancia.

### ![][image53]

| Estado | Detalle |
| :---- | :---- |
| 1\. Idle | Estado predeterminado del componente sin interacción del usuario. Representa su apariencia por defecto. |
| 2\. Pressed | Se activa todo el tiempo que el usuario clickee o tapee sobre el área del Button icon shape |
| 3\. Active | Se muestra luego de que el usuario hace click o tap sobre el componente. Refuerza que la acción fue reconocida mediante un cambio visual más notorio. |
| 4\. Loading | Aparece un indicador de carga (spinner) dentro del campo mientras finaliza una acción en segundo plano. Este estado se activa, por ejemplo, al validar datos contra un servicio externo. |
| 5\. Disabled | Indica que el componente no está disponible. No responde a interacción y presenta un contraste reducido para señalar su inactividad. |

## **Recomendaciones**

![][image54]     ![][image55]

**✓ Do:** Usar este botón en interfaces donde los usuarios ya conocen la función del ícono.  
Asegurar que el ícono sea semánticamente coherente con la acción.

✗ **Don’t:** No cambiar el tamaño o estilo arbitrariamente según contexto: mantené consistencia visual.

 \- 

