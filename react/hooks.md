# Hook de estados.

Cuando un estado se actualiza tanto el componente como sus hijos se actualizan.

# Utilizacion

Para usar este hook, primero debemos importarlo desde la librería de React.

```js
import React, { useState } from 'react'
```


## Ejemplo de encender y apagar coche

```js
import React,{useState} from "react";
import logo from './logo.svg';
import './App.css';

export default function App() {
  
  const [stateCar,setStateCar] = useState(false);
  
  const encenderApagar = ()=>{
    setStateCar(preValue => !preValue);
  }
  
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <h3>El coche esta : {stateCar ? 'Encendido' : 'Apagado'}</h3>
        <button onClick={encenderApagar}> Encender / Apagar </button>
      </header>
    </div>

  )
}
```
Ejecutar el método useState con el valor inicial de nuestro estado ( useState( false ); )  nos devuelve un array que tendrá el valor del estado y un método para actualizar el estado.
usando array destructuring nos permite extraer los elementos de un array y crear variables directamente con el estado y el metodo para actualizarlo.

# Hook de efectos.

Para usar este hook, primero debemos importarlo desde la librería de React.

```js
import React,{useEffect, useState} from "react";
```

# Ejemplo de contador

```js
export default function App() {
  
  const [stateCar,setStateCar] = useState(false);
  const [contar,setContar] = useState(0); 

  useEffect(()=>{
    console.log(`Total : ${contar}`);
  },[contar])

  const encenderApagar = ()=>{
    setStateCar(preValue => !preValue);
    setContar(contar+1);
  }
  
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <h3>El coche esta : {stateCar ? 'Encendido' : 'Apagado'}</h3>
        <h4>Clicks : {contar}</h4>
        <button onClick={encenderApagar}> Encender / Apagar </button>
      </header>
    </div>

  )
}
```
El use effect lo unico que hace es hacer el console log una vez que se ejecuto el componente.

¿Se ejecuta useEffect después de cada renderizado? ¡Sí! Por defecto se ejecuta después del primer renderizado y después de cada actualización. Más tarde explicaremos cómo modificar este comportamiento. En vez de pensar en términos de “montar” y “actualizar”, puede resultarte más fácil pensar en efectos que ocurren “después del renderizado”. React se asegura de que el DOM se ha actualizado antes de llevar a cabo el efecto.

