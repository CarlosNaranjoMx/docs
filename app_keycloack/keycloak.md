
- [configuracion-keycloack](#configuracion-keycloack)

## configuracion-keycloack

cliente, base url: http://192.168.1.74:11111/auth/admin/jhipster/console/

Para configurar Keycloak en JHipster, deberá crear un "cliente" en Keycloak. El
cliente es una entidad que representa una aplicación o un servicio que desea
utilizar Keycloak para autenticar a sus usuarios.

En Keycloak, puede crear un nuevo cliente haciendo clic en el botón "Crear" en
la página de administrador de clientes. A continuación, se le pedirá que
proporcione algunos detalles básicos sobre el cliente, como su nombre y su URL
de redirección.

Algunas opciones importantes a configurar en el cliente son:

    "Access Type": "confidential"
    "Valid Redirect URIs": url de su aplicación
    "Web Origins": url de su aplicación
    "Aditional AuthZ settings": si desea que el servidor de autorización valide el token de acceso

Una vez que haya configurado estas opciones, podrá guardar el cliente y comenzar
a utilizar Keycloak en su aplicación JHipster.