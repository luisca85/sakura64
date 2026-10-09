# Feature: Diseño visual estilo web japonés  ·  id: visual
Historia de usuario: Como lector de LATAM que llega desde un link público, quiero una interfaz ordenada, liviana y amable, para concentrarme en mi objetivo sin ruido visual.
Objetivo: aplicar a toda la app un lenguaje visual inspirado en la web japonesa "amable" (referencia: choooodoii.com): fondos claros con papel cuadriculado, bordes finos, sin sombras, tipografía Noto Sans JP, un acento amarillo, píldoras blancas, campos y ayudas como globos de diálogo, íconos de línea con temática japonesa y un patrón fijo de pantalla. Aprobado en la exploración (rama `explorar/diseno-visual`, commits f46f58f a cfd5b4a). Cambia solo la apariencia: no cambia datos ni comportamiento.

Criterios de aceptación:
Patrón de pantalla
  - Dada cualquier pantalla con navegación (inicio, tablero, asistente), cuando la miro, entonces tiene tres capas: barra de navegación blanca arriba, subheader a todo el ancho con fondo de papel cuadriculado y, debajo, la zona de trabajo sobre gris claro.
  - Dado el subheader, cuando lo miro, entonces tiene cuadros de 20px con todas las líneas de la misma intensidad (gris azulado al 10% en claro, blanco al 4.5% en oscuro) sobre un blanco cálido (`#FDFDFA`).
  - Dado el inicio, cuando lo miro, entonces el subheader tiene el título, la bajada y "Nuevo tablero →", y debajo van las tarjetas.
  - Dado un tablero, cuando lo miro, entonces el subheader tiene "Volver al inicio", el objetivo, las 3 cifras, el progreso general, el aviso del ejemplo, las pestañas y "Exportar PDF", y la grilla o el panel van debajo.
  - Dado el asistente, cuando lo miro, entonces el subheader tiene los pasos, el título y las instrucciones, y el bloque y sus opciones van debajo.
  - Dado cualquier subheader y su zona de trabajo, cuando mido los bordes, entonces el contenido empieza donde empieza el logo de la navegación y termina donde termina el botón de tema (mismo ancho de contenedor, 1240px como máximo).
Base
  - Dada la app en claro, cuando la miro, entonces el fondo es `#F1F4F5`, las superficies blancas, la tinta `#1F1F1F`, el texto secundario casi negro (`#2E2E2E`) y los bordes `#D6D6D6`/`#E3E3E3`.
  - Dada la app en oscuro, cuando la miro, entonces usa grises neutros (`#141414` de fondo, `#1C1C1C` en superficies) y todo se lee.
  - Dado cualquier texto, cuando lo miro, entonces usa Noto Sans JP (500 en el cuerpo, 700 en títulos), con fuentes del sistema japonesas o `system-ui` de respaldo.
  - Dada cualquier pantalla, cuando la miro, entonces no hay sombras; solo queda el anillo que marca el color elegido del objetivo.
Componentes
  - Dada una acción principal ("Nuevo tablero", "Exportar PDF", "Agregar tarea", avanzar en el asistente), cuando la miro, entonces es texto subrayado con "→" y no un botón relleno.
  - Dados los botones secundarios, chips, ejemplos, etiquetas de tarjeta y pasos del asistente, cuando los miro, entonces son píldoras blancas con borde gris sutil y esquinas de 2px.
  - Dados los pasos del asistente, cuando los miro, entonces el actual tiene borde de tinta, negrita y número sobre amarillo, y cada paso lleva su ícono (Fuji en Objetivo, torii en Pilares).
  - Dado un campo de texto, de fecha o un selector con etiqueta, cuando lo miro, entonces tiene borde de tinta, fondo blanco y un piquito de globo de chat arriba a la izquierda.
  - Dada una ayuda (consejo del inicio, explicación bajo la grilla), cuando la miro, entonces es un globo de diálogo con borde de tinta, piquito y el logo como avatar.
  - Dado un ícono "?", cuando paso el mouse o llego con el teclado, entonces se abre un globo blanco con borde fino y piquito, y oculto no genera desplazamiento horizontal.
  - Dada una tarjeta del inicio, cuando la miro, entonces tiene: etiqueta "EJEMPLO" o "TABLERO" y fecha arriba, ícono del tablero y objetivo con una línea de tinta debajo, 3 etiquetas de datos y los links "Abrir", "Duplicar" y "Eliminar" (este último en gris; no aparece en el ejemplo).
Color
  - Dados los 8 pilares, cuando miro el anillo central, entonces van en orden horario: rojo `#D9282F`, naranja `#F39800`, amarillo `#FFD400`, verde manzana `#8CC63F`, turquesa `#00B5A5`, cian `#00A7E1`, azul `#2F5DCF` y magenta `#E4007F`.
  - Dado un pilar, cuando miro su casilla rellena, su chip o su marca, entonces el texto es oscuro en los claros y blanco en rojo, azul y magenta, con contraste de al menos 4.5:1.
  - Dado el PDF, cuando lo exporto, entonces usa los mismos colores (`PHEX`) y el mismo color de texto por pilar (`PFG`), y el estado de cada acción va en tinta cuando el pilar es claro.
  - Dado el acento amarillo `#F5C400`, cuando aparece (etiqueta "Ejemplo", contador de tareas, cuadradito de "MI OBJETIVO", paso actual, texto seleccionado), entonces siempre lleva texto oscuro encima; no hay líneas amarillas bajo títulos ni pestañas (la pestaña activa se subraya en tinta).
