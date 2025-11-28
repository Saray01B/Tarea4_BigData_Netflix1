# Código de consultas para el Dataset peliculas y series de Netflix

## 1️⃣ Consultas básicas

## Inserción

### _Código_ 

- InsertOne()

```python
db.Catalogo.insertOne({
  ID: "s10001",
  Tipo: "Movie",
  Título: "Ejemplo 1",
  Director: "Director 1",
  Elenco: ["Actor 1", "Actor2"],
  País: "United States",
  Fecha_Agregación: 2022-09-25,
  Año_Lanzamiento: 2020,
  Clasificación: "PG-13",
  Duración: "100 min",
  Género: "Drama",
  Descripción: "Película de prueba 1"
})
```
- InsertMany()

```python
db.Catalogo.insertMany([
{
  ID: "s10002",
  Tipo: "Movie",
  Título: "Ejemplo 2",
  Director: "Director 2",
  Elenco: ["Actor 1", "Actor3"],
  País: "Colombia",
  Fecha_Agregación: 2024-01-10,
  Año_Lanzamiento: 2023,
  Clasificación: "PG-13",
  Duración: "120 min",
  Género: "Drama",
  Descripción: "Película de prueba 2"
},
{
  ID: "s10003",
  Tipo: "TV Show",
  Título: "Ejemplo 3",
  Director: "Director 1",
  Elenco: ["Actor 3", "Actor2"],
  País: "México",
  Fecha_Agregación: 2023-09-23,
  Año_Lanzamiento: 2022,
  Clasificación: "TV-MA",
  Duración: "1 temporada",
  Género: "Acción",
  Descripción: "Película de prueba 3"
},
{
  ID: "s10004",
  Tipo: "Movie",
  Título: "Ejemplo 4",
  Director: "Director 3",
  Elenco: ["Actor 3", "Actor 4"],
  País: "España",
  Fecha_Agregación: 2022-09-14,
  Año_Lanzamiento: 2021,
  Clasificación: "R",
  Duración: "98 min",
  Género: "Comedia",
  Descripción: "Película de prueba 4"
}
])
```
### _MongoDB_ 

Se realizó la inserción de 4 documentos en la colección "Catalogo", utilizando dos métodos distintos de consulta "InsertOne()" para agregar un registro específico y "InserMany()" para agregar varios registros en una operación, optimizando el proceso.

- InsertOne()

InsertOne() permite insentar un documentos individual en la colección. Se usa cuando se quiere agregar solo un nuevo registro al catalogo.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/f70c32b1-5687-4275-8e3f-5e4e603fd81b" /></p>

- InserMany()

InsertMany() permite insertar múltiples documentos en una sola operación. Es util cuando se quiren agregar varios registros al mismo tiempo.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/487adeba-c1c2-4b91-a133-a31034ad6bfd" /></p>

## Selección

### _Código_ 

El comando find() permite consultar documentos dentro de una colección. Puede usarse para buscar documentos completos, aplicar filtros o devolver un campo en específico.

- Seleccionar un documento por ID

```python
db.Catalogo.find({
  ID: "s10001"
})
```
- Seleccionar solo títulos y años

```python
db.Catalogo.find(
  {}, {Título:1, Año_Lanzamiento: 1, _id: 0}
)
```
- Seleccionar películas

```python
db.Catalogo.find({
  Tipo: "Movie"
})
```

### _MongoDB_ 

Se realizaron tres tipos de consultas con el método find(), selección por ID, con proyección y por tipo de contenido. Estas consultas permiten explorar la colección "Catalogo".

- Documento por ID

Busca un documento en donde el campo "ID" coincidad exactamente con "s10001". Este tipo de consulta se usa para un registro específico.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/87c0c8db-9fa5-4f80-8823-fd1bee1def4a" /></p>

- Documentos solo títulos y años

Selecciona todos los documento con {} y muestra el título, año de lanzamiento y excluye el _id.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/9685c1ab-128f-4835-a44f-f6951067966f" /></p>

- Documentos por tipo

Filtra los documentos donde el campo "Tipo" es igual a "Movie" para obtener las películas.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/91f7be91-27dc-44e0-9066-0fe7ce509522" /></p>

