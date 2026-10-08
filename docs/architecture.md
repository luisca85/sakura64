# Arquitectura

## Módulos (todos dentro del `<script>` de `index.html`)
- Helpers: `$`, `esc`, `uid`, fechas (`dk`, `pdk`, `addDays`, `dow`, `today0`), constantes
  (`DAYS`, `NEI`, `STATUS`, `PRI`, `PHEX`).
- Modelo: `cellAt`, `blankBoard`, `EX` + `buildExample` (tablero de ejemplo),
  `getText` / `setText`.
- Tareas y estadísticas: `isDue`, `streak`, `rate`, `freqLabel`, `boardStats`,
  `pillarStats`, `countdown`, `weekData`.
- Persistencia: `load`, `save` (debounce 250 ms), `markSeen`.
- Vistas (devuelven HTML como string): `onbHTML`/`updateOnb` (onboarding), `homeHTML`
  y `cardHTML` (inicio), `wizHTML` (asistente de 3 pasos), `boardHTML` con pestañas
  `mapHTML` (grilla + `inspHTML`), `todayHTML` (Hoy), `sumHTML` (Resumen y PDF).
- Render: `render()` redibuja todo `#app` preservando foco y selección;
  `patch()` actualiza solo grilla y métricas mientras se escribe; `toast()` con deshacer.
- Exportación: `buildPDF` / `exportPDF` (jsPDF, A4: mapa apaisado + detalle),
  `textSummary` (copiar como texto), `slug` para el nombre del archivo.
- Eventos: objeto `A` de acciones despachadas por `data-act`; inputs con `data-bind`;
  teclado en la grilla (flechas); cambio de ancho re-renderiza.

## Dónde vive cada cosa
- `index.html`: toda la app.
- `vendor/jspdf.umd.min.js`: jsPDF 2.5.1 local, para no depender de una CDN.
- `README.md`: cómo probar y publicar. `CLAUDE.md`: contexto para el agente.
- `docs/`: esta documentación spec-lite.

## Modelo de datos
Tablero: `{id, example, goal, goalDate, pillars[8], actions[8][8], tasks[], created}`.
- Acción: `{t, pri: alta|media|baja, st: sin|curso|lograda}`.
- Tarea: `{id, k, i, title, freq: daily|weekdays|days|once, days[], done{AAAA-MM-DD: true}, start}`.
  `k`/`i` apuntan a pilar/acción; `days` en base lunes = 0.
Estado de UI en `S` (vista, tablero abierto, pestaña, modo, selección, asistente). No se persiste.

## Persistencia
`sessionStorage`, clave `harada-v1` → `{boards: [...]}`; `harada-seen` = "1" tras el
onboarding. Si no hay nada guardado se carga solo el ejemplo. Todo en try/catch: sin
storage la app funciona igual, sin guardar.

## Publicación
Sitio estático; README describe Cloudflare Pages (sin build, salida `/`).
Destino en Uxuaria (dominio, ruta, proyecto): A CONFIRMAR. Ver `specs/publicacion.md`.
