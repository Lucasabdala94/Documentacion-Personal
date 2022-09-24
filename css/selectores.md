# Selectores

## Selectores Simples

- Selectores Elementales
- Selectores de Atributos

## Selectores Compuestos

- Selectores Agrupados
- Selectores Combinados
- Pseudoclases - Pseudoelementos

## Selectores

### Selector universal

```CSS
*{
}
```

### Selector por etiqueta

```CSS
NombreEtiqueta {
}
```

## Selectores de atributo

### ID

```CSS
#id {
}
```

### Clase

```CSS
.clase {
}
```

### Selector por Atributos

atributo de la etiqueta solo o atributo de etiqueta y valor.

```CSS
[href] {
}

[href="http://www.google.com"] {
}
```

si el valor del atributo comienza con un nombre.

```CSS

[href^="http"] {
}
```

Dará estilos a todo los href que comience su valor con http.

si la palabra se encuentra al final

```CSS

[href$="http"] {
}
```

si necesitamos que este valor que coincida no este necesariamente al comienzo y tampoco al final.

```CSS

[href*="http"] {
}
```
