# Slider o marquesina

Vamos a crear una especie de slider, que tenga un desgradado y contenga un titular, ocuparemos parte de la pantalla, y que tenga un fondo desgradado.
Similar a un jumbotrón de bootstrap

Crearemos debajo del header...

```html
...
<!-- Slider -->
    <div id="slider" class="slider-big slider-medium">
        <h1>Bienvenido a mi web!</h1>
        <a href="#" class="btn-white">Ir al blog</a>
    </div>
...
```

Ahora, en css podemos estilar
```css
#slider{
  width: 100%;
  background: #153448;
  height: 350px;
  line-height: 320px;
  color: white;
  text-shadow: 0px 0px 5px #444;
}
```

Pero, ahora que ya tenemos esto, vamos a cambiar el background por un desgradado.
Para ello, buscamos en google.
https://cssgradient.io/

y podemos hacer el degradado que nosotros creamos conveniente.

```css
#slider {
  width: 100%;
  background: rgb(22, 121, 171);
  background: radial-gradient(
    circle,
    rgba(22, 121, 171, 1) 39%,
    rgba(7, 65, 115, 1) 100%
  );
  height: 350px;
  line-height: 320px;
  color: white;
  text-shadow: 0px 0px 5px #444;
}
```

Lo siguiente que haremos es modificar los estilos del h1 del slider, para que no nos meta ese margen superior.

```css
#slider h1{
  margin-top: 0.2px;
  padding: 0px;
  text-align: center;
}
```

Aún nos haría falta modificar un poco por el botón de "ir al blog"

```css
#slider {
  width: 100%;
  background: rgb(22, 121, 171);
  background: radial-gradient(
    circle,
    rgba(22, 121, 171, 1) 39%,
    rgba(7, 65, 115, 1) 100%
  );
  height: 350px;
  /* line-height: 320px; QUITARLO */
  color: white;
  text-shadow: 0px 0px 5px #444;
}

#slider h1 {
  margin-top: 0.2px;
  padding: 0px;
  padding-top: 115px;
  text-align: center;
}

.btn-white {
  display: block;
  background: white;
  color: #868585;
  padding: 10px;
  width: 95px;
  height: 35px;
  margin: 0px auto;
  font-size: 18px;
  text-transform: uppercase;
  text-shadow: none;
  text-decoration: none;
  line-height: 35px;
  box-shadow: 0px 0px 5px #868585;
  margin-top: 40px;
  border-radius: 4px;
  transition: 300ms all;
}

.btn-white:hover{
  background: #444;
  color: white;
}
``` 

Listo, con esto ya tenemos el Slider hecho. Entonces hace falta hacer que este Slider tenga diferentes tamaños.
Haremos la parte del blog, y aprovecharemos de meter la parte del slider y hacerla más pequeña.

- Creamos un nuevo archivo que se llame `blog.html`, copiamos todo lo que se encuentra en el `index.html` y lo pegamos dentro. 
y modificamos el enlace `<a href="blog.html">Blog</a>` para que del index llamemos a la ruta del blog, y luego en el blog modificamos la sección del slider
```html
<!-- Slider -->
    <div id="slider" class="slider-big slider-small">
        <h1>Blog!</h1>
    </div>
``` 

Luego, en el css creamos la clase del `slider-small` 

Deberemos colocar el css de tal forma que le dé prioridad, porque css da prioridad a lo específico, y para que nos tome y coloque los estilos, deberemos llamar desde el id, y decirle que el id que posea la clase pues hay que aplicarle los estilos, ya que si no lo hacemos así, no los toma en cuenta porque anteriormente tenemos la configuración.
```css
#slider.slider-small{
  height: 150px;
}

#slider.slider-small h1{
  margin-top: 0.2px;
  padding: 0px;
  padding-top: 50px;
}
```