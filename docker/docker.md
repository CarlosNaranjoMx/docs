`docker run -p 80:80 -e PGADMIN_DEFAULT_EMAIL=user@domain.com -e PGADMIN_DEFAULT_PASSWORD=hola123., -d dpage/pgadmin4`

`docker run --name pg-docker -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=hola123., -e POSTGRES_DB=postgres -d -p 5432:5432 postgres`

`docker run --name <nombre> jhipster/jhipster -d`
`docker exec -it <nombre> sh`

`docker rm 5d1b067fea4b`

` docker run --name keycloak -e KEYCLOAK_USER=admin -e KEYCLOAK_PASSWORD=admin -p 11111:11111 jboss/keycloak -Djboss.http.port=11111`

## puertos de servicios
- [keycloak](http://localhost:11111)
