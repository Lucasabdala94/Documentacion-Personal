# video

El elemento video se utiliza para incrustar vídeos en un documento HTML o XHTML.

## Atributos

1. src - Direccion del recurso
Es opcional; podrás optar, en su lugar, por el elemento `<source>`dentro del bloque de vídeo para especificar el video que se va a incrustar.

2. crossorigin - Cómo maneja el elemento las solicitudes de origen cruzado(ver imagenes donde se explica).

3. poster -( Una URL ) Cuadro de póster para mostrar antes de la reproducción de video

4. preload - Sugerencias de cuánto almacenamiento en búfer necesitará probablemente el recurso de medios.
El objetivo de este atributo es proporcionar una sugerencia al navegador sobre qué cree el autor que llevará a la mejor experiencia para el usuario . Puede tener uno de los siguientes valores:
  + none: sugiere que el autor cree que el usuario no tendrá que consultar ese video,o bien que el servidor desea minimizar su tráfico; es decir, esta sugerencia indica que no se debe almacenar en caché este video.
  + metadatos: sugiere que aunque el autor piensa que el usuario no tendrá que consultar este video, es razonable capturar los metadatos (p. ej. longitud).
  + auto: esta sugerencia indica que, si es necesario, se puede descargar el video completo, incluso aunque el usuario no vaya a usarlo.

     Si no está configurado, su valor predeterminado está definido por el navegador (es decir, cada navegador puede elegir su propio valor predeterminado), aunque la especificación aconseje que se establezca a metadata.
El atributo autoplay  tiene prioridad sobre éste si se desea reproducir automáticamente un video, el navegador obviamente tendrá que descargarlo. La especificación permite establecer los atributos autoplay y preload.
La especificación no fuerza al navegador a seguir el valor de este atributo; es tan sólo una sugerencia.

5. autoplay - Sugerencia de que el recurso de medios se puede iniciar automáticamente cuando se carga la página.

6. playsinline - El atributo playsinline es un atributo booleano. Si está presente, sirve como una sugerencia para el navegador muestre el video  "en línea" en el documento de forma predeterminada, restringido al área de reproducción del elemento, en lugar de mostrarse a pantalla completa o en una ventana de tamaño independiente.
La ausencia no implica que el video se muestre a pantalla completa de forma predeterminada. De hecho, la mayoría de los navegadores han optado por reproducir todos los vídeos en línea de forma predeterminada, y en dichos agentes de usuario el atributo de reproducción en línea no tiene ningún efecto.

7. muted - silencia el recurso multimedia de forma predeterminada.

8. loop - El video se reproduce una y otra vez.

9. controls - Muestra los controles que dependen del navegador.

10. width y height dimensiones.

## media types

| Formato |      tipo     |
|---------|---------------|
|   MP4   |    video/mp4  |
|   WebM  |    video/webm |
|   Ogg   |    video/ogg  |

Otros formatos como MOV, FLV, 3GP, MPG, RMVB o ASF/WMV no se recomiendan para su utilización en web ya que son anticuados.


ejemplo 1

```html
<video width="400" controls autoplay muted>
  <source src="mov_bbb.mp4" type="video/mp4">
  <source src="mov_bbb.ogg" type="video/ogg">
  Your browser does not support HTML video.
</video>
```

ejemplo 2

```html
<article>
    <figure>
        <h2>Artículo 1: video</h2>
        <video src="media/gatito.mp4" controls poster="media/gatito.jpg"> </video>
        <figcaption>Figura: descipción video</figcaption>
    </figure>
</article>
```

### Insertar video de youtube

El código de inserción podemos obtener dando clic derecho sobre el video y elegir la opción: copiar código de inserción. otra forma de hacerlo es dando clic sobre la opción compartir ubicada debajo de cada video, aparecerá una ventana emergente, en ella seleccionamos la opción incorporar, aparecerá un fragmento de código y copiamos para luego pegar en nuestro documento html5. Debería verse algo así:

```html
<iframe width="560" height="315" src="https://www.youtube.com/embed/xwUUvc9eUhc" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
```
Es posible que algunos videos queden restringidos por parte de YouTube y no se puedan reproducir, entonces simplemente prueba con otro.