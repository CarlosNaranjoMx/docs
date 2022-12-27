- 1:00 `mkdir category`
`mkdir gateway`
`cd category`
`jhipster`
`microservice application`

- 2:45 `cd gateway`
`microservice gateway`

- 6:34 creacion de las entidades y de los microservicios en el jdl
- creacion del dto en `jhipster`
- indicar que cada servicio tenga un serviceImpl
documentar las cosas junto con el tiempo en el que las hice

- 6:53 creacion del dto con map struct:
`dto * with mapstruct`
- 7:05 `service all with serviceImpl`
- 7:38 `microservice Category with category`
- 8:26 salvando en el proyecto

% desglozar todos los directorios de jhipster
% hacer la otra actividad que me dejaron
% dependiendo del json, crear una ventana que te diga que datos agregar
% con actualizacion inmediata en el servidor
% todos los elementos en subdirectorios
% un atributo validador del tipo de elemento cuando es creado el archivo
% forma en que tu modelas tu base de datos

- 9:18 `jhipster import-jdl <archivo>`

% agregar <proyecto-name> a los directorios de jhipster

% elegir que proyecto de git hacer push
% crear mi propio script de shell

- 9:18 *pendiente*

- 14:11 `mkdir docker-compose`
- 14:31 `docker-compose`
- 14:35 eleccion con el modo de `gateway`
- 14:40 include `category` y `gateway`
- 15:26 `docker image ls -a`
- 15:42 `./mvnw verify jib:dockerBuild`
- 17:26 mismo comando pero para gateway `./mvnw verify jib:dockerBuild`
- 19:34 `docker image ls -a`
- 19:50 extension de docker en vscode
- 20:10 `cd docker-compose;ls -l`
- 20:17 `docker-compose up -d`

# - [jhipster developer mode]()