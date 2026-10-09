# Feature: Ajustes para celular  ·  id: movil
Historia de usuario: Como lector que abre el link desde el celular, quiero que la introducción y la navegación entren cómodas en la pantalla, para avanzar sin buscar botones ni perder espacio.
Objetivo: adaptar a celular el onboarding (título arriba, stepper con progreso y botón fijo abajo), la barra de navegación (menú hamburguesa) y el pie (se quita). Solo cambia celular: escritorio queda igual. Aprobado en la exploración (rama `explorar/ajustes-movil`, commits 4e9e22c a 117f139).

Criterios de aceptación:
Onboarding (hasta 859px)
  - Dado el onboarding en celular, cuando lo miro, entonces el orden es: barra con el logo y el link chico "Saltar introducción" (12px, un renglón), stepper, "PASO N DE 4" en magenta, título, gráfico del tablero (hasta 340px), texto y ejemplo.
  - Dado el stepper, cuando lo miro, entonces son 4 círculos numerados unidos por una línea con el nombre debajo; los hechos van en tinta con ✓ y la línea pintada, el actual en magenta con un halo suave y los que faltan en gris; tocar uno salta a ese paso.
  - Dado el paso 1, cuando miro la franja fija de abajo, entonces "Siguiente: pilares →" ocupa todo el ancho.
  - Dados los pasos 2 a 4, cuando miro la franja, entonces el link "‹ Atrás" ocupa la mitad izquierda y el botón principal la derecha, con el texto corto ("Siguiente →", "Crear tablero →"); los lectores de pantalla anuncian el nombre completo.
  - Dado el botón principal, cuando lo miro, entonces tiene fondo blanco, borde magenta de 2px y texto negro, con letra de 14 a 17px según el ancho, sin que la flecha se salga desde 320px.
  - Dado el paso 4, cuando lo miro, entonces "Ver el ejemplo" es un link debajo de las tareas de ejemplo, fuera de la franja.
  - Dado cualquier paso, cuando bajo hasta el final, entonces la franja no tapa contenido.
  - Dado que cambio el ancho de la ventana con el onboarding abierto, cuando cruzo los 860px, entonces se redibuja con la versión que corresponde.
Barra y pie (hasta 640px)
  - Dada cualquier pantalla con barra, cuando la miro, entonces solo están el logo y el botón ☰ (barra de 61px, un renglón).
  - Dado el botón ☰, cuando lo toco, entonces se abre debajo un menú con "Inicio", "Cómo funciona", "Modo oscuro" o "Modo claro", los links "Privacidad", "Términos de uso" y "Créditos y licencias", y "Diseñado por Luis Carlos Romero León · uxuaria.com"; el ☰ pasa a ✕ y `aria-expanded` a "true".
  - Dado el menú abierto, cuando elijo una opción, toco afuera o presiono Esc, entonces se cierra (con Esc el foco vuelve al ☰).
  - Dada cualquier pantalla en celular, cuando bajo hasta el final, entonces no hay pie de página.
Escritorio
  - Dado un ancho de 860px o más (onboarding) o de 641px o más (barra y pie), cuando lo miro, entonces se ve igual que antes de este cambio.
Alcance: `onbMob`, `onbHTML` (versión celular), `updateOnb` (rama celular), `ONB`, resize con `wasOnbMob`, `barHTML` (`.themebtn`, `.burger`, `.mmenu`), estado `S.menu`, acción `menu`, cierre en el click global y Esc; CSS `.onb-head`, `.ostep`, `.os`, `.ostep-n`, `.ob-cta`, `.ob-back`, `.ob-link`, `.onb-skip`, `.onb-ex`, `.mmenu`, `.mitem`, `.msub`, `.mcred`, `.foot` oculto hasta 640px.
Fuera de alcance / No tocar: escritorio, contenido del onboarding, el tablero, el asistente y la nube del personaje en celular.
Dependencias: `legal`, `theme`, `home`, `onb`, `markSeen`, `.lnk`.
Estados (UI): menú abierto o cerrado. Sin carga ni error (todo es local).
Diseño: N/A (aprobado en la exploración).
Conocido:
  - Sin pie en celular no se ve la frase "SAKURA 64 es una herramienta gratuita y sin fines comerciales"; sigue en Términos.
  - El botón principal relleno de borde magenta es una excepción a "acciones principales como links subrayados", solo en el onboarding en celular.
  - Pendientes de celular: la nube del personaje tapa contenido, la grilla del tablero aparece muy abajo, el botón del asistente queda lejos y la ayuda de la grilla dice "estado".
Definición de hecho: la del AGENTS.md, más:
  - Recorrer los 4 pasos del onboarding en 320, 375 y 414px y en 1280px (igual que antes).
  - Abrir y cerrar el menú en el inicio, el tablero y la página legal, en claro y en oscuro.
