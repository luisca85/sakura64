# Feature: Mapa del tablero  ·  id: mapa
Historia de usuario: Como dueño de un tablero, quiero escribir directo en la grilla de 9x9 y tener a mano el progreso y las secciones del tablero, para completar y seguir mi tablero sin abrir formularios, y entrar al detalle solo cuando lo necesito.
Objetivo: la pestaña Mapa muestra la grilla a todo el ancho del contenedor, con cada casilla editable en el lugar y un botón para abrir su panel (ver `panel-casilla.md`). Arriba, una tarjeta de encabezado compacta reúne la vuelta al inicio, el objetivo, las cifras, el progreso general y las pestañas. Reemplaza al inspector lateral. Aprobado en la exploración (rama `explorar/onboarding`).

Criterios de aceptación:
Grilla
  - Dado el Mapa en 1240px, cuando lo abro, entonces la grilla ocupa todo el ancho del contenedor y no hay panel lateral.
  - Dada cualquier casilla, cuando hago clic, entonces puedo escribir ahí mismo, en cualquier orden; el "+" de las vacías desaparece al entrar.
  - Dado que escribo en una casilla, cuando cambia el texto, entonces se guarda en la sesión y se actualizan las cifras del encabezado sin perder el foco.
  - Dado un pilar, cuando escribo en una de sus dos apariciones (anillo central o centro de su bloque), entonces la otra se actualiza en el momento.
  - Dado el foco en una casilla, cuando presiono Enter, entonces paso a la siguiente en orden horario dentro del bloque y, al terminar el bloque, al bloque del pilar siguiente (en celular cambia el bloque visible).
  - Dado el foco en una casilla, cuando presiono las flechas arriba o abajo, entonces paso a la casilla vecina; izquierda y derecha mueven el cursor y solo saltan de casilla en el borde del texto.
  - Dado el foco en una casilla, cuando presiono Esc, entonces salgo del texto y el foco queda en el botón de abrir panel.
  - Dada una casilla, cuando paso el mouse o estoy escribiendo en ella, entonces aparece el botón ↗; al tocarlo o con Ctrl+Enter (Cmd+Enter en Mac) se abre su panel.
  - Dado un texto que no entra en la casilla, cuando lo miro, entonces se corta y el texto completo se ve al pasar el mouse y en el panel.
  - Dada una acción con tareas, prioridad alta o estado, cuando la miro, entonces muestra el número de tareas, la marca "Alta" y el ícono de estado.
  - Dado un ancho menor a 760px, cuando abro el Mapa, entonces se ve un bloque a la vez con chips para cambiar y las casillas siguen siendo editables.
Encabezado
  - Dado un tablero abierto, cuando lo miro, entonces veo una tarjeta con "Volver al inicio" con ícono, el color y el texto del objetivo, 3 cifras (acciones definidas de 64, logradas y días para la meta o "Sin fecha"), una barra de progreso general y las pestañas.
  - Dada la barra de progreso general, cuando la miro, entonces la parte clara son las acciones definidas y la sólida las logradas sobre 64, con el porcentaje logrado al lado.
  - Dadas las pestañas, cuando las miro, entonces se llaman "Mapa", "Tus tareas para hoy" y "Mi avance", con ícono, y "Exportar PDF" queda a la derecha.
  - Dadas tareas pendientes para hoy, cuando miro la pestaña "Tus tareas para hoy", entonces muestra cuántas faltan cumplir.
  - Dado el tablero de ejemplo, cuando lo abro, entonces veo la etiqueta "Ejemplo" y el aviso con "Duplicar como mío", y no se puede eliminar.
  - Dado un ancho de 375px, cuando miro el encabezado, entonces las 3 pestañas entran sin desplazamiento horizontal y "Exportar PDF" va debajo a todo el ancho.
  - Dado el modo oscuro, cuando elijo "Un pilar a la vez", entonces el chip "Objetivo" seleccionado se lee.

Alcance: `mapHTML` (sin inspector), `gridHTML`, `blockHTML`, `cellHTML`, `cellCls`, `cellLive`, `cellNext`, `fitCell`/`fitCells`, `toolbarHTML`, `boardHTML`, `metaHTML`, íconos `ic`/`IC`, teclado de la grilla, CSS de `.cell`, `.copen`, `.ntk`, `.bd-top`, `.stats`, `.gprog`, `.tabsrow`, `.tab`, `.bdg`. Ya no se usan `inspHTML`, `scrollInsp` ni el CSS `.insp` (ver Conocido). Texto del inicio que nombra la pestaña Hoy pasa a "Tus tareas para hoy".
Fuera de alcance / No tocar: contenido de los paneles por casilla (`panel-casilla.md`), contenido de las pestañas "Tus tareas para hoy" y "Mi avance" (solo cambia el nombre), PDF, persistencia.
Dependencias: `cellAt`/`NEI`, `getText`/`setText`, `boardStats`, `isDue`, `tipHTML`, `gcs()` y `goalColor` (de `asistente.md`), `openDet` (de `panel-casilla.md`).
Estados (UI): casilla vacía con "+"; sin fecha meta, la cifra dice "Sin fecha"; sin tareas para hoy, la pestaña no muestra número. Sin carga ni error (todo es local).
Diseño: N/A (aprobado en la rama `explorar/onboarding`, commits 1218647, e0bc658, f21e3b3 y 81939ee).
Definición de hecho: la del AGENTS.md, más:
  - En el ejemplo y en un tablero nuevo: escribir en la grilla, Enter, flechas, Esc, abrir el panel con el botón y con Ctrl+Enter.
  - Escribir en una de las dos apariciones de un pilar y ver la otra actualizada sin perder el foco.
  - Comprobar que `scrollWidth` es igual a `clientWidth` en 1240px y en 375px, en claro y en oscuro.
  - El test de regresión del AGENTS.md cambia el paso 3 por: escribir en la grilla y abrir el panel de una acción para agregar una tarea.
Conocido:
  - `inspHTML`, `scrollInsp` y el CSS `.insp` quedaron en `index.html` sin uso desde que se reemplazó el inspector. Se pueden borrar en un cambio aparte.
  - Las acciones de un pilar sin nombre se pueden escribir: no hay bloqueo, a propósito.
