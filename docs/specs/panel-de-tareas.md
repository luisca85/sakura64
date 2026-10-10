# Feature: Panel de acción y tareas  ·  id: tareas-panel
Historia de usuario: Como dueño de un tablero, quiero ver y marcar en un solo lugar la prioridad, si la acción está lograda y las tareas que la hacen realidad, para avanzar sin saltar entre pantallas.
Objetivo: reordenar el panel de una acción (prioridad y "Acción lograda" dentro del cuadro, pregunta guía, checkbox por tarea, volver al tablero), mostrar la prioridad de cada acción en la grilla y explicar mejor la descarga desde el personaje. Aprobado en la exploración (rama `explorar/panel-de-tareas`, commits 9d7150f a 731fd08). Ajusta `panel-casilla.md`, `mapa.md` y `exportacion.md`.

Criterios de aceptación:
Cuadro de la acción
  - Dado el panel de una acción, cuando lo miro, entonces la etiqueta del cuadro dice "Pilar N · nombre del pilar" (o solo "Pilar N" si no tiene nombre).
  - Dado el cuadro, cuando lo miro, entonces abajo a la izquierda está el selector de prioridad (Alta, Media, Baja) y abajo a la derecha la casilla "Acción lograda".
  - Dada la casilla "Acción lograda", cuando la marco, entonces el estado pasa a "Lograda"; cuando la desmarco, a "Sin empezar". "En curso" ya no se elige desde el panel.
  - Dado un ancho de 820px o menos, cuando miro el cuadro, entonces crece con el contenido y el área para escribir tiene al menos 140px.
Columna de tareas
  - Dado el panel, cuando lo miro, entonces arriba de las tareas dice "¿Qué tareas vas a realizar para que esta acción sea verdad?".
  - Dada una tarea de la acción, cuando marco su casilla, entonces queda completada hoy (título tachado, "completada hoy" y racha actualizada), igual que en "Tus tareas para hoy".
  - Dado el formulario de nueva tarea, cuando marco "Ya la completé hoy" y agrego, entonces la tarea se crea completada hoy y la casilla vuelve a quedar desmarcada.
  - Dado el formulario, cuando lo miro, entonces "Agregar tarea" va alineado a la derecha.
  - Dado el pie del panel, cuando lo miro, entonces "Vaciar casilla" va a la izquierda y "Volver al tablero principal" a la derecha; este vuelve a la grilla.
Grilla
  - Dada una acción escrita, cuando miro la grilla, entonces muestra su prioridad: Alta (etiqueta rellena de tinta), Media (blanca con borde de tinta) o Baja (blanca con borde gris y texto gris).
Exportación
  - Dado un tablero, cuando miro el subheader, entonces no hay link "Exportar PDF"; se exporta desde el personaje flotante (y desde "Mi avance").
  - Dada la nube del personaje, cuando la miro, entonces dice "頑張って！" chico en magenta (decorativo, `aria-hidden` por estar en la nube), "Llevate tu tablero, tus tareas y tu avance en un PDF" y "No lo guardamos en ningún servidor: al cerrar la pestaña, se borra.", y debajo el link chico en magenta "Descargar mi tablero" (12px, subrayado), en celular y escritorio.
  - Dado el link "Descargar mi tablero", cuando lo toco, entonces hace lo mismo que tocar al personaje: sin suscripción abre el formulario; con suscripción descarga el PDF. En celular, con la nube cerrada, el link no se ve (queda solo la flechita).
Alcance: `detHTML` (acción), `tasksSection`, `resetDraft` (`done`), acción `draft-done`, envío del formulario de tarea, `cellHTML` (etiqueta `.pri.p-*`), `boardHTML` (sin `export-top`), `mascotHTML` (nube, link `.mc-dl` y `aria-label`), CSS `.dact-foot`, `.dact-pri`, `.dact-done`, `.dq`, `.btnrow.end`, `.btnrow.split`, `.pri.p-media`, `.pri.p-baja`, `.task .check`, `.task.is-done`, `.mc-jp`, `.mc-note`, `.mc-dl`.
Fuera de alcance / No tocar: el modelo de datos (sin campos nuevos; "completada" usa `done[hoy]`), el panel del objetivo y del pilar, "Tus tareas para hoy".
Dependencias: `toggle`, `streak`, `PRI`, `pcv`/`pfv`, `.check`, `det-close`.
Estados (UI): acción sin texto, la columna de tareas pide escribirla primero (sin cambios). Sin carga ni error (todo es local).
Diseño: N/A (aprobado en la exploración).
Conocido:
  - "Completada" es por día: en tareas que se repiten, al día siguiente vuelven a quedar pendientes.
  - Las acciones que ya estaban "En curso" (como varias del ejemplo) conservan ese estado y su ícono hasta que se toque la casilla.
  - En celular, el personaje flotante tapa en parte "Agregar tarea".
A CONFIRMAR:
  - Si se quita el botón "Descargar PDF" de "Mi avance".
Definición de hecho: la del AGENTS.md, más:
  - En el ejemplo: cambiar prioridad y "Acción lograda" desde el cuadro, marcar una tarea, crear una con "Ya la completé hoy" y volver con "Volver al tablero principal".
  - Ver las 3 prioridades en la grilla y la nube nueva, en 1240px y 375px, sin desplazamiento horizontal.
