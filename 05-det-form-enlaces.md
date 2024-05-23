# Detalles de artículos, formulario con HTML5 y estilos con CSS, y enlaces con HTML
## Página de detalle de los artículos
Vamos a crear la página de detalle de los artículos, basicamente copiamos todo el contenido de `index.html` y cambiamos algunas cosas...
Creamos el archivo llamado `article.html` y pegamos el contenido. 
Quitaremos:
- el script de los artículos
- subheader y div de articles
- el slider

dejándolo así:
![alt text](image-1.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Maquetación Web</title>
    <!-- Hoja de Estilos -->
    <link rel="stylesheet" href="assets/css/styles.css">
</head>
<body>
    <header id="header">
        <div class="center" >
            <!-- LOGO -->
            <div id="logo" >
                <img src="assets/images/logodizpixel.png" class="app-logo" alt="Logotipo">
                <span id="brand">
                    <strong>Staenly</strong>Rivas
                </span>
            </div>

            <!-- MENÚ -->
            <nav id="menu" >
                <ul>
                    <li>
                        <a href="./index.html">Inicio</a>
                    </li>
                    <li>
                        <a href="./blog.html">Blog</a>
                    </li>
                    <li>
                        <a href="#">Formulario</a>
                    </li>
                    <li>
                        <a href="#">Página 1</a>
                    </li>
                </ul>
            </nav>

            <!-- LIMPIAR FLOTADOS -->
            <div class="clearfix"></div>
        </div>
    </header>
    
    <!-- Sidebar -->
    <div class="center">
        <section id="content">
                <article class="article-item" id="article-template">
                    <div class="image-wrap">
                        <img src="./assets/images/writting.png" alt="writting image">
                    </div>
                    <h2>Artículo de prueba</h2>
                    <span class="date">
                        Hace 5 minutos
                    </span>
                    <a href="#">Leer más</a>
                    <div class="clearfix">

                    </div>
                </article>
        </section>

        <aside id="sidebar">
            <div id="nav-blog" class="sidebar-item">
                <h3>Creación de artículo!</h3>
                <a href="#" class="btn btn-success">Crear artículo</a>
            </div>

            <div id="search" class="sidebar-item">
                <h3>Buscador</h3>
                <p>Encuentra el artículo que buscas</p>
                <form>
                    <input type="text" name="search">
                    <input class="btn" type="submit" name="submit" value="Buscar">
                </form>
            </div>
        </aside>
        
        <!-- LIMPIAR FLOTADOS -->
        <div class="clearfix"></div>
    </div>

    <footer id="footer">
        <div class="center">
            &copy; Developed by Nestor Rivas
        </div>
    </footer>

</body>
</html>
```

Y vamos a dejarlo como si tuvieramos un artículo en concreto
Regresamos al `article.html` y en lugar de tener un `h2` lo dejamos con `h1` 
Quitaremos lo de leer más
y vamos a colocar un párrafo que será donde lleve todo el contenido, en mi caso, haré un párrafo con *lorem ipsum* pero en su caso deberán escribir algo relacionado con el artículo del que hablen en esta sección.
Esto podría ir en un sólo párrafo o en párrafos separados.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Maquetación Web</title>
    <!-- Hoja de Estilos -->
    <link rel="stylesheet" href="assets/css/styles.css">
</head>
<body>
    <header id="header">
        <div class="center" >
            <!-- LOGO -->
            <div id="logo" >
                <img src="assets/images/logodizpixel.png" class="app-logo" alt="Logotipo">
                <span id="brand">
                    <strong>Staenly</strong>Rivas
                </span>
            </div>

            <!-- MENÚ -->
            <nav id="menu" >
                <ul>
                    <li>
                        <a href="./index.html">Inicio</a>
                    </li>
                    <li>
                        <a href="./blog.html">Blog</a>
                    </li>
                    <li>
                        <a href="#">Formulario</a>
                    </li>
                    <li>
                        <a href="#">Página 1</a>
                    </li>
                </ul>
            </nav>

            <!-- LIMPIAR FLOTADOS -->
            <div class="clearfix"></div>
        </div>
    </header>

    <!-- Sidebar -->
    <div class="center">
        <section id="content">
            <!-- agregar clase article-detalle y quitamos el id -->
                <article class="article-item article-detalle">
                    <div class="image-wrap">
                        <img src="./assets/images/writting.png" alt="writting image">
                    </div>
                    <h1 class="subheader" >Artículo de prueba</h1>
                    <span class="date">
                        Hace 5 minutos
                    </span>
                    <p>
                        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Voluptatem ipsa obcaecati veritatis molestiae explicabo id laborum nisi ipsam totam? Optio distinctio vitae neque cupiditate blanditiis commodi autem quidem, incidunt exercitationem?
                        <br><br>
                        Voluptate mollitia, repudiandae tempore illo cum vel tempora natus vero perferendis ipsum ut veniam accusamus, quasi non quaerat doloremque laborum? Eos deserunt at distinctio ipsum dolore doloribus alias explicabo deleniti?
                        Non laudantium quisquam at totam quidem asperiores id rem molestias dicta temporibus, veritatis vero perferendis, voluptatum deleniti cum consequatur in vitae quos quae esse? Labore, voluptatum odio? Consequatur, repellat quos.
                        Asperiores, accusamus nostrum sequi ipsum distinctio natus quos amet beatae perspiciatis, fuga nemo ducimus esse ipsam qui unde, mollitia necessitatibus dolorem eum id eligendi excepturi dolores omnis. Provident, iure alias.
                        Provident unde molestiae ullam nostrum ipsa modi ipsum neque earum necessitatibus minus ea expedita rerum non, veritatis tempora maiores cumque. Dignissimos numquam aliquam ratione nobis necessitatibus aut, dolores inventore veniam.
                        <br><br>
                        Quis laborum accusantium beatae repellat perspiciatis mollitia ea ducimus sunt ab rerum. Omnis sit corrupti nostrum quas eaque optio, veniam non? Maxime quidem nam, vitae atque aut ipsum velit omnis!
                    </p>
                    <div class="clearfix">

                    </div>
                </article>
        </section>

        <aside id="sidebar">
            <div id="nav-blog" class="sidebar-item">
                <h3>Creación de artículo!</h3>
                <a href="#" class="btn btn-success">Crear artículo</a>
            </div>

            <div id="search" class="sidebar-item">
                <h3>Buscador</h3>
                <p>Encuentra el artículo que buscas</p>
                <form>
                    <input type="text" name="search">
                    <input class="btn" type="submit" name="submit" value="Buscar">
                </form>
            </div>
        </aside>
        
        <!-- LIMPIAR FLOTADOS -->
        <div class="clearfix"></div>
    </div>

    <footer id="footer">
        <div class="center">
            &copy; Developed by Nestor Rivas
        </div>
    </footer>

</body>
</html>
```

Ya tenemos el HTML, ahora vamos con los estilos...

```css
/* Estilos a detalles de artículo */
.article-detalle .image-wrap{
  float: none;
  width: 100%;
  height: 300px;
}

.article-detalle .image-wrap img{
  float: none;
  width: 100%;
  height: auto;
}

.article-detalle .subheader{
  margin-bottom: 10px;
  margin-top: 10px;
  border: none;
}
```

Con esto, ya tenemos la página de detalle de artículo, hecha.