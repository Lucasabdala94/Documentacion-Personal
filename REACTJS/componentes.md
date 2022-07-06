# Ubicacion

En la carpeta src de la app => Creamos la carpeta componentes.


# Nombre de los componentes

La primera letra siempre con mayusculas.


# Extructura interna

```js
import React from "react";

function HolaMundo(){


    return(
        <div>
            <h1>Hola Mundo</h1>
            <h2>Agustin Navarro</h2>

        </div>
    ) 
}

export default HolaMundo;
```
Esto se conoce con el nombre de componenete funcional.
Esta fincion puede llevar propiedades. Estas propiedades solo pueden ser enviados de un componente padre a un componente hijo.
No es posible pasar propiedades de un componente hijo a un componente padre.

```js
import React from "react";

function Saludar( props ){

    return <h1> Hola, {props.nombre} </h1>; 
}

export default Saludar;
```


Primero las importaciones....
Segundo la funcion con el nombre del componente, siendo obligatorio el return...

Tenemos un solo export default por archivo, Se puede tener mas de una funcion por componente y tendriamos que hacer la exportacion normal.

Lo normal seria tener un solo componente por archivo pero se puede tener ams de uno.



# Importamos y utilizamos en componente principal app.js


```javascript
import logo from './logo.svg';
import './App.css';
import HolaMundo from './componentes/HolaMundo'; // importamos componente...

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <HolaMundo/>  /* Utilizamos el componente... */
      </header>
    </div>
  );
}

export default App;
```

# Componentes de Clases

```js
import React from "react";

class Saludo extends React.Component{
  render(){
    return <h1> Hola, {this.props.nombre} </h1>;
  } 
}

```

