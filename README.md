# SAKURA 64

Herramienta web para armar un tablero de 64 acciones inspirado en el método Harada: un objetivo ambicioso, 8 pilares y 8 acciones por pilar (64 acciones), con tareas recurrentes y exportación a PDF. Es una prueba de concepto para los lectores del boletín.

Es un sitio estático. No tiene build, ni servidor, ni base de datos. Los tableros viven en el navegador de cada persona durante la sesión.

## Archivos

- `index.html`: toda la aplicación (estilos, lógica y marcado en un solo archivo).
- `vendor/jspdf.umd.min.js`: jsPDF 2.5.1, incluido para no depender de una CDN.
- `CLAUDE.md`: contexto del proyecto para seguir trabajando con Claude Code.

## Probarlo en local

Abrí `index.html` en el navegador, o levantá un servidor simple:

```
python3 -m http.server 8080
```

Después entrá a http://localhost:8080.

## Publicarlo en Cloudflare Pages

1. Subí esta carpeta a un repositorio de GitHub.
2. En Cloudflare, andá a Workers y Pages, creá un proyecto de Pages y conectalo con el repositorio.
3. Configuración de build: framework en "None", comando de build vacío y directorio de salida `/`.
4. Cada push a la rama principal publica una versión nueva.

La tipografía (Noto Sans JP) se carga desde Google Fonts. Si no carga, el sitio usa fuentes del sistema. Los íconos (set "Japan Icons (Community)" de Figma) van incrustados en `index.html`.
