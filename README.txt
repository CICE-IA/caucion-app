# Calculadora de Caución (PWA)

Esta aplicación es una **calculadora web simple** para estimar una caución y está preparada como **PWA** (se puede instalar en el celular o en escritorio y funciona offline con caché).

La idea de este README es que una persona nueva pueda:
1. Entender rápido qué hace el proyecto.
2. Levantarlo en local sin complicaciones.
3. Publicarlo en un hosting.
4. Saber dónde tocar código para seguir mejorándolo.

---

## 1) ¿Qué contiene este repo?

Proyecto estático (sin backend):

- `index.html`
  Contiene la interfaz y también la lógica principal de la calculadora (HTML + CSS + JS en un mismo archivo).
- `manifest.json`
  Configuración de la PWA (nombre, íconos, colores, modo de visualización, etc.).
- `sw.js`
  Service Worker: maneja la caché para que la app funcione offline.
- `icon-192.png` y `icon-512.png`
  Íconos usados por la PWA.

---

## 2) Requisitos

- Navegador moderno (Chrome, Edge, Firefox, Safari).
- Para probar correctamente PWA/offline, conviene servirlo con HTTP local (no abrir el archivo con `file://`).

Opcional para desarrollo local:
- Python 3 (para levantar un server rápido).

---

## 3) Cómo ejecutarlo en local

Desde la carpeta del proyecto, levantá un servidor:

```bash
python3 -m http.server 8000
```

Luego abrí:

- `http://localhost:8000`

> Tip: si abrís `index.html` directo con doble click, algunas funciones de Service Worker/PWA pueden no comportarse igual que en producción.

---

## 4) Cómo instalar/probar como PWA

1. Abrí la app en el navegador con HTTP/HTTPS.
2. En Chrome/Edge, buscá el botón **Instalar app** en la barra de direcciones o menú.
3. Instalá.
4. Para probar offline:
   - Abrí DevTools → Application → Service Workers.
   - Activá modo offline y recargá.

Si todo está bien, la app debería seguir cargando gracias a `sw.js`.

---

## 5) Publicación (deploy)

Como es un sitio estático, podés publicarlo en cualquier hosting HTTPS (GitHub Pages, Netlify, Vercel, etc.).

### Opción simple: GitHub Pages

1. Subí estos archivos al repo.
2. En GitHub: **Settings → Pages**.
3. Seleccioná la rama y carpeta raíz (`/root`).
4. Esperá la URL pública.

Importante:
- Subí **todo** el contenido de esta carpeta.
- Verificá que `manifest.json`, `sw.js` e íconos estén en las rutas correctas.

---

## 6) Guía rápida para seguir desarrollando

### Dónde tocar cada cosa

- Cambios de interfaz (textos, botones, layout): `index.html`.
- Cambios de lógica/calculadora: `index.html` (bloque `<script>`).
- Cambios de comportamiento offline/caché: `sw.js`.
- Nombre/íconos/configuración de instalación: `manifest.json`.

### Buenas prácticas recomendadas

- Si cambiás recursos críticos (HTML/CSS/JS), revisá la estrategia de caché en `sw.js`.
- Cuando actualices la app, considerá versionar la caché (nombre nuevo) para evitar que usuarios queden con versión vieja.
- Probá siempre:
  1. Carga normal.
  2. Reapertura de app instalada.
  3. Funcionamiento offline.

---

## 7) Checklist de verificación antes de publicar

- [ ] La calculadora realiza el cálculo esperado.
- [ ] El diseño se ve bien en móvil y escritorio.
- [ ] La app se puede instalar como PWA.
- [ ] Funciona offline (al menos la pantalla principal).
- [ ] No hay errores en consola del navegador.

---

## 8) Próximas mejoras sugeridas

- Separar `index.html` en archivos `styles.css` y `app.js` para mantenimiento.
- Agregar tests de lógica de cálculo (si se extrae a módulo JS).
- Incluir changelog con versiones de caché.
- Añadir CI simple (por ejemplo, validación de HTML/JS).

---

Si te sumás al proyecto y querés empezar rápido: levantalo local, hacé un cambio pequeño en `index.html`, probá en navegador y luego verificá que siga funcionando offline.
