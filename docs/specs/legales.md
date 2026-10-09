# Feature: Información legal y nombre de la app  ·  id: legal
Historia de usuario: Como lector que prueba la herramienta desde un link público, quiero saber qué pasa con lo que escribo, en qué condiciones la uso y de dónde viene el método, para usarla con confianza.
Objetivo: la app pasa a llamarse "SAKURA 64" y suma una página legal con tres secciones (Privacidad, Términos de uso y Créditos y licencias), a la que se llega desde el pie de página. Deja claro que la herramienta es gratuita y sin fines comerciales, y que el método Harada es solo la inspiración. Aprobado en la exploración (rama `explorar/temas-legales`, commits ebf4e59 y 46678ea).

Criterios de aceptación:
Nombre
  - Dada cualquier pantalla, cuando la miro, entonces la marca del encabezado, el onboarding, el título de la pestaña del navegador y la descripción para buscadores dicen "SAKURA 64".
  - Dado el inicio, cuando lo abro, entonces el título dice "Tus tableros" y el botón "Nuevo tablero".
  - Dado un tablero, cuando exporto el PDF, entonces el encabezado dice "SAKURA 64", el título del documento es "SAKURA 64" y el archivo se llama `sakura64-<objetivo>.pdf`.
  - Dado un tablero, cuando copio el resumen como texto, entonces la primera línea es "SAKURA 64".
  - Dado el texto visible de la app, cuando lo recorro, entonces "Harada" solo aparece en la sección Inspiración de los términos.
  - Dados tableros guardados en la sesión antes del cambio, cuando recargo, entonces siguen ahí (las claves internas `harada-v1` y `harada-seen` no cambian).
Acceso
  - Dado el pie de página de cualquier pantalla con encabezado, cuando lo miro, entonces veo "SAKURA 64 es una herramienta gratuita y sin fines comerciales." y los links "Privacidad", "Términos de uso" y "Créditos y licencias".
  - Dado un link del pie, cuando lo toco, entonces se abre la página legal en esa sección, arriba de todo.
  - Dada la página legal, cuando toco otra sección en su barra, entonces cambia el contenido y la sección actual queda marcada (`aria-current="page"`).
Contenido
  - Dada Privacidad, cuando la leo, entonces explica qué datos se usan, que se guardan solo en `sessionStorage` y se borran al cerrar la pestaña, que el PDF y el resumen se generan en el dispositivo, que no hay servidor, cuentas, cookies, analítica ni publicidad, que no se venden ni comparten datos, y que Google Fonts recibe datos técnicos como la IP.
  - Dados los Términos, cuando los leo, entonces incluyen: gratuita y sin fines comerciales (no se cobra, no hay publicidad, no se venden ni comparten datos, no hay productos ni servicios pagos), qué es y qué no es (no es asesoramiento profesional), sin garantías, el contenido es de quien lo escribe, inspiración en el método de Takashi Harada sin afiliación, propiedad del sitio y ley aplicable.
  - Dados los Créditos, cuando los leo, entonces nombran jsPDF 2.5.1 (licencia MIT), las tipografías Bricolage Grotesque y Atkinson Hyperlegible, y que el ejemplo usa datos inventados.
  - Dado un dato que falta, cuando lo miro, entonces aparece resaltado como "[A COMPLETAR: ...]" y arriba de la página hay un aviso de borrador.
Visual
  - Dado un ancho de 375px y de 1240px, en claro y en oscuro, cuando abro cada sección, entonces no hay desplazamiento horizontal y el texto se lee en una columna de hasta 68 caracteres.

Alcance: `TBD`, `LEGAL`, `legalHTML`, `footHTML` (texto nuevo y `.foot-links`), vista `S.view='legal'` y `S.legal`, acción `legal`, rama `legal` en `render`, CSS `.legal*`, `mark.tbd`, `.foot-links`. Cambios de nombre en `<title>`, meta description, `barHTML`, `onbHTML`, `homeHTML`, `ONB` (paso 1), `aria-label` de la grilla, `textSummary`, `buildPDF` y `exportPDF`.
Fuera de alcance / No tocar: las claves de `sessionStorage`, el logo y el favicon, servir las tipografías desde el propio sitio, el texto de los datos marcados A COMPLETAR (hasta que se definan), el contenido de `publicacion.md`.
Dependencias: `render`, `barHTML`, `footHTML`, `.tab` (estilo de pestañas del encabezado del tablero), `slug`, `buildPDF`.
Estados (UI): sin datos legales definidos, los marcadores amarillos y el aviso de borrador. Sin carga ni error (todo es local).
Diseño: N/A (aprobado en la rama `explorar/temas-legales`).
A CONFIRMAR (texto legal; no se publica hasta completarlos):
  - Correo de contacto.
  - Responsable y titular del sitio (nombre o razón social, país y domicilio).
  - Ley y jurisdicción aplicables.
  - Fecha de última actualización.
  - Licencia de cada tipografía (Google Fonts indica SIL Open Font License 1.1).
  - Revisión con asesoría legal de la mención al método Harada como inspiración.
  - Si las tipografías se sirven desde el propio sitio para que ningún dato llegue a Google.
  - Cuándo se quitan el aviso de borrador y los marcadores (condición para publicar).
Definición de hecho: la del AGENTS.md, más:
  - Buscar "Harada" en el texto visible y encontrarlo solo en la sección Inspiración.
  - Recargar con tableros creados antes del cambio y verificar que siguen.
  - Abrir las tres secciones desde el pie en 375px y 1240px, en claro y en oscuro.
  - Exportar el PDF y copiar el resumen y verificar el nombre nuevo.
  - Actualizar README, CLAUDE.md, AGENTS.md y architecture.md con el nombre "SAKURA 64".
