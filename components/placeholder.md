
# **Placeholder**

> [!ABSTRACT]
> Placeholder es un componente que aparece en áreas vacías de la interfaz donde aún no existe contenido para mostrar, combinando un ícono ilustrativo con un texto descriptivo. Resuelve la necesidad de comunicar un estado temporal antes de que haya contenido disponible, orientando al usuario sobre la función o resultado esperado del área.

## Comunica un estado temporal antes de que haya contenido disponible. Orienta al usuario sobre la función o resultado esperado del área que ocupa.

![][image163]

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=18194-10612) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=2658-2279) |

## **Descripción general**

Placeholder es un componente que aparece en áreas vacías de la interfaz donde aún no existe contenido para mostrar. Combina un ícono ilustrativo con un texto descriptivo para indicarle al usuario qué tipo de información verá una vez que el contenido esté disponible.

## **Anatomía**

*![][image164]*

**1\. Icon:** representación visual decorativa del tipo de contenido esperado.  
**2\. Label:** texto que describe el estado vacío o el resultado esperado.  
                                                                                                                                     

## **Variantes**

![][image165]

### Desktop

Variante para pantallas de mayor visualización.

### Handheld

Variante para devices con pantalla pequeña.

## **Ejemplos**

### Área de imagen antes del escaneo

![][example-scan]

En la Product card, el estado Placeholder aparece en el área de imagen antes de que el operario escanee un producto. El ícono central y el texto indican que el sistema está en espera. Una vez escaneado, la transición al estado Standard ocurre automáticamente con la imagen y datos del producto.

## **Recomendaciones**

**✓ Do:** Utilizar Placeholder para resultados a mostrarse al realizar una acción.

✗ **Don’t:** No utilizar Placeholder como Empty state.

## **Accesibilidad**

Esta sección incluye solo las consideraciones esenciales de accesibilidad que están implementadas en los componentes de Tetris, como por ejemplo el uso de roles y etiquetas que facilitan comprender el propósito de los componentes cuando son interpretados por lectores de pantalla, así como la navegación por teclas o gestos que garantizan una interacción inclusiva. 

Para conocer más en detalle sobre tecnologías asistivas, te recomendamos visitar la [guia de accesibilidad digital.](https://sites.google.com/mercadolibre.com/accesibilidad-digital/tecnolog%C3%ADas-asistivas)

Para saber más sobre cómo hacer un hand off accesible te recomendamos visitar la documentación de [Accesibility notes.](https://andes.mercadolibre.com/924dc6ec5/p/770b77-accessibility-notes) 

### Roles y etiquetado

Placeholder es un componente no interactivo. El ícono es decorativo: `aria-hidden="true"`. El Label debe estar disponible como texto legible por lectores de pantalla para comunicar el estado vacío del área.

Si el Placeholder ocupa un área con un propósito específico (ej. "Resultados de búsqueda"), el contenedor debe tener un `aria-label` o estar asociado a un encabezado que identifique ese propósito.

### Navegación

El componente no recibe foco de teclado ni responde a gestos directos, ya que no es interactivo.

#### Teclado

| Tecla | Detalle |
| :---- | :---- |
| — | Placeholder no recibe foco por teclado. |

#### Gestos

| Gestos | Detalle |
| :---- | :---- |
| — | Placeholder no responde a gestos directos. |

