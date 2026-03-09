# Tavo Store Pro (Firebase -> Appwrite)

Este proyecto ahora usa **Appwrite** en lugar de Firebase para guardar:

- Configuración general (`rate`, `settings.logo`, `settings.banner`, `settings.background`)
- Productos

## 1) Configurar Appwrite

En tu proyecto de Appwrite crea:

1. **Database** (anota el `DATABASE_ID`)
2. Colección **`configuracion`**
   - Documento fijo con ID: **`general`**
   - Atributos:
     - `rate` (float)
     - `settings` (object)
3. Colección **`productos`**
   - Atributos:
     - `name` (string)
     - `price` (float)
     - `img` (string, opcional, largo)
     - `status` (string)

Permisos recomendados para empezar rápido (luego los endureces):

- `read("any")`
- `create("any")`
- `update("any")`
- `delete("any")`

## 2) Editar credenciales en `index.html`

Busca este bloque y reemplaza valores:

```js
const APPWRITE_ENDPOINT = "https://cloud.appwrite.io/v1";
const APPWRITE_PROJECT_ID = "REEMPLAZA_CON_TU_PROJECT_ID";
const APPWRITE_DATABASE_ID = "REEMPLAZA_CON_TU_DATABASE_ID";
```

## 3) Probar localmente

```bash
python -m http.server 8080
```

Abre: `http://localhost:8080`

## 4) Publicar en la web

Como es estático, puedes subirlo tal cual a:

- Netlify
- Vercel (static)
- GitHub Pages
- Cloudflare Pages

Solo necesitas subir:

- `index.html`
- carpeta `assets/`

## Notas

- El panel admin sigue funcionando igual, pero ahora guarda en Appwrite.
- Si no configuras `PROJECT_ID` y `DATABASE_ID`, la app mostrará errores en consola y no guardará datos.
