- [memoria](#memoria)
  - [multiprogramacion](#multiprogramacion)
  - [problema de la reubicacion](#problema-de-la-reubicacion)
  - [intercambio entre memoria principal y secundaria swapping](#intercambio-entre-memoria-principal-y-secundaria-swapping)
  - [particiones de tamaño variable](#particiones-de-tama%C3%B1o-variable)
  - [Problemas en el manejo de la memoria](#problemas-en-el-manejo-de-la-memoria)
  - [Traslapes (overlays)](#traslapes-overlays)
  - [Memoria virtual (paginacion)](#memoria-virtual-paginacion)
    - [Reemplazo de paginas](#reemplazo-de-paginas)
    - [Algoritmo optimo para el reemplazo de paginas](#algoritmo-optimo-para-el-reemplazo-de-paginas)
    - [conjunto de trabajo](#conjunto-de-trabajo)
- [glosario](#glosario)

## memoria
- Ley de Parkinson: los programas se exapanden para llenar toda la memoria de la que disponen

- ejecucion de programas:
  - texto, medio no volatil
  - codigo objeto, (explicacion) codigo maquina para la aruitectura utilizada
  - enlaces modulo objeto, y rutinas (el resultado) una copia imagen del progrma que se ejecutara y se almacena en el disco
  - se coloca en memoria principal (motivo) para que en algun momento sea ejecutada

- extension de la memoria principal
- (caso) tecnicas de paginacion e intercambio (swapping)

- administracion de memoria, (depende) cantidad de procesos

- mayor cantidad de procesos dificulta la administracion
- mayor cantidad de procesos en la memoria principal, mayor eficiencia

- (caso) un solo programa en la memoria principal
- (implica) hacerse cargo de toda la interaccion con los dispositivos

- (en la practica) elementos basicos del sistema operativo
- (implica) la memoria se divide en secciones que se utilizan para fines especificos

- (casos) (3)

### multiprogramacion
- `cambio de contexto` `quantum`, tempode espera dispositivos perifericos

- colocar varios procesos en la memoria principal

- `espacio de direcciones`

(caso 1)
- definicion
- cada tamaño de particion se maneja una cola
- (problema 1)
- (problema 2)

### problema de la reubicacion

### intercambio entre memoria principal y secundaria swapping

### particiones de tamaño  variable
- administrador de la memoria `compactacion de la memoria`

### Problemas en el manejo de la memoria

`sistema de los asociados buddy system`

### Traslapes (overlays)

### Memoria virtual (paginacion)

dividir los procesos, cada proceso con su propio spacio de direcciones virtuales `unidad de manejo de memoria`

`paginas`, `marcos de paginas`

`tablas de pagina` -> memoria principal

`tabla para marcos de pagina`

memoria asociativa, translation lookaside buffer

`hit raio` (depende) alta cantidad de accesos a la memoria asociativa

#### Reemplazo de paginas

- copia del contenido al almacenamiento secundario

#### Algoritmo optimo para el reemplazo de paginas
- cola de llegadas, reeplazo de paginas en el orden en el que llegaron, fueron acomodadas en la memoria principal, no se toma en cuenta si la pagina es de uso frecuente 

- `principio de localidad`, uso menos reciente, 2 bits especiales

- reemplazo estilo reloj

- eliminar la pagina que ha estado sin utilizar por mas tiempo, hardware especial

- trashing

#### conjunto de trabajo 

## glosario
- administrador de la memoria
- memoria
- procesos
- programas de aplicacion
- productividad
- tamaño,velocidad,persistencia,costo
- registro, procesos, recuperar espacio liberado, principal y secundaria
- ejecucion de un programa
- elementos basicos del sistema oprativo
- ROM (read only memory)
- primeras localidades de memoria
- controladores de dispositivo
- sistemas multiusuario


------------------------------------------------------