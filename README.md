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
{
 filter: {
  house_rules: {
   $in: [
    RegExp('NO smoke', i),
    RegExp('not smoke', i)
   ]
  }
 }
}
```

![smoke](img/3.png)

### Propiedades que no permitan fiestas ni fumadores.

```json
{
 filter: {
  $and: [
   {
    house_rules: {
     $in: [
      RegExp('no smoke', i),
      RegExp('not smoke')
     ]
    }
   },
   {
    house_rules: {
     $in: [
      RegExp('no parties', i),
      RegExp('not parties')
     ]
    }
   }
  ]
 }
}
```

![no fiestas ni fumar](img/4.png)

## Reto 2: Notación punto y arreglos

Usando la colección `sample_airbnb.listingsAndReviews`,  agrega un filtro que permita obtener todas las publicaciones que tengan  50 o más comentarios, que la valoración sea mayor o igual a 80, que  cuenten con conexión a Internet vía cable y estén ubicada en Brazil.

```json
{
    "review_scores.review_scores_rating":{
        $gte:80
    },
    "number_of_reviews":{
        $gte:50
    }
    ,amenities:{
        $in:[/ethernet/i]
    },
    "address.country":/brazil/i
}
```

![reto2](img/5.png)

## Reto 3: Introducción a las agregaciones

Usando la colección `sample_airbnb.listingsAndReviews`,  mediante el uso de agregaciones, encontrar el número de publicaciones  que tienen conexión a Internet, sea desde Wifi o desde cable (Ethernet).

```json
{amenities:
 	{
    $in:[/net/i,/wifi/i]
	}
}
```

![internet](img/6.png)

