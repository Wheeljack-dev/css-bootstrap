# CSS y Bootstrap 5

Sitio estático de una sola página: cada elemento de CSS y Bootstrap 5 con su definición, una explicación simple, el resultado en vivo y el código, más un probador con revisor de CSS y un diccionario de propiedades.

No necesita compilación, base de datos ni servidor especial: se publica tal cual.

## Archivos

| Archivo | Para qué sirve |
|---|---|
| `index.html` | La página completa (HTML, CSS y JavaScript en un solo archivo) |
| `favicon.svg` | Ícono de la pestaña del navegador |
| `vercel.json` | Encabezados de seguridad para Vercel (en otros servicios se ignora) |
| `.gitignore` | Archivos que Git no debe subir |
| `README.md` | Este instructivo |

Bootstrap 5.3.3 se carga desde jsDelivr, así que el sitio necesita conexión a internet. Para no depender del CDN, ver el final de este documento.

## Probarlo en la computadora

Abrir `index.html` con doble clic. Para verlo exactamente como en un servidor:

```bash
python -m http.server 8000
```

y entrar a <http://localhost:8000>.

## Opción 1: GitHub + Vercel (recomendada)

Cada cambio que se sube a GitHub se publica solo en unos segundos.

### 1. Subir los archivos a GitHub

**Desde la web, sin instalar nada:**

1. Entrar a <https://github.com>, iniciar sesión y elegir **New repository**.
2. Nombre: `css-bootstrap`. Visibilidad: **Public**. Crear el repositorio sin agregar README.
3. En la página del repositorio vacío, elegir **uploading an existing file**.
4. Arrastrar `index.html`, `favicon.svg`, `vercel.json` y `README.md` (el `.gitignore` es opcional) y confirmar con **Commit changes**.

**Con Git, desde la carpeta del sitio:**

```bash
git init
git add .
git commit -m "Primera versión"
git branch -M main
git remote add origin https://github.com/USUARIO/css-bootstrap.git
git push -u origin main
```

Reemplazar `USUARIO` por el nombre de usuario de GitHub.

### 2. Publicar en Vercel

1. Entrar a <https://vercel.com> y registrarse con la cuenta de GitHub.
2. **Add New… → Project**, buscar el repositorio `css-bootstrap` y elegir **Import**.
3. **Framework Preset: Other**. No hace falta tocar *Build Command* ni *Output Directory*.
4. **Deploy**.

Vercel entrega una dirección del tipo `https://css-bootstrap.vercel.app` (si el nombre está ocupado, agrega un sufijo). Desde **Settings → Domains** se puede conectar un dominio propio.

## Opción 2: GitHub Pages

Con el repositorio ya creado (paso 1 de la opción anterior):

1. En el repositorio: **Settings → Pages**.
2. En **Build and deployment**, *Source*: **Deploy from a branch**.
3. *Branch*: **main** y carpeta **/ (root)**. **Save**.

En uno o dos minutos el sitio queda en `https://USUARIO.github.io/css-bootstrap/`.

## Opción 3: Vercel desde la terminal (sin GitHub)

Requiere Node.js. Dentro de la carpeta del sitio:

```bash
npx vercel@latest          # primera vez: inicia sesión y crea una vista previa
npx vercel@latest --prod   # publica en producción
```

## Opción 4: Servidor propio con Nginx

```bash
# desde la computadora
scp index.html favicon.svg usuario@servidor:/var/www/css-bootstrap/
```

Bloque de configuración (`/etc/nginx/sites-available/css-bootstrap`):

```nginx
server {
    listen 80;
    server_name css.midominio.com;
    root /var/www/css-bootstrap;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

```bash
sudo ln -s /etc/nginx/sites-available/css-bootstrap /etc/nginx/sites-enabled/
sudo nginx -t && sudo systemctl reload nginx
sudo certbot --nginx -d css.midominio.com   # certificado HTTPS gratuito
```

## Actualizar el sitio

Editar `index.html` y subir el cambio: en GitHub con **Add file → Upload files** (reemplaza el archivo) o con `git commit` y `git push`. Vercel y GitHub Pages vuelven a publicar solos.

## Usarlo sin depender del CDN

1. Descargar `bootstrap.min.css` y `bootstrap.bundle.min.js` (versión 5.3.3) desde <https://getbootstrap.com>.
2. Copiarlos junto a `index.html`.
3. En `index.html`, cambiar el `href` del `<link id="bs-css">` por `bootstrap.min.css` y el `src` del `<script id="bs-js">` por `bootstrap.bundle.min.js`.

Los ejemplos en vivo toman las rutas de esos dos elementos, así que no hay que cambiar nada más.
