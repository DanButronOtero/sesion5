## Reto 1: Expresiones regulares



### Propiedades que no permitan fiestas.

```json
{
 filter: {
  house_rules: RegExp('NO parties', i)
 }
}
```

![1](img/1.png)

### Propiedades que admitan mascotas.

```json
{
 filter: {
  $and: [
   {
    house_rules: {
     $not: RegExp('can't accept pets', i)
    }
   },
   {
    $or: [
     {
      house_rules: RegExp('accept pets', i)
     },
     {
      house_rules: RegExp('pets allowed', i)
     }
    ]
   }
  ]
 },
 project: {
  name: 1,
  house_rules: 1
 }
}
```

![1](img/2.png)

### Propiedades que no permitan fumadores.

```json

```



### Propiedades que no permitan fiestas ni fumadores.

```json

```

