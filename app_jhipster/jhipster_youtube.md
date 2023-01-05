- &t=1m00s `mkdir category`
`mkdir gateway`
`cd category`
`jhipster`
`microservice application`

- &t=2m45s `cd gateway`
`microservice gateway`

- &t=6m34s creacion de las entidades y de los microservicios en el jdl
- creacion del dto en `jhipster`
- indicar que cada servicio tenga un serviceImpl
documentar las cosas junto con el tiempo en el que las hice

- &t=6m53s creacion del dto con map struct:
`dto * with mapstruct`
- &t=7m05s `service all with serviceImpl`
- &t=7m38s `microservice Category with category`
- &t=8m26s salvando en el proyecto

% desglozar todos los directorios de jhipster
% hacer la otra actividad que me dejaron
% dependiendo del json, crear una ventana que te diga que datos agregar
% con actualizacion inmediata en el servidor
% todos los elementos en subdirectorios
% un atributo validador del tipo de elemento cuando es creado el archivo
% forma en que tu modelas tu base de datos

- &t=9m18s `jhipster import-jdl <archivo>`

% agregar <proyecto-name> a los directorios de jhipster

% elegir que proyecto de git hacer push
% crear mi propio script de shell

- &t=9m18s *pendiente*

- &t=14m11s `mkdir docker-compose`
- &t=14m31s `docker-compose`
- &t=14m35s eleccion con el modo de `gateway`
- &t=14m40s include `category` y `gateway`
- &t=15m26s `docker image ls -a`
- &t=15m42s `./mvnw verify jib:dockerBuild`
- &t=17m26s mismo comando pero para gateway `./mvnw verify jib:dockerBuild`
- &t=19m34s `docker image ls -a`
- &t=19m50s extension de docker en vscode
- &t=20m10s `cd docker-compose;ls -l`
- &t=20m17s `docker-compose up -d`

# [jhipster developer mode](https://www.youtube.com/watch?v=SVUB3Yhv3sQ)

- &t=1m22s creación de la aplicacion de jhipster
- &t=4m19s ejecucion de la aplicacion

# [jhipster database](https://www.youtube.com/watch?v=dTzGQNOKWug)

- &t=0m54s jhipster lite
- &t=26m37s ejecutando en intelliidea

## [youtube jhipster postgres](https://www.youtube.com/watch?v=vK3_bntpOQ0)

- &t=t0m25s `docker image ls -a`
- &t=0m42s `docker pull dpage/pgadmin4`
- &t=2m38s `docker run -p 80:80 -e PGADMIN_DEFAULT_EMAIL=user@domain.com -e PGADMIN_DEFAULT_PASSWORD=hola123., -d dpage/pgadmin4`
- &t=3m46s docker vscode
- &t=4m02s mostrar pgadmin4
- &t=4m44s `docker pull postgres`
- &t=5m31s `docker image ls -a`
- &t=5m54s `docker run --name pg-docker -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=hola123., -e POSTGRES_DB=postgres -d -p 5432:5432 postgres`
- &t=7m49s crear un server con pgadmin4
- &t=8m16s captura de datos
- &t=9m27s agregado de informacion

## [youtube boostasoft](https://www.youtube.com/watch?v=0moy9oGcohs)
- &t=0m26s ./mvnw clean
- &t=2m30s abirendo <aplication-dev.yml>
- &t=2m31s modificando el `datasource` del `yml`
- &t=2m52s `docker-compose -f <archivo>.yml up -d `
- &t=3m01s ingresando a postgres


## [JHipster - Build and Deploy application by using Docker](https://www.youtube.com/watch?v=6f87fg_MsLw)

- &t=5m40s `./mvnw -Pprod verify jib:dockerBuild`
- &t=10m23s `docker-compose -f src/main/docker/app.yml up -d`

## [Instalación y configuración de JHipster en Docker](https://www.youtube.com/watch?v=4MQyWwlhui4)

- &t=0m20s `docker exec -it jhipster sh`