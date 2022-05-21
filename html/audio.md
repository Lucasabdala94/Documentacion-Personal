# Audio

El elemento audio se usa para insertar contenido de audio en un documento HTML o XHTML.

# Atributos

## src

La URL del audio que se va a insertar. Está sujeta a los Controles de acceso HTTP. Es opcional; en su lugar puedes usar el elemento source dentro del bloque de audio para especificar el audio que se va a insertar.

## controls

Si está presente este atributo, el navegador ofrecerá controles para permitir que el usuario controle la reproducción de audio, incluyendo volumen, búsqueda y pausar/reanudar reproducción.

## Autoplay

Un atributo booleano; si se especifica (incluso aunque el valor sea "false"), el sonido comenzará a reproducirse automáticamente en cuanto sea posible, sin detenerse para terminar de cargar los datos.

## preload

El objetivo de este atributo enumerado es proporcionar una sugerencia al navegador sobre qué cree el autor que proporcionará la mejor experiencia para el usuario . Puede tener uno de los siguientes valores:
+ none: sugiere bien que el autor cree que el usuario no tendrá que consultar ese video, bien que el servidor desea minimizar su tráfico; es decir, esta sugerencia indica que no se debe almacenar en caché este video;
+ metadata: sugiere que aunque el autor piensa que el usuario no tendrá que consultar ese video, es razonable capturar los metadatos (p. ej. longitud);
+ auto: sugiere que el usuario necesita tener prioridad; es decir, esta sugerencia indica que, si es necesario, se puede descargar el video completo, incluso aunque el usuario no vaya a usarlo;
the empty string: que es sinónimo del valor auto.

Si no está configurado, su valor predeterminado está definido por el navegador (es decir, cada navegador puede elegir su propio valor predeterminado), aunque la especificación aconseje que se establezca a metadatos.

El atributo `autoplay` tiene prioridad sobre éste puesto que si se desea reproducir automáticamente un video, el navegador obviamente tendrá que descargarlo. La especificación permite establecer los atributos autoplay y preload.


## buffered

Un atributo que se puede leer para determinar qué intervalos de tiempo del multimedia se han almacenado en búfer. Este atributo contiene un objeto TimeRanges (en-US).
Al cargar un recurso multimedia para que lo use un elemento `<audio>` o `<video>`.

El atributo almacenado en búfer nos dirá qué partes de los medios se han descargado. Devuelve un objeto TimeRanges, que nos dirá qué fragmentos de medios se han descargado. Esto suele ser contiguo, pero si el usuario salta mientras los medios se almacenan en el búfer, es posible que contenga agujeros.

Esto funcionará con `<audio>` o `<video>`; por ahora, consideremos un ejemplo de audio:

```html
<audio id="my-audio" controls src="music.mp3">
</audio>
```
Podemos acceder a estos atributos así:

```JS
let myAudio = document.getElementById('my-audio');

let bufferedTimeRanges = myAudio.buffered;
```
TimeRanges son una serie de rangos de tiempo que no se superponen, con horas de inicio y fin.

Un objeto TimeRanges consta de las siguientes propiedades:

+ lenght : El número de rangos de tiempo en el objeto.
+ start (index) : La hora de inicio, en segundos, de un intervalo de tiempo.
+ end (index) : La hora de finalización, en segundos, de un intervalo de tiempo.

Sin ninguna interacción del usuario, generalmente solo hay un rango de tiempo, pero si salta en los medios, puede aparecer más de un rango de tiempo, como se ilustra en la siguiente visualización. Esto representa dos intervalos de tiempo almacenados en búfer: uno que abarca de 0 a 5 segundos y el segundo que abarca de 15 a 19 segundos.

    ------------------------------------------------------
    |=============|                    |===========|     |
    ------------------------------------------------------
    0             5                    15          19    21

Para esta instancia de audio, el objeto TimeRanges asociado tendría las siguientes propiedades disponibles:

```JAVASCRIPT

myAudio.buffered.length;   // returns 2
myAudio.buffered.start(0); // returns 0
myAudio.buffered.end(0);   // returns 5
myAudio.buffered.start(1); // returns 15
myAudio.buffered.end(1);   // returns 19

```
[Enlace donde se explica a fondo](https://developer.mozilla.org/en-US/docs/Web/Guide/Audio_and_video_delivery/buffering_seeking_time_ranges)


## autobuffer (Obsoleto)

## Ejemplos

```HTML
<audio src="https://developer.mozilla.org/@api/deki/files/2926/=AudioTest_(1).ogg"
       autoplay>Su navegador no tiene soporte para <code>audio</code>.
</audio>
```

```html
<audio controls>
  <source src="audio-tag-example.mp3" type="audio/mpeg">
  <source src="audio-tag-sample.wav" type="audio/wav">
  <source src="audio-tag-demo.ogg" type="audio/ogg">
  Audio tag is not supported in this browser.
</audio>
```

```html
<audio controls="controls" autoplay="autoplay" loop="loop" preload="metadata">
 <source src="/html5/html5-audio-example-mp3.mp3" />
 <source src="/html5/html5-audio-example-wav.wav" />
 <b>Your browser does not support HTML5 audio element</b>
</audio>
```

```html
<a href="media/sea.mp3">Track 1</a>
<a href="media/wind.mp3">Track 2</a>
```
