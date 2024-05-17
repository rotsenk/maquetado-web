# Footer y Listado de Artículos

## Maquetando el footer

Utilizando el selector de id del footer le vamos a dar estilos

```css
/* footer */
#footer {
  background: #e6e6e6;
  width: 100%;
  height: 70px;
  line-height: 65px;
  color: #484848;
}

#footer p {
  margin: 0px;
  padding: 0px;
}
```

## Listado de los artículos con HTML, CSS y JS

Vamos a realizar la parte de los artículos en el html.
Para ello, nos iremos a la etiqueta `<section>` que tiene el id `"content"` y donde anteriormente habíamos dejado un comentario en el que listaríamos artículos.
Podemos descargar una imagen de internet para colocarla, sólo como ejemplo.

```html
<section id="content">
  <h2 class="subheader">Últimos artículos</h2>

  <!-- Listado de artículos -->
  <div id="articles">
    <article class="article-item" id="article-template">
      <div class="image-wrap">
        <img src="./assets/images/writting.png" alt="writting image" />
      </div>
      <h2>Artículo de prueba</h2>
      <span class="date"> Hace 5 minutos </span>
      <a href="#">Leer más</a>
      <div class="clearfix"></div>
    </article>

     <!--AQUÍ SE VAN A AÑADIR ARTÍCULOS VÍA JS-->
  </div>
</section>
```
## Listar artículos con JS

Podríamos copiar y pegar el código, para simular que tenemos varios artículos pero también podríamos hacer un script de javascript para que se carguen dinámicamente.

Bien, haremos el script, lo colocaremos después de la `section` debido a que es JavaScript, y estamos intentando acceder a elementos de HTML y para ello, estos elementos deben estar dibujado antes para poder acceder a ellos.

```html
<script>
  window.addEventListener("load", function () {
    var template = document.getElementById("article-template");

    var articles = document.getElementById("articles");
    for (let i = 1; i <= 5; i++) {
      var clonado = template.cloneNode(true);
      clonado.removeAttribute("id");
      var h2 = clonado.getElementsByTagName("h2")[0];
      h2.innerHTML = h2.textContent + " " + i;
      articles.appendChild(clonado);
    }
  });
</script>
```
Este script en JavaScript se ejecuta cuando la ventana del navegador se carga completamente. Su propósito es clonar un elemento de plantilla de artículo (`template`) cinco veces, modificar su contenido y luego agregarlo al contenedor de artículos (`articles`). A continuación, te explico paso a paso cómo funciona el script:

1. **Evento de carga de la ventana**: `window.addEventListener("load", function () {...})`
   - Se añade un evento que se ejecutará cuando toda la página (incluyendo todos los recursos como imágenes, hojas de estilo, etc.) haya terminado de cargarse.

2. **Obtener la plantilla de artículo**: `var template = document.getElementById("article-template");`
   - Se obtiene el elemento de la plantilla del DOM (Document Object Model) utilizando su ID (`article-template`). Este elemento contiene la estructura HTML que se clonará.

3. **Obtener el contenedor de artículos**: `var articles = document.getElementById("articles");`
   - Se obtiene el contenedor donde se añadirán los artículos clonados utilizando su ID (`articles`).

4. **Bucle para clonar y modificar la plantilla**:
   ```javascript
   for (let i = 1; i <= 5; i++) {
       var clonado = template.cloneNode(true);  // Clona la plantilla, incluyendo sus elementos hijos
       clonado.removeAttribute("id");           // Elimina el atributo ID para evitar duplicados en el DOM
       var h2 = clonado.getElementsByTagName("h2")[0];  // Obtiene el primer elemento <h2> dentro del clon
       h2.innerHTML = h2.textContent + ' ' + i; // Modifica el contenido del <h2> añadiendo un número
       articles.appendChild(clonado);           // Añade el clon al contenedor de artículos
   }
   ```
   - **Clonación**: `var clonado = template.cloneNode(true);`
     - Clona la plantilla completa (incluyendo sus elementos hijos) y la guarda en una nueva variable `clonado`.
   - **Eliminar atributo ID**: `clonado.removeAttribute("id");`
     - Elimina el atributo `id` del clon para evitar tener elementos con IDs duplicados en el DOM.
   - **Modificar el contenido del encabezado**:
     ```javascript
     var h2 = clonado.getElementsByTagName("h2")[0];
     h2.innerHTML = h2.textContent + ' ' + i;
     ```
     - Encuentra el primer elemento `<h2>` dentro del clon.
     - Modifica su contenido agregando un número (`i`), que corresponde al número de iteración actual del bucle.
   - **Añadir el clon al contenedor**: `articles.appendChild(clonado);`
     - Añade el clon modificado al contenedor de artículos (`articles`).

El resultado de este script es que, una vez que la página se carga completamente, cinco copias de la plantilla de artículo se crean, se modifican (añadiendo un número secuencial al texto del encabezado `<h2>`) y se añaden al contenedor de artículos.

## CSS del listado de artículos

```css
/* Maquetación de sección de artículos */
.article-item{
  width: 100%;
  border-bottom: 1px solid #eee;
  padding-bottom: 20px;
  padding-top: 20px;
  text-align: left;
}

.article-item .image-wrap{
  width: 130px;
  height: 130px;
  float: left;
  margin-right: 15px;
  border: 1px solid #ccc;
  overflow: hidden; /* para ocultar todo lo que sobresalga de la imagen*/
}

.article-item .image-wrap img{
  height: 100%;
  text-align: center;
}

.article-item h2{
  display: block;
  width: 100%;
  padding: 0px;
  margin: 0px;
  margin-bottom: 7px;
}

.article-item .date{
  display: block;
  width: 100%;
  color: rgb(122, 122, 122);
}

.article-item a{
  display: block;
  color: #444;
  text-decoration: none;
  margin-top: 10px;
}

.article-item a:hover{
  text-decoration: underline;
}

.subheader{
  font-size: 32px;
  border-bottom: 1px solid #eee;
  padding-bottom: 5px;
}
```