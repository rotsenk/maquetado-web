# Cambiar las fuentes y el tipo de letra con CSS 3

Podemos cambiar la fuente muy fácilmente utilizando la etiqueta *font-family*, sin embargo también podemos hacerlo mediante fuentes de Google, como ustedes quieran.

```css
body {
  text-align: center;
  margin: 0px;
  padding: 0px;

  /* Fuentes */
  font-family:
    'Segoe UI', 
    Roboto, Oxygen, 
    Ubuntu, Cantarell, 
    'Open Sans', 'Helvetica Neue', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-font-smoothing: antialiased;
  -moz-osx-font-smoothing: antialiased;
}
```
Estas propiedades CSS están relacionadas con la suavidad de renderizado de fuentes en los navegadores web. Permíteme desglosarlo:

`-webkit-font-smoothing: antialiased;:` Esta propiedad se aplica a navegadores basados en WebKit (como Google Chrome y Safari). Cuando se establece en antialiased, mejora la legibilidad de las fuentes al aplicar un suavizado antialiasing. Esto significa que los bordes de los caracteres se renderizan de manera más suave, lo que reduce el efecto de “dientes de sierra” en las letras.
`-moz-font-smoothing: antialiased;:` Similar al caso anterior, esta propiedad se aplica a navegadores basados en Gecko (como Mozilla Firefox). Al establecerla en antialiased, también se logra un suavizado antialiasing para mejorar la apariencia de las fuentes.
`-moz-osx-font-smoothing: antialiased;:` Esta propiedad específica para macOS se aplica solo en Firefox en sistemas operativos macOS. Al igual que las anteriores, se utiliza para mejorar la legibilidad de las fuentes mediante el suavizado antialiasing.

# Estilando la cabecera
Agregaremos las reglas para modificar un poco el menú
```css
#menu {
  width: 70%;
  float: right;
  font-size: 18px;
}
``` 

## Maquetar Logo
Maquetaremos la sección del logo y la marca
```css
/* Maquetando logo, y marca */
#logo {
  width: 30%; /* cambiar a 30% */
  font-size: 30px;
  float: left;
  margin-top: 35px; /* colocar margen */
}

#logo img {
  display: block;
  float: left;
  height: 75px;
  
  /* colocar margen */
  margin-top: -15px; 
  margin-right: 20px;
}
```
## Maquetar menú
Seguiremos maquetando el menú 

```css
/* Maquetar menú */
#menu {
  width: 70%;
  float: right;
  font-size: 18px;
}

#menu ul{
  line-height: 85px;
  width: 60%;
  float: right;
}

#menu ul li{
  list-style: none;
}

#menu a{
  text-decoration: none;
  color: #153448;
  transition: 300ms all;
}

#menu a:hover{
  color: #03AED2;
}
```

Con esto tendríamos los enlaces estilados, pero hace falta modificar altura, y demás...

```css
#menu ul li{
  list-style: none;
  /* agregar cambios */
  height: 46px;
  display: inline-block;
  margin-left: 15px;
  margin-right: 15px;
}
```

Con esto ya tendríamos el menú, está súper bien.
Pero, ahora pasa algo, con los elementos flotados, si nosotros no limpiamos esos flotados, los elementos que vayamos agregando en el html van a querer colocarse en los huecos que quedan, porque no estaríamos limpiando eso. así que vamos a arreglar eso, para evitar que se quieran colar ahí.

Agregamos debajo de `nav` en nuestro html
```html
...
<!-- LIMPIAR FLOTADOS -->
<div class="clearfix"></div>
...

``` 
y luego agregamos en el css

```css
.clearfix{
  width: 75%;
  margin: 0px auto;
}
```
Leamos este artículo para saber más: https://developer.mozilla.org/es/docs/Web/CSS/clear 

Ahora ya tenemos esto, falta que le demos un toque de animación

## Animaciones con CSS3
Ahora que tenemos el menú hecho, ahora lo que vamos a hacer es darle una animación al logo.
`animation: nombre-animacion infinite 30s linear;`
el nombre de la animación lo hacemos por medio de keyframes, cuando nosotros creamos un `keyframes` significa que vamos a hacer una animación.
infinite: significa que nunca va a detenerse de hacer la animación.
los segundos: el tiempo que dura.
linear: quiere decir que lo hará a una velocidad constante, no al principio lento y después rápido.

```css
#logo img {
  display: block;
  float: left;
  height: 75px;
  margin-top: -15px; 
  margin-right: 20px;
  /* Colocar animaciones */
  animation: girar infinite 30s linear;
}

@keyframes girar {
  10%{
    height: 100px;
  }
  100%{
    height: 200px;
  }
}
```

En nuestro caso, utilizaremos algo que vaya desde el inicio hasta el fin de la transición utilizando *from* y * to* 

```css
#logo img {
  display: block;
  float: left;
  height: 75px;
  margin-top: -15px; 
  margin-right: 20px;
  /* Colocar animaciones */
  animation: girar infinite 5s linear;
}

@keyframes girar {
  from{
    transform: rotate(0deg);
  }
  100%{
    transform: rotate(360deg);
  }
}
```

Con esto, ya tenemos la animación hecha, y estilada la cabecera