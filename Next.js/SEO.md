# SEO

si no se aplica esto solo la primera pagina tiene esto por defecto.

## Devemos importar la libreria.

```js
import Head from 'next/head'
```

Luego la implementamos en el componente.

```js
export default function Game (){
    const router = useRouter();
    const { platform , game } = router.query;
    return (
        <>
            <Head>
                <title>{game} | {platform}</title>
            </Head>
            <h2>En la categoria: {platform}</h2>
            <h1>estamos en juegos: {game}</h1>
        </>
    )
}
```

El ejemplo es aplicada en un path dinamico haciendo cambiar el titulo de la pagina segun lo que se busque. Se puede agregar una descripcion y todos los metas necesarios.
