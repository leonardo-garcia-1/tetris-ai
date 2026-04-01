
# **List**

> [!ABSTRACT]
> List organiza ítems en una estructura vertical de filas navegables, donde cada ítem actúa como punto de entrada hacia una sección o acción específica. Resuelve la necesidad de presentar conjuntos de opciones navegables, desde listas simples hasta ítems de producto con imagen, descripción y badges.

## Dispone filas ordenadas verticalmente y permite navegar entre distintas opciones.

![][image141]

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=224-2012) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=5-347) |

## **Descripción general**

List organiza ítems en una estructura vertical de filas navegables. Cada ítem actúa como un punto de entrada hacia una sección o acción específica. El componente se adapta al contexto de dispositivo y a la complejidad del contenido: desde listas simples con etiqueta y chevron hasta ítems con imagen, descripción, badges y contadores.

### Usos habituales

* Cuando se necesita presentar un conjunto de opciones navegables en pantalla completa o dentro de un contenedor  
* Para listar acciones u opciones dentro de un flujo operativo  
* Para mostrar ítems con información secundaria o badges de estado  
* Para exponer listados de productos con código, descripción y cantidades

                                                                                                                                          

## **Variantes**

![][image142]

### List Default Small

Variante compacta para dispositivos móviles. Pensada para listas de navegación simples dentro de flujos operativos en pantalla pequeña. Está compuesta por:

**1\. Icon (Opcional):** representación visual del ítem.  
**2\. Label:** texto principal del ítem. Máximo 1 línea. Se corta con ellipsis cuando supera el ancho disponible.  
**3\. Chevron:** indicador de navegación hacia el detalle.

![][image143]

### List Default Large

Variante compacta para desktop. Estructura simplificada con etiqueta y chevron, sin soporte para ícono o contenido secundario. Está compuesta por:

**1\. Icon (Opcional):** representación visual del ítem. Tamaño de 48×48px. Se ignora en la lectura del lector de pantalla.  
**2\. Label:** texto principal. Máximo 1 línea, con ellipsis.  
**3\. Description (Opcional):** texto secundario. Máximo 1 línea.  
**4\. Badge (Opcional):** indicador de estado. Acepta jerarquías Loud y Quiet con tipos Positive, Caution, Negative e Informative.  
**5\. Action:** acción secundaria dentro del ítem. También puede ser implementado como botón independiente.  
**6\. Chevron:** indicador de navegación.

![][image144]

### List Product Small

Variante especializada para listados de productos en contextos operativos. Es la variante más densa en contenido e incorpora información de stock y múltiples badges.

**1\. Product image:** imagen representativa del producto.  
**2\. Product code:** código identificador de producto. Máximo 2 líneas.  
**3\. Product description:** texto descriptivo del producto.  
**4\. Unit/Counter:** cantidad actual de unidades.  
**5\. Badges (Opcional):** indica las tipologías de producto (frágil, líquido, etc.)  
**6\. Alert (Opcional):** indica que se necesita de atención con el producto que identifica.

![][image145]

### List Product Large

Variante especializada para listados de productos en contextos operativos. Es la variante más densa en contenido e incorpora información de stock y múltiples badges.

**1\. Product image:** imagen representativa del producto.  
**2\. Product code:** código identificador de producto. Máximo 1 línea.  
**3\. Product description:** texto descriptivo del producto.  
**4\. Unit/Counter:** cantidad actual de unidades.  
**5\. Badges (Opcional):** indica las tipologías de producto (frágil, líquido, etc.)

## **Variantes por device**

Todas las variantes antes mencionadas de List tienen su versión Handheld y Desktop.

![][image146]

## **Propiedades**

### State

List Default Small

![][image147]

