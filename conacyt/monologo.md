## beans
- [configuracion-jdl](#configuracion-jdl)

- `archivo configuracion` revisando el link de configuracion de los beans
[link](https://docs.spring.io/spring-framework/docs/3.2.x/spring-framework-reference/html/beans.html)
notamos que se crea un xml indicando que tiene una configuracion
de spring con beans, se usan daos, data access object
como conexión a la `base de datos`
- `capas de xml`
cada configuracion de archivo xml representa una capa,
se puede cargar la configuracion de los beans con la etiqueta import resource

- separar la logica de los controladores, se crean interfaces e injecciones de
código para 

## configuracion-jdl
- atributos requeridos en el jdl
- opsciones de paginacion con scroll infinito etc...
- variable en el jdl, tipo de relacion uno a muchos
- dto, microservice, paginacion y serviceImpl

## comando para ejecutar jhipster en modo produccion
- aprendi a conectarme a docker con vscode

## inversion de control
- tiene un cliente que llama a un grupo de clases, para finalmente
realizar la tarea del cliente
- puede usar IoC con una implementacion mas basica para las pruebas
y despues usar una forma mas avanzada

## comando de docker
- se usa el comando para generar un archivo de docker adecuado a `jhipster`
`./mvnw -Pprod package verify jib:dockerBuild --offline`