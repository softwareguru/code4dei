# Code4DEI — CSS modular

## Estructura

- `main.css`: punto de entrada; importa los módulos en el orden necesario.
- `base/`: variables, reset y estilos globales.
- `components/`: botones, tarjetas, galería, videos y elementos reutilizables.
- `layout/`: estructura general, encabezado, secciones y pie de página.
- `pages/home/`: estilos propios de la página principal.
- `pages/content.css`: páginas de contenido/editoriales.
- `pages/internal.css`: páginas internas (comité, ponentes, perfiles, agenda, sesiones, ediciones y Hackeando barreras).
- `pages/sessions.css`: bloque de ediciones/listado de sesiones.
- `responsive/`: ajustes responsive que estaban agrupados al final del CSS original.

## Integración con Hugo

Copia la carpeta `css` dentro de `static/`, para obtener `static/css/main.css` y sus subcarpetas.

En el layout base (`layouts/_default/baseof.html` o el partial donde cargas CSS), agrega:

```html
<link rel="stylesheet" href="{{ "css/main.css" | relURL }}">
```

No cargues además el CSS original monolítico, porque duplicaría reglas.

## Importante

- Se conservaron los selectores, valores y reglas del archivo original; el trabajo fue principalmente de organización.
- El orden de `@import` en `main.css` es intencional para mantener la cascada y los overrides existentes.
- Los imports son relativos a `main.css`; por eso las rutas funcionan al servir toda la carpeta `css/`.
- Para producción, puedes mantener este esquema tal cual o concatenar/minificar los módulos durante el build. Si usas el pipeline de Hugo, verifica que el proceso de minificación preserve o resuelva correctamente los `@import`.
- `responsive/home.css` conserva los media queries globales y de la home en el orden original. Los media queries de páginas internas permanecen junto a sus componentes para no alterar la cascada.
