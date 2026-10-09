# Decisiones

2026-10-08 - Toda la app en un solo `index.html`, sin framework ni build. Motivo: micro app simple de publicar como sitio estático (sembrada al adoptar, A CONFIRMAR si hubo otro motivo).
2026-10-08 - Guardar en `sessionStorage` y no en `localStorage`. Motivo: A CONFIRMAR (el footer dice que los tableros se borran al cerrar la pestaña; parece buscado por privacidad).
2026-10-08 - Sin importación de datos. Motivo: decisión de producto explícita en CLAUDE.md ("es a propósito"); el detalle del porqué A CONFIRMAR.
2026-10-08 - El PDF y el texto copiado son la forma de conservar el resultado. Motivo: consecuencia de la persistencia efímera.
2026-10-08 - jsPDF 2.5.1 incluido en `vendor/` en lugar de CDN. Motivo: no depender de una CDN (README).
2026-10-08 - Tablero de ejemplo con datos inventados, no eliminable, solo duplicable. Motivo: que quien llega vea un tablero completo sin riesgo de perderlo.
2026-10-08 - Los datos no salen del navegador (sin backend ni analytics). Motivo: A CONFIRMAR (privacidad del lector).
2026-10-08 - Adoptar spec-lite (docs/) para publicar la micro app en Uxuaria. Motivo: pasar de prueba de concepto a pieza publicada con trazabilidad.
2026-10-08 - El asistente pasa a 2 pasos (Objetivo y Pilares); las acciones se escriben en la grilla editable del tablero. Motivo: el paso 3 repetía la grilla y es mejor tener una sola forma de cargar acciones.
2026-10-08 - El objetivo tiene color propio (campo `goalColor`, vacío = color por defecto), visible en el tablero, el inicio y el PDF. Motivo: pedido para que el objetivo se vea como un bloque personalizable; la paleta final queda A CONFIRMAR.
2026-10-08 - Recargar a mitad del asistente vuelve al inicio con el tablero a medio armar en la lista. Motivo: se mantiene a propósito; no se guarda el paso del asistente.
2026-10-08 - La grilla del Mapa se edita en el lugar y el inspector lateral se reemplaza por paneles por casilla. Motivo: escribir rápido en la grilla y entrar al detalle solo cuando hace falta.
2026-10-08 - Las acciones de un pilar sin nombre quedan bloqueadas en la grilla. Motivo: respetar el orden del método (primero el pilar, después sus acciones).
2026-10-08 - El texto largo se corta en la casilla; se ve completo al pasar el mouse y en el panel. Motivo: mantener la grilla estable y legible.
2026-10-08 - Pestañas renombradas: "Hoy" pasa a "Tus tareas para hoy" y "Resumen y PDF" a "Mi avance". El progreso general va como barra en el encabezado, no como pestaña. Motivo: nombres más claros para el lector y evitar una pestaña que repita "Mi avance".
2026-10-08 - Vaciar un pilar borra solo su nombre: sus acciones y tareas se conservan atenuadas y de solo lectura hasta que el pilar vuelva a tener nombre. Motivo: no perder trabajo por un borrado del pilar.
2026-10-08 - El panel de una acción bloqueada muestra "Primero escribí el pilar" con un botón al pilar, en lugar de saltearla en anterior y siguiente. Motivo: que la navegación sea predecible y explique por qué no se puede editar.
2026-10-08 - Los paneles por casilla son pantallas dentro de la pestaña Mapa con entradas propias en el historial del navegador (con el id del tablero), no modales. Motivo: poder ir y volver con migas de pan, anterior y siguiente, y el botón "atrás".
2026-10-08 - Se toma como fuente de verdad la exploración aprobada (rama `explorar/onboarding`) y se revierten tres decisiones de arriba: el asistente sigue en 3 pasos con bloques (Objetivo, Pilares y Acciones con el tablero completo al lado), las acciones de un pilar sin nombre no se bloquean, y no hay aviso de acción bloqueada. Motivo: malentendido al escribir las specs; lo aprobado es lo probado en la exploración.
2026-10-08 - "Vaciar pilar" borra solo el nombre; sus acciones y tareas se conservan y siguen editables. Motivo: es el comportamiento aprobado en la exploración y no se pierde trabajo.
2026-10-08 - El asistente conserva el diseño en bloques de la exploración pero queda en 2 pasos (Objetivo y Pilares); al terminar abre el Mapa, donde las acciones se escriben en la grilla editable. Motivo: pedido explícito; el paso 3 repetía la grilla del tablero.
2026-10-08 - La app se llama "Objetivo 64"; "Harada" queda solo como mención de inspiración en los términos. Motivo: evitar usar como nombre del producto el de un método y una persona con los que no hay afiliación.
2026-10-08 - Objetivo 64 es gratuita y sin fines comerciales: no se cobra, no hay publicidad, no se venden ni comparten datos y no hay productos ni servicios pagos. Se declara en el pie, en Privacidad y en Términos. Motivo: decisión de producto.
2026-10-08 - Las claves internas de `sessionStorage` (`harada-v1`, `harada-seen`) no se renombran. Motivo: no se ven y cambiarlas haría perder los tableros abiertos en la sesión.
2026-10-09 - Lenguaje visual inspirado en la web japonesa "amable" (referencia choooodoii.com): Noto Sans JP, bordes finos sin sombras, píldoras de 2px, acento amarillo, globos de diálogo. Motivo: pedido de producto para una interfaz ordenada y liviana.
2026-10-09 - Patrón fijo de pantalla: navegación, subheader a todo el ancho con papel cuadriculado y zona de trabajo. Motivo: jerarquía clara y repetible entre herramientas y contenido.
2026-10-09 - Las acciones principales son links subrayados con flecha, no botones rellenos. Motivo: coherencia con la referencia.
2026-10-09 - Pilares en rojo, naranja, amarillo, verde manzana, turquesa, cian, azul y magenta, con color de texto por pilar (`--f1`..`--f8`, `PFG`). Reemplaza la paleta anterior. Motivo: pedido de producto; el texto por pilar asegura contraste de 4.5:1.
2026-10-09 - Íconos del set "Japan Icons (Community)" de Figma, incrustados en `index.html`; logo de flor de sakura con pistilos rojos. Motivo: identidad japonesa coherente; incrustados para que la app funcione sin servidor. Licencia: A CONFIRMAR.
2026-10-09 - La app se llama "SAKURA 64" (reemplaza a "Objetivo 64"). "Harada" queda solo como mención del método que inspira la grilla. Las claves internas `harada-v1` y `harada-seen` no se renombran. Motivo: pedido de producto; el nombre acompaña la identidad visual (logo de sakura).
2026-10-09 - El acento pasa de amarillo a magenta `#E4007F` con texto blanco. Motivo: pedido de producto.
2026-10-09 - Se construye primero `legales` y después `visual` sobre `main`. El ícono de tarjeta se calcula por posición y la página legal usa el patrón de subheader. Motivo: las dos ramas tocan el mismo archivo; lo demás se acepta como quedó en la exploración.
