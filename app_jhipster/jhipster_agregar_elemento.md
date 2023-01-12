- [patron-de-diseño-ioc](#patron-de-diseño-ioc)
- [back-end](back-end)
    - [petsdto-java](#petsdto-java)
- [front-end](#front-end)

# spring-beans

- `@Component`: crea una instancia dentro del contexto de spring y la guarda ahí,
no es posible guardar variables de tipo entero dentro de spring

- `@Configuration`: indica que la calase contiene metodos que regreseran algun
bean, o sea para que puedas crear tus propios beans

- `@Service`: en esta clase se pueden inyectar los metodos de los beans de spring

la notación configuration es una de las anotaciones más usadas en Sprint ya que
nos facilita la creación de beans o instancias dentro del contexto de Sprint esto
resuelve algunas limitaciones de la notación component 

que si no sabes lo que es
te dejo un vídeo aquí arriba o en la descripción de este 

para verlo como
detenimiento he creado tres clases la primera es usuario servicio que es la
clase que vamos a necesitar inyectar nuestro nuevo bean la segunda es apeconfic
que es nuestra clase de configuración Y dónde va a estar administrado nuestros
Pines y la última es la clase versión que es la clase que vamos a necesitar
inyectar en usuarios de servicio para saber qué versión estamos utilizando

actualmente en nuestro proyecto como ya hemos visto anteriormente utilizando la
oración component le estamos diciendo a Sprint que nos Crea una instancia dentro
del contexto de Sprint y que la guarde ahí 

el problema de aquí es que cuando
nosotros queremos crear una instancia de versión necesitamos como parámetros en
el constructor de tipo entero Major Minor y revision tres tipos de variables que
no contienen en su en su contexto además de ello para guardar una variable de
tipo entero no es posible en Sprint ya que no es un tipo de objeto si ahora
corremos lo que es nuestro programa Sprint se quejará diciendo los que el
parámetro el número 0 del constructor de versión requiere un Bean de tipo entero
incluso nos recomienda que definamos un Bean de tipo entero en la configuración
para resolver esto en vez de utilizar la notación component lo que tenemos que
utilizar es una clase en la cual administramos nuestro Sprint que será con la
notación configuration.

la notación configuración no es más ni menos para
dedicarle a Sprint que esta clase va a contener métodos en los cuales van a
retornar un bean es decir una clase una instancia que Sprint va a tener que
guardar en su contexto de Sprint para hacer ello básicamente tenemos que
declarar una clase que sea por ejemplo public versión por ejemplo y aquí tenemos
que retornar una nueva versión que va a ser 1 0.0 Y por último le vamos a
indicar que este método va a ser un bean es decir aquí le estamos indicando dos
cosas a Sprint la primera que la clase ap-confic va a ser una clase en la cual
nosotros tendremos métodos en los cual crearemos instancias que Sprint deberá
guardar en su contexto y segundo tenemos una notación llamada bean

 que aquí le
estamos indicando a Sprint que este método es un método que devuelve una
instancia que queremos que guarde en su contexto ya que nosotros Aunque tengamos
la anotación configuration podríamos perfectamente crear otro método que sea por
ejemplo otro método y aquí no le estamos indicando de ninguna forma Sprint que
este otro método no tiene que ser guardado en el contexto de Sprint por tanto
ahora una vez que queramos inyectar lo que es dentro de nuestro constructor de
usuario servicio que es por ejemplo la clase versión y nosotros le invitamos a
través del constructor aquí Sprint va a intentar Buscar qué tipo de clase hay en
su contexto de y la va a inyectar ya que solemos indicado a través de la
configuración de Sprint si ahora corremos nuestro programa y te ponemos tanto en
el constructor de usuario servicios que es donde queremos inyectar la versión de
nuestra aplicación y en el método bim que será llamado a través de Sprint para
guardar la instancia que le hemos mencionado de versión y corremos nuestro
programa vemos Que exactamente primero Sprint irá y mirará qué tipo de clases
tiene la notación configuration e irá y mirará en cada una de esas clases Cuáles
métodos tienen la notación Pin y verá que nosotros estamos devolviendo una
instancia de un objeto que quiere que se guardaron y luego creará las instancias
de tipo component que en este caso es de tipo service y como hemos visto en
apconfic que tenemos la versión 1.00 vemos Que Exactamente La versión que
tenemos inyectando en nuestra clase de servicio es exactamente 100 otra de las
formas que tenemos para utilizar este tipo de creación de instancia dentro del
concepto de Sprint es como por ejemplo si queremos crear una instancia dentro
del contenedores Sprint de una clase que no es nuestro proyecto por ejemplo en
esa clase que tenemos propio de Java se llama http client nosotros no podemos de
ninguna forma crear ningún tipo de instancia con componentes ya que no es
accesible a través de nuestro código lo que podemos hacer es simplemente que
haremos otro método que devolverá un http y por ejemplo aquí podemos así se te
proclagin Y una vez más lo que podemos hacer es retornar un http client que será
New builder.bilt Y de esa forma podemos configurar nuestro http client con las
propiedades que queremos utilizar y utilizarlo como cualquier otro tipo de The
Bing o de instancia dentro del contexto de Sprint en nuestro proyecto como por
ejemplo que podríamos inyectarlo en aquí usando http client http Black client
entonces Sprint ya sabrá que en su contexto hay un tipo http client y lo
inyectará ya que la hemos definido dentro de la clase de configuración app de
config y con el método http client además de ello también nos múltiple las
formas de utilizar este método ya que si tenemos por ejemplo y queremos utilizar
http client 2 en el cual tendremos podremos utilizar diferentes versiones Time
out o cualquier otro tipo de propiedad que queremos utilizar tendremos dos
distancias dentro de guardadas en el contexto de Sprint y que nosotros podemos
configurar manualmente gracias a las clases de configuration y los métodos
anotados con Bin bueno y espero que te haya gustado mucho este vídeo La verdad
que no es muy difícil de entender y si has visto los vídeos anteriores de
autoware y components que te dejaré en la descripción de este vídeo La verdad
que es bastante sencillo de comprender cómo funciona el contexto de Sprint si
tienes por supuesto algún tipo de duda de cómo funciona ya puedes dejar en la
caja de comentarios que te intentará responder lo más rápido posible o si tienes
algún tipo de feedback o alguna forma en la que puedo mejorar te lo agradecería
que también me lo dejas en la caja de los comentarios Espero que te haya gustado
mucho este vídeo No olvides suscribirte para ayudar a este canal y nos vemos en
el próximo vídeo hasta


# patron-de-diseño-ioc

El patrón de diseño IoC es una solución para el problema de la dependencia de
software y la complexidad se debe al hecho de que los diferentes components de
software se interconectan de muchas formas diferentes.

IoC ayuda a evitar esta complejidad y este problema de interconexión al permitir
que los componentes de software se conecten a través de interfaces y no a través
de la conexión directa entre los dos components que se estan conectando entre
sí.

# back-end

- ayuda a evitar la complejidad de las interconexiones, permite
que los componentes de softwares se
conecten a través de las interfaces y no a través de la conexión directa

## petsdto-java
- En el archivo `src/main/java/mx/conacyt/crip/ejemplos/service/dto/PetsDTO.java`, 
- directorio `service/dto`:
crear los metodos get, set y modificar la instancia de toString

```java
    public String getPaisNacimiento() {
        return paisNacimiento;
    }

    public void setPaisNacimiento(String paisNacimiento){
        this.paisNacimiento = paisNacimiento;
    }
```

- y se modifico:

```java
    // prettier-ignore
    @Override
    public String toString() {
        return "PetsDTO{" +
            "id=" + getId() +
            ", name='" + getName() + "'" +
            ", birthname='" + getBirthname() + "'" +
            ", typeid=" + getTypeid() +
            ", ownerid=" + getOwnerid() +
            ", visits=" + getVisits() +
            ", paisNacimiento=" + getPaisNacimiento() +
            "}";
    }
```


- directorio `service/imp`:

- directorio  `service/criteria`:
operaciones de autenticacion, usar
los controladores y el frontend

- crear setters y getters de los string filters tambien

```java
    public StringFilter getPaisNacimiento(){
        return paisNacimiento;
    }

    public StringFilter paisNacimiento() {
        if (paisNacimiento == null){
            paisNacimiento = new StringFilter();
        }
        return paisNacimiento;
    }

    public void setPaisNacimiento(String FIlter paisNacimiento){
        this.paisNacimiento = paisNacimiento;
    }
```

- DIRECTORIO: `service`:
- ARCHIVO: `PetsQueryService.java`
```java
if (criteria.getPaisNacimiento() != null) {
    specification = 
        specification.and(
            buildSpecification(criteria.getPaisNacimiento(), root -> root.join(Pets_.paisNacimiento, JoinType.LEFT).get(Pets_.id) )
        );
}
```

- DIRECTORIO: `domain`
- ARCHIVO: `Pets.java`

- agregando columna
```java
@Column(name = "paisNacimiento")
private String paisNacimiento;
```

- ejemplo de setters y getters
```java
    public String getPaisNacimiento() {
        return this.paisNacimiento;
    }

    public Pets paisNacimiento(String paisNacimiento){
        this.setPaisNacimiento(paisNacimiento);
        return this;
    }
    
    public void setPaisNacimiento(String paisNacimiento){
        this.paisNacimiento = paisNacimiento;
    }
```
- sobrescribir el metodo toString:
```java
@Override
    public String toString() {
        return "Pets{" +
            "id=" + getId() +
            ", name='" + getName() + "'" +
            ", birthname='" + getBirthname() + "'" +
            ", typeid=" + getTypeid() +
            ", ownerid=" + getOwnerid() +
            ", paisNacimiento=" + getPaisNacimiento() +
            "}";
    }
```




# front-end


- DIRECTORIO: `.jhipster/Pets.json`
- ARCHIVO: `Pets.json`

```json
{
    "fieldName": "fechaNacimiento",
    "fieldType": "String"
}
```
- DIRECTORIO: `src/main/webapp/i18n/en`
- ARCHIVO: `/pets.json`

```json
},
      "id": "Id",
      "name": "Name",
      "birthname": "Birthname",
      "typeid": "Typeid",
      "ownerid": "Ownerid",
      "types": "Types",
      "owners": "Owners",
      "visits": "Visits",
      "paisNacimiento": "paisNacimiento"
    }
```

- ARCHIVO: `src/main/resources/config/liquibase/changelog/20221219192500_added_entity_Pets.xml`
```xml
<column name="paisNacimiento" type="varchar(255)">
    <constraints nullable="true">
</column>
```

- ARCHIVO: `src/main/webapp/app/entities/pets/pets.vue`
```html
<th scope="row" v-on:click="changeOrder('paisNacimiento')">
    <span v-text="$t('proyecto01App.pets.paisNacimiento')"> Pais Nacimiento </span>
    <jhi-sort-indicator :current-order="propOrder" :reverse="reverse" :field-name="'paisNacimiento'"></jhi-sort-indicator>
</th>
```

```html
<td>{{ pets.name }}</td>
<td>{{ pets.birthname }}</td>
<td>{{ pets.typeid }}</td>
<td>{{ pets.ownerid }}</td>
<td>{{ pets.paisNacimiento }}</td>
```

- ARCHIVO:
`src/main/webapp/app/entities/pets/pets-details.vue`

```html
<div class="form-group">
    <label class="form-control-label" v-text="$t('proyecto01App.pets.paisNacimiento')" for="pets-paisNacimiento">Pais Nacimiento</label>
    <input
        type="number"
        class="form-control"
        name="paisNacimiento"
        id="pets-paisNacimiento"
        data-cy="paisNacimiento"
        :class="{ valid: !$v.pets.paisNacimiento.$invalid, invalid: $v.pets.paisNacimiento.$invalid }"
        v-model.number="$v.pets.paisNacimiento.$model"
    />
</div>
```

```html
<dt>
    <span v-text="$t('proyecto01App.pets.paisNacimiento')">paisNacimiento</span>
</dt>
<dd>
    <span>{{ pets.paisNacimiento }}</span>
</dd>
```


- ARCHIVO: `src/main/webapp/app/entities/pets/pets-update.component.ts`

```ts
const validations: any = {
  pets: {
    name: {},
    birthname: {},
    typeid: {},
    ownerid: {},
    paisNacimiento: {},
  },
};
```


- DIRECTORIO: `domain`
- ARCHIVO: `Types.java`

```java

    @ManyToOne
    @JsonIgnoreProperties(value = { "types", "owners", "visits","paisNacimiento" }, allowSetters = true)
    
```

