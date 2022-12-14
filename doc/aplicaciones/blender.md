- [creacion de un personaje en 3d](#creacion-de-un-personaje-en-3d)
  - [consideraciones](#consideraciones)
  - [cargar referentes](#cargar-referentes)
  - [modo de esculpido](#modo-de-esculpido)
  - [planeado para animacion](#planeado-para-animacion)
  - [referencias](#referencias)
- [teoria](#teoria)
    - [tipos de capas](#tipos-de-capas)
    - [teclas](#teclas)

# creacion de un personaje en 3d

## consideraciones
- teclado numerico

## cargar referentes
- dividir la seccion
- uv/image editor
- open
- ver miniaturas
- texturas cambian uv/image (*)
- anclar imagen
- n menu, menu +, background image, añadir
- ajustar x y y, centro en el piso
- elegir el axis dependiendo de la vista
- repetir agregando otras imagenes de acuerdo a la vista

- insertar un plano
- modo edicion tab
- alt m -> combinar vertices en uno solo
- agregar modificadores, mirror, skin, subdivision surface

- extruir con la tecla e

- z,x,y, para restringir la extrucion hacia ese eje

- cuidar la raiz del modificador skin, marcar raiz

- ctrl a para inflar el modelo
- subdivir para agregar vertices

- vertice mark loose, distinta proyeccion de los vertices

- g mover vertice, g 2 veces mover por la arista que lo contiene

- punto de rotacion, pivote, del ultimo seleccionado
- quitar los modificadores en orden, o alt c, para convertir todo a una maya

## modo de esculpido

- dypology creacion de nueva geometria
- pincel de inflar, tecla i
- f tamaño al pincel, shift f, fuerza del pincel
- tecla h para ocultar una pierna

## planeado para animacion
- loops en la caras
- snap para que se encaje a la superficie

## referencias

- zybot body 

# teoria

### tipos de capas
- diffuse
- specular
- lighthing

### teclas
- las teclas se encuentran en preferences

movimiento:
- bolita mouse rotar
- ctrl bolita zoom, (girar bolita)
- shift bolita movimiento

shift y click para mas de una:
- s scale
- r rotate
- g move, g 2 veces mover por arista

- tab modo edicion
- f, tamaño del pincel, shift f fuerza del pincel 
- e, extruccion, x,y,z, excluir extrusion
- alt m, combinar vertices en uno solo
- n menu
- h ocultar objetos