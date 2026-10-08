# Feature: Tareas y Hoy  ·  id: tareas
Historia de usuario: Como dueño de un tablero, quiero convertir acciones en tareas que se repiten y marcarlas cada día, para sostener el avance con rachas.
Objetivo: tareas por acción con frecuencia (todos los días, lunes a viernes, días elegidos, una vez), vista Hoy agrupada por pilar, racha y cumplimiento de 7 y 14 días. Retrospectiva.
Criterios de aceptación:
  - Dada una acción sin texto, cuando abro su inspector, entonces se pide escribirla antes de agregar tareas.
  - Dada una tarea "Días que elijo" con Lun y Mié, cuando es martes, entonces no aparece en Hoy.
  - Dada una tarea de hoy, cuando la marco, entonces se registra en `done[AAAA-MM-DD]` y sube la racha.
  - Dada una tarea "Una sola vez" ya cumplida, cuando pasa el día, entonces deja de aparecer en Hoy.
  - Dado un tablero sin tareas, cuando abro Hoy, entonces veo el estado vacío con acceso al mapa.
Alcance: `tasksSection`, `isDue`, `streak`, `rate`, `freqLabel`, `todayHTML`, `weekData`, acciones `toggle`, `deltask`, `day`, formulario `task`.
Fuera de alcance / No tocar: recordatorios o notificaciones (no existen).
Dependencias: `dow` (lunes = 0), `today0`, `dk`.
Estados (UI): vacío en Hoy y en el inspector; "Hoy no te toca ninguna tarea". Sin carga ni error.
Diseño: N/A
Definición de hecho: la del AGENTS.md, más probar una tarea de cada frecuencia.
