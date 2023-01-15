- [jhipster-directorios](#jhipster-directorios)

# jhipster-directorios
JHipster es un generador de aplicaciones de código abierto que se utiliza para
crear proyectos de Java y JavaScript modernos. La estructura de directorios de
un proyecto JHipster es similar a la de cualquier otro proyecto de Spring Boot,
pero con algunas diferencias debido a la presencia de código JavaScript y a la
configuración adicional proporcionada por JHipster.

jhipster
├── src/main/resources/config
├── src/main/java/.../service
├── src/main/webapp
└── webapp

Algunos de los directorios más importantes en un proyecto JHipster incluyen:

    - src/main/java: contiene el código fuente de Java de la aplicación, como los controladores, servicios y entidades.

    - src/main/resources: contiene los recursos de la aplicación, como las plantillas de vista, los archivos de configuración y los mensajes de idioma.

    - src/main/webapp: contiene el código JavaScript y los recursos web de la aplicación, como las plantillas HTML, los archivos CSS y los scripts.

    - src/test/java: contiene los casos de prueba de Java de la aplicación.

    - src/test/javascript: contiene los casos de prueba JavaScript de la aplicación.

    - target: contiene los archivos generados por el proceso de compilación, como el archivo JAR o WAR de la aplicación.

    - node_modules: contiene las dependencias de npm necesarias para el proyecto de javascript.

    - yarn.lock o package-lock.json: contiene información sobre las dependencias de javascript y su versión.

    - mvnw o mvnw.cmd : es un script de shell/batch para ejecutar maven.

    - gradlew o gradlew.bat : es un script de shell/batch para ejecutar gradle.

JHipster también genera una serie de archivos de configuración adicionales, como
docker-compose.yml y Jenkinsfile, para facilitar el despliegue y la integración
continua de la aplicación.