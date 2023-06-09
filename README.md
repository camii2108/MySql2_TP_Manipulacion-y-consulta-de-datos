# TP_Manipulacion-y-consulta-de-datos
/*Micro desafío - Paso 1: Insert, Update, Delete,*/
/*1. Insertar en la tabla genres un nuevo género con los siguientes datos:
○ name: Investigación
○ ranking: 13
○ active: 1*/
/*Me traigo la tabla genres*/
select * from movies_db.genres;
/*Inserto dato*/
insert into genres values (
13, now(), null , "Investigación", 13,1
);
/*Prueba*/
select name,id from movies_db.genres
limit 13
offset 9;
/*2. Actualizar el nuevo registro “name: Investigación” por “Investigación Científica”*/
update genres 
set name = 'Investigación Científica' 
where id = 13;
/*3. Eliminar el registro cuyo name es: “Investigación Científica”. Recordemos verificar
cuál es el id de dicho registro.*/
delete from movies_db.genres where id = 13;
/*Haciendo uso del Select, debemos afrontar las siguientes consultas:
4. Mostrar todos los registros de la tabla “movies”.*/
select * from movies_db.movies;
/*5. Mostrar el nombre, apellido y rating de todos los actores.*/
select first_name, last_name, rating from actors;
/*6. Mostrar el título de todas las series. 
* Tomar en cuenta que tanto el nombre de la
tabla como el campo estén en español.*/
select title as titulo from series; 
/*Micro desafío - Paso 2:
Utilizando el Where y Order by, ejecutemos las siguientes consultas (ten en cuenta el uso
de los operadores lógicos y relacionales).*/
/*1. Mostrar el nombre y apellido de los actores cuyo rating sea mayor a 7.5.*/
select first_name, last_name from actors
where rating > 7.5;
/*2. Mostrar el título de las películas, el rating y los premios de las películas con un rating
mayor a 7.5 y con más de dos premios.*/
select title as titulo,rating, awards as premios from movies
where rating > 7.5
and awards >= 2;
/*3. Mostrar el título de las películas y el rating ordenadas por rating en forma
ascendente.*/
select title, rating from movies
order by rating asc;
/*Micro desafío - Paso 3:
* Vamos muy bien, no nos desanimemos ni por un minuto. Ahora, para la realización de las
consultas debemos valernos del Limit y Offset.*/
/*1. Mostrar los títulos de las primeras tres películas en la base de datos.*/
select title from movies
limit 3;
/*2. Mostrar el top 5 de las películas con mayor rating.*/
select title, rating from movies
order by rating desc 
limit 5;
/*3. Mostrar las top 5 a 10 de las películas con mayor rating. 
* Me trae las oeliculas con mayor rating desde las 5 a la 10. y recuera esos datos desde la 
* quinta columna y tiene un limite de 10 peliculas*/
select title, rating from movies 
order by rating desc 
limit 10
offset 5;
/*4. Listar los primeros 10 actores (sería la página 1).
a. Luego, usar offset para traer la página 3. 0 a 10 = priemra pagina, 10 a 20 = segunda pagina, 20 a 30 = tercera pagina*/
select * from actors
limit 10
offset 20;
/*Micro desafío - Paso 4:*/
/*1. Mostrar el título y rating de todas las películas cuyo título sea Harry Potter.*/
select title as titulo, rating from movies 
where title like '%Harry Potter%';
/*2. Mostrar a todos los actores cuyos nombres empiecen con Sam.*/
select last_name as nombre from actors 
where last_name like 'Sam%'
/*3. Mostrar el título de las películas que salieron entre el 2004 y 2008.*/
select title, release_date from movies
where release_date between "2004-01-01" and "2008-12-31";

