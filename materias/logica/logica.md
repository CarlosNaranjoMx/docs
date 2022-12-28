- [notas1](#notas1)
  - [los origenes de la logica matematica](#los-origenes-de-la-logica-matematica)
    - [preguntas](#preguntas)
  - [Logica proposicional](#Logica-proposicional)
  - [LOgica de primer orden](#LOgica-de-primer-orden)
  - [verificacion de programas](#verificacion-de-programas)
- [notas2](#notas2)
  - [oraciones declarativas](#oraciones-declarativas)
  - [sintaxis](#sintaxis)
  - [induccion estructural](#induccion-estructural)
  - [semantica](#semantica)
  - [sustitucion](#sustitucion)
  - [conceptos semanticos basicos](#conceptos-semanticos-basicos)
- [notas3](#notas3)
  - [deduccion natural](#deduccion-natural)
  - [propiedades de los sistemas de demostracion](#propiedades-de-los-sistemas-de-demostracion)
- [notas4 tableux semanticos](#notas4-tableux-semanticos)
  - [clasificacion de las formulas](#clasificacion-de-las-formulas)
  - [algoritmo para construir tableaux semanticos](#algoritmo-para-construir-tableaux-semanticos)
  - [tableaux semanticos para determinar que un argumento logico es correcto](#tableaux-semanticos-para-determinar-que-un-argumento-logico-es-correcto)
- [notas 5 Resolucion binaria](#notas-5-Resolucion-binaria)
  - [resolucion](#resolucion)
- [notas 6](#notas-6)
  - [la necesidad de un lenguaje mas expresivo](#la-necesidad-de-un-lenguaje-mas-expresivo)
  - [logica de predicados como un lenguaje formal](#logica-de-predicados-como-un-lenguaje-formal)
- [notas 7](#notas-7)
  - [deduccion natural](#deduccion-natural-1)
  - [reglas de derivacion para el cuantificador universal](#reglas-de-derivacion-para-el-cuantificador-universal)
  - [reglas de derivacion para el cuantificafor existencial](#reglas-de-derivacion-para-el-cuantificafor-existencial)
  - [logica minimal](#logica-minimal)
  - [logica intusionista](#logica-intusionista)
  - [logica clasica](#logica-clasica)
  - [reglas de inferencia para igualdad](#reglas-de-inferencia-para-igualdad)
  - [equivalencia entre formulas con cuantificadores](#equivalencia-entre-formulas-con-cuantificadores)
- [notas 8](#notas-8)
  - [semantica de la logica de predicados](#semantica-de-la-logica-de-predicados)
  - [modelos](#modelos)
  - [consecuencia logica](#consecuencia-logica)
- [notas 9](#notas-9)
  - [tableaux semanticos](#tableaux-semanticos)
  - [clasificacion de las formulas γ Δ](#clasificacion-de-las-formulas-%CE%B3-%CE%94)
  - [construcion de tableaux semanticos](#construcion-de-tableaux-semanticos)
  - [el metodo de tableaux semanticos es correcto y completo](#el-metodo-de-tableaux-semanticos-es-correcto-y-completo)
  - [una rama puede no terminar](#una-rama-puede-no-terminar)
- [notas 10 formas normales para la logica de predicados](#notas-10-formas-normales-para-la-logica-de-predicados)
  - [FNCP y forma clausular](#FNCP-y-forma-clausular)
  - [algoritmo de skolem](#algoritmo-de-skolem)
- [notas 11 algoritmos de resolucion. regla de resolucion y procedimiento de resolucion general](#notas-11-algoritmos-de-resolucion-regla-de-resolucion-y-procedimiento-de-resolucion-general)
  - [ideas previas](#ideas-previas)
  - [unificacion](#unificacion)
  - [algoritmo de unificacion por martelli y montanari](#algoritmo-de-unificacion-por-martelli-y-montanari)
  - [algoritmo de unificacion de robinson](#algoritmo-de-unificacion-de-robinson)
  - [resolucion general](#resolucion-general)
- [notas 12 resolucion sdl y programacion logica](#notas-12-resolucion-sdl-y-programacion-logica)
  - [clausulas de horns y resolucion sdl](#clausulas-de-horns-y-resolucion-sdl)
  - [clausulas de horn](#clausulas-de-horn)
  - [sustitucion de respuesta correcta](#sustitucion-de-respuesta-correcta)
  - [resolucion sld](#resolucion-sld)
  - [teoremas de correctud y completud](#teoremas-de-correctud-y-completud)
  - [arbol sld](#arbol-sld)
  - [prolog](#prolog)
  - [busqueda a profundidad](#busqueda-a-profundidad)
  - [prolog y la teoria de la programacion logica](#prolog-y-la-teoria-de-la-programacion-logica)
- [notas 13 teoria de herbrand](#notas-13-teoria-de-herbrand)
  - [interpretacion de clausulas](#interpretacion-de-clausulas)
  - [universo y modelos de herbrand](#universo-y-modelos-de-herbrand)
  - [representacion de los modelos de herbrand](#representacion-de-los-modelos-de-herbrand)
  - [el teorema de herbrand](#el-teorema-de-herbrand)
  - [semantica declarativa de los programas logicos](#semantica-declarativa-de-los-programas-logicos)
  - [procedimiento para encontrar el modelo minimo de herbrand](#procedimiento-para-encontrar-el-modelo-minimo-de-herbrand)
  - [semantica opracional de los programas logicos](#semantica-opracional-de-los-programas-logicos)
  - [equivalencia de ambas semanticas](#equivalencia-de-ambas-semanticas)
  - [incompletud e incorrectud de prolog](#incompletud-e-incorrectud-de-prolog)
- [notas 14 verificacion de modelos](#notas-14-verificacion-de-modelos)
  - [logica temporal de tiempo lineal](#logica-temporal-de-tiempo-lineal)
  - [sintaxis de ltl](#sintaxis-de-ltl)
  - [semantica de ltl](#semantica-de-ltl)
  - [patrones practicos de especificaciones](#patrones-practicos-de-especificaciones)
  - [equivalencias importantes entre formulas ltl](#equivalencias-importantes-entre-formulas-ltl)
  - [conjunto adecuado de conectivos para ltl](#conjunto-adecuado-de-conectivos-para-ltl)
  - [verificacion de modelos: exclusion mutua](#verificacion-de-modelos-exclusion-mutua)
  - [logica de arbol de computacion](#logica-de-arbol-de-computacion)
  - [sintaxis de ctl](#sintaxis-de-ctl)
  - [semantica de ctl](#semantica-de-ctl)
  - [patrones practicos de especificacion](#patrones-practicos-de-especificacion)
  - [equivalencias importantes entre formulas de ctl](#equivalencias-importantes-entre-formulas-de-ctl)
  - [algoritmo de verificacion de modelos para ctl](#algoritmo-de-verificacion-de-modelos-para-ctl)

## notas1

### los origenes de la logica matematica

#### preguntas

### Logica proposicional

### LOgica de primer orden

### verificacion de programas

## notas2

### oraciones declarativas

### sintaxis

### induccion estructural

### semantica

### sustitucion

### conceptos semanticos basicos

## notas3

### deduccion natural

### propiedades de los sistemas de demostracion

## notas4 tableux semanticos

### clasificacion de las formulas 

### algoritmo para construir tableaux semanticos

### tableaux semanticos para determinar que un argumento logico es correcto

## notas 5 Resolucion binaria

### resolucion

## notas 6

### la necesidad de un lenguaje mas expresivo
### logica de predicados como un lenguaje formal

## notas 7

### deduccion natural

### reglas de derivacion para el cuantificador universal
### reglas de derivacion para el cuantificafor existencial

### logica minimal
### logica intusionista
### logica clasica

### reglas de inferencia para igualdad

### equivalencia entre formulas con cuantificadores


## notas 8

### semantica de la logica de predicados
### modelos
### consecuencia logica


## notas 9
### tableaux semanticos
### clasificacion de las formulas γ Δ
### construcion de tableaux semanticos
### el metodo de tableaux semanticos es correcto y completo
### una rama puede no terminar



## notas 10 formas normales para la logica de predicados
### FNCP y forma clausular
### algoritmo de skolem



## notas 11 algoritmos de resolucion. regla de resolucion y procedimiento de resolucion general

### ideas previas
### unificacion
### algoritmo de unificacion por martelli y montanari
### algoritmo de unificacion de robinson
### resolucion general



## notas 12 resolucion sdl y programacion logica

### clausulas de horns y resolucion sdl
### clausulas de horn 
### sustitucion de respuesta correcta
### resolucion sld
### teoremas de correctud y completud
### arbol sld
### prolog
### busqueda a profundidad
### prolog y la teoria de la programacion logica

## notas 13 teoria de herbrand

### interpretacion de clausulas
### universo y modelos de herbrand
### representacion de los modelos de herbrand
### el teorema de herbrand
### semantica declarativa de los programas logicos
### procedimiento para encontrar el modelo minimo de herbrand
### semantica opracional de los programas logicos
### equivalencia de ambas semanticas
### incompletud e incorrectud de prolog

## notas 14 verificacion de modelos

### logica temporal de tiempo lineal
### sintaxis de ltl
### semantica de ltl
### patrones practicos de especificaciones
### equivalencias importantes entre formulas ltl
### conjunto adecuado de conectivos para ltl
### verificacion de modelos: exclusion mutua
### logica de arbol de computacion
### sintaxis de ctl
### semantica de ctl
### patrones practicos de especificacion
### equivalencias importantes entre formulas de ctl
### algoritmo de verificacion de modelos para ctl

