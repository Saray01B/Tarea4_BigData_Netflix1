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

<img width="962" height="494" alt="image" src="https://github.com/user-attachments/assets/f70c32b1-5687-4275-8e3f-5e4e603fd81b" />

<img width="962" height="494" alt="image" src="https://github.com/user-attachments/assets/487adeba-c1c2-4b91-a133-a31034ad6bfd" />

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

<img width="962" height="494" alt="image" src="https://github.com/user-attachments/assets/5b6667f2-2e0e-4727-87f0-00eb95f64513" />

<img width="962" height="494" alt="image" src="https://github.com/user-attachments/assets/91f7be91-27dc-44e0-9066-0fe7ce509522" />
