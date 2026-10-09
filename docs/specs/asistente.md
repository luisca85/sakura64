# Feature: Asistente de creación  ·  id: wiz
Historia de usuario: Como persona que arranca su tablero, quiero armar el objetivo y los pilares viendo los bloques del tablero mientras escribo, para entender desde el primer momento cómo se arma un tablero Harada y no enfrentarme a 81 casillas vacías.
Objetivo: crear un tablero en 2 pasos visuales, con el diseño en bloques aprobado en la exploración (rama `explorar/onboarding`). Paso 1: el objetivo se escribe dentro de un bloque grande, con color, ejemplos y fecha meta. Paso 2: el bloque de 3x3 con el objetivo en el centro y 8 casillas de pilar. Al terminar se abre el tablero completo, donde las acciones se escriben directo en la grilla (ver `mapa.md`). Reemplaza al asistente de formularios.
Criterios de aceptación:
Paso 1, Objetivo
  - Dado un tablero nuevo, cuando abro el asistente, entonces veo los pasos "Objetivo" y "Pilares", y el foco queda dentro del bloque del objetivo.
  - Dado el paso Objetivo, cuando escribo, entonces el texto aparece dentro del bloque y un contador muestra "N de 140".
  - Dado un tablero nuevo, cuando abro el asistente, entonces el objetivo ya tiene un color al azar de la paleta (sin selector en el paso; ver `haikus.md`), y ese color se ve en la casilla del objetivo del mapa y en el PDF.
  - Dado el paso Objetivo, cuando toco un ejemplo, entonces su texto reemplaza el del bloque y se puede editar.
  - Dado el paso Objetivo, cuando elijo una fecha meta, entonces aparece la cuenta regresiva debajo.
  - Dado el paso Objetivo vacío, cuando miro "Siguiente: definir pilares", entonces está deshabilitado; con texto se habilita.
Paso 2, Pilares
  - Dado el paso Pilares, cuando lo abro, entonces veo un bloque de 3x3 con el objetivo (con su color) en el centro y 8 casillas con ideas en gris que no se guardan.
  - Dado el paso Pilares, cuando escribo en una casilla, entonces se pinta con el color de su pilar y sube el contador "N de 8 pilares".
  - Dado el paso Pilares, cuando presiono Enter en una casilla, entonces el foco pasa al pilar siguiente en orden horario (1 a 8) sin insertar un salto de línea.
  - Dado el paso Pilares sin ningún pilar escrito, cuando miro "Terminar y ver el tablero completo", entonces está deshabilitado; con al menos un pilar se habilita.
  - Dado al menos un pilar, cuando toco "Terminar y ver el tablero completo" (o presiono Enter en el último pilar y después el botón), entonces se abre el tablero en la pestaña Mapa con la grilla editable y un aviso que invita a escribir las acciones.
General
  - Dado el paso Pilares, cuando toco "Atrás", entonces vuelvo al paso Objetivo con lo escrito.
  - Dado un tablero sin objetivo, cuando toco "Cancelar", entonces se descarta y vuelvo al inicio.
  - Dado un ícono "?" junto a un campo, cuando paso el mouse o llego con el teclado, entonces veo una ayuda corta, y el tooltip oculto no genera desplazamiento horizontal.
  - Dado que recargo la página a mitad del asistente, cuando vuelve a cargar, entonces estoy en el inicio y el tablero a medio armar aparece en la lista.
  - Dado un ancho de 375px, cuando recorro los 2 pasos, entonces todo entra sin desplazamiento horizontal y el bloque del objetivo se ve más bajo (4:3).
  - Dado una ventana baja, cuando miro un bloque, entonces su tamaño se limita para entrar en la altura visible.
Alcance: `wizHTML`, `wizSync`, `wizCounts`, `wcellHTML`, `wstaticHTML`, `tipHTML`, paleta `GCOL` y `gcs()`, acciones `wiz-*` (incluida `wiz-color`; se eliminan `wiz-pillar`, `wiz-nextp` y `wizMapHTML` del paso 3), Enter en `.wiz textarea.wct`, CSS del asistente (`.wgrid`, `.wgoal`, `.wblk`, `.wc`, `.swatches`, `.tipi`; se elimina el CSS solo del paso 3: `.wgrid.three`, `.wblk-h`, `.wmap*`, `.wmb*`). Campo `goalColor` en el tablero, aplicado también a `.cell.goal`, `.mini .m-goal`, `.recall` y al objetivo en `buildPDF`.
Fuera de alcance / No tocar: la grilla del Mapa y los paneles por casilla (`mapa.md`, `panel-casilla.md`), el onboarding animado, la persistencia (`sessionStorage`, `harada-v1`).
Dependencias: `blankBoard` (suma `goalColor: ''`), `cellAt`/`NEI`, `PHEX` y `--p1`..`--p8`, `buildPDF`/`rgb()`, `openBoard`, `save`, `render`, y la grilla editable de `mapa.md` para cargar las acciones.
Estados (UI): vacío = botones deshabilitados y textos de ayuda en gris. Sin carga ni error (todo es local). Tableros guardados sin `goalColor` usan el color por defecto.
Diseño: N/A (aprobado en la rama `explorar/onboarding`, commits 82a060f y 5f34e4b).
Paleta de colores del objetivo: Blanco (sin color, borde de tinta), Granate #9E2A2B, Bosque #1D5C4D, Índigo #3E2C7A, Ámbar #8A5A0B y Petróleo #0E5A73.
Definición de hecho: la del AGENTS.md, más:
  - Recorrer los 2 pasos con teclado solo (Tab, Enter) y con mouse, en 1240px y en 375px, en claro y en oscuro.
  - Elegir un color, terminar y verificar ese color en el mapa, la tarjeta del inicio y el PDF descargado.
  - Abrir un tablero creado antes del cambio (sin `goalColor`) y verificar que se ve igual que antes.
