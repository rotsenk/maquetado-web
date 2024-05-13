# Sidebar
## HTML de la barra lateral y del contenido central
Vamos a hacer el html del contenido central y del sidebar, para ello vamos a colocar debajo del slider el contenido que vamos a necesitar.

```html

...
    <!-- Slider -->
    <div id="slider" class="slider-big slider-medium">
        <h1>Bienvenido a mi web!</h1>
        <a href="#" class="btn-white">Ir al blog</a>
    </div>

    <!-- Sidebar -->
    <div class="center">
        <section id="content">
            <h2 class="subheader">Últimos artículos</h2>
            <!-- Listado de artículos -->
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
...

```

## Maquetando con CSS el Sidebar y la caja de contenido central
Ahora nos tocaría hacer el CSS de cada uno de los elementos.

```css
/* Maquetar el contenido central */
#content{
  width: 70%;
  float: left;
  border: 1px solid red;
  min-height: 650px;
  margin-right: 20px;
}

/* Maquetar el contenido lateral */
#sidebar{
  width: 25%;
  float: left;
  border: 1px solid green;
}

/* Estilos para cada uno de los sidebar-item */
.sidebar-item{
  background: #f7f7f7;
  padding: 20px;
  margin-top: 30px;
}

.sidebar-item h3{
  text-transform: uppercase;
  font-size: 18px;
  margin: 0px;
  padding-bottom: 10px;
  margin-bottom: 10px;
  border-bottom: 3px solid #eee;
}
```

Ahora, veremos el inconveniente con el clearfix...
El problema es que no está implementando la técnica típica de clearfix, que generalmente se usa para limpiar los elementos flotantes dentro de un contenedor. La técnica clearfix típica se implementa de la siguiente manera en CSS:

```css

.clearfix::after {
  content: "";
  display: table;
  clear: both;
}

```
Esta definición crea un pseudo-elemento después del contenido de la clase .clearfix que se comporta como un elemento vacío con una propiedad de clear: both;, lo que garantiza que el contenedor .clearfix se expanda para contener los elementos flotantes dentro de él.

##  CSS para el formulario de busqueda y los botones de la web
Vamos a darle estilos a la parte del sidebar, también a los botoncitos...

```css
/* CSS para el formulario de búsqueda y botones del sitio web */
.btn{
  display: block;
  background: black;
  color: white;
  padding: 15px;
  font-weight: bold;
  text-transform: uppercase;
  font-size: 14px;
  text-decoration: none;
  max-width: 120px;
  transition: 300ms all; /* para usar pseudoclases*/
  border: none;
  cursor: pointer;
}

.sidebar-item .btn{
  margin: 0px auto;
  margin-top: 10px;
}

.btn-success{
  background: rgba(22, 121, 171, 1) 39%
}

.btn-success:hover{
  background-color: black;
}
```

Ahora, nos quedaría la maquetación del input, vamos a utilizar un selector nuevo, bueno, que no hemos utilizado aún, es el selector de atributos.
Si lo le pongo corchetes al seleccionar el elemento, y pongo el atributo y el valor, les puedo estilar a ese tipo de elemento. Porque en este caso elementos *inputs* hay varios, pero los de tipo text son los que estilaríamos.

```css
/* Maquetar inputs */
input[type="text"], 
textarea{
    width: 100%;
    height: 30px;
    border: 1px solid #eee;
    padding: 3px;
    margin-bottom: 5px;
    transition: 300ms all;
}

input[type="text"]:focus, 
textarea:focus{
    box-shadow: 0px 0px 3px #ccc inset;
}
```