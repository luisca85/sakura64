# Constitución de SAKURA 64

Propósito: SAKURA 64, micro app web de una sola página para armar un tablero
inspirado en el método Harada (1 objetivo, 8 pilares, 64 acciones), convertir acciones en tareas
recurrentes y llevarse el resultado en PDF. Público: lectores hispanohablantes de
LATAM que la prueban desde un link público de Uxuaria.

## Principios
- Simplicidad: todo vive en `index.html` (CSS, marcado y un único `<script>` IIFE,
  sin framework). Sin build, sin servidor, sin base de datos. No agregar
  dependencias ni pasos de build sin registrarlo en decisions.md.
- Privacidad: los datos no salen del navegador. Nada de `fetch`, analytics ni
  servicios de terceros que reciban contenido del usuario. Única carga externa
  permitida: Google Fonts, con fuente del sistema como respaldo.
- Persistencia efímera a propósito: `sessionStorage` (`harada-v1`, `harada-seen`).
  Se pierde al cerrar la pestaña; la forma de conservar es el PDF o el texto copiado.
  No hay importación de datos (decisión de producto).
- Seguridad de render: todo texto del usuario que entra a HTML pasa por `esc()`.
  El PDF y el texto plano usan `L()` (normaliza a Latin-1 para jsPDF).
- Accesibilidad: roles y `aria-*` en tabs, radios, checkboxes y progreso; navegación
  por teclado en la grilla; foco preservado al re-renderizar (`data-fid`).
- Responsividad: debajo de 760px la grilla se muestra un pilar a la vez (`narrow()`).
- Navegación: los paneles por casilla usan `history.pushState` con `{det, b}`; toda
  entrada nueva del historial lleva el id del tablero.
- Sistema visual: colores como variables CSS en `:root` con versión oscura. Los 8
  colores de pilar (`--p1`..`--p8`) están duplicados en `PHEX` para el PDF, y su
  color de texto (`--f1`..`--f8`) en `PFG`: si cambiás uno, cambiá los dos y
  verificá contraste de 4.5:1. Sin sombras, bordes finos, esquinas de 2px en
  píldoras, acento magenta `--accent` con texto blanco.
- Patrón de pantalla: navegación, subheader a todo el ancho (`subHTML`, papel
  cuadriculado) y zona de trabajo. Toda pantalla nueva lo respeta.
- Idioma: español rioplatense con voseo ("Creá", "Elegí"). Sin rayas largas (em dash).

## Comportamiento del agente
- Planificar antes de codear. Cambios acotados, uno por vez.
- Preguntar ante la ambigüedad. No inventar datos, URLs ni endpoints: marcar A CONFIRMAR.
- Redibujar con `render()`; mientras se escribe en un campo usar `patch()` para no
  perder el foco.
- Listar los archivos modificados al terminar.

## Zonas sensibles (tocar con cuidado)
- `cellAt(r, c)` y `NEI`: mapean la grilla 9x9 al modelo. Cada pilar aparece dos
  veces en la grilla pero es un solo dato. Un error acá desordena todo el tablero.
- Forma del objeto tablero y la clave `harada-v1`: si cambia, `load()` tiene que
  seguir aceptando lo guardado en la sesión (o descartar sin romper).
- Tablero de ejemplo (`id: ejemplo`): no se puede eliminar, solo duplicar.
- `buildPDF()`: depende de `PHEX`, `L()` y de `vendor/jspdf.umd.min.js` (2.5.1).
- `isDue`, `streak`, `rate`: `days` en base lunes = 0 (`dow()`), no domingo.

## Definición de hecho
- El script inline compila:
  `awk '/^<script>$/{f=1;next}/^<\/script>/{f=0}f' index.html > /tmp/h.js && node --check /tmp/h.js`
- Sin errores en la consola del navegador al recorrer el test de regresión.
- Texto nuevo de interfaz en voseo y sin em dashes.
- Si se tocó un color de pilar: `:root`, modo oscuro, `PHEX` y `PFG` coinciden.

## Test de regresión (a mano, con `python3 -m http.server 8080`)
1. Pestaña nueva: aparece el onboarding (4 pasos); "Saltar" lleva al inicio y no
   vuelve a aparecer al recargar.
2. Crear un tablero con el asistente en bloques (objetivo con color y pilares); al
   terminar se abre la grilla. Recargar: persiste.
3. En el Mapa, escribir una acción directo en la grilla (Enter pasa a la siguiente),
   abrir su panel con el botón ↗, cambiar prioridad y estado, agregar una tarea
   "Lun, Mié, Vie"; en "Tus tareas para hoy" marcarla si corresponde y ver la racha.
   Volver con el "atrás" del navegador: panel, después grilla.
4. "Exportar PDF" descarga un PDF con el mapa a color y el detalle. "Copiar resumen
   como texto" copia (o muestra el textarea si no hay portapapeles).
5. Abrir el ejemplo: no tiene botón de eliminar; "Duplicar como mío" crea una copia editable.
6. Eliminar un tablero propio y usar "Deshacer".
7. Repetir 2 a 4 en ancho de celular (375px) y en modo oscuro.
