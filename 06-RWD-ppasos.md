# Primeros pasos con el diseño web adaptable
## Explicación de media queries
Nuestra página web ya está maquetada, se mira muy bien, en la vista de escritorio, en una pantalla de PC pero qué pasaría si quisieramos ver en el móvil esta web? se miraría distorsionada.

Vamos a verificar, en el navegador, abriendo la sección de código fuente, inspeccionando el diseño adaptable, podemos notar que no se ve bien. Esto hay que arreglarlo aplicando Responsive Web Design (RWD).

Para hacer que una web sea responsive, tenemos que capturar los puntos de quiebre en donde hay que hacerle cambios en el CSS, comprimiendo la pantalla hasta ver en qué puntos la página tiene defectos, es ahí donde debemos usar *media queries*

Le decimos a la media que, desde el pixel cero de anchura, hasta el pixel 1488, de pantalla, se van a ejecutar estos estilos. Simplemente un media querie significa eso. 

```css
/*desde la anchura 0px hasta la anchura 1488px de pantalla*/
@media (max-width: 1488px) {
  body {
    background-color: red;
  }
}
```
Esta regla se aplica solamente cuando yo voy desde el pixel 0 de la pantalla, hasta el tamaño en concreto, en este caso 1488px, nosotros podemos ir aplicando más media queries, desde un media querie hasta otro.

Por ejemplo, si quiero que el máximo ancho de pixeles en pantalla sea 963px el fondo sea verde, perfectamente lo podemos aplicar, esto significaría que, cuando lleguemos a ese tamaño, cuando reduzcamos la pantalla por debajo de esa anchura, el fondo va a ser verde, y si no, o sea que, si lo hago más grande, el media querie, va a ser rojo el fondo.

Lo que sucede es que el media querie más pequeño sobreescribe lo que hace el media querie más grande.
```css
/*desde la anchura 0px hasta la anchura 963px de pantalla*/
@media (max-width: 963px) {
  body {
    /* el fondo será verde */
    background-color: rgb(0, 255, 0);
  }
}
```

Entonces ahora resulta que, 
```css
/*desde la anchura 963px hasta la anchura 1488px de pantalla*/
@media (max-width: 1488px) {
  body {
    /* fondo será rojo */
    background-color: red;
  }
}

/*desde la anchura 0px hasta la anchura 963px de pantalla*/
@media (max-width: 963px) {
  body {
    /* fondo será verde */
    background-color: rgb(0, 255, 0);
  }
}
```

Asi que, estos son los media queries, y así funcionan, es simple, pero a la vez es de darles un buen análisis.

## Aplicando media queries para diferentes puntos
Vamos a empezar a depurar nuestra web para las diferentes pantallas.
Quitaremos las reglas que teníamos en las media queries anteriormente, y veremos en qué puntos podemos capturar para modificar estilos.

A ese wrap que hace que todos los elementos se queden centrados, pues le vamos a configurar la anchura, a la clase `.center`

```css
/* Responsive */
/*desde la anchura 1314px hasta la anchura 1488px de pantalla*/
@media (max-width: 1488px) {
  body {
    /* fondo será cyan */
    background-color: rgb(0, 255, 204);
  }

  .center {
    width: 85%;
  }
}

/*desde la anchura 0px hasta la anchura 1314px de pantalla*/
@media (max-width: 1314px) {
  body {
    /* fondo será verde */
    background-color: rgb(0, 255, 0);
  }

  .center {
    width: 95%;
  }
}
```
Apun le he dejado el fondo por el hecho de verificar su cumplimiento según las reglas.

Ahora, en lugar de hacer muchas media queries podemos agregar algunas clases dentro de la media querie y así modificar.

```css
/*desde la anchura 797px hasta la anchura 1314px de pantalla*/
@media (max-width: 1314px) {
  body {
    /* fondo será verde */
    background-color: rgb(0, 255, 0);
  }

  .center {
    width: 95%;
  }

  #menu ul{
    width: auto; /* anchura automática, la que el navegador nos dé */
  }

  #logo{
    float: none; /*no flote a ningún lado, lo deje tal cual */
    font-size: 25px;
  }

  #logo img {
    height: 60px;
  }

}
```
Seguimos buscando los puntos, hasta que veamos que algo se descuadra en la pantalla.
Así quedaría el media querie...
```css
/*desde la anchura 0px hasta la anchura 797px de pantalla*/
@media (max-width: 797px) {
  body {
    /* fondo será verde */
    background-color: rgba(255, 0, 255, 0.92);
  }

  /* .center {
    width: 95%;
  /* } */ /* quitamos este porque ya lo heredamos del media querie de arriba */

  #logo{
    float: none; /*no flote a ningún lado, lo deje tal cual */
    width: 270px;
    margin: 0px auto;
    margin-top: 35px;
    font-size: 25px;
  }

  #logo img {
    display: block;
    float: left;
    height: 55px;
  }

  #menu,
  #menu ul {
    clear: both; /* que se limpie los posibles flotados */
    float: none; /*no flote a ningún lado, lo deje tal cual */
    width: 100%;
    margin: 0px; 
    padding: 0px;
    line-height: 50px;
  }

  /* modifica la barra lateral */
  #content {
    float: none;
    width: 100%;
  }

  #sidebar {
    float: none;
    width: 60%;
    margin: 0px auto;
    margin-bottom: 50px;
  }

  #slider h1 {
    padding-top: 115px;
    font-size: 25px;
  } 

  /* modifica el formulario */
  .mid-form {
    width: 70%;
  }

}
```