## Actualización

### _Código_ 

El comando updateOne() permite modificar campos específicos de un documento usando el operador $set.

- Actualizar país por ID

```python
db.Catalogo.updateOne(
  {ID: "s10001"},
  {$set: {País: "Colombia"}}
)
```
- Actualizar clasificación por título

```python
db.Catalogo.updateOne(
  {"Título": "Ejemplo 2"},
  {$set: {Clasificación: "TV-14"}}
)
```
- Actualizar duración por Tipo

```python
db.Catalogo.updateOne(
  {"Tipo": "Movie", "Duración": "90 min"},
  {$set: {Duración: "100 min"}}
)
```

### _MongoDB_ 

Se realizó la actualización de 3 documentos, modificando el pais, la clasificación y la duración por diferentes filtros. Estas consultas permiten mantener la información del catalogo actualizada.

- Actualizar país por ID

Modificar el país del ID "S10001" a "Colombia"

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/8118305b-253f-4afc-89f2-eaa97769ee7f" /></p>
  
- Actualizar clasificación por título

Se modifica la clasificación de las películas con título "Ejemplo 2" a "TV-14"

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/154bd822-1867-419d-8d68-2c134e0352ad" /></p>
  
- Actualizar duración por Tipo

Cambiar la duración de las películas de tipo "Movie" y duración de "90 min" a una duración de "100 min"

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/da6c238d-4429-4fe6-a389-e38a1c560fcc" /></p>


## Eliminación

### _Código_ 

- deleteOne()

```python
db.Catalogo.deleteOne({
  ID: "s10001",
})
```
- deleteMany()

```python
db.Catalogo.deleteMany({
  Duración: "100 min"
})
```
### _MongoDB_ 

Se realizó la eliminación de documentos por ID y por duración. Estas consultan permiten eliminar registros innecesario o duplicados.

- deleteOne()

Permite eliminar un documentos individual en la colección. Se usa cuando se quiere borrar solo un nuevo registro al catalogo, si hay varios solo se elimina el primer documento. Se elimina el documento con IDE "S10001"

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/50d6cbfe-61a3-4213-af41-00f6fd61890f" /></p>

- deleteMany()

Permite eliminar múltiples documentos en una sola operación  que cumplen con una condición. Es util cuando se quieren borrar varios registros al mismo tiempo. Se eliminan todas las películas con duración de 100 min que fueron un total de 109 películas

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/974a171b-0161-44ac-b252-38c8a7c0f688" /></p>

## 2️⃣ Consultas con filtros y operadores

## Consultas con filtros

### _Código_ 

El comando find() permite consultar documentos dentro de una colección. Puede usarse para buscar documentos completos, aplicar filtros o devolver un campo en específico.

- Películas posteriores a 2015

```python
db.Catalogo.find({
  Año_Lanzamiento: {$gt: 2015}
})
```
- Seleccionar pais

```python
db.Catalogo.find(
  {País: "Colombia"}
)
```
- Seleccionar tipo y clasificación

```python
db.Catalogo.find({
  Tipo: "TV Show", Clasificación: "TV-14"
})
```

### _MongoDB_ 

Se realizaron tres tipos de consultas con el método find() para filtrar las peliculas y series según su año de lanzamiento, pais, tipo y clasificación. Estas consultas permiten conocer los documentos con codiciones especificas dentro del catálogo

- Fitro año de lanzamiento

Busca los documentos en donde el año de lanzamiento se mayor a 2015, utilizando el operador $gt que permite compara valores numéricos.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/20b02c98-2fda-4fb0-a34e-5aac9d91d852" /></p>

- Fitro país

Selecciona todos los documento en donde el pais es exactamente "Colombia"

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/d88131b1-dbbf-4f6d-96be-22c40021c53d" /></p>

- Fitro tipo y clasificación

Filtra los documentos donde el campo "Tipo" es igual a "TV Show" para obtener las series y su clasificación es "TV-14".

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/734b1c6d-2d36-4edc-bc6d-e9d4f23ce47e" /></p>

## Consultas con operadores

### _Código_ 

