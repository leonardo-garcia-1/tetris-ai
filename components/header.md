
# **Header**

> [!ABSTRACT]
> El Header es el módulo de apertura del contenido que resume y adelanta la información de la pantalla, guiando al usuario dentro de un flujo o sección. Resuelve la necesidad de comunicar el contexto de la pantalla y habilitar acciones relevantes sin distraer de la tarea principal.

| | |
|---|---|
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=7224-3683) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=5-343) |

## El header es el módulo de apertura del contenido. Resume y adelanta la información de la pantalla.

![][image113]

## **Descripción general**

El Header cumple la función de guiar al usuario dentro de un flujo o sección, mostrando el contexto de la pantalla y habilitando acciones relevantes sin distraer de la tarea principal. Su diseño asegura que el acceso a las acciones críticas esté siempre visible para reforzar la orientación y la eficiencia de la navegación.

### Usos habituales

* Usar para dar soporte a las tareas del usuario en flujos operativos.  
* Usar para dar acceso rápido a acciones claves sin desplazar el foco de la tarea principal.

## **Variantes**

**Flow**

![][image114]

Aparece en secuencias de pantallas diseñadas para guiar al usuario en una tarea puntual. No forman parte de la jerarquía permanente de navegación: comienzan cuando la persona inicia una acción específica y desaparecen al completarla. En los flows, la tarea o título funciona como una sentencia breve que indica claramente lo que debe hacer el usuario en la pantalla actual, reforzando el foco en el objetivo inmediato. Tiene su variante Desktop y Handheld. Este nivel se reconoce porque el título del Header se expresa como un verbo o instrucción (ej.: Escanear, Mover, Colocar una etiqueta), orientando al usuario hacia la acción inmediata.

Anatomía

![][image115]

**1\. Task:** Es el texto con mayor jerarquía en el Header del flow y tiene como objetivo guiar a la persona en el paso actual del proceso. Indica la tarea o acción a realizar. Por ejemplo, “Prepara la estación de trabajo”, “Toma la unidad indicada y escanéala”, o “Guarda la unidad escaneada y oprime el botón rojo”.

**2\. Information:** Información complementaria al flujo que está realizando el usuario operativo. Por ejemplo, en el flujo de Packing, mostrar la información que pertenece a la orden, el id de un tote, etc. Por ejemplo, el número de un tote con el que se está trabajando (“Tote 4AE Mixto”), el número de la orden de packing, etc. 

### **Status** 

![][image116]

Indicado para flujos handheld o flujos Desktop donde existan drawers de navegación única. Sirve para dar información de status de un flujo o tarea o para flujos de salida.

Anatomía

![][image117]

**1\. Title**

**2\. Subtitle** (Opcional)

**3\. Hour (Opcional):** muestra el horario actual al usuario.

**4\. Close** (Opcional en Handheld)

**Navigation**

![][image118]

Se utiliza mas frequente, por ejemplo, dentro de Drawers para reforzar la navegación interna de subflujos o tareas secundarias.

**1\. Title** (Opcional)

**2\. Subtitle** (Opcional)

**3\. Hour (Opcional):** muestra el horario actual al usuario.

**4\. Close** (Opcional en Handheld)

## **Ejemplos**

**Contador de unidades \- Packing**

![][image119]

## **Recomendaciones**

**✓ Do:** Usar el Header Flow cuando la pantalla corresponde a un paso dentro de una secuencia de tarea. El título debe expresarse como verbo o instrucción.

**✓ Do:** Usar el Header Status para flujos de salida o para comunicar el estado de una tarea sin navegación hacia atrás.

**✓ Do:** Usar el Header Navigation dentro de Drawers o subflujos con navegación interna.

✗ **Don’t:** No mezclar variantes de Header en una misma pantalla.

✗ **Don’t:** No usar el Header como contenedor de acciones primarias: las acciones van en la barra inferior o en el Touchless.

✗ **Don’t:** No modificar los tamaños de encabezados preestablecidos ni los colores.

## **Accesibilidad**

Esta sección incluye solo las consideraciones esenciales de accesibilidad que están implementadas en los componentes de Tetris, como por ejemplo el uso de roles y etiquetas que facilitan comprender el propósito de los componentes cuando son interpretados por lectores de pantalla, así como la navegación por teclas o gestos que garantizan una interacción inclusiva. 

Para conocer más en detalle sobre tecnologías asistivas, te recomendamos visitar la [guia de accesibilidad digital.](https://sites.google.com/mercadolibre.com/accesibilidad-digital/tecnolog%C3%ADas-asistivas)

Para saber más sobre cómo hacer un hand off accesible te recomendamos visitar la documentación de [Accesibility notes.](https://andes.mercadolibre.com/924dc6ec5/p/770b77-accessibility-notes) 

### Roles y etiquetado

El Header es un componente no interactivo en la mayoría de sus variantes. El Task o Title se implementa como encabezado (`h1` en Flow, `h2` en Status y Navigation) para que los lectores de pantalla puedan identificar el contexto de la pantalla. El Subtitle se implementa como párrafo. El Hour, si está presente, debe tener un `aria-label` descriptivo (ej. `aria-label="Hora actual: 12:34"`).

Si el Header incluye un botón de cierre (Close) o de navegación hacia atrás (Step back), esos elementos sí reciben foco y deben tener `aria-label` descriptivo.

### Navegación

El Header no recibe foco propio. Los únicos elementos focusables son los botones de acción que pueda contener (Close, Step back).

#### Teclado

| Tecla | Detalle |
| :---- | :---- |
| Tab | Alcanza los botones de acción del Header (Close, Step back) si están presentes |
| Space / Enter | Acciona el botón en foco |

