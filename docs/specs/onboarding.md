# Feature: Onboarding  ·  id: onb
Historia de usuario: Como lector que llega desde un link público, quiero entender el método Harada en pocos pasos, para animarme a armar mi tablero.
Objetivo: introducción animada de 4 pasos (objetivo, 8 pilares, 64 acciones, tareas) sobre una grilla 9x9 que se va encendiendo. Es retrospectiva: describe lo que ya existe.
Criterios de aceptación:
  - Dado que es la primera visita en la pestaña, cuando abro la app, entonces veo el paso 1 del onboarding.
  - Dado el onboarding, cuando toco "Siguiente", "Atrás" o un punto, entonces cambia el paso y se anima la grilla.
  - Dado el paso 4, cuando elijo "Crear mi tablero" o "Ver el ejemplo", entonces voy al asistente o al ejemplo y `harada-seen` queda en "1".
  - Dado que toqué "Saltar introducción", cuando recargo, entonces entro directo al inicio.
Alcance: `onbHTML`, `ONB`, `updateOnb`, acciones `onb-*`, `markSeen`.
Fuera de alcance / No tocar: contenido del ejemplo (`EX`).
Dependencias: `cellAt`, `EX`, `sessionStorage`.
Estados (UI): sin storage disponible se muestra siempre (no rompe). Sin carga ni error de red.
Diseño: N/A. En celular (hasta 859px) el diseño cambia; ver `ajustes-movil.md`. Botones y alineación de escritorio en `ajustes-escritorio.md`.
Definición de hecho: la del AGENTS.md.