Por último tenemos esta media querie
```css
/*desde la anchura 0px hasta la anchura 497px de pantalla*/
@media (max-width: 497px) {
  #header {
      min-height: 130px;
      overflow: hidden; /* si se sale algún elemento del menu, pues que lo oculte */
      /* aunque lo optimo es que cuando el menú se encoge, se convierte en hamburguesa */
  }

  #menu,
  #menu ul {
    line-height: 50px;
  }
  
  #menu,
  #menu ul li {
    /* para que quepan más elementos dentro del menú */
    margin-left: 7px;
    margin-right: 7px;
  }

  #slider {
    height: 180px;
  }

  #slider h1 {
    font-size: 19px;
    padding-top: 30px;
  }

  #slider .btn-white {
    margin-top: 20px;
    width: 15%;
    height: 10%;
    font-size: 14px;
    line-height: 20px;
  }

  #slider.slider-small {
    height: 100px; /* para la sección del blog */
  }

  #slider.slider-small h1 {
    padding-top: 35px;
  }
}
```

y todo el css del responsive sería así:
```css
/* Responsive */
/*desde la anchura 1314px hasta la anchura 1488px de pantalla*/
@media (max-width: 1488px) {
  .center {
    width: 85%;
  }
}

/*desde la anchura 797px hasta la anchura 1314px de pantalla*/
@media (max-width: 1314px) {
  .center {
    width: 95%;
  }

  #menu ul{
    width: auto; /* anchura automática, la que el navegador nos dé */
  }

  #logo{
    float: none; /*no flote a ningún lado, lo deje tal cual */
    font-size: 25px;
  }

  #logo img {
    height: 60px;
  }

}

/*desde la anchura 497px hasta la anchura 797px de pantalla*/
@media (max-width: 797px) {
  /* .center {
    width: 95%;
  /* } */ /* quitamos este porque ya lo heredamos del media querie de arriba */

  #logo{
    float: none; /*no flote a ningún lado, lo deje tal cual */
    width: 270px;
    margin: 0px auto;
    margin-top: 35px;
    font-size: 25px;
  }

  #logo img {
    display: block;
    float: left;
    height: 55px;
  }

  #menu,
  #menu ul {
    clear: both; /* que se limpie los posibles flotados */
    float: none; /*no flote a ningún lado, lo deje tal cual */
    width: 100%;
    margin: 0px; 
    padding: 0px;
    line-height: 50px;
  }

  /* modifica la barra lateral */
  #content {
    float: none;
    width: 100%;
  }

  #sidebar {
    float: none;
    width: 60%;
    margin: 0px auto;
    margin-bottom: 50px;
  }

  #slider h1 {
    padding-top: 115px;
    font-size: 25px;
  } 

  /* modifica el formulario */
  .mid-form {
    width: 70%;
  }

}

/*desde la anchura 0px hasta la anchura 497px de pantalla*/
@media (max-width: 497px) {
  #header {
      min-height: 130px;
      overflow: hidden; /* si se sale algún elemento del menu, pues que lo oculte */
      /* aunque lo optimo es que cuando el menú se encoge, se convierte en hamburguesa */
  }

  #menu,
  #menu ul {
    line-height: 50px;
  }
  
  #menu,
  #menu ul li {
    /* para que quepan más elementos dentro del menú */
    margin-left: 7px;
    margin-right: 7px;
  }

  #slider {
    height: 180px;
  }

  #slider h1 {
    font-size: 19px;
    padding-top: 30px;
  }

  #slider .btn-white {
    margin-top: 20px;
    width: 25%;
    height: 10%;
    font-size: 12px;
    line-height: 20px;
  }

  #slider.slider-small {
    height: 100px; /* para la sección del blog */
  }

  #slider.slider-small h1 {
    padding-top: 35px;
  }
}
```
Le quitamos los colores de fondo, porque no son necesarios, solamente era para verificar que se cumplan las reglas de las media queries.
Hemos hecho un responsive rápido, a modo de que la maquetación dé la mejor cara, sin embargo se puede mejorar mucho, cada uno puede adaptarla a las necesidades personales y del sitio.

# Configurar Viewport para mejorar el Responsive
Ahora que tenemos todo bien adaptado y bien maquetado con html css3 y el responsive.
pero claro ahora mismo lo tenemos en vista de responsive entonces qué pasa que si tú por ejemplo abres tu página web en un móvil? 
vas a ver que no se está adaptando correctamente a la pantalla, te va a pasar esto de acuerdo si le das aquí al desplegable, podemos seleccionar algún dispositivo móvil que ya esté preconfigurado por ejemplo en Chrome si yo selecciono el `Galaxy S5`, si yo lo selecciono se vería su tamaño de pantalla o si selecciono por ejemplo un `iPhone X` se sería el tamaño de pantalla del teléfono entonces qué está pasando aquí? cómo se vería realmente la pantalla del iphone? que todo se ve muy pequeño vale todo se ve en una escala que sí está más o menos adaptado pero no se ve digamos en la escala original del diseño adaptable. de acuerdo? 
pero claro si lo cambiamos a un `iPhone x` vemos que la escala digamos que es bastante diferente aunque lo pongamos a digamos que a un tamaño "original", hay cosas que se ven muy grandes entonces lo que tenemos que hacer es configurar el `Viewport`, este lo que hace es que realmente esté responsive y se adapte bien a cada una de las pantallas en el cual cargue la página web entonces para hacer esto lo que tenemos que hacer es abrir nuestros archivos *.html* para esto se aplica cualquier tipo de web, debajo de la `meta charset` 
podemos meter viewport okay? y le vamos a indicar todo para que luego podemos ver proporcionado porque la escala inicial la hemos modificado.

`<meta name="viewport" content="width=device-width, initial-scale=1.0">`

Con esto, ya podemos ver la adaptabilidad en la escala original, relativa a las pantallas.