Para este tipo de consultas se usan operadores como **$in** que busca valores dentro de una lista, **$regex** que busca documentos cuyo campo cumpla con un patrón de texto, **$lte** que selecciona documentos con valores menores o iguales a un límite, **$ne** que selecciona documentos con valores diferentes a un específico, **$or** permite combinar varias condiciones.

- País Estados unidos o India - **operador $or**

```python
db.Catalogo.find({
  $or: [{País: "United States"}, {País: "India"}]
})
```
- Títulos que tengan la palabra "Love" - **operador $regex**

```python
db.Catalogo.find({
  Título: {$regex: /Love/i }
})
```
- Año de lanzamiento menor o igual a 2010 - **operador $lte**

```python
db.Catalogo.find({
  Año_Lanzamiento: {$lte:2010}
})
```

### _MongoDB_ 

Se realizaron tres tipos de consultas utilizando los operadores $or, $regex y $lte, para mostrar documentos que sean de dos paises, que contengan un texto específico y que sean igual o menor que una condición. Estas consultas permiten extraer información especifica del catálogo de acuerdo con diferentes condiciones de búsqueda.

- País Estados unidos o India - **operador $or**

Muestran los documentos que su país es Estados unidos o India, utilizando el operado $or.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/9afe55ca-eca4-4768-8313-aed8cb898698" /><p>

- Títulos que tengan la palabra "Love" - **operador $regex**

Muestra las peliculas que en su titulo tiene la palabra "Love" al final de $regex se i para ignorar si son mayúsculas o mínusculas.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/75ed6e80-983b-4e6f-b25d-b166e095b116" /></p>

- Año de lanzamiento menor o igual a 2010 - **operador $lte**

Muestra los documentos donde el año de lanzamiento es 2010 o el año es menor, utilizando el operados $lte.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/0cdac488-698c-43bc-9438-8da20ab9b13d" /></p>

## 3️⃣Consultas de agregación para calcular estadísticas

El comando aggregate() permite realizar consultas de agregación como contar, sumar, promediar y otras estadisticas sobre los documentos de la colección.

## Contar

### _Código_ 
 
- Contar todas las películas

```python
db.Catalogo.aggregate([
  {$match: {Tipo: "Movie"}},
  {$count: "TotalPelículas"}
])
```
- Contar películas por país

```python
db.Catalogo.aggregate([
  {$group: {_id: "$País", Total: {$sum: 1}}},
  {$sort: {Total: -1}}
])
```
- Contar series con clasificación "TV-14"

```python
db.Catalogo.aggregate([
  {$match: {Tipo: "TV Show", Clasificación: "TV-14"}},
  {$count: "TotalSeriesTVMA"}
])
```

### _MongoDB_ 

Se realizaron tres tipos de consultas para contar documentos de la coleción Catálogo. Estas consultas permiten contar todas las películas, agruparlas por país y contar las series con clasificación TV-14.

- Contar todas las películas

Cuenta el número total de películas en el Catálogo. Se utiliza $match para filtrar los documentos tipo "Movie" y $count para devolver el total de coincidencias. 

**Resultado:** El total de películas en la colección Catálogo es de 6025. Por lo que se puede realizar una comparación con la cantidad de series para tomar desiciones estrategicas.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/61d37cce-d2f3-4a09-806d-091261bf1804" /></p>

- Contar películas por país

Agrupa los documento por país y utiliza $sum: 1 para contar cuántas peliculas hay en cada uno. Utiliza "$" delante de País para indicar que es el valor tomado de cada documento.

**Resultado:** Los 2 paises con más películas son Estados Unidos con 2784 y seguido de India con 968. Por lo que en el catálogo de Netflix la mayoría de películas son de Estados Unidos.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/ce4465dd-84c9-4019-b967-a1df82d46c44" /></p>

- Contar series con clasificación "TV-14"

Cuenta los documentos de tipo "TV Show" y con una clasificación "TV-14".

**Resultado:** El total de películas con clasificación TV-14 son 733. Lo que reprensenta la cantidad de contenido que esta orientado a adolescentes en el catálogo.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/e092cf04-94d0-4123-85f9-7b48820a553a" /></p>

## Sumar

### _Código_ 

- Sumar el total de la duración de las películas

