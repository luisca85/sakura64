# Feature: Resumen y PDF  ·  id: pdf
Historia de usuario: Como persona que armó su tablero, quiero descargarlo en PDF o copiarlo como texto, para conservarlo porque la app no guarda nada al cerrar la pestaña.
Objetivo: pestaña Resumen con avance por pilar, tabla de tareas y semana; exportación PDF (mapa 9x9 a color apaisado + detalle por pilar y tareas) y texto plano. Retrospectiva.
Criterios de aceptación:
  - Dado cualquier tablero, cuando toco "Exportar PDF", entonces se descarga `<slug-del-objetivo>.pdf` sin conexión a internet.
  - Dado un texto con comillas tipográficas, rayas o emojis, cuando exporto, entonces el PDF no muestra caracteres rotos (`L()`).
  - Dado que el navegador no permite el portapapeles, cuando toco "Copiar resumen como texto", entonces aparece un textarea seleccionado.
  - Dado un cambio en un color de pilar, cuando exporto, entonces el PDF usa el mismo color que la pantalla (`PHEX`).
Alcance: `sumHTML`, `textSummary`, `buildPDF`, `exportPDF`, `slug`, `L`, acciones `export`, `copysum`.
Fuera de alcance / No tocar: importación (no existe a propósito).
Dependencias: `vendor/jspdf.umd.min.js` 2.5.1, `PHEX`.
Estados (UI): sin tareas, la tabla muestra una nota. Error de exportación: A CONFIRMAR (no se ve manejo explícito en `exportPDF`).
Diseño: N/A
Definición de hecho: la del AGENTS.md, más abrir el PDF generado en claro y en oscuro.
