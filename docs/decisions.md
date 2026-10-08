# Decisiones

2026-10-08 - Toda la app en un solo `index.html`, sin framework ni build. Motivo: micro app simple de publicar como sitio estático (sembrada al adoptar, A CONFIRMAR si hubo otro motivo).
2026-10-08 - Guardar en `sessionStorage` y no en `localStorage`. Motivo: A CONFIRMAR (el footer dice que los tableros se borran al cerrar la pestaña; parece buscado por privacidad).
2026-10-08 - Sin importación de datos. Motivo: decisión de producto explícita en CLAUDE.md ("es a propósito"); el detalle del porqué A CONFIRMAR.
2026-10-08 - El PDF y el texto copiado son la forma de conservar el resultado. Motivo: consecuencia de la persistencia efímera.
2026-10-08 - jsPDF 2.5.1 incluido en `vendor/` en lugar de CDN. Motivo: no depender de una CDN (README).
2026-10-08 - Tablero de ejemplo con datos inventados, no eliminable, solo duplicable. Motivo: que quien llega vea un tablero completo sin riesgo de perderlo.
2026-10-08 - Los datos no salen del navegador (sin backend ni analytics). Motivo: A CONFIRMAR (privacidad del lector).
2026-10-08 - Adoptar spec-lite (docs/) para publicar la micro app en Uxuaria. Motivo: pasar de prueba de concepto a pieza publicada con trazabilidad.
