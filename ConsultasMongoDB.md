# Código de consultas para el Dataset peliculas y series de Netflix

## 1️⃣ Consultas básicas

## Inserción

### _Código_ 

InsertOne() permite insentar un documentos individual en la colección. Se usa cuando se quiere agregar solo un nuevo registro al catalogo.

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
InsertMany() permite insertar múltiples documentos en una sola operación. Es util cuando se quiren agregar varios registros al mismo tiempo.

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

<p align="center"><img width="818" height="420" alt="image" src="https://github.com/user-attachments/assets/f70c32b1-5687-4275-8e3f-5e4e603fd81b" /></p>

<p align="center"><img width="818" height="420" alt="image" src="https://github.com/user-attachments/assets/487adeba-c1c2-4b91-a133-a31034ad6bfd" /></p>

## Selección

### _Código_ 

El comando find() permite consultar documentos dentro de una colección. Puede usarse para buscar documentos completos, aplicar filtros o devolver un campo en específico.

- Seleccionar un documento por ID

Busca un documento en donde el campo "ID" coincidad exactamente con "s10001". Este tipo de consulta se usa para un registro específico.

```python
db.Catalogo.find({
  ID: "s10001"
})
```
- Seleccionar solo títulos y años

Selecciona todos los documento con {} y muestra el título, año de lanzamiento y excluye el _id.

```python
db.Catalogo.find(
  {}, {Título:1, Año_Lanzamiento: 1, _id: 0}
)
```
- Seleccionar películas

Filtra los documentos donde el campo "Tipo" es igual a "Movie" para obtener las películas.

```python
db.Catalogo.find({
  Tipo: "Movie"
})
```

### _MongoDB_ 

Se realizaron tres tipos de consultas con el método find(), selección por ID, con proyección y por tipo de contenido. Estas consultas permiten explorar la colección "Catalogo".

<p align="center"><img width="818" height="420" alt="image" src="https://github.com/user-attachments/assets/5b6667f2-2e0e-4727-87f0-00eb95f64513" /></p>

<p align="center"><img width="818" height="420" alt="image" src="https://github.com/user-attachments/assets/91f7be91-27dc-44e0-9066-0fe7ce509522" /></p>

## Actualización

### _Código_ 

El comando updateOne() permite modificar campos específicos de un documento usando el operador $set.

- Actuarlizar país por ID

Modificar el país del ID "S10001" a "Colombia"

```python
db.Catalogo.updateOne(
  {ID: "s10001"},
  {$set: {País: "Colombia"}}
)
```
- Actualizar clasificación por título

Se modifica la clasificación de las películas con título "Ejemplo 2"

```python
db.Catalogo.updateOne(
  {"Título": "Ejemplo 2"},
  {$set: {Clasificación: "TV-14"}}
)
```
- Actualizar duración por Tipo

Cambiar la duración de las películas de tipo "Movie" y duración "1 temporada"

```python
db.Catalogo.updateOne(
  {"Tipo": "TV Show", "Duración": "1 temporada"},
  {$set: {Duración: "100 min"}}
)
```

### _MongoDB_ 

Se realizó la actualización de 3 documentos, modificando el pais, la clasificación y la duración por diferentes filtros. Estas consultas permiten mantener la información del catalogo actualizada.

<p align="center"><img width="818" height="420" alt="image" src="https://github.com/user-attachments/assets/c5b9689f-986a-457a-887e-5c0f4c9f955e" /></p>

## Eliminación

### _Código_ 

deleteOne() permite eliminar un documentos individual en la colección. Se usa cuando se quiere borrar solo un nuevo registro al catalogo, si hay varios solo se elimina el primer documento. Se elimina el documento con IDE "S10001"

```python
db.Catalogo.deleteOne({
  ID: "s10001",
})
```
deleteMany() permite eliminar múltiples documentos en una sola operación  que cumplen con una condición. Es util cuando se quieren borrar varios registros al mismo tiempo. Se eliminan todas las películas con duración de 100 min.

```python
db.Catalogo.deleteMany({
  Duración: "100 min"
})
```
### _MongoDB_ 

Se realizó la eliminación de documentos por ID y por duración. Estas consultan permiten eliminar registros innecesario o duplicados. Se eliminó el registro con ID "s1001" y 109 películas con duración de 100 minutos.

<p align="center"><img width="818" height="420" alt="image" src="https://github.com/user-attachments/assets/6eb9f194-dd05-40c4-b364-197d91a54dd8" /></p>
