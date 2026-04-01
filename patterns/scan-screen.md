
# **Scan screen**

| | |
|---|---|
| **Owner** | Tetris |
| **Status** | Stable |
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=15645-3166) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=1297-5915) |

## Es una pantalla que indica como principal acción un scan de un código.

![][image226]

## **Descripción general**

Esta pantalla le permite al rep ingresar un código cuando el sistema no provee sugerencias ni direccionamiento.

Es clave comprender que debemos usarla solamente cuando el origen, objeto o destino es libre. Es decir, cuando el sistema no está determinando un código específico que debe ser escaneado.

### Usos habituales

* Siempre que el input de origen, objeto o destino sea libre, sin direccionamiento por parte del sistema.  
* Los más habituales son scan de tote, scan de producto, scan de estación de trabajo, scan de estantería, scan de carrito.

## **Anatomía**

*![][image227]*

**Scan screen**  
**1\. Header:** Usamos el header con el menú secundario y sin el título.  
**2\. Instruction:** El title es el large, donde se colocará la instrucción sobre el tipo de código que debe ser escaneado.  
**3\. Support text:** Elemento opcional para casos de uso que requieran información complementaria para que el usuario pueda ejecutar el escaneo.  
**4\. Image:** Es una representación 3D alineada con lo que el rep ve físicamente en campo. Incluye el tipo de código y una animación que ilustre el escaneo.  
**5\. Counter:** Elemento opcional para procesos que requieren más de un escaneo secuencial. El contador muestra al usuario cuántos ítems han sido escaneados.  
Los avances pueden realizarse automáticamente al alcanzarse una cantidad predeterminada (por ejemplo: 1/3 cuando se espera que el rep escanee 3 ítems), o bien mediante un botón.

## **Variantes**

**Default:** las variantes pueden contener sólo título o título con instrucción (opcional).

### ![][image228] 

**Con counter:** las variantes pueden incluír el counter con cantidad predeterminada, con cantidad predeterminada \+ button o puede ser un contador simple \+button.  
![][image229]

**Con counter editable:** las variantes incluyen el contador editable \+ button y el contador editable \+ cantidad predeterminada \+ button  
![][image230]

**Con switch:** la variante con switch incluye instrucción \+ on/off option  
![][image231]

## **Recomendaciones**

       

**✓ Do:** …

✗ **Don’t:** …

## **Accesibilidad**

Esta sección incluye solo las consideraciones esenciales de accesibilidad que están implementadas en los componentes de Andes, como por ejemplo el uso de roles y etiquetas que facilitan comprender el propósito de los componentes cuando son interpretados por lectores de pantalla, así como la navegación por teclas o gestos que garantizan una interacción inclusiva. 

Para conocer más en detalle sobre tecnologías asistivas, te recomendamos visitar la [guia de accesibilidad digital.](https://sites.google.com/mercadolibre.com/accesibilidad-digital/tecnolog%C3%ADas-asistivas)

Para saber más sobre como hacer un hand off accesible te recomendamos visitar la documentación de [Accesibility notes.](https://andes.mercadolibre.com/924dc6ec5/p/770b77-accessibility-notes) 

### Roles y etiquetado

![][image232]

