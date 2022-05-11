# imagenes

## etiqueta

< img > No debe llevar etiqueta de cierre.

Al ser un elemento vacio no puede tener nodos secundario es decir, no puede ir anidado.
En caso de tener cierre es una etiqueta de html no válida.

## Atributos

+ ### alt 

ste atributo define el texto alternativo que describe la imagen, texto que los usuarios verán si la URL de la imagen es errónea o la imagen tiene un formato no soportado o si la imagen aún no se ha descargado.

+ ## longdesc

especifica un hipervínculo a una descripción detallada de una imagen.
2022 casi no tiene soporte

+ ### crossorigin

Las páginas web a menudo realizan solicitudes para cargar recursos en otros servidores. Aquí es donde entra CORS. Una solicitud de origen cruzado es una solicitud de un recurso (por ejemplo, hojas de estilo, iframes, imágenes, fuentes o scripts) de otro dominio.
CORS significa Cross-Origin Resource Sharing, y es un mecanismo que permite que los recursos de una página web se soliciten desde otro dominio fuera de su propio dominio. Define una forma de cómo un navegador y un servidor pueden interactuar para determinar si es seguro permitir la solicitud de origen cruzado.
Lo opuesto a las solicitudes de origen cruzado son las solicitudes del mismo origen
Esto significa que una página web solo puede interactuar con otros documentos que también están en el mismo servidor. 
El estándar de Intercambio de Recursos de Origen Cruzado trabaja añadiendo nuevas cabeceras HTTP que permiten a los servidores describir el conjunto de orígenes que tienen permiso para leer la información usando un explorador web.     

**Valores posibles :**

 anonymous una solicitudes de este elemento no tendrán establecido el indicador de credenciales.

**use-credentials :**

CORS, las solicitudes de este elemento tendrán marcado el indicador de credenciales; esto significa que la solicitud proporcionará credenciales.

Por defecto, es decir cuando el atributo no es específicado, CORS no se usa.

+ ## height o width

Altura en pixeles  html5
altura en porcentaje html4

+ ## src

La URL de la imagen. Este atributo es obligatorio para el elemento < img >.

