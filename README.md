# proyectoPostgres
Proyecto final de curso en base de datos Postgres Avanzado

## 👧 Authors

- [@gabriellagii](https://www.github.com/gabriellagii) 🌻

## 📝 Obtención de datos

![Entidad-Relacion](imagenes/datos.PNG)

- Se crea la base de datos `monitoreoGps` y el esquema `gps`:


## 💻 Configuración del entorno SQL

## ✏️ Diseño de la base de datos

- 1M (un dispositivo a muchas ubicaciones)
  
![Entidad-Relacion](imagenes/entidad_relacion.PNG)

## 👨 Gestión de usuarios

`CREATE USER superUsuario WITH PASSWORD '123456' 

ALTER USER superUsuario WITH 
  LOGIN
  SUPERUSER
  INHERIT
  CREATEDB
  CREATEROLE
  REPLICATION
  BYPASSRLS;`

## 🔐 Creando una copia de seguridad

## 📈 Optimizando consultas

## Preparando un proceso de réplica y alta disponibilidad

## Preparando el monitoreo

## Migración de datos
