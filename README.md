# Finanzas (versión web)

App de finanzas personales (ingresos, gastos, transferencias, cuentas, metas y proyecciones), convertida desde el APK `Finanzas v1.0.0` a una aplicación web instalable (PWA) que funciona sin conexión.

- Los datos se guardan **solo en el navegador** (localStorage) del dispositivo donde se usa. No hay servidor ni base de datos.
- Usa **Ajustes → Exportar respaldo** para guardar tus datos; en web se descarga un archivo `.json`.
- Diseño adaptable: móvil (barra inferior), tablet (2 columnas) y PC (barra lateral + panel amplio). Los estilos de escritorio están en `web/responsive.css`.
- Se puede instalar en el celular o en el computador (“Agregar a pantalla de inicio” / “Instalar app”).

## Publicar en GitHub Pages

1. Crea un repositorio en GitHub y sube este proyecto (rama `main`).
2. En el repositorio: **Settings → Pages → Build and deployment → Source: GitHub Actions**.
3. El workflow `.github/workflows/pages.yml` publica la carpeta `web/` en cada push a `main`.
4. La app queda en `https://TU-USUARIO.github.io/NOMBRE-DEL-REPO/`.

Todas las rutas son relativas, así que funciona tanto en `usuario.github.io/repo/` como en un dominio propio.

## Probar en local

```bash
python3 -m http.server 8080 --directory web
# abrir http://localhost:8080
```

## Estructura

- `web/` – sitio estático (build original de la app + `responsive.css`, `manifest.webmanifest`, `sw.js` e íconos).
- `.github/workflows/pages.yml` – despliegue automático.

## Notas

- Al publicar cambios, sube el número de `CACHE` en `web/sw.js` (p. ej. `finanzas-v2`) para que los usuarios reciban la nueva versión.
- Los datos de la versión APK (instalada en el teléfono) **no se transfieren solos**: exporta un respaldo en la app Android e impórtalo en la web.
