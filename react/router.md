# router con React Router

## Configuracion en el proyacto

instalamos el npm

```
npm install react-router-dom@6
```

## Estructura de carpetas y configuracion para tener router react en toda la aplicacion incluido app.js.

- src
  - components
  - pages
    - Contato.js
    - Home.js
    - Error404.js
    - Tacos.js
  - routers
    - AppRouter.js
  - index.js
  - App.js

En pages se almacenaran todas los componentes paginas.

## Para tener react Router en toda la App...

```javascript
import React from 'react';
import { createRoot } from 'react-dom/client';
import { BrowserRouter } from 'react-router-dom';
import App from './App';

const rootElement = document.getElementById('root');
const root = createRoot(rootElement);

root.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);
```

En app importamos el routers...

```javascript
import React from 'react';
import './style.css';
import RouterApp from './routers/RouterApp';

export default function App() {
  return (
    <div>
      <header>
        <h1>Estamos en app</h1>
      </header>
      <RouterApp />
    </div>
  );
}
```

En routers se almacenan todos los componentes que generan las rutas.
ej de AppRouter donde tenemos tres paginas (contacto,home,Tacos) y una ruta dinamica ( tacos/:tipo ).
En cada ruta se imprime un componente que debe ser importado.

```javascript
import React from 'react';
import { Routes, Route } from 'react-router-dom';
import Home from '../pages/Home';
import Contacto from '../pages/Contacto';
import Tacos from '../pages/Tacos';
import TiposTacos from '../components/TiposTacos';

export default function RouterApp() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/contacto" element={<Contacto />} />
      <Route path="/tacos" element={<Tacos />} />
      <Route path="/tacos/:tipo" element={<TiposTacos />} />
      <Route path="*" element={<Error404 />} />
    </Routes>
  );
}
```

Actualmente no hace falta enviar el parametro exact al componente Route ya que por defecto hace una busqueda especifica de la ruta por lo que tampoco importa el orden ( de mas especifico a menos especifico ) en el path de las rutas.

# Link (React Router)

Ejemplo de un Link que nos lleva a la pagino home.

```javascript
<Link to="/">Home</Link>
```

Obviamente debe existir la ruta pertinente.

```javascript
 <Route path="/" element={<Home />} />
```

# Rutas Dinamicas

Ruta

```javascript
 <Route path="/tacos/:tipo" element={<TiposTacos />} />
```

implemetacion de la ruta en el componente Tacos con Link para armar unas opciones de busqueda.

```javascript
 import React from 'react';
import { Link } from 'react-router-dom';

export default function Tacos() {
  const tacos = ['CARNE', 'POLLO', 'ESPECIAL', 'DOBLE QUESO'];

  return (
    <div>
      <h1>Tacos</h1>
      <div className="ListaTacos">
        {tacos.map((taco) => (
          <Link key={taco} to={`/tacos/${taco}`}>
            {taco}
          </Link>
        ))}
      </div>
    </div>
  );
}
```

# useParams (Hooks para extraer datos de la url);

Ej extraemos de la ruta dinamica

```javascript
 <Route path="/tacos/:tipo" element={<TiposTacos />} />
```

el elemento tipo de la url en el componente TipoTacos.

```javascript
import React from 'react';
import { useParams } from 'react-router-dom';

export default function TiposTacos() {
  const { tipo } = useParams();
  return (
    <div>
      <h1>{tipo}</h1>
    </div>
  );
}
```

# Rutas anidadas (React Router).

ej. ruta dinamica anidada con ruta details que mostrar un componente TacoDetalles.
lo siguiente se encuentra en routers....

```javascript
<Route path="/tacos/:tipo" element={<TiposTacos />}>
  <Route path="details" element={<TacoDetalles />} />
</Route>
```

El path de la ruta anidada quedara pagina/tacos/tipo/details
Se debe usar una ruta relativa en la ruta anidada.
Implementacion en el componente TiposTacos con un link que te lleva a detalles del taco elegido...

```javascript
import React from 'react';
import { useParams, Link, Outlet } from 'react-router-dom';

export default function TiposTacos() {
  const { tipo } = useParams();
  return (
    <div className="container">
      <h1>{tipo}</h1>
      <hr />
      <Link to="details">Ir a los detalles</Link>
      <Outlet />
    </div>
  );
}
```

Para que el componente que se manda por la ruta anidada sea visible see debe colocar el Outlet.
Nótese que dentro del componente ruta tambien tenemos el parametro de la ruta padre.

```javascript
import React from 'react';
import { useParams, Link } from 'react-router-dom';
export default function TacoDetalles() {
  const { tipo } = useParams();
  return (
    <div className="container">
      <h1>Detalles</h1>
      <p>Nombre : {tipo} </p>
      <p>Compojnentes: </p>
      <Link to="./../">Cerrar</Link>
    </div>
  );
}
```

# index router (React Router)

Carga la ruta anidada en el mismo path que la ruta padre.

```javascript
<Route path="/tacos" element={<Tacos />}>
  <Route index element={<ComponenteIndex />} />
  <Route path="details" element={<TacoDetalles />} />
</Route>
```

# NavLink (React Router)

Funciona igual que el link pero agrega una clase al Link que se encuentra activo.

Debemos importar el NavLink

```javascript
import { NavLink } from 'react-router-dom';

export default function App() {
  let activeClassName = 'nombreClaseActiva';
  return (
      <header>
        <h1>Titulo Header APP</h1>
        <nav className="navbar">
          <ul>
            <li>
              <NavLink
                to="/contacto"
                className={({ isActive }) =>
                  isActive ? activeClassName : undefined
                }
              >
                Contacto
              </NavLink>
            </li>
            <li>
              <NavLink
                className={({ isActive }) =>
                  isActive ? activeClassName : undefined
                }
                to="/"
              >
                Home
              </NavLink>
            </li>
          </ul>
        </nav>
      </header>
```

Luego en style.css le damos estilos a .nombreClaseActiva para que se meustre como deseamos.

Para evitar agregar funciones en cada NavLink podemos crear un componente personalizado que retorne el Navlink con el classname con el valor que le asignamos al props clase.
Ej del componente que llamaremos NavLinkPersonalizado:

```javascript
import React from 'react';
import { NavLink } from 'react-router-dom';

export default function NavLinkPersonalizado({
  to,
  clase,
  children,
  ...props
}) {
  return (
    <NavLink
      {...props}
      className={({ isActive }) => (isActive ? clase : undefined)}
      to={to}
    >
      {children}
    </NavLink>
  );
}
```

Implementacion el NavLink personalizado pasandole el path y por clase el nombre de la clase que se aplicara cuando este activo...

```javascript
<li>
  <NavLinkPersonalizado to="/" clase="nombreclase">
    Home
  </NavLinkPersonalizado>
</li>
<li>
  <NavLinkPersonalizado to="/contacto" clase="nombreclase">
    Contacto
  </NavLinkPersonalizado>
</li>
```

Ahora solo debemos dar estilos a la clase .nombreclase, este valor es modificable desde el props del NavLinkPersonalizado.
