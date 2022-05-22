# Crear DB

Necesitamos primero conectarnos a la base de datos.

```JS
let openRequest = indexedDB.open( name, version);
```

+ name – una cadena, el nombre de la base de datos.
+ version – una versión de entero positivo, por defecto 1

Podemos tener muchas bases de datos con diferentes nombres, pero todas ellas existen dentro del origen actual (dominio/protocolo/puerto). Diferentes sitios web no pueden acceder a las bases de datos de los demás.

La llamada devuelve openRequestun objeto, debemos escuchar los eventos en él:

+ **success** : la base de datos está lista, está el "objeto de la base de datos" openRequest.result, deberíamos usarlo para futuras llamadas.

+ **error** : apertura fallida.

+ **upgradeneeded** : la base de datos está lista, pero su versión está desactualizada.


<br>
<br>

### **IndexedDB tiene un mecanismo integrado de "versiones de esquema", ausente en las bases de datos del lado del servidor.**

<br>
A diferencia de las bases de datos del lado del servidor, IndexedDB es del lado del cliente, los datos se almacenan en el navegador, por lo que nosotros, los desarrolladores, no tenemos acceso a tiempo completo. Entonces, cuando hayamos publicado una nueva versión de nuestra aplicación y el usuario visite nuestra página web, es posible que necesitemos actualizar la base de datos.

Si la versión de la base de datos local es inferior a la especificada en open, se activa un evento especial **upgradeneeded** y podemos comparar versiones y actualizar estructuras de datos según sea necesario.

El evento **upgradeneeded** también se activa cuando la base de datos aún no existe (técnicamente, su versión es 0), por lo que podemos realizar la inicialización.

<br>
<br>

## **No podemos abrir una base de datos utilizando una versión anterior de convocatoria abierta**.

<br>

Si la base de datos del usuario actual tiene una versión superior a la de la openllamada, por ejemplo, la versión de la base de datos existente es 3, y lo intentamos open(...2), entonces se trata de un error openRequest.onerror.



Eso es raro, pero tal cosa puede suceder cuando un visitante carga un código JavaScript desactualizado, por ejemplo, desde un caché de proxy. Entonces el código es viejo, pero su base de datos es nueva.
<br>
<br>


## Ejemplo

<br>

```javascript

document.addEventListener('DOMContentLoaded',()=>{
    generadores();
})

function generadores(){
    // creamos base de datos.
    let basegeneradores = window.indexedDB.open('generadores',1);

    // si algo falla.
    basegeneradores.onerror = function(){
        console.log('Hubo un errror');
    }
    //si se creo bien.
    basegeneradores.onsuccess= function(){
        console.log('base de datos creada !!');
    }

    //configuracion de base de datos.
    basegeneradores.onupgradeneeded = function(e){
        // se ejecuta al crear la base de datos y cuando la version es superior a la anterior.
        const db = e.target.result;

        const objectStore = db.createObjectStore('generadores',{
            keyPath:'generadores',
            autoIncrement:true    
        });
        //definir las columnas
        objectStore.createIndex('nombre','nombreconquereferenciamos',{unique:false});
        objectStore.createIndex('email','nombreconquereferenciamosemail',{unique:true});
    }

}


```

Para ver la base de datos creada y sus procedimientos...

` e.target.result `  

<br>
<br>

# objectStore
<br>

Para almacenar algo en IndexedDB, necesitamos un almacén de objetos .

Un objectStore es un concepto central de IndexedDB. Las contrapartes en otras bases de datos se denominan "tablas" o "colecciones". Es donde se almacenan los datos. Una base de datos puede tener múltiples almacenes: uno para usuarios, otro para bienes, etc.
<br>
<br>

![INGRE cROME](../../imagenes/formato%20indexeddb.png)

<br>
A pesar de ser llamado "almacén de objetos",Podemos almacenar casi cualquier valor, incluidos objetos complejos.
IndexedDB utiliza el algoritmo de serialización estándar para clonar y almacenar un objeto. Es como JSON.stringify, pero más potente, capaz de almacenar muchos más tipos de datos.

Un ejemplo de un objeto que no se puede almacenar: un objeto con referencias circulares. Dichos objetos no son serializables. JSON.stringifytambién falla para tales objetos.
<br>
<br>

# key

TIENE QUE HABER UN UNICO key para cada valor en el store.
La clave puede ser numerica, date, string, o array.
Este identificador unico nos permite  podemos buscar/eliminar/actualizar valores por clave.(CRUD)
<br>
<br>

# Crear objectStore

La operación es síncrona, no es await necesario.

La sintaxis para crear un almacén de objetos:
<br>

```javascript
1 db.createObjectStore(name[, keyOptions]);
```
<br>

name : es el nombre del store, ejemplo 'autogeneradores'

keyOptions: es un objeto opcional con una de dos propiedades

  keyPath – una ruta a una propiedad de objeto que IndexedDB usará como clave, por ejemplo, id.
  autoIncrement - si es true, la clave para un objeto recién almacenado se genera automáticamente, como un número en constante incremento.

Si no proporcionamos keyOptions, tendremos que proporcionar una clave explícitamente más adelante, al almacenar un objeto.

Por ejemplo, este almacén de objetos usa id la propiedad como clave:

```javascript
db.createObjectStore('books', {keyPath: 'id'});
```


Un objectStore solo se puede crear/modificar mientras se actualiza la versión de la base de datos, en el upgradeneededcontrolador.

Esa es una limitación técnica. Fuera del controlador, podremos agregar/eliminar/actualizar los datos, pero los store de objetos solo se pueden crear/eliminar/alterar durante una actualización de versión.


