# router con React Router

## Configuracion en el proyacto

instalamos el npm

```
npm install react-router-dom@6
```

## Estructura de carpetas y configuracion para que tener router react en toda la aplicacion incluido app.js.

- src
  - pages
    - Aboutpages.js
    - ContatoPages.js
    - HomePages.js
    - Error404Pages.js
  - routers
    - AppRouter.js
  - index.js
  - App.js

En pages se almacenaran todas los componentes paginas.
En routers se almacena un unico archivo con las importacioens de los componentes que se mostrara al cargar las rutas y las rutas existentes.
ej de AppRouter:

```javascript
import React from 'react';
import {BrowserRouter as Router,Route,Routes} from 'react-router-dom';
import AboutPages from '../pages/AboutPages';
import ContactoPages from '../pages/ContactoPages';
import HomePages from '../pages/HomePages';
import App from '../App';

export default function AppRouter() {
  return (
    <Router>
      <Routes>
        <Route path='/about' element={ <AboutPages />}  />
        <Route path='/contacto' element={<ContactoPages />}  />
        <Route path='/' element={<App />}  />
        <Route path='*' element={<Error404Pages />}  />
      </Routes>
    </Router>
  )
}
```

actualmente no hace falta enviar el parametro exact al Route.

El index.js :

```javascript
import React from 'react';
import ReactDOM from 'react-dom/client';
import AppRouter from "./routers/AppRouter";
import './index.css';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <AppRouter />
  </React.StrictMode>
);
```
