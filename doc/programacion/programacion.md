- [Complejidades](#Complejidades)
- [Merge Sort](#Merge-Sort)
- [problema](#problema)
- [mejora](#mejora)
  - [mejora](#mejora-1)


### Complejidades
- comparar por parejas 2 arreglos -> n²
- traduccion a un hash


### Merge Sort

- funciones con valor piso
 
- cuando son iguales definicion de cual elegir, izquierdo o derecho
- division entre 2 particion en algun punto (defines) si el lado izquierdo o el lado derecho es el mas grande
- 
- doble condicion de paro, uso de while
- doble condicion de paro, alguna de las 2 variables a llegado a su limite
  
- condicion de paro llego al limite

### problema
- copiado de arreglos a temporales contra sobreescritura, respaldar la informacion porque escribiremos sobre el arreglo que guarda los datos
### mejora
- escribir la informacion en nuevo arreglo, y regresar ese, y acceder a los datos del otro arreglo

#### mejora
- problema si no se cumple alguna de las 2 condiciones me gustaria un redireccionamiento directo a la fraccion de codigo (while) de acuerdo a la condicion que no se cumplio.
- 0 y 1 -> primer while
- 1 y 0 -> segundo while