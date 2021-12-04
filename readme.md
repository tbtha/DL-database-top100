````sql

--1. crear base de datos
CREATE DATABASE peliculas
    WITH 
    OWNER = postgres
    ENCODING = 'UTF8'
    CONNECTION LIMIT = -1;

--2. cargar ambos archivos a su tabla 

create table peliculas(
	id_peliculas int,
	pelicula varchar(100),
	anio_estreno int,
	director varchar(100),
	primary key(id_peliculas) 
);

create table reparto (
	id_peliculas int,
	actores varchar(100),
	id_reparto serial,
	primary key (id_reparto),
	foreign key (id_peliculas) references peliculas(id_peliculas)
);


--3. obtener id de la pelicula titanic 
select id_peliculas from peliculas
where pelicula = 'Titanic';

--4. listas a todos los actores que aparecen en titanic
select actores from reparto 
where id_peliculas = 2;

--5. consultar en cuantas peliculas participa harrison ford
select 
count (actores) as "pelis Harrison"
from reparto
where actores = 'Harrison Ford'

--6.peliculas entre 1990 y 1999
select 
pelicula from peliculas
where anio_estreno between '1990' and '1999'
order by pelicula;

--7.titulos con su longitud
select pelicula,
length (pelicula) as longitud_titulo
from peliculas;

--8.longitud mas grande entre todos los titulos 
select max(length (pelicula))
from peliculas;








```