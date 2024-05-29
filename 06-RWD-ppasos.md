# Primeros pasos con el diseño web adaptable
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