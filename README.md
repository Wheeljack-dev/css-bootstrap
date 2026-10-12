# Guía de CSS y Bootstrap 5

Guía práctica en español para aprender a diseñar páginas web con CSS. Funciona como un MDN simplificado y dedicado exclusivamente a CSS, con Bootstrap 5.3 como complemento. Cada tema reúne una explicación concisa, un ejemplo en funcionamiento y el código listo para copiar o modificar.

| Parte | Contenido |
|---|---|
| 1. Estructura de la página (HTML) | Esqueleto del documento; el `head` con el título, el favicon y las hojas de estilo; secciones de la página (`header`, `nav`, `main`, `footer`); organización de la hoja de estilos; análisis de una hoja de estilos completa, parte por parte. |
| 2. Fundamentos de CSS | Sintaxis, selectores (con un probador de selectores), pseudo-clases y pseudo-elementos, cascada y especificidad, colores y unidades, tipografía, modelo de caja, `display`, `position`, Flexbox, Grid, diseño adaptable, variables y animaciones. |
| 3. Referencia | Soluciones por objetivo (131), estilos por etiqueta (46) y diccionario de propiedades (115): partes del valor, efecto de omitir cada parte, valores admitidos y un probador interactivo. |
| 4. Práctica | 67 actividades con corrección automática, un probador con revisión del código línea por línea y los errores más frecuentes. |
| 5. Bootstrap 5 | Incorporación, sistema de rejilla, clases utilitarias, componentes y equivalencias entre CSS y Bootstrap. |

El buscador superior (atajo: tecla `/`) encuentra etiquetas (`hr`), propiedades (`border-top`) y también descripciones del resultado buscado («línea separadora», «centrar», «color de fondo»).

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
| `js-datos-recetas` | Las soluciones por objetivo. |
| `js-datos-actividades` | Las actividades y lo que revisa cada una. |
| `js-revisor` | El revisor de CSS que usan el probador y las actividades. |
| `js-verificador` | La comprobación automática de las actividades. |
| `js-app` | El funcionamiento de la página: buscador, pestañas, fichas, probadores. |
| `bs-css` y `bs-js` | Bootstrap 5.3.3, sin modificar. |

Cada entrada de datos se agrega a una lista con `push`. Para incorporar una solución, una etiqueta o una actividad, puede copiarse una entrada existente del mismo bloque y modificarla. El texto entre `` `backticks` `` se muestra como código.

El avance de las actividades se guarda solo en el navegador de cada persona: no se envía a ningún servidor.
