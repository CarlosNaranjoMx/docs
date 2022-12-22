- [clinica-de-mascotas](#clinica-de-mascotas)
- [orden-de-insercion](#orden-de-insercion)
- [base-de-datos-poostgres](#base-de-datos-poostgres)
- [jdl](#jdl)

# clinica-de-mascotas

## orden-de-insercion

- insertar primero un veterinario
    - insertar especialidad
        - insertar especialidad de veterinario
- insertar una mascota
    - insertar un dueño
    - insertar un tipo
    - insertar una visita

## base-de-datos-poostgres


## jdl

```jdl
DROP TABLE vets;
CREATE TABLE vets(
  first_name VARCHAR(60) primary key,
  last_name VARCHAR(60)
);
DROP TABLE specialties;
CREATE TABLE specialties(
  id INT primary key,
  name TEXT  
);
DROP TABLE vet_specialties;
CREATE TABLE vet_specialties(
  vet_id INT references vets(first_name),
  specialty_id INT references specialties(id)
);

DROP TABLE pets;
CREATE TABLE pets(
  id INT primary key,
  name VARCHAR(60),
  birth_name VARCHAR(60),
  type_id INT references types(id),
  owner_id INT
);
DROP TABLE owners;
CREATE TABLE owners(
  id INT primary key,
  first_name VARCHAR(60),
  last_name VARCHAR(60),
  address VARCHAR(60),
  city VARCHAR(60),
  telephone VARCHAR(60)
);

DROP TABLE visits;
CREATE TABLE visits(
  id INT primary key,
  pet_id INT references pets(id),
  visit_name VARCHAR(60),
  description VARCHAR(60)
);
DROP TABLE types;
CREATE TABLE types(
  id INT primary key,
  name VARCHAR(60)
);

}
```