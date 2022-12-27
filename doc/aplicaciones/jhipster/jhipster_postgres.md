## [youtube jhipster postgres](https://www.youtube.com/watch?v=vK3_bntpOQ0)

- 0:25 `docker image ls -a`
- 0:42 `docker pull dpage/pgadmin4`
- 2:38 `docker run -p 80:80 -e PGADMIN_DEFAULT_EMAIL=user@domain.com -e PGADMIN_DEFAULT_PASSWORD=hola123., -d dpage/pgadmin4`
- 3:46 docker vscode
- 4:02 mostrar pgadmin4
- 4:44 `docker pull postgres`
- 5:31 `docker image ls -a`
- 5:54 `docker run --name pg-docker -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=hola123., -e POSTGRES_DB=postgres -d -p 5432:5432 postgres`
- 7:49 crear un server con pgadmin4
- 8:16 captura de datos
- 9:27 agregado de informacion

## [youtube boostasoft](https://www.youtube.com/watch?v=0moy9oGcohs)
- 0:26 ./mvnw clean
- 2:30 abirendo <aplication-dev.yml>
- 2:31 modificando el `datasource` del `yml`
- 2:52 `docker-compose -f <archivo>.yml up -d `
- 3:01 ingresando a postgres