| Estado | Detalle |
| :---- | :---- |
| 1\. Idle | Estado predeterminado del componente sin interacción del usuario. Representa su apariencia por defecto. |
| 2\. Pressed | Aparece mientras el usuario hace click o tap sobre el componente. Refuerza que la acción fue reconocida mediante un cambio visual más notorio que Hover. |
| 3\. Disabled | Indica que el componente no está disponible. No responde a interacción y presenta un contraste reducido para señalar su inactividad. |

List Default Large

![][image148]

| Estado | Detalle |
| :---- | :---- |
| 1\. Idle | Estado predeterminado del componente sin interacción del usuario. Representa su apariencia por defecto. |
| 2\. Pressed | Aparece mientras el usuario hace click o tap sobre el componente. Refuerza que la acción fue reconocida mediante un cambio visual más notorio que Hover. |
| 3\. Disabled | Indica que el componente no está disponible. No responde a interacción y presenta un contraste reducido para señalar su inactividad. |
| 4\. Urgent | Se activa cuando se quiere llamar la atención del usuario sobre el elemento de la lista. |
| 5\. Placeholder | Indica una acción a realizar para llenar ese espacio con un ítem nuevo de la lista.  |

List Product Large

![][image149]

| Estado | Detalle |
| :---- | :---- |
| 1\. Idle | Estado predeterminado del componente sin interacción del usuario. Representa su apariencia por defecto. |
| 2\. Placeholder | Indica una acción a realizar para llenar ese espacio con un ítem nuevo de la lista.  |

## **Ejemplos** 

**List Small**

![][image150]

**List Large**

![][image151]

**List Product Large**

![][image152]

## **Recomendaciones**

**✓ Do:** Usar texto concreto y de rápida lectura.

**✓ Do:** Utilizar los roles de color con el propósito para el cúal fueron pensados genera una aplicación consistente y familiar.

**✓ Do:** Usar íconos solo si facilita el reconocimiento de la información dentro del ítem de la lista.

✗ **Don’t:** No usar íconos solo en algunos ítems de la lista.

✗ **Don’t:** No usar acciones ambiguas, poco claras o con textos largos.

## **Accesibilidad**

Esta sección incluye solo las consideraciones esenciales de accesibilidad que están implementadas en los componentes de Tetris, como por ejemplo el uso de roles y etiquetas que facilitan comprender el propósito de los componentes cuando son interpretados por lectores de pantalla, así como la navegación por teclas o gestos que garantizan una interacción inclusiva. 

Para conocer más en detalle sobre tecnologías asistivas, te recomendamos visitar la [guia de accesibilidad digital.](https://sites.google.com/mercadolibre.com/accesibilidad-digital/tecnolog%C3%ADas-asistivas)

Para saber más sobre cómo hacer un hand off accesible te recomendamos visitar la documentación de [Accesibility notes.](https://andes.mercadolibre.com/924dc6ec5/p/770b77-accessibility-notes) 

### Roles y etiquetado

Las variantes de **List** están compuestas por distintos componentes y **heredan sus propiedades de accesibilidad**.

Según el tipo de **ListRow**, los ítems serán anunciados por las tecnologías asistivas como **botones** o **enlaces**, de acuerdo con su comportamiento (acción interna → botón; navegación → enlace).

Al utilizar cualquiera de las variantes **full‑slot**, la **definición de roles, estados y etiquetado** (por ejemplo, atributos ARIA) queda a cargo del equipo responsable de la experiencia.

### Navegación

La navegación sigue el orden de lectura de izquierda a derecha y de arriba hacia abajo. Cada ítem de la lista es un elemento focusable independiente.

#### Teclado

| Tecla | Detalle |
| :---- | :---- |
| Tab | Mueve el foco al siguiente ítem de la lista |
| Shift + Tab | Mueve el foco al ítem anterior |
| Space / Enter | Acciona el ítem en foco (navega o ejecuta la acción asociada) |

#### Gestos

| Gestos | Detalle |
| :---- | :---- |
| Tap | Acciona el ítem tocado |
| Swipe hacia arriba / abajo | Desplaza la lista si el contenido supera la altura visible |

