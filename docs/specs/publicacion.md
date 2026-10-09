# Feature: Publicación en Uxuaria  ·  id: pub
Historia de usuario: Como editor de Uxuaria, quiero publicar SAKURA 64 en un link público estable, para que los lectores de LATAM lo prueben.
Objetivo: servir la app como sitio estático en Cloudflare Pages, conectado a un repositorio de GitHub, en `sakura64.uxuaria.com`. Primero para pruebas finales en el servidor; la apertura al público depende de los A CONFIRMAR.

Criterios de aceptación:
  - Dado un push a `main` en GitHub, cuando Cloudflare Pages termina, entonces el sitio publicado es el `index.html` y `vendor/` de ese commit, sin paso de build.
  - Dado `https://sakura64.uxuaria.com` en una pestaña nueva, cuando lo abro, entonces veo el onboarding con HTTPS y todo el test de regresión del AGENTS.md pasa.
  - Dado el sitio publicado, cuando reviso la red, entonces solo hay pedidos al propio dominio, a Google Fonts y, al suscribirse, a `sibforms.com`.
  - Dado el sitio publicado, cuando me suscribo con un correo propio, entonces el contacto aparece en la lista de Brevo y el PDF se descarga.
Alcance: repositorio de GitHub, proyecto de Cloudflare Pages (framework "None", sin comando de build, salida `/`), dominio personalizado `sakura64.uxuaria.com`, `LEGAL_URL`.
Fuera de alcance / No tocar: lógica del tablero, modelo de datos, persistencia.
Dependencias: cuenta de GitHub y de Cloudflare del usuario; DNS de `uxuaria.com` en Cloudflare.
Estados (UI): sin cambios.
Diseño: N/A.
A CONFIRMAR (antes de abrir al público):
  - Privacidad y Términos actualizados por el envío del correo a Brevo.
  - Datos legales marcados [A COMPLETAR] y quitar el aviso de borrador.
  - Licencia y crédito del set de íconos de Figma.
  - Etiquetas Open Graph para la vista previa al compartir.
  - Si el repositorio de GitHub es público o privado.
Definición de hecho: la del AGENTS.md, más el test de regresión corrido sobre `https://sakura64.uxuaria.com`.
