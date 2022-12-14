- predicate
```java
// una lista de los sample que
Predicate condition = new Predicate() {
   boolean evaluate(Object sample) {
        return ((Sample)sample).value3.equals("three");
   }
};
List result = CollectionUtils.select( list, condition );
```

- lambda
```java
List<Sample> result = list.stream()
     .filter(item -> item.value3.equals("three"))
     .collect(Collectors.toList());
```