```python
db.Catalogo.aggregate([
  {$match: {Tipo: "Movie"}},
  {$group: {_id: null, TotalDuración: {$sum: "$Duración_min"}}}
])
```

- Suma de la duración de las películas por país

```python
db.Catalogo.aggregate([
  {$match: {Tipo: "Movie"}},
  {$group: {_id: "$País", TotalDuración: {$sum: "$Duración_min"}}},
  {$sort: {TotalDuración: -1}}
])
```
- Suma de la duración de las películas por clasificación TV-14

```python
db.Catalogo.aggregate([
  {$match: {Clasificación: "TV-14"}},
  {$group: {_id: null, TotalDuración: {$sum: "$Duración_min"}}}
])
```
### _MongoDB_ 

Se realizaron tres tipos de consultas para sumar la duración total de las películas en general, por país y por clasificación.Estas consultas permiten analizar la duración acumulada de los contenidos del catálogo y detectar patrones según país o clasificación.

- Sumar el total de la duración de las película

Suma los minutos de todas las películas del catálogo par determinar la duración total de las películas.

**Resultado:** La duración total es de 599637 minutos. Esto permite conocer la cantidad total de contenido en minutos que ofrece el catálog.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/437f9186-67df-4291-aa24-5727536d288e" /></p>

- Suma de la duración de las películas por país

Suma los minutos de las películas de acuerdo con el país de origen.

**Resultado:** Los países con mayor duración duración son Estados Unidos e India, dado que son los paises que tienen más cantidad de películas en el catálogo.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/2b1b257d-a58a-46b3-84fb-d72a27dd3482" /></p>

- Suma de la duración de las películas por clasificación TV-14

Suma los minuto de las películas clasificadas en TV-14

**Resultado:** La duración total de las películas clasificadas en TV-14 es de 155305 minutos.Permite entender la proporción de este contenido para este público dentro del catálogo.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/14aeac76-c7a5-4137-a224-a229cc670f4c" /></p>

## Promedio

### _Código_ 

- Promedio de duración de todas las películas

```python
db.Catalogo.aggregate([
  {$match: {Tipo: "Movie"}},
  {$group: {_id: null, DuraciónPromedio: {$avg: "$Duración_min"}}}
])
```
- Promedio de duración por género

```python
db.Catalogo.aggregate([
  {$group: {_id: "$Género", DuraciónPromedio: {$avg: "$Duración_min"}}},
  {$sort: {DuraciónPromedio: -1}}
])
```
- Promedio de duración de películas con clasificación "TV-14"

```python
db.Catalogo.aggregate([
  {$match: {Clasificación: "TV-14"}},
  {$group: {_id: null, DuraciónPromedio:  {$avg: "$Duración_min"}}}
])
```
### _MongoDB_ 

Se realizaron tres tipos de consultas para obtener el promedio de la duración total de las películas en general, por génro y por clasificación.Estas consultas permiten identifcar los géneros con películas más largas y evaluar la duración según la clasificación.

- Promedio de duración de todas las películas

Tiempo promedo de todas las películas ofrecidas en el catálogo de Netflix.

**Resultado:** La duración promedio de todas las películas es de 99.52 minutos. Proporciona el tiempo de visualización típico de una película en el catálogo.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/0ac6ca5b-5a46-4a1c-a9f3-1e3839708f43" /></p>

- Promedio de duración por género

Determina la duración promedio de las películas que se encuentran en los diferentes géneros

**Resultado:** Los géneros con mayor promedio en la duración de las películas es "Classic Movies, Music & Musicals" con un promedio de 173 minutos y "Actión & Aventure, Cult Movies, Drama". Por lo que ayuda a entender la variación del contenido según el tipo de contenido.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/74ba636c-d2f7-4125-9037-23491f2ee46e" /></p>

- Promedio de duración de películas con clasificación "TV-14"

Muestra la duración promedio de las películas clasificadas en "TV-14"

**Resultado:** La duración promedio las películas clasificadas en "TV-14" es de 110.45 minutos. Esto permite analizar la duración típica de las películas para este grupo de edad.

<p align="center"><img width="654" height="336" alt="image" src="https://github.com/user-attachments/assets/5023ffce-9073-4b75-94d0-f988a1e96771" /></p>
