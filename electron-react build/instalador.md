# iniciar la aplicacion con forge electron

- Pagina de instrucciones...

```Bash
https://www.electronforge.io/guides/framework-integration/react#create-the-app-and-setup-the-webpack-config
```
- En consola ponemos...

```Bash
    npm init electron-app@latest my-new-app -- --template=webpack
```

- Luego instalamos las dependencis de desarrollo

```Bash
    npm install --save-dev @babel/core @babel/preset-react babel-loader
```


- ingresamos a webpack.rules.js y pegamos:

```Bash
  {
    test: /\.jsx?$/,
    use: {
      loader: 'babel-loader',
      options: {
        exclude: /node_modules/,
        presets: ['@babel/preset-react']
      }
    }
  }
```

- Luego en la carpeta src/renderer.js agregamos:

```Bash
  import './app.js';
```

- Creamos archivo app.js en src

```Bash
import * as React from 'react';
import * as ReactDOM from 'react-dom';

function render() {
  ReactDOM.render(<h2>Hello from React!</h2>, document.body);
}

render();
```

-Instalamos las dependencias de desarrollo

```Bash
  npm install --save react react-dom
```

## Pagina de aplicacion 

```Bash
  https://www.electronforge.io/
```