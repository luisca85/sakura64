# Feature: Asistente de creación  ·  id: wiz
Historia de usuario: Como persona que arranca su tablero, quiero que me guíen paso a paso, para no enfrentarme a 81 casillas vacías.
Objetivo: crear un tablero en 3 pasos: objetivo (con ejemplos y fecha meta opcional), pilares y acciones por pilar. Retrospectiva.
Criterios de aceptación:
  - Dado el paso Objetivo vacío, cuando miro el botón Siguiente, entonces está deshabilitado; al escribir o elegir un ejemplo se habilita.
  - Dado el paso Pilares, cuando hay al menos un pilar escrito, entonces puedo avanzar.
  - Dado el paso Acciones, cuando recorro los pilares definidos y toco "Terminar y abrir el tablero", entonces se abre el tablero en el Mapa.
  - Dado un tablero sin objetivo, cuando toco "Cancelar", entonces se descarta y vuelvo al inicio.
Alcance: `wizHTML`, `wizSync`, `WIZ_EX`, `WIZ_PH`, acciones `wiz-*`.
Fuera de alcance / No tocar: modelo de tablero (`blankBoard`).
Dependencias: `blankBoard`, `save`, `render`/`patch`.
Estados (UI): vacío = botones deshabilitados. Sin carga ni error.
Diseño: N/A
Definición de hecho: la del AGENTS.md.
