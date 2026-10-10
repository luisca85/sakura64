# Feature: Exportación en PDF con personaje y boletín  ·  id: export
Historia de usuario: Como persona que armó su tablero, quiero llevarme un PDF prolijo de 3 páginas con mi tablero, mis tareas y mi avance, para conservarlo fuera de la sesión del navegador.
Objetivo: rediseñar el PDF (3 páginas apaisadas, numeradas, con encabezado, pie y aviso legal) y mover "Exportar PDF" a un personaje flotante que da saltitos y, antes de la primera descarga de la sesión, pide suscribirse al boletín de Uxuaria (formulario público de Brevo). Aprobado en la exploración (rama `explorar/exportacion`, commits 053e55e, 5e12fa2 y la reversión e723c8e). Reemplaza el PDF descrito en `resumen-pdf.md`.

Criterios de aceptación:
PDF
  - Dado cualquier tablero, cuando exporto, entonces se descarga `sakura64-<objetivo>.pdf` con exactamente 3 páginas A4 apaisadas: el tablero de 9x9 a color, "Lista de tareas" y "Resumen general".
  - Dada cualquier página, cuando la miro, entonces tiene encabezado con el logo de sakura y "SAKURA 64", y pie con `uxuaria.com` e `info@uxuaria.com` (con link) y "Página N de 3".
  - Dada la página 3, cuando la miro, entonces al final hay un aviso legal en letra muy chica (5.8pt) con lo esencial de los términos y un link a las políticas (`LEGAL_URL`).
  - Dado un texto con comillas tipográficas, rayas o emojis, cuando exporto, entonces no hay caracteres rotos (`L()`), y los colores de pilar y su texto salen de `PHEX` y `PFG`.
  - Dado que el generador de PDF no cargó o falla, cuando exporto, entonces aparece un aviso y no se rompe la pantalla.
Personaje
  - Dada cualquier pantalla de tablero, cuando la miro, entonces abajo a la derecha hay un personaje fijo (cabeza rosa, cuerpo violeta) que da saltitos, con una nube arriba que explica la descarga y lleva el link "Descargar mi tablero" (ver `panel-de-tareas.md`); con `prefers-reduced-motion` no salta.
  - Dada la sesión sin suscripción, cuando toco el personaje, la nube o su link "Descargar mi tablero" (o "Descargar PDF" en "Mi avance"), entonces la nube se agranda con "Antes de descargar", el campo "Tu correo", la casilla de aceptación y "Suscribirme y descargar".
  - Dado el formulario, cuando envío un correo inválido o sin marcar la casilla, entonces veo el error y no se envía nada.
  - Dado un correo válido y la casilla marcada, cuando envío, entonces el botón dice "Enviando…", el correo va al formulario público de Brevo, la nube dice "¡Gracias por suscribirte! Tu PDF se está descargando." y se descarga el PDF.
  - Dado un error de red al enviar, cuando falla, entonces veo un mensaje de error y puedo reintentar.
  - Dada la sesión ya suscripta (`harada-sub`), cuando toco el personaje, entonces el PDF se descarga directo.
  - Dado el formulario abierto, cuando presiono Esc o toco ×, entonces se cierra; al abrir otro tablero vuelve a la nube chica.
Alcance: `buildPDF` (3 páginas, `logoPNG`, `PDF_CONTACT`, `LEGAL_URL`), `exportPDF`, `MASCOT_SVG`, `mascotHTML`, `isSubscribed`, `subscribe`, `NEWSLETTER_URL`, estado `S.mascot`, acciones `export`, `mascot`, `mascot-close`, envío del formulario `data-form="sub"`, Esc, CSS `.mascot`, `.mc-*`, `@keyframes mc-hop`. Clave nueva `harada-sub` en `sessionStorage`.
Fuera de alcance / No tocar: "Copiar resumen como texto", la pestaña "Mi avance", el modelo de datos.
Dependencias: `vendor/jspdf.umd.min.js` 2.5.1, `PHEX`, `PFG`, `L()`, `slug`, `boardStats`, `logo()`, formulario público de Brevo (`sibforms.com`, POST `no-cors`, sin doble opt-in).
Estados (UI): idle (nube chica), form (formulario), enviando, error, done. La respuesta de Brevo no se puede leer (`no-cors`): solo se detectan errores de red.
Diseño: N/A (aprobado en la exploración; el personaje se basa en la imagen de referencia del usuario).
A CONFIRMAR:
  - Privacidad y Términos deben decir que el correo se envía a Brevo para el boletín; hoy dicen que no se comparten datos (condición para publicar en abierto).
  - `LEGAL_URL` apunta a la dirección pública de la app (`https://sakura64.uxuaria.com`), donde están las políticas en el pie.
  - Probar una suscripción real con un correo del usuario en el sitio publicado.
Conocido:
  - Sin doble opt-in, por decisión de producto.
  - Un correo ya suscripto o rechazado por Brevo se ve igual que un éxito (`no-cors`).
Definición de hecho: la del AGENTS.md, más:
  - Exportar el ejemplo y un tablero nuevo, abrir el PDF y ver las 3 páginas, colores, logo, links y aviso legal.
  - Recorrer el formulario con teclado (Tab, Esc) en 1240px y 375px, en claro y en oscuro.
