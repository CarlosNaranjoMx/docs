- Ejemplo con una lista
```java
list.forEach(
    (param) -> function(param)
);
```
no puedes hacer break mientras itera

- Ejemplo con Threads
```java
//nueva clase que extiende a Thread con una funcion
//funcion que no recibe nada
new Thread(
    () -> function(param)
)
.start();
```