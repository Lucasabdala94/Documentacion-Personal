# Branch

## Listar TODAS las ramas en local y remoto.  

```console
git branch -a
```

## Listar ramas en local .  

```console
git branch
```
Para tener las ramas del repo de GitHu en local hay que hacer git fetch primero y luego movernos a esa rama con git checkout NOMBRE DE RAMA EN REPO.

a modo de ej. si en el repositorio tenemos la rama helado... Al poner git branch no aparecera en la lista de ramas ya que no se encuentra entre las ramas locales...
con git fetch nos descargamos todas las ramas del repositorio de GitHub. Si hacemos git brach seguira sin aparecer...
para que la rama este en local hay que moverse a ella y esto lo hacemos con git checkout helado, NO HACE FALTA PONER EL NOMBRE DEL REPOSITORIO (NORMALMENTE ORIGIN)

## Crear Rama en local  

```console
git branch NOMBRE DE RAMA
```
Permaneceremos en la rama que estabamos antes de crearla.

## Crear Rama en local  y moverse a esa rama.

```console
git checkout -b NOMBREDERAMA 
```

## Moernos a una rama local o remota.

```console
git checkout NOMBRE DE RAMA
```

## Borrar rama en local

```console
git branch -d NOMBRE DE RAMA
```

si no funciona....Hay veces que no se borra porque no se hizo un merge.

```console
git branch -D NOMBRE DE RAMA
```

Si la rama solo esta en el repo local la borrara definitivamente.
Si la rama esta en el repo local y remoto de Github solo borrara la rama en local.

para poder eliminar no nos tenemos que encontrar en esa rama

## Borrar rama del repositorio local y Github.

```console
git push origin --delete practica-React-Router
```













