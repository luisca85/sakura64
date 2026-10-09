# Feature: Publicación en Uxuaria  ·  id: pub
Historia de usuario: Como editor de Uxuaria, quiero publicar SAKURA 64 en un link público estable, para que los lectores de LATAM lo prueben.
Objetivo: dejar la micro app servida como sitio estático bajo Uxuaria, con textos, metadatos y avisos acordes a una pieza publicada (hoy dice "prueba de concepto para lectores del boletín").
Criterios de aceptación:
  - Dado el link público, cuando lo abro en una pestaña nueva, entonces veo el onboarding y todo el test de regresión del AGENTS.md pasa.
  - Dado el link compartido en redes o mensajería, cuando se genera la vista previa, entonces muestra título, descripción e imagen: A CONFIRMAR (hoy no hay etiquetas Open Graph).
  - Dado el sitio publicado, cuando reviso la red, entonces solo hay pedidos al propio dominio y a Google Fonts.
  - Dado el footer, cuando lo leo, entonces menciona a Uxuaria y explica que los datos viven en la sesión: texto final A CONFIRMAR.
Alcance: A CONFIRMAR. Candidatos: dominio/ruta, hosting, textos de footer y meta, Open Graph, link de vuelta a Uxuaria.
Fuera de alcance / No tocar: lógica del tablero, modelo de datos, persistencia.
Dependencias: hosting (README propone Cloudflare Pages: A CONFIRMAR), dominio de Uxuaria (A CONFIRMAR), repo remoto en GitHub (hoy no hay remoto).
Estados (UI): sin cambios.
Diseño: A CONFIRMAR (¿marca de Uxuaria en el header o footer?).
Definición de hecho: la del AGENTS.md, más el test de regresión corrido sobre la URL pública.
