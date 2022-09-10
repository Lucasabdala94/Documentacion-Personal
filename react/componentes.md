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

# Componentes con mas de un un objeto

```js
import React from "react";

function HolaMundo(){
  return(
    <>
      <h1>Hola Mundo</h1>
      <h2>Agustin Navarro</h2>
    </>
  ) 
}
export default HolaMundo;
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

# Pasar valores entre componenetes

En app.js 
```js
import logo from './logo.svg';
import './App.css';
import Saludar from './componentes/Saludar';
function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <Saludar name='Lucas abdala' agno='28'/>
        <Saludar name='Gonzalo abdala' agno='26'/>
        <Saludar name='Lourdes abdala' agno='20'/>
      </header>

    </div>

  )
}
export default App;

```
En el componente
```js
import React from "react";

function Saludar(props){

    return(
        <>
            <h2>Hola,{props.name},tiene {props.agno}</h2>
        </>
    ) 
}

export default Saludar;
```

# Pasar Objetos o Variables entre componenetes

En app.js creamos el objeto user.
```js
import './App.css';
import Saludar from './componentes/Saludar';
function App() {

  const user ={
    name: 'Abdala Lucas',
    edad: 26,
    color:'verde'
  };
  
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <Saludar userInfo={user}/>
      </header>
    </div>
  )
}
export default App;
```
En el componente saludar el objeto lleva el nombre que le dimos al pasarlo al componente, en este caso userInfo .
```js
import React from "react";

function Saludar(props){
    console.log(props)
    return(
        <>
            <h2>Hola {props.userInfo.name},tienes {props.userInfo.edad} años.</h2>
            <h3>Tu color favorito es {props.userInfo.color}.</h3>
        </>
    ) 
}
export default Saludar;
```
# Mandar funciones entre  componentes

En app.js creamos la funcion saludarFn.
```js
import './App.css';
import Saludar from './componentes/Saludar';
function App() {

  const user ={
    name: 'Abdala Lucas',
    edad: 26,
    color:'verde'
  };

  const saludarFn = name =>{
    console.log('Hola ' + name);
  }

  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <Saludar userInfo={user} saludar={saludarFn}/>
      </header>

    </div>

  )
}
export default App;
```
En el componente hijo Saludar usamos la funcion como la llamamos en el componente padre app.js al momento de asignarla al hijo(saludar).
```js
import React from "react";

function Saludar(props){
    const {userInfo,saludar}=props;
    return(
        <>
            <button onClick={()=>saludar(userInfo.name)}>Saludar</button>
        </>
    ) 
}
export default Saludar;
```
Si no creamos onClick={ ()=> con esta funcion anonima, la misma se ejecuta sin esperar el click en el boton.

En este ejemplo pasamos una funcion al componente hijo.Y el componente hijo devuelve la informacion que necesita el componente padre para hacer el console.log como ser el nombre que se extrae del objeto user.