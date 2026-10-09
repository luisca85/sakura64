# Feature: Haikus y ajustes finales de interfaz  ·  id: haiku
Historia de usuario: Como lector que llega desde un link público, quiero una interfaz con un detalle amable y un asistente más directo, para arrancar mi tablero sin decisiones de más.
Objetivo: sumar haikus originales que se escriben solos en los subheaders y cerrar ajustes del asistente, el encabezado del tablero, las tarjetas y el pie. Aprobado en la exploración (rama `explorar/haikus`, commits 3992286, e714a05 y 17d12a8).

Criterios de aceptación:
Haikus
  - Dado cualquier subheader en 820px o más, cuando lo miro, entonces arriba a la derecha hay una nube de alto fijo (60px) donde se escribe un haiku en japonés y después su versión en español, se mantiene, se borra y sigue el siguiente, en bucle.
  - Dada la lista, cuando la recorro, entonces son 10 haikus originales y el primero es sobre gambatte (darlo todo siempre).
  - Dado `prefers-reduced-motion`, cuando lo miro, entonces el haiku aparece completo sin animación y cambia cada tanto.
  - Dado un lector de pantalla, cuando recorre la página, entonces el haiku no se lee (`aria-hidden`); debajo de 820px no se muestra.
Asistente
  - Dado un tablero nuevo, cuando abro el asistente, entonces el objetivo recibe un color al azar de la paleta y no hay selector de color en el paso 1.
  - Dado un tablero sin color (`goalColor` vacío), cuando lo miro, entonces el objetivo es blanco con borde y texto de tinta.
  - Dado el campo de fecha meta, cuando hago clic en cualquier parte, entonces se abre el selector de fechas del navegador.
  - Dado cualquier paso, cuando lo miro, entonces los botones van debajo de la columna derecha.
Tablero
  - Dado un tablero, cuando miro el subheader, entonces el objetivo usa todo el ancho de su columna, con corte de línea equilibrado y sin nube.
Inicio
  - Dadas las tarjetas, cuando las miro, entonces el ícono va en magenta sobre un fondo de acento muy suave.
Pie
  - Dada cualquier pantalla, cuando miro el pie, entonces es una franja blanca alineada al contenedor, con letra de 12px y "Diseñado por Luis Carlos Romero León · uxuaria.com" con link.
Alcance: `HAIKUS`, `HK`, `haikuHTML`, `haikuTick`, `subHTML`, `homeHTML`, CSS `.haiku`, `.hk-*`; `A.new` (color al azar), `GCOL[0]=['','Blanco']`, `gcs()`, `--goal-bg`/`--goal-fg`, `wizHTML` (sin paleta, `.wside`), `input.datepick` con `showPicker()`; `.bd-title`, `.bd-main`; `.card-ico`; `footHTML`, `.foot`, `.foot-cred`.
Fuera de alcance / No tocar: el selector de color del panel del objetivo (sigue), datos y persistencia.
Dependencias: `subHTML` (patrón de pantalla), `GCOL`, `cardHTML`, `boardIcon`.
Estados (UI): sin carga ni error (todo es local). Con la pestaña oculta, el haiku se pausa.
Diseño: N/A (aprobado en la exploración).
A CONFIRMAR:
  - Revisión del japonés de los haikus por una persona nativa.
  - Si el selector de color se queda en el panel del objetivo.
Definición de hecho: la del AGENTS.md, más:
  - Ver el haiku escribirse sin que cambie el alto del subheader, en 1240px, y oculto en 375px.
  - Crear dos tableros y ver colores de objetivo distintos; abrir uno viejo sin color y verlo blanco.
