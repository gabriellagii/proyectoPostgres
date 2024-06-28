# proyectoPostgres
Se requiere monitorear y visualizar las ubicaciones de objetivos (dispositivos gps).

## 👧 Authors

- [@gabriellagii](https://www.github.com/gabriellagii) 🌻

## 📝 Obtención de datos

![Entidad-Relacion](imagenes/datos.PNG)

- Se crea la base de datos `monitoreoGps` y el esquema `gps`:


## 💻 Configuración del entorno SQL
![postgres](imagenes/postgres.PNG)

![postgres](imagenes/postgres1.PNG)

## ✏️ Diseño de la base de datos

- 1M (un dispositivo a muchas ubicaciones)
  
![Entidad-Relacion](imagenes/entidad_relacion.PNG)

```bash
-- This script was generated by a beta version of the ERD tool in pgAdmin 4.
-- Please log an issue at https://redmine.postgresql.org/projects/pgadmin4/issues/new if you find any bugs, including reproduction steps.
BEGIN;
CREATE TABLE IF NOT EXISTS gps.tbl_bracelet
(
    id_bracelet integer NOT NULL,
    imei character varying NOT NULL,
    open_close boolean NOT NULL,
    status integer NOT NULL,
    description character varying(50),
    phone_num character varying,
    PRIMARY KEY (id_bracelet)
);

CREATE TABLE IF NOT EXISTS gps.tbl_ubicacion
(
    id_ubicacion integer NOT NULL,
    id_bracelet integer,
    fecha_ubicacion date,
    hora_ubicacion time without time zone,
    latitud double precision,
    longitu double precision,
    estado character varying(80),
    municipio character varying(400),
    PRIMARY KEY (id_ubicacion)
);
ALTER TABLE gps.tbl_ubicacion
    ADD FOREIGN KEY (id_bracelet)
    REFERENCES gps.tbl_bracelet (id_bracelet)
    NOT VALID;
END;
````

## 👨 Gestión de usuarios
```bash
CREATE ROLE superadmon LOGIN PASSWORD 'root15' SUPERUSER;

CREATE ROLE createdb LOGIN PASSWORD 'rootdb' CREATEDB;//--ROL PARA SOLO CREAR BASE DE DATOS

CREATE ROLE usersimple LOGIN PASSWORD 'user123';//--ROL USUARIO SIMPLE

ALTER ROLE createdb CREATEROLE; //--ROL DE CRAEAR ROLES

CREATE DATABASE prueba;

SET ROL usersimple;

GRANT createdb TO usersimple;

\du //--- es para ver los roles creados
```
![lista_roles](imagenes/lista_roles.PNG)

```bash
 CREATE USER superUsuario WITH PASSWORD '123456' 
  ALTER USER superUsuario WITH 
    LOGIN
    SUPERUSER
    INHERIT
    CREATEDB
    CREATEROLE
    REPLICATION
    BYPASSRLS;
```

![nuevo_super](imagenes/nuevo_super.PNG)

## 🔐 Creando una copia de seguridad

![respaldo](imagenes/resoaldo.PNG)

## 📈 Optimizando consultas

` explain analyze select * from gps.tbl_ubicacion; `

![antes](imagenes/analyze.jpeg)

![despues](imagenes/despues.jpeg)

```bash
CREATE INDEX ON gps.tbl_ubicacion(id_ubicacion);
```
![index](imagenes/index.PNG)

## Preparando un proceso de réplica y alta disponibilidad

## Preparando el monitoreo

## Migración de datos
