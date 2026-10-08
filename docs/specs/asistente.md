# Feature: Asistente de creación  ·  id: wiz
Historia de usuario: Como persona que arranca su tablero, quiero armar el objetivo y los pilares viendo el bloque del tablero mientras escribo, para entender desde el primer momento cómo se arma un tablero Harada y no enfrentarme a 81 casillas vacías.
Objetivo: crear un tablero en 2 pasos visuales. Paso 1: el objetivo se escribe dentro de un bloque grande, con color, ejemplos y fecha meta. Paso 2: el bloque de 3x3 con el objetivo en el centro y 8 casillas de pilar alrededor. Al terminar se abre el tablero completo, donde las acciones se escriben directo en la grilla (ver `mapa.md`). Reemplaza al asistente de 3 pasos con formularios.
Criterios de aceptación:
  - Dado un tablero nuevo, cuando abro el asistente, entonces veo los pasos "Objetivo" y "Pilares", y el foco queda dentro del bloque del objetivo.
  - Dado el paso Objetivo, cuando escribo, entonces el texto aparece dentro del bloque y un contador muestra "N de 140".
  - Dado el paso Objetivo, cuando toco un color de la paleta, entonces el bloque toma ese color y el mismo color se ve después en la casilla del objetivo del mapa, en la miniatura de la tarjeta del inicio y en el PDF.
  - Dado el paso Objetivo, cuando toco un ejemplo, entonces su texto reemplaza el del bloque y se puede editar.
  - Dado el paso Objetivo, cuando elijo una fecha meta, entonces aparece la cuenta regresiva debajo.
  - Dado el paso Objetivo vacío, cuando miro "Siguiente", entonces está deshabilitado; con texto se habilita.
  - Dado el paso Pilares, cuando lo abro, entonces veo un bloque de 3x3 con el objetivo (con su color) en el centro y 8 casillas con ideas en gris como texto de ayuda, que no se guardan.
  - Dado el paso Pilares, cuando escribo en una casilla, entonces se pinta con el color de su pilar y sube el contador "N de 8 pilares".
  - Dado el paso Pilares, cuando presiono Enter en una casilla, entonces el foco pasa a la siguiente en orden horario (pilar 1 a 8) sin insertar un salto de línea.
  - Dado el paso Pilares sin ningún pilar escrito, cuando miro el botón para terminar, entonces está deshabilitado; con al menos un pilar se habilita.
  - Dado al menos un pilar, cuando toco el botón para terminar, entonces se abre el tablero en la pestaña Mapa con la grilla completa.
  - Dado un tablero sin objetivo, cuando toco "Cancelar", entonces se descarta y vuelvo al inicio.
  - Dado un ícono "?" junto a un campo, cuando paso el mouse o llego con el teclado, entonces veo una ayuda corta, y el tooltip oculto no genera desplazamiento horizontal.
  - Dado que recargo la página a mitad del asistente, cuando vuelve a cargar, entonces estoy en el inicio y el tablero a medio armar aparece en la lista (comportamiento actual, se mantiene).
  - Dado un ancho de 375px, cuando recorro los 2 pasos, entonces todo entra sin desplazamiento horizontal y el bloque del objetivo se ve más bajo (4:3).
Alcance: `wizHTML`, `wizSync`, `wizCounts`, `wcellHTML`, `wstaticHTML`, `tipHTML`, paleta `GCOL` y `gcs()`, acciones `wiz-*` (incluida `wiz-color`), Enter en `.wiz textarea.wct`, CSS del asistente (`.wgrid`, `.wgoal`, `.wblk`, `.wc`, `.swatches`, `.tipi`). Campo nuevo `goalColor` en el tablero, aplicado también a `.cell.goal`, `.mini .m-goal`, `.recall` y al objetivo en `buildPDF`.
Fuera de alcance / No tocar: la grilla editable y los paneles por casilla (van en `mapa.md` y `panel-casilla.md`), el onboarding animado, la persistencia (`sessionStorage`, `harada-v1`).
Dependencias: `blankBoard` (suma `goalColor: ''`), `cellAt`/`NEI`, `PHEX` y `--p1`..`--p8`, `buildPDF`/`rgb()`, `openBoard`, `save`, `render`. Para que al terminar se puedan escribir las acciones hace falta la grilla editable de `mapa.md`.
Estados (UI): vacío = botón deshabilitado y textos de ayuda en gris. Sin carga ni error (todo es local). Tableros guardados sin `goalColor` usan el color por defecto.
Diseño: N/A (prototipo en la rama `explorar/onboarding`, commits 82a060f y 5f34e4b).
Paleta de colores del objetivo: A CONFIRMAR. El prototipo usa Tinta (por defecto, `--goal-bg`), Granate #9E2A2B, Bosque #1D5C4D, Índigo #3E2C7A, Ámbar #8A5A0B y Petróleo #0E5A73.
Definición de hecho: la del AGENTS.md, más:
  - Recorrer los 2 pasos con teclado solo (Tab, Enter) y con mouse, en 1240px y en 375px, en claro y en oscuro.
  - Elegir un color, terminar y verificar ese color en el mapa, la tarjeta del inicio y el PDF descargado.
  - Abrir un tablero creado antes del cambio (sin `goalColor`) y verificar que se ve igual que antes.
