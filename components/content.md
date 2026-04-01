
# **Content**

> [!ABSTRACT]
> Content es un componente de layout que estandariza tamaños y estructuras de contenido, combinando imágenes, títulos y descripciones en estructuras fijas para estados vacíos, instrucciones y vistas de presentación. Se utiliza como módulo dentro de componentes contenedores flexibles para guiar al usuario a través de una tarea.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=1329-15269) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=5-341) |

## Son armados de texto que estandarizan tamaños y estructuras de contenido.

![][image64]

## **Descripción general**

Content es un componente de layout que estructura bloques de contenido en estados vacíos, instrucciones y vistas de presentación. Estandariza la composición visual combinando imágenes, títulos y descripciones en dos estructuras fijas. Se utiliza como módulo dentro de componentes contenedores flexibles.

### Usos habituales

* Para guiar al usuario a través de una tarea con ícono, título y descripción

## **Anatomía**

**![][image65]**

**![][image66]**

**A. Instruction**  
**1\. Icon:** Ícono ilustrativo que refuerza el mensaje. Tamaño entre 80px y 160px, con radio de borde circular.  
**2\. Title:** Texto principal. Máx. 3 líneas.  
**3\. Description:** Texto secundario de apoyo. Máx. 2 líneas.

**B. Scan**  
**1\. Overline:** Texto de etiqueta superior. Máx. 3 líneas.  
**2\. Description:** Texto principal. Máx. 2 líneas. 

**C. Slot+Content**  
**1\. Slot:** Slot de imagen intercambiable. Permite reemplazar con un componente local.  
**2\. Overline:** Texto de etiqueta superior. Máx. 1 línea.  
**3\. Title:** Texto principal en tipografía grande. Máx. 2 líneas.                                                                                                                                    

## **Variantes**

![][image67]  
![][image68]

### A. Instruction

Se usa para comunicar una instrucción a la persona usuaria acompañada de un ícono ilustrativo (generalmente animado) que muestra la acción a realizar.

### B. Scan

Indica una acción de scan a la persona usuaria.

### C. Slot+Content

Indica una acción a realizar a la persona usuaria, acompañada de un slot de imagen para mayor flexibilidad.

## **Ejemplos** 

**Instruction**

![][image69]

**Drawer**

![][image70]

**Scan**

![][image71]

## **Recomendaciones**

![][image72]     ![][image73]

**✓ Do:** Usar como módulo dentro del componente contenedor flexible.

✗ **Don’t:** Evitar usar tokens de color de texto secundarios o terciario, cuando hay un solo texto.

![][image74]     ![][image75]

**✓ Do:** Usar la variante Medium dentro del drawer.

✗ **Don’t:** No usar la variante Medium fuera del drawer.

![][image76]     ![][image77]

**✓ Do:** Usar las variables del componente.

✗ **Don’t:** No alterar los encabezados ni los tokens de color de textos.

## **Accesibilidad**

Esta sección incluye solo las consideraciones esenciales de accesibilidad que están implementadas en los componentes de Tetris, como por ejemplo el uso de roles y etiquetas que facilitan comprender el propósito de los componentes cuando son interpretados por lectores de pantalla, así como la navegación por teclas o gestos que garantizan una interacción inclusiva. 

Para conocer más en detalle sobre tecnologías asistivas, te recomendamos visitar la [guia de accesibilidad digital.](https://sites.google.com/mercadolibre.com/accesibilidad-digital/tecnolog%C3%ADas-asistivas)

Para saber más sobre cómo hacer un hand off accesible te recomendamos visitar la documentación de [Accesibility notes.](https://andes.mercadolibre.com/924dc6ec5/p/770b77-accessibility-notes) 

### Roles y etiquetado

Content es un componente no interactivo. Su estructura semántica depende del tipo de variante:

- El **ícono** es decorativo en todos los casos: `aria-hidden="true"`.
- El **Title** se implementa como un encabezado (`h2` o `h3` según jerarquía de la pantalla) para que los lectores de pantalla puedan navegarlo por encabezados.
- La **Description** y el **Overline** se implementan como párrafos (`p`).
- El componente no recibe foco ni tiene rol interactivo propio. Si está contenido dentro de un área navegable (ej. Drawer), hereda la navegación del contenedor.

### Navegación

El componente no es interactivo: no recibe foco de teclado ni responde a gestos directos. La navegación opera a nivel del contenedor que lo aloja.

#### Teclado

| Tecla | Detalle |
| :---- | :---- |
| — | Content no recibe foco por teclado. |

#### Gestos

| Gestos | Detalle |
| :---- | :---- |
| — | Content no responde a gestos directos. |

