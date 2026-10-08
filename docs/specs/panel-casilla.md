# Feature: Panel por casilla  ·  id: panel
Historia de usuario: Como dueño de un tablero, quiero abrir cada casilla en su propia pantalla y moverme entre ellas sin volver a la grilla, para trabajar con detalle el objetivo, un pilar y sus acciones, o una acción y sus tareas.
Objetivo: cada casilla de la grilla (objetivo, pilar o acción) tiene una pantalla de edición propia dentro de la pestaña Mapa, no un modal. Cada pantalla tiene migas de pan, anterior y siguiente, y responde al botón "atrás" del navegador. Reemplaza al inspector lateral. Aprobado en la exploración (rama `explorar/onboarding`).

Criterios de aceptación:
Navegación
  - Dada la grilla, cuando abro una casilla con el botón ↗, con Ctrl+Enter (Cmd+Enter en Mac) o desde una lista de otro panel, entonces la grilla se reemplaza por el panel de esa casilla y la página baja hasta el panel.
  - Dado un panel, cuando miro arriba, entonces veo migas de pan: "Tablero completo › Pilar N: nombre › Acción M" (cada nivel anterior es un botón) y los botones de anterior y siguiente con el nombre del destino.
  - Dado el panel del objetivo, cuando toco siguiente, entonces voy al pilar 1; del pilar 1, anterior lleva al objetivo; del pilar 8 no hay siguiente.
  - Dado el panel de una acción, cuando toco siguiente en la acción 8, entonces voy a la acción 1 del pilar siguiente; anterior en la acción 1 lleva a la acción 8 del pilar anterior.
  - Dado que navegué grilla › pilar › acción, cuando uso el botón "atrás" del navegador, entonces vuelvo a pilar y después a grilla.
  - Dado que abrí antes otro tablero, cuando uso "atrás" desde un panel, entonces nunca se abre un panel de otro tablero (cada entrada del historial guarda su tablero).
  - Dado un panel, cuando toco "Tablero completo" en las migas o cambio de pestaña, entonces vuelvo a la grilla.
Panel del objetivo
  - Dado el panel del objetivo, cuando lo abro, entonces veo el bloque grande del objetivo editable, la paleta de color (acción `wiz-color`), la fecha meta con cuenta regresiva y la lista de los 8 pilares con "N/8" acciones definidas; tocar un pilar abre su panel.
Panel del pilar
  - Dado el panel de un pilar, cuando lo abro, entonces veo su bloque de 3x3 con el pilar editable en el centro y sus 8 acciones editables alrededor, y al lado la lista de acciones con estado y cantidad de tareas; tocar una acción abre su panel.
  - Dado el panel de un pilar, cuando presiono Enter en una casilla del bloque, entonces paso a la siguiente en orden (pilar, acción 1 a 8).
  - Dado el panel de un pilar, cuando toco "Vaciar pilar", entonces se borra solo el nombre del pilar (sus acciones y tareas se conservan y siguen editables) y "Deshacer" lo restaura.
Panel de la acción
  - Dado el panel de una acción, cuando lo abro, entonces veo el bloque de la acción editable (con su número y su pilar), prioridad, estado, sus tareas con el formulario para agregar y "Vaciar casilla".
  - Dado el panel de una acción, cuando agrego una tarea, entonces aparece en la lista, en "Tus tareas para hoy" si corresponde y como número en la casilla de la grilla.
Disposición
  - Dado un ancho mayor a 820px, cuando miro un panel, entonces el bloque va a la izquierda (hasta 540px y nunca más alto que la ventana) y la columna derecha ocupa todo el ancho restante, sin hueco en el medio; prioridad y estado se reparten a lo ancho.
  - Dado un ancho de 375px, cuando miro un panel, entonces el bloque va arriba, las opciones abajo y no hay desplazamiento horizontal.

Alcance: `S.det`, `openDet`, `detHTML`, `detNavHTML`, `detSib`, `detName`, `detBtn`, acciones `det-go`, `det-close`, `selpillar`, `selaction`, `gopillar` (ahora abre el panel del pilar), `pri`, `st`, `clear`, `tasksSection` dentro del panel, `history.pushState`/`popstate` con `{det, b}`, `openBoard` (crea la entrada de la grilla), CSS `.det`, `.det-nav`, `.crumbs`, `.det-head`, `.wgoal.dact`, `.dtasks` y la regla de columnas para más de 820px.
Fuera de alcance / No tocar: la grilla y el encabezado (`mapa.md`), el asistente (`asistente.md`), el contenido de "Tus tareas para hoy" y "Mi avance", el modelo de tareas.
Dependencias: `wcellHTML`, `tipHTML`, `GCOL`/`gcs()` (de `asistente.md`), `segHTML`, `stIcon`, `pillarStats`, `countdown`, `tasksSection` y el envío del formulario de tareas, `render`, `save`, `toast` con deshacer.
Estados (UI): pilar sin acciones, la lista dice "Acción N vacía"; acción sin tareas, el texto de ayuda de tareas. Sin carga ni error (todo es local).
Diseño: N/A (aprobado en la rama `explorar/onboarding`, commits 1218647, e0bc658 y f71e2fe).
Definición de hecho: la del AGENTS.md, más:
  - Recorrer grilla › objetivo › pilar 1 › acción 1 › siguiente hasta la acción 1 del pilar 2, y volver con "atrás" del navegador paso a paso hasta la grilla.
  - Abrir el ejemplo, después un tablero propio, y comprobar que "atrás" no mezcla tableros.
  - Vaciar un pilar con acciones, ver que las acciones siguen ahí, deshacer y ver que el nombre vuelve.
  - Agregar una tarea desde el panel y verla en la grilla y en "Tus tareas para hoy".
  - Comprobar en 1240px y 375px, en claro y en oscuro, que no hay desplazamiento horizontal.
