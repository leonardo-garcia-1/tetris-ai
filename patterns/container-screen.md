
# **Container screen**

| | |
|---|---|
| **Owner** | Tetris |
| **Status** | WIP |
| **Última revisión** | Marzo 2026 |
| **Figma Library** | [Tetris Library 2.0 ↗](https://www.figma.com/design/xMJ3tIYgPC2FQnyhWYOxSf/Tetris-Library-2.0?m=auto&node-id=23847-1019) |
| **Figma Specs** | [Component Specs ↗](https://www.figma.com/design/Rbg2kw9fx5wqFDOmSIoG7m/Component-Specs?node-id=1297-6674) |

> [!ABSTRACT]
> El Container screen es un preset de pantalla completa para Handheld que guía al operador de warehouse (rep) a buscar desde un origen o depositar en un destino. También se utiliza para indicar qué contenedor debe manipular. Estructura flujos de picking y stowing donde el rep necesita identificar claramente una posición física o un contenedor específico.

---

## Descripción general

El Container screen combina información de dirección (ubicación física), identificación del contenedor o posición, dato principal (código), metadatos y una acción de avance. Es un preset: no es un componente atómico sino una pantalla lista para usar con slots configurables según el contexto de la operación.

La pantalla se adapta a distintas combinaciones de información según el flujo — algunos contextos requieren slot map y dirección completa, otros solo el dato principal. La acción de avance puede ser automática (timeout), por escaneo o por botón.

---

## Usos habituales

- Indicar al rep desde dónde recoger un producto (origen) o dónde depositarlo (destino).
- Mostrar el contenedor específico que debe manipularse (tote, MU, posición).
- Presentar la dirección física completa (calle + módulo) junto a una representación visual del slot map cuando hay múltiples posiciones disponibles.
- Confirmar la operación mediante escaneo del código del contenedor.

---

## Cuándo elegir alternativas

- Usar `Action screen` cuando el flujo requiere una decisión entre dos opciones con contenido visual (imagen o slot) más prominente.
- Usar `Scan screen` cuando el flujo principal es la captura de un código por cámara como acción primaria de la pantalla.
- Usar `System state` cuando el contenido comunica un estado de excepción (error, vacío, éxito) en lugar de una instrucción operativa.

---

## Anatomía

1. **Header**: barra superior con menú secundario. El título actúa como instrucción para el rep (ej. "Escaneá el código").
2. **Dirección**: indica la ubicación física. Máximo 2 niveles (ej. Calle + Módulo). Solo presente en contextos Full con dirección.
3. **Slot map**: representación visual de los soportes físicos disponibles. Solo se muestra cuando hay ≥3 posiciones por nivel, ≤7 niveles y ≤7 posiciones por nivel.
4. **Identificación**: etiqueta que identifica con qué tipo de elemento va a interactuar el rep (Posición, Tote, MU, etc.).
5. **Dato principal**: código del contenedor o dirección (número de tote, MU, posición exacta). Es el dato más prominente visualmente.
6. **Metadato**: información complementaria del destino (afinidad, canalización). Aparece en contextos que requieren más contexto operativo.
7. **Info de soporte**: representación del producto o capacidad del contenedor. Solo cuando es estrictamente necesario para la operación.
8. **Símbolo**: símbolos físicos de identificación (olas, canalización, etc.). No debe reemplazarse por pictogramas no físicos.
9. **Acción**: mecanismo de avance al siguiente paso. Puede ser timeout automático, escaneo (con instrucción en el header) o tap en botón.

---

## Variantes

### Con dirección + slot map
Muestra la dirección completa (hasta 2 niveles) y el slot map. Usado cuando el rep debe navegar a una posición específica dentro de una estructura física con múltiples slots.

### Con dirección + slot map + info de soporte
Igual al anterior pero agrega información del producto o capacidad del contenedor en la zona de soporte.

### Con dirección + dato principal
Muestra dirección y el código del contenedor sin slot map. Para ubicaciones simples donde el mapa visual no aporta valor.

### Solo dato principal
La pantalla se centra únicamente en el código del contenedor o posición. Para flujos donde la dirección ya fue comunicada en pasos anteriores.

### Con dato principal + metadato
Agrega información contextual (afinidad, canalización) al dato principal. Para flujos donde el rep necesita ese contexto para operar correctamente.

### Con dato principal + metadato + info de soporte
Combinación completa de dato principal, metadato e información del soporte físico o producto.

### Con progress bar
Agrega una barra de progreso para indicar el avance dentro de una tarea multi-paso (ej. picking de múltiples unidades).

### Con escaneo
La acción de avance requiere que el rep escanee el código del contenedor. La instrucción se muestra en el título del header.

### Con botón
La acción de avance es un botón explícito en la parte inferior de la pantalla.

---

## Propiedades

| Propiedad | Tipo | Default | Descripción |
|---|---|---|---|
| `variant` | `"Con dirección + slot map"` / `"Con dirección + dato principal"` / `"Solo dato principal"` / `"Con dato principal + metadato"` / `"Con dato principal + metadato + info de soporte"` / `"Con progress bar"` / `"Con escaneo"` / `"Con botón"` | — | Define la combinación de elementos visible en la pantalla. |
| `showSlotMap` | `boolean` | `false` | Muestra u oculta el slot map. Requiere ≥3 posiciones/nivel, ≤7 niveles, ≤7 posiciones/nivel. |
| `showDireccion` | `boolean` | `false` | Muestra u oculta el bloque de dirección (hasta 2 niveles). |
| `showMetadato` | `boolean` | `false` | Muestra u oculta el bloque de metadato (afinidad, canalización). |
| `showInfoSoporte` | `boolean` | `false` | Muestra u oculta la sección de info de soporte. Solo cuando es estrictamente necesaria. |
| `showSimbolo` | `boolean` | `false` | Muestra u oculta el símbolo físico de identificación. |
| `showProgressBar` | `boolean` | `false` | Muestra u oculta la barra de progreso. |
| `accionTipo` | `"timeout"` / `"scan"` / `"button"` | `"scan"` | Define el mecanismo de avance al paso siguiente. |
| `identificacionLabel` | `string` | `"Posición"` | Etiqueta que identifica el tipo de elemento (Posición, Tote, MU, etc.). |
| `datoPrincipalText` | `string` | — | Código del contenedor o dirección (número de tote, MU, posición). |

---

## Comportamiento

- **Dimensiones**: ancho `360px`, alto `640px`. Rango Handheld (alto: `530px`–`640px`).
- **Slot map**: solo visible con ≥3 posiciones por nivel, máximo 7 niveles y 7 posiciones por nivel. Fuera de ese rango, se omite.
- **Dirección**: máximo 2 niveles jerárquicos (ej. Calle + Módulo). No se deben mostrar más de 2 niveles simultáneamente.
- **Dato principal**: es el elemento con mayor jerarquía visual en todas las variantes. Debe ser legible a distancia y en condiciones de operación.
- **Símbolo**: representa identificación física real. No reemplazar por pictogramas decorativos o no operativos.
- **Acción timeout**: avanza automáticamente al siguiente paso tras un período de espera. No requiere interacción del rep.
- **Acción scan**: el rep escanea el código del contenedor para avanzar. La instrucción de escaneo se muestra en el título del header.
- **Acción button**: el rep toca un botón explícito para confirmar y avanzar.

---

## Ejemplos

### Identificación de posición con slot map e info de soporte

Variante **Con dirección + slot map + info de soporte**, acción **scan**. La instrucción al rep aparece en el título del header ("Escaneia a posição"). Debajo, dos bloques de dirección en fila horizontal muestran el nivel macro de ubicación: "Área / 81" e "Ilha / 588". El slot map ocupa el área central con una grilla de 5 columnas × 4 filas; la posición B2 aparece resaltada en amarillo con un tooltip encima que muestra su código, indicando visualmente al rep exactamente dónde debe ir dentro de la estructura física. En la parte inferior, la barra de info de soporte muestra la capacidad del contenedor: "60% ocupação" con un ícono de nivel y "29 vol." alineado a la derecha, dando al rep contexto sobre el estado del tote o posición antes de depositar.

---

## Recomendaciones

### ✅ Do
- Usar el slot map solo cuando la estructura física lo justifica (≥3 posiciones, ≤7 niveles, ≤7 posiciones/nivel).
- Mantener el dato principal como el elemento más prominente: grande, legible y sin competir visualmente con otros bloques.
- Usar el título del header como instrucción activa (ej. "Escaneá el código de la posición").
- Limitar la dirección a 2 niveles máximo para no saturar la pantalla.
- Usar símbolos físicos reales para identificación — los reps los asocian con marcas visuales del depósito.

### ❌ Don't
- No mostrar más de 2 niveles de dirección simultáneamente.
- No reemplazar los símbolos físicos por pictogramas que no existen en el depósito real.
- No usar este preset en Desktop — es exclusivo de Handheld.
- No agregar info de soporte si no es estrictamente necesaria para la operación — aumenta la carga cognitiva.
- No usar este preset para estados de excepción (error, vacío) — usar `System state`.

---

## Componentes relacionados

- **Header**: componente de encabezado con instrucción y menú secundario.
- **Slot map**: componente de representación visual de soportes físicos.
- **Progress bar**: componente de progreso usado en la variante multi-paso.
- **Action screen**: preset alternativo para flujos de decisión con contenido visual.
- **Scan screen**: preset alternativo cuando el escaneo es la acción principal de la pantalla.
- **System state**: preset para estados de excepción del sistema.

---

## Accesibilidad

### Roles y etiquetado

La pantalla debe tener un `<main>` como contenedor principal. El dato principal debe implementarse con una jerarquía de encabezado adecuada (`<h1>` o `<h2>`). La etiqueta de identificación debe estar asociada semánticamente al dato principal.

Las instrucciones del header (ej. "Escaneá el código") deben ser legibles por lectores de pantalla sin depender del contexto visual.

### Navegación

Orden de lectura: header → dirección → slot map → identificación → dato principal → metadato → info de soporte → símbolo → acción.

### Interacciones con teclado

| Tecla | Función |
|---|---|
| Tab | Navegar entre elementos interactivos (botón, menú del header) |
| Enter / Space | Activar el botón enfocado |

### Gestos

| Gesto | Función |
|---|---|
| Tap en botón | Avanzar al siguiente paso (variante con botón) |
| Tap en menú (header) | Abrir menú de navegación secundaria |

### Consideraciones de diseño

- El dato principal debe tener tamaño de fuente suficiente para ser legible con guantes y en condiciones de baja luz de depósito.
- Los botones de acción deben cumplir un área de toque mínima de `72px` de alto.
- El slot map debe incluir indicadores de posición con contraste suficiente para diferenciar la posición activa del resto.
