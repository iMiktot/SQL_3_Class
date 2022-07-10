## Новая схема БД SQL 

![](https://github.com/iMiktot/SQL_3_Class/blob/main/1.png)


## Команды SQL для создания таблиц.

```sql
CREATE TABLE IF NOT EXISTS Исполнители (
	id_artist SERIAL PRIMARY key,
	Имя VARCHAR(50) NOT NULL unique,
);
CREATE TABLE IF NOT EXISTS Альбомы (
	id_album SERIAL PRIMARY key,
	Название_альбома VARCHAR(100)  NOT NULL, 
	Год_выпуска INTEGER check(Год_выпуска >= 1993),
	id_artist INTEGER REFERENCES Исполнители(id_artist) NOT NULL
);

CREATE TABLE IF NOT EXISTS Треки (
	id_track SERIAL PRIMARY key,
	Название_трека VARCHAR(100)  NOT NULL,
	Длительность time NOT NULL,
	id_album INTEGER REFERENCES Альбомы(id_album) NOT NULL
);
CREATE TABLE IF NOT EXISTS Жанры (
	id_genre SERIAL PRIMARY key,
	Название_жанра VARCHAR(100)  NOT NULL UNIQUE
);
```
##  Команды SQL для создания дополнительных таблиц.

```sql

CREATE TABLE IF NOT EXISTS Жанры_Исполнители (
	id_genre INTEGER REFERENCES Жанры(id_genre) NOT null,
	id_artist INTEGER REFERENCES Исполнители(id_artist) NOT null
);	

CREATE TABLE IF NOT EXISTS Альбомы_Исполнители (
	id_album INTEGER REFERENCES Альбомы(id_album) NOT null,
	id_artist INTEGER REFERENCES Исполнители(id_artist) NOT null
);	

CREATE TABLE IF NOT EXISTS Сборники (
	id_collection SERIAL PRIMARY key,
	Название_сборника VARCHAR(100)  NOT NULL, 
	Год_выпуска INTEGER check(Год_выпуска >= 1993),
);

CREATE TABLE IF NOT EXISTS Сборники_Треки (
	id_collection INTEGER REFERENCES Сборники(id_collection) NOT null,
	id_track INTEGER REFERENCES Треки(id_track) NOT null
);	
```