
# **Drawer**

> [!ABSTRACT]
> El Drawer es un panel lateral o inferior que se superpone sobre la pantalla principal para mostrar contenidos secundarios sin interrumpir el flujo principal. Resuelve la necesidad de presentar confirmaciones, acciones complementarias o contenido adicional sin redirigir al usuario a una nueva vista.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=1208-4043) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=5-342) |

## Panel que permite mostrar contenidos secundarios sin interrumpir el flujo principal.

![][image89]

## **Descripción general**

El Drawer es un panel lateral o inferior que se superpone sobre la pantalla principal mediante un overlay oscuro. Permite mostrar contenido secundario, confirmaciones o acciones complementarias sin redirigir al usuario a una nueva vista. Está disponible para dispositivos Desktop y Handheld, con tres tipos de contenido: Dialog, Slot hug y Slot fill.

### Usos habituales

* Para mostrar contenido secundario o acciones complementarias sin interrumpir el flujo principal  
* Para solicitar confirmación de acciones críticas (ej. finalizar tote, reportar producto)  
* Para mostrar información adicional con posibilidad de scroll en Desktop  
* Para presentar contenido libre (imágenes, formularios, listas) mediante un slot intercambiable

## **Anatomía**

*![][image90]*

**A. Slot hug (Desktop)**  
**1\. Step back (opcional):** Botón de navegación hacia atrás.  
**2\. Title (opcional):** Texto de título del header.  
**3\. Subtitle (opcional):** Texto secundario debajo del título.  
**4\. Close (opcional):** Botón para cerrar el drawer.  
**5\. Slot:** Área de contenido intercambiable.  
**6\. Bottom actions:** Barra de acciones inferior.

**B. Slot hug (Handheld)**  
**1\. Step back (opcional):** Botón de navegación hacia atrás.  
**2\. Close (opcional):** Botón para cerrar el drawer.  
**3\. Title (opcional):** Texto de título del header.  
**4\. Slot:** Área de contenido intercambiable.

**![][image91]**

**C. Dialog (Desktop)**  
**1\. Step back (opcional):** Botón de navegación hacia atrás.  
**2\. Title (opcional):** Texto de título del header.  
**3\. Subtitle (opcional):** Texto secundario debajo del título.  
**4\. Close (opcional):** Botón para cerrar el drawer.  
**5\. Icon:** Ícono que acompaña al mensaje del Drawer.  
**6\. Drawer title:** Título del Drawer. Generalmente es una pregunta para que el usuario confirme o cancele.  
**7\. Description:** Descripción de la acción a realizar por el usuario.  
**8\. Secondary Button:** Botón secundario.  
**9\. Primary Button:** Botón primario.             

**D. Dialog (Handheld)**           
**1\. Step back:** Botón de navegación hacia atrás.  
**2\. Close (opcional):** Botón para cerrar el drawer.  
**4\. Drawer title (opcional):** Texto de título del header.  
**5\. Drawer description (opcional):** Texto secundario debajo del título.  
**6\. Cancel button:** Botón de cancelar.  
**7\. Confirm button:** Botón de confirmar.

                                                                                 

## **Variantes**

### Dialog (Desktop+Handheld)

Muestra un ícono, título, descripción y botones de acción agrupados. Usada para confirmaciones y alertas que requieren decisión del usuario (ej. "¿Deseas finalizar el tote?").

![][image92]

![][image93]

### Slot hug & Slot fill (Desktop+Handheld)

Muestra un header con navegación y un área de contenido libre (slot intercambiable). La altura se ajusta al contenido.

*![][image94]*

## **Ejemplos**

**Dialog (Desktop)**

![][image95]

**Slot fill (Desktop)**

![][image96]

## **Recomendaciones**

![][image97]     ![][image98]

**✓ Do:** Utilizar para contenido secundario o acciones complementarias.

**✓ Do:** Intentar que siempre exista un indicador de acción de cierre o continuidad (Close. Step back o Touchless).

![][image99]     ![][image100]

**✓ Do:** Priorizar uso de 2 botones o Touchless en caso de única acción.

✗ **Don’t:** No priorizar el uso de un solo botón.

![][image101]

✗ **Don’t:** No modificar el tamaño del Drawer.

## **Accesibilidad**

Esta sección incluye solo las consideraciones esenciales de accesibilidad que están implementadas en los componentes de Tetris, como por ejemplo el uso de roles y etiquetas que facilitan comprender el propósito de los componentes cuando son interpretados por lectores de pantalla, así como la navegación por teclas o gestos que garantizan una interacción inclusiva. 

Para conocer más en detalle sobre tecnologías asistivas, te recomendamos visitar la [guia de accesibilidad digital.](https://sites.google.com/mercadolibre.com/accesibilidad-digital/tecnolog%C3%ADas-asistivas)

Para saber más sobre cómo hacer un hand off accesible te recomendamos visitar la documentación de [Accesibility notes.](https://andes.mercadolibre.com/924dc6ec5/p/770b77-accessibility-notes) 

### Roles y etiquetado

El Drawer se implementa con `role="dialog"` y `aria-modal="true"` cuando está abierto. Debe incluir un `aria-labelledby` que apunte al elemento de título del header para que el lector de pantalla anuncie de qué trata al abrirse.

Al abrirse el Drawer, el foco debe moverse al primer elemento interactivo dentro del panel (generalmente el botón de cierre o el primer botón de acción). El foco debe quedar atrapado dentro del Drawer mientras está abierto: Tab y Shift+Tab deben ciclar únicamente entre los elementos interactivos del panel.

Al cerrarse, el foco debe volver al elemento que disparó la apertura del Drawer.

### Navegación

La navegación sigue el orden de lectura de izquierda a derecha y de arriba hacia abajo dentro del panel.

#### Teclado

| Tecla | Detalle |
| :---- | :---- |
| Tab | Navega entre los elementos interactivos del Drawer en orden de lectura |
| Shift + Tab | Navega hacia atrás entre los elementos interactivos |
| Space / Enter | Acciona el elemento en foco (botón, enlace) |
| Escape | Cierra el Drawer y devuelve el foco al elemento disparador |

#### Gestos

| Gestos | Detalle |
| :---- | :---- |
| Tap | Acciona el elemento tocado |
| Tap fuera del Drawer | Cierra el Drawer (si está habilitado el cierre por overlay) |

