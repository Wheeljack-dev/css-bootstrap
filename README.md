# Aprender CSS con Bootstrap 5

Guía en español para aprender a dar estilo a una página web, paso a paso. Funciona como un MDN simplificado y dedicado solo a CSS, con Bootstrap 5.3 como apoyo.

| Parte | Qué contiene |
|---|---|
| 1. Armar la página (HTML) | El esqueleto de una página; el `head` con el título, el favicon y las hojas de estilo; las zonas de la página (`header`, `nav`, `main`, `footer`); cómo ordenar la hoja de estilos; una hoja de estilos real explicada parte por parte. |
| 2. Aprender CSS paso a paso | Reglas, selectores (con un probador de selectores), estados como `:hover`, qué regla gana, colores y medidas, texto, espacios y bordes, `display`, `position`, Flexbox, Grid, adaptación al celular, variables y animaciones. |
| 3. Buscar y consultar | "¿Qué quiero hacer?" (131 soluciones buscables), estilos para cada etiqueta (46 etiquetas) y el diccionario de propiedades (115 propiedades): qué va en cada parte del valor, qué pasa si falta una parte, todos los valores posibles y un probador para ver el resultado. |
| 4. Practicar | 67 actividades que se corrigen solas, un probador que revisa el código línea por línea y los errores más comunes. |
| 5. Bootstrap 5 | Cómo se agrega, la rejilla, las clases útiles, los componentes y qué clase hace lo mismo que cada propiedad de CSS. |

Arriba de la página hay un buscador (atajo: tecla `/`) que encuentra etiquetas (`hr`), propiedades (`border-top`) y también lo que se quiere lograr escrito con palabras propias ("línea separadora", "centrar", "fondo de toda la página").

## Archivos

| Archivo | Para qué sirve |
|---|---|
| `index.html` | **La guía completa en un solo archivo**: el contenido, los estilos, el programa, los datos y Bootstrap 5.3.3 (licencia MIT). No depende de ningún otro archivo ni de internet. |
| `favicon.svg` | Ícono de la pestaña del navegador. |
| `.nojekyll` | Archivo vacío: indica a GitHub Pages que publique los archivos tal cual. |
| `.gitignore` | Archivos que Git no debe subir. |
| `README.md` | Este instructivo. |

## Abrir la guía en la computadora

Abrir `index.html` con doble clic. Funciona sin conexión a internet.

También se puede abrir con la extensión Live Server de VS Code, o con un servidor local:

```bash
python -m http.server 8000
```

y entrar a <http://localhost:8000>.

## Publicar en GitHub Pages

### 1. Subir los archivos

**Desde la web de GitHub, sin instalar nada:**

1. Entrar a <https://github.com>, iniciar sesión y elegir **New repository**.
2. Nombre: `css-bootstrap`. Visibilidad: **Public**. Crear el repositorio.
3. En el repositorio, elegir **Add file → Upload files**.
4. Arrastrar `index.html` y `favicon.svg` (y, si se quiere, `README.md` y `.nojekyll`). Confirmar con **Commit changes**.

`index.html` tiene que quedar en la raíz del repositorio, no dentro de otra carpeta.

**Con Git, desde la carpeta de la guía:**

```bash
git init
git add .
git commit -m "Guía de CSS"
git branch -M main
git remote add origin https://github.com/USUARIO/css-bootstrap.git
git push -u origin main
```

Reemplazar `USUARIO` por el nombre de usuario de GitHub.

### 2. Activar GitHub Pages

1. En el repositorio: **Settings → Pages**.
2. En **Build and deployment**, *Source*: **Deploy from a branch**.
3. *Branch*: **main** y carpeta **/ (root)**. **Save**.

En uno o dos minutos la guía queda en `https://USUARIO.github.io/css-bootstrap/`. El nombre del repositorio va al final de la dirección.

### Si algo no se ve bien

- **"There isn't a GitHub Pages site here":** revisar la dirección (tiene que terminar con el nombre del repositorio) y esperar a que termine la publicación. En la pestaña **Actions**, el proceso *pages build and deployment* tiene que terminar con un tilde verde.
- **Se ve una versión vieja:** recargar con Ctrl + F5 para que el navegador no use la copia guardada (caché).
- **Aparece un aviso rojo arriba de la página:** el aviso dice qué falló. Lo más común es que el archivo `index.html` se haya subido incompleto: volver a subirlo.
- **Aviso "Cargando la guía…" que no desaparece:** el navegador tiene JavaScript desactivado o bloqueado. Activarlo y recargar.

## Actualizar la guía

Reemplazar `index.html` por la versión nueva: en GitHub con **Add file → Upload files**, o con `git commit` y `git push`. GitHub Pages vuelve a publicar solo.

## Cómo está armado el archivo

Dentro de `index.html` hay bloques `<script>` con un `id` que dice qué contienen:

| Bloque | Contenido |
|---|---|
| `js-datos-propiedades` | Las fichas del diccionario de propiedades. |
| `js-datos-elementos` | Los estilos para cada etiqueta. |
| `js-datos-recetas` | Las soluciones de "¿Qué quiero hacer?". |
| `js-datos-actividades` | Las actividades y lo que revisa cada una. |
| `js-revisor` | El revisor de CSS que usan el probador y las actividades. |
| `js-verificador` | La comprobación automática de las actividades. |
| `js-app` | El funcionamiento de la página: buscador, pestañas, fichas, probadores. |
| `bs-css` y `bs-js` | Bootstrap 5.3.3, sin modificar. |

Cada entrada de datos se agrega a una lista con `push`. Para sumar una solución, una etiqueta o una actividad, se puede copiar una entrada existente del mismo bloque y cambiarla. El texto entre `` `backticks` `` se muestra como código.

El avance de las actividades se guarda solo en el navegador de cada persona: no se envía a ningún servidor.
