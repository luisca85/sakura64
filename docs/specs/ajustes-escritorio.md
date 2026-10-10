# Feature: Ajustes de escritorio en onboarding y asistente  ·  id: escritorio
Historia de usuario: Como persona que arma su tablero en la computadora, quiero que los botones del onboarding se distingan por importancia y que el asistente se vea ordenado y centrado, para saber qué hacer en cada paso sin buscar.
Objetivo: jerarquía de botones en el onboarding de escritorio (primario, secundario y terciario), columnas alineadas arriba, y en el asistente columnas compactas y centradas con una tarjeta que agrupa campos y botones. Solo escritorio: celular queda igual (ver `ajustes-movil.md`). Aprobado en la exploración (rama `explorar/botones-onboarding`, commits 7114232 a e8d1415).

Criterios de aceptación:
Onboarding (860px o más)
  - Dado cualquier paso, cuando miro los botones, entonces van alineados a la izquierda: "‹ Atrás" (secundario: blanco con borde de tinta, 46px) desde el paso 2 y "Siguiente →" (primario: relleno magenta con texto blanco, 46px, 16px de letra).
  - Dado el paso 4, cuando miro los botones, entonces son "‹ Atrás", "Crear mi tablero →" (primario) y, separado por un espacio mayor (22px contra 10px), el link gris subrayado "Ver el ejemplo" (terciario).
  - Dadas las dos columnas (tablero animado y texto con botones), cuando cambio de paso, entonces sus bordes superiores coinciden (alineadas arriba) y el conjunto sigue centrado en la pantalla.
Asistente (821px o más)
  - Dados los pasos Objetivo y Pilares, cuando los miro, entonces el bloque va a la izquierda y la columna derecha es una tarjeta blanca con borde fino (hasta 520px) que agrupa ejemplos y fecha (paso 1) o contador y consejos (paso 2), a 24px del bloque.
  - Dada la tarjeta, cuando miro su pie, entonces los botones ("Cancelar" y "Siguiente: definir pilares →", o "Atrás" y "Terminar y ver el tablero completo") van dentro, separados por una línea fina y alineados a la derecha.
  - Dado el bloque, cuando lo miro, entonces mide el 50% del ancho o lo que permita el alto de la ventana (el menor), sin pasarse de la altura visible.
  - Dado cualquier ancho de escritorio, cuando mido los márgenes, entonces el contenido está centrado con el mismo espacio a cada lado (106px en 1280×800, 231px en 1600×1000).
Alcance: `updateOnb` (rama de escritorio: `.od`, `.od-1`, `.od-2`, `.od-3`), `.onb-body` en 860px o más (`align-items:start`), CSS de `.wiz .wgrid`, `.wiz .wstage`, `.wiz .wside`, `.wiz .wbtns` en 821px o más.
Fuera de alcance / No tocar: celular, textos, comportamiento del onboarding y del asistente, paneles por casilla (`.det .wgrid`).
Dependencias: `onbMob`, `wizHTML`, `.btn`.
Estados (UI): botones deshabilitados del asistente sin cambios. Sin carga ni error (todo es local).
Diseño: N/A (aprobado en la exploración).
Conocido:
  - El primario relleno en magenta del onboarding de escritorio es distinto del de celular (blanco con borde magenta).
  - El subheader del asistente sigue alineado a la izquierda del contenedor; el contenido de abajo queda centrado y más adentro.
Definición de hecho: la del AGENTS.md, más recorrer los 4 pasos del onboarding y los 2 del asistente en 1280×800 y 1600×1000, en claro y en oscuro.
