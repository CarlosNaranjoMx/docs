- [patron-de-diseño-ioc](#patron-de-diseño-ioc)
- [back-end](back-end)
    - [petsdto-java](#petsdto-java)
- [front-end](#front-end)

# patron-de-diseño-ioc

El patrón de diseño IoC es una solución para el problema de la dependencia de software y la complexidad se debe al hecho de que los diferentes components de software se interconectan de muchas formas diferentes.

IoC ayuda a evitar esta complejidad y este problema de interconexión al permitir que los componentes de software se conecten a través de interfaces y no a través de la conexión directa entre los dos components que se estan conectando entre sí.

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

