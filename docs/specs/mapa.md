# Feature: Mapa del tablero  ·  id: mapa
Historia de usuario: Como dueño de un tablero, quiero ver y editar el 9x9 completo o un pilar a la vez, para trabajar mi objetivo con visión global y foco.
Objetivo: grilla 9x9 con colores por pilar, inspector lateral para editar objetivo, pilar o acción (texto, prioridad, estado), vaciar con deshacer. Retrospectiva.
Criterios de aceptación:
  - Dado el mapa, cuando toco una casilla, entonces el inspector muestra objetivo, pilar o acción según `cellAt`.
  - Dado un pilar editado en su bloque, cuando miro el anillo central, entonces muestra el mismo texto (un solo dato).
  - Dado un ancho menor a 760px, cuando abro el mapa, entonces se ve un pilar a la vez con chips para cambiar.
  - Dado el foco en la grilla, cuando uso las flechas, entonces se mueve la selección.
  - Dado que vacío una casilla o pilar, cuando toco "Deshacer" en el aviso, entonces vuelve el contenido.
  - Dado el ejemplo, cuando lo abro, entonces veo el aviso y "Duplicar como mío", y no puedo eliminarlo.
Alcance: `mapHTML`, `gridHTML`, `blockHTML`, `cellHTML`, `toolbarHTML`, `inspHTML`, `patch`, teclado.
Fuera de alcance / No tocar: PDF.
Dependencias: `cellAt`, `NEI`, `getText`/`setText`, `boardStats`/`pillarStats`.
Estados (UI): casilla vacía con "+"; sin selección, el inspector invita a elegir una casilla.
Diseño: N/A
Definición de hecho: la del AGENTS.md.