Íconos y marca
  - Dado el logo (encabezado, onboarding, avatar de ayudas y favicon), cuando lo miro, entonces es la flor de sakura del set, con los 5 pistilos y el centro rellenos en rojo `#D9282F`.
  - Dadas las pestañas, cuando las miro, entonces llevan caja bento (Mapa), pincel (Tus tareas para hoy) y bambú (Mi avance).
  - Dadas las tarjetas, cuando las miro, entonces el ejemplo lleva el té y los tableros propios reciben en orden bonsái, loto, origami, sakura, piedras, pagoda, linterna y té.
  - Dado cualquier ícono, cuando cambio a modo oscuro, entonces toma el color del texto (`currentColor`).
Responsivo
  - Dados el inicio, el tablero, el asistente y un panel, en 375px y 1240px, en claro y en oscuro, cuando los recorro, entonces `scrollWidth` es igual a `clientWidth`.

Alcance: tokens de `:root` y de modo oscuro (`--bg`, `--surface*`, `--ink`, `--muted`, `--line*`, `--p1`..`--p8`, `--f1`..`--f8`, `--accent`, `--on-accent`, `--grid-a`, `--paper`), `PHEX`, `PFG`, `pfv`, link de Google Fonts (Noto Sans JP), `subHTML` y clases `.band`, `.sub`, `.sub-in`, `.has-tabs`, cambios de marcado en `homeHTML`, `boardHTML` y `wizHTML` para el patrón, `JI` (13 íconos), `jicon`, `CARD_ICONS`, `boardIcon`, `logo` con `PISTILS`, favicon, `bubbleHTML`, `cardHTML`, estilos de `.btn`, `.btn.primary`, `.chip`, `.exchip`, `.wst`, `.card*`, `.lnk`, `.bubble`, `.tipi`, campos con piquito, `buildPDF` (texto por pilar).
Fuera de alcance / No tocar: datos y persistencia, comportamiento de grilla, paneles, asistente y tareas, textos de la interfaz (salvo los ya cambiados en la exploración), el nombre de la app (lo define `legales.md`), la página legal (vive en `explorar/temas-legales`).
Dependencias: Google Fonts (Noto Sans JP), set "Japan Icons (Community)" de Figma (archivo JNMYB81luFx3U7mWFqVyg3), `boardStats`, `isDue`, `render`, `buildPDF`. Convive con `asistente.md`, `mapa.md` y `panel-casilla.md`, que no cambian de comportamiento.
Estados (UI): sin cambios de comportamiento. Si Noto Sans JP no carga, se usan las fuentes del sistema. Sin carga ni error propios.
Diseño: referencia https://choooodoii.com/ ; íconos https://www.figma.com/design/JNMYB81luFx3U7mWFqVyg3/Japan-Icons--Community- (node 0:1). Prototipo aprobado en la rama `explorar/diseno-visual`.
A CONFIRMAR:
  - Licencia y autor del set "Japan Icons (Community)" y el crédito que exige; sumarlo a "Créditos y licencias" de `legales.md` antes de publicar.
  - Orden de construcción frente a `legales.md`: las dos ramas tocan el mismo `index.html` (nombre "SAKURA 64", pie, página legal); hay que integrarlas sin perder ninguna.
  - Si el ícono de cada tarjeta se guarda como dato del tablero (hoy depende de su posición en la lista y cambia si se elimina uno anterior).
  - Si la flor de sakura se saca de la lista de íconos de tarjeta para no repetir el logo.
  - Si la página legal también usa el patrón de subheader.
  - Revisión del asistente con el subheader en pantalla, y de celular y modo oscuro después de los últimos cambios (no se llegó a verificar en la exploración).
  - Dependencia de Google Fonts frente al pendiente de privacidad de `legales.md` (servir Noto Sans JP desde el propio sitio).
Conocido:
  - Quedan sin uso `miniHTML` y su CSS `.mini`, `inspHTML`, `scrollInsp` y el CSS `.insp`; borrarlos al construir.
  - El daruma de la exploración se reemplazó por los íconos del set; su idea (pintar un ojo al fijar la meta y otro al lograrla) quedó sin usar.
  - Los íconos van incrustados en `index.html` (unos 52 KB) para que la app funcione al abrir el archivo directo.
Definición de hecho: la del AGENTS.md, más:
  - `:root`, modo oscuro, `PHEX` y `PFG` coinciden (regla de colores de pilar del AGENTS.md).
  - Contraste de al menos 4.5:1 en cada combinación de texto sobre pilar y sobre acento.
  - Recorrer inicio, asistente (2 pasos), tablero, panel de una acción y "Tus tareas para hoy" en 375px y 1240px, en claro y en oscuro, sin desplazamiento horizontal ni errores en consola.
  - Exportar un PDF y ver los colores nuevos y el texto legible en los 8 pilares.
  - Actualizar `architecture.md` (patrón de pantalla, íconos, tokens) y la regla de colores del AGENTS.md (`--f1`..`--f8` y `PFG`).
