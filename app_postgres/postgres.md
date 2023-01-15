- [todos-los-grant-en-postgres](#todos-los-grant-en-postgres)
- [creacion-de-un-nuevo-role-y-asignacion-a-un-grupo](#creacion-de-un-nuevo-role-y-asignacion-a-un-grupo)

# POSTGRES

## todos-los-grant-en-postgres

El comando GRANT en PostgreSQL se utiliza para asignar permisos a un rol en una tabla, vista, esquema, secuencia, función o procedimiento almacenado. Los permisos que se pueden asignar incluyen:

    SELECT: permite seleccionar datos de una tabla o vista.
    INSERT: permite insertar datos en una tabla.
    UPDATE: permite actualizar datos en una tabla.
    DELETE: permite eliminar datos de una tabla.
    TRUNCATE: permite vaciar una tabla.
    REFERENCES: permite crear una restricción de clave externa en una tabla.
    TRIGGER: permite crear o ejecutar un disparador en una tabla.
    EXECUTE: permite ejecutar un procedimiento almacenado o función.
    USAGE: permite utilizar un esquema o secuencia.
    CREATE: permite crear objetos en un esquema.
    TEMPORARY: permite crear y acceder a tablas temporales.
    TEMP: es un sinónimo de TEMPORARY.
    ALL: permite todos los permisos anteriores (SELECT, INSERT, UPDATE, DELETE, TRUNCATE, REFERENCES, TRIGGER, EXECUTE, USAGE, CREATE, TEMPORARY).

Además, existen permisos para administrar roles y asignarlos como:

    CREATE ROLE: permite crear roles.
    INHERIT: permite que un rol herede los permisos de otro rol.
    LOGIN: permite iniciar sesión en el servidor.
    CREATEDB: permite crear bases de datos.
    CREATEROLE: permite crear roles.

Es importante mencionar que el usuario que esta ejecutando el comando GRANT debe tener los permisos necesarios para asignar los permisos deseados.

## creacion-de-un-nuevo-role-y-asignacion-a-un-grupo

```sql
CREATE ROLE mi_grupo NOLOGIN;
```

```sql
GRANT mi_usuario TO mi_grupo;
```

```sql
GRANT SELECT ON ALL TABLES IN SCHEMA public TO mi_grupo;
```