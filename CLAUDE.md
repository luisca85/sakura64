# SAKURA 64

Aplicación web de una sola página (SAKURA 64) para armar un tablero de 64 acciones inspirado en el método Harada. Público objetivo: lectores de habla hispana de LATAM que prueban la herramienta desde un link público.

## Estructura

- Todo vive en `index.html`: CSS, marcado inicial y un único `<script>` (IIFE, JavaScript sin framework).
- `vendor/jspdf.umd.min.js` genera el PDF en el navegador.
- No hay build. Para probar, abrí el archivo o usá `python3 -m http.server`.

## Modelo de datos

Un tablero es un objeto: `goal`, `goalDate`, `pillars[8]` (texto), `actions[8][8]` (`{t, pri, st}`) y `tasks[]` (`{id, k, i, title, freq, days, done, start}`).

- `cellAt(r, c)` convierte una casilla de la grilla de 9x9 en objetivo, pilar o acción. Cada pilar aparece dos veces (anillo del centro y centro de su bloque) pero es un solo dato.
- `freq` de una tarea: `daily`, `weekdays`, `days` (con `days` en base lunes = 0) o `once`.
- Los tableros se guardan en `sessionStorage` bajo la clave `harada-v1`. La clave `harada-seen` marca que ya se vio el onboarding.

## Decisiones de producto

- No hay importación de datos. Es a propósito.
- Exportar a PDF es la forma de conservar el resultado. También hay "Copiar resumen como texto".
- El tablero de ejemplo (`id: ejemplo`) usa datos inventados y no se puede eliminar, solo duplicar.
- Los datos no salen del navegador de cada persona.

## Convenciones

- Texto de la interfaz en español rioplatense con voseo (por ejemplo "Creá", "Elegí").
- Sin rayas largas (em dashes) en los textos en español.
- Colores definidos como variables CSS en `:root`, con versión oscura. Los 8 colores de pilar (`--p1` a `--p8`) también están repetidos en `PHEX` dentro del script para el PDF. Si cambiás uno, cambialo en los dos lugares.
- La interfaz se vuelve a dibujar completa con `render()`. Mientras se escribe en un campo se usa `patch()` para no perder el foco.

## Pendiente de ideas

- Micro objetivos dentro de cada acción (hoy se resuelven con tareas).
- Más plantillas de ejemplo.
