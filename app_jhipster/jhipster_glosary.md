# Jhipster

- [Diseño de la aplicación](#diseño-de-la-aplicación)
- [Framework](#framework)
- [Autenticacion](#autenticacion)
- [Okta](#okta)
- [Keycloak](#keycloak)
- [Datos en memoria](#datos-en-memoria)
- [Docker](#docker)
- [Motores de busqueda de base de datos](#motores-de-busqueda-de-base-de-datos)
- [dto](#dto)
- [jpa](#jpa)
- [directorios](#directorios)
- [transpilador](#transpilador)
- [programacion-reactiva](#programacion-reactiva)
- [string-filter](#string-filter)

## string-filter
'StringFilter' se puede usar para que se pueda 'limpiar' o que se pueda cambiar
los 'caracteres' de un 'string' de texto se pueda usar dentro de una 'class' de
una application web.

Para que solo admita los caracteres validos dentro de una aplicación web.

Este se puede usar como se puede usar una 'class' para que se pueda tener
'limpiado' el 'string' de texto.

## programacion-reactiva

'Reactive programming' es un tipo de programación que se usa para que se pueda
hacer una application web que se pueda usar en tiempo real, este tipo de
programación se puede usar junto con un 'frontend' y un 'back-end' que se pueda
usar en la 'web-app'.

Una example de 'Reactive programming' se puede ver en 'Angular' se puede usar
para que se pueda hacer una application web con 'TypeScript' para que se pueda
hacer una application web que tenga una serie de 'events' que tengan una orden
de que se puedan usar dentro de una application web.

## transpilador
Un transpilador es algo que se puede usar para que se pueda pasar de una
programacion programada en un lenguaje a otra que se pueda usar en otro
lenguaje.

Por ejemplo, si una persona quiere usar 'TypeScript' para programar una
application, pues se puede usar para que se pueda usar el código como que está
programado usando 'JavaScript' en 'JavaScript'.

## directorios
- `/home/psycho/web/linuxmint_jhipster/src/main/webapp/app/app.component.ts`
- web:
  `/home/psycho/web/linuxmint_jhipster/src/main/java/mx/conacyt/crip/ejemplos/web/rest/VetsResource.java`
- domain:
  `/home/psycho/web/linuxmint_jhipster/src/main/java/mx/conacyt/crip/ejemplos/domain/Vets.java`
- config:
  `/home/psycho/web/linuxmint_jhipster/src/main/java/mx/conacyt/crip/ejemplos/config/CacheConfiguration.java`
- `/home/psycho/web/linuxmint_jhipster/.jhipster/Vets.json`

## jpa
JPA es la abreviatura de 'Java Persistence API' que se puede usar en 'Java' y se
puede usar con 'Spring Boot' para se pueda hacer una base de datos en 'SQL' y
poder usarlo dentro de una application web para hacer una base de datos dentro
del 'spring boot'.

## dto
'dto' se puede entender como 'datasource to object' y se puede usar en 'angular'
para poder hacer que la 'application web' se pueda conectar con lo que son las
'datasets' o los 'datos que se puedan hacer en una application web.

### conexion con los data sets


## Diseño de la aplicación

Con la opción de 'monolith' se puede usar JHipster para diseñar una única
application web que en su designación pueda tener una única base de datos.

El 'gateway' se usa para conectar una application web con alguna otra
application web, y se usa para poder hacer un sistema que tenga más de un
application web, pero que todo funcione como una única `application web`.

Mientras que con el 'microservice' podes hacer más de una application web y
tener más de una base de datos pero que funcione como un `servicio web`.


## Framework

- spring

framework o una librería de código que se usa para hacer aplicaciones web en
Java

- jpa 

JPA es un framework o una librería de código que se usa para poder hacer una
connection a una base de dados como puede ser una base de datos MySql o una base
de datos SQL Server.

JPA se usa para hacer una coneción a una base de datos y para cargar datos a la
application web o al servicio web que va a estar usando JPA.

## Autenticacion

- jwt, oauth2

JWT se puede hacer tokens de acceso para que los usuarios que tienen acceso a
alguna app web se pueden autenticar y poder usar esa app web.

Y con OAuth2 se puede hacer que los usuario tengan una seguridad más avanzada,
pudiendo usar tokens de acceso que se pueden crear en apps web, y para poder
hacer eso se usa el sistema de seguridad OAuth2, y con el sistema OAuth2 se
pueden crear applications web que puedan tener tokens de acceso.


## Okta

Okta es un software que se usa para verificar la identidad de todos los usuarios
que están haciendo login en un proyecto, y se usa para poder enviar un token de
verificación para que los usuarios que están haciendo login en una aplicación
web puedan verificarse sus identidades.

## Keycloak

Keycloak es una application web que se puede usar como Single-Sign-On (SSO),
pero se puede usar también para hacer un directorio de usuarios para todas las
apps web de una empresa, y para poder hacer un control de acceso a esas app web.

- sso

Single-Sign-On es un sistema que se usa para simplificar el acceso a varias apps
web a la vez, solo se tiene que hacer login una sola vez y la página web de ese
sistema te va a abrir todas las apps web que esten conectadas a ese sistema, y
para poder hacerlo se usan tokens de acceso.


## Datos en memoria

- Que son ehcache, caffeine, hazelcast, infinispan, memcached, redis, cuales son
sus diferencias

    Ehcache, Caffeine, Hazelcast, Infinispan, MemCached, Redis, son librerías o
    Framework que se usan para guardar datos en la memoria y trabajar con las
    data guardadas.

    Las diferencia entre ellas son:

    - El consumo de memoria por object.

    - La performance al insertar o borrar un object.

    - La performance por key/value.

    - La facilidad de uso.

## Docker
Docker es un comando o una orden que se usa para poder empezar o ayudar a subir
a las coontenedores una application web.

Mientras que 'docker-compose' es un 'command' o una orden que se usa para poder
empezar o hacer correr los servicios web que están dentro de un texto 'yml', así
se puede subir la application web a una computadora.

## Motores de busqueda de base de datos    

- que son elasticsearch, apache kafka y openapi-generator cuales son sus
  diferencias

    Elasticsearch es un motor de búsqueda para bases de datos, mientras que
    Apache Kafka es un motor de busqueda pero usado para mensajeria.

    Elasticsearch permite buscar en bases de datos al mismo tiempo que se pueden
    buscar en bases de datos varias, es decir, al mismo tiempo se pueden hacer
    buscar en bases de datos y encontrar los datos en cualquier momento.

    Apache Kafka es un motor que se usa para encontrar datos y mensajes pero en
    mensajeria, así que se usan diferentes sistemas para ayudar a encontrar data
    en mensajeria.

- que son cypress,gatling y cucumber cuales son sus diferencias

    - Cypress es una librería web para hacer pruebas de un website desde el
      punto de vista de un usuario.

    - EnGatling se usa como un framework web para encontrar fallas en código y
      apps web.

    - Cucumber es un framework web para automatizar las pruebas que se pueden
      hacer a un sistema web.