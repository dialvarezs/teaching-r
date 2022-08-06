El contar con un único valor por variable es una limitante a la hora de abordar problemas que involucren datos reales, ya que es común que existan múltiples mediciones, o que los datos puedan estar compuestos por múltiples atributos. Para estos casos son útiles las **colecciones**, que permiten agrupar datos y asignarlos a una variable determinada.

## Vectores

### Creación de vectores
Un vector es una colección unidimensional con datos del mismo tipo. Para crear un vector se utiliza la función `c()`, pasándole como argumentos los elementos que queremos incluir.
```r
# vector de números enteros
c(1, 2, 3, 5, 8, 13) 
# vector de strings
animales <- c("gato", "perro", "vaca", "serpiente", "gallina")
```
Igualmente, podemos utilizar la función `c()` para añadir elementos a un vector o combinar vectores.
```r
nuevos_animales <- c(animales, "cangrejo", "rana")

nombres_grupo_1 <- c("Luis", "Nataly", "Andrea")
nombres_grupo_2 <- c("Karen", "Rodrigo", "Carlos")
nombres_curso <- c(nombres_grupo_1, nombres_grupo_2)
```

### Operaciones sobre vectores
Una de las características de R es que puede trabajar con vectores de forma natural, lo que quiere decir que la mayoría de las funciones y operaciones funcionan directamente esperando un vector como entrada. Ejemplo de esto son las operaciones matemáticas, donde al realizar una operación matemática que involucre, esta se realizará por cada uno de sus elementos.
```r
v1 <- c(1 , 3, 5, 7, 11, 13, 17)
v2 <- c(2, 4, 6, 8, 10, 12, 14)

v1 + 5   ## [1] 6 8 10 12 16 18 22
v1 * 2   ## [1] 2 6 10 14 22 26 34
v1 + v2  ## [1] 3 7 11 15 21 25 31
v2 / v1  ## [1] 2.0 1.3 1.2 1.1 0.9 0.9 0.8
```
También se pueden evaluar operaciones lógicas en vectores, donde la operación será aplicada a cada elemento y será entregado un valor lógico dependiendo del resultado para cada elemento.
```r
v1 > 7  ## [1] FALSE FALSE FALSE FALSE TRUE TRUE TRUE
```

### Obtención de elementos desde vectores
Dentro de un vector, cada elemento tiene una posición asociada, que parten desde el 1. Se pueden utilizar corchetes (`[]`) para obtener un elemento específico del vector de acuerdo a su posición.
```r
v <- c(3, 10, 21, 25, 33, 41, 55)
v[1]  ## 3
v[4]  ## 25
v[length(v)]  ## 55 (último elemento)
```
Dentro de los corchetes es posible especificar múltiples posiciones mediante un vector, lo que creará un nuevo vector extrayendo los elementos indicados por el vector de posiciones.
```r
v[c(1, 2, 5, 6)]  ## [1]  3 10 33 41
```
En muchos casos nos interesará sub seleccionar múltiples elementos en posiciones consecutivas, y si bien es posible escribir el vector con todas las posiciones, se puede escribir de una forma mucho más conveniente mediante el uso de rangos. Un rango consiste en dos números separados por dos puntos (por ejemplo `1:10`), que se comporta en la mayoría de los casos como un vector con todos los valores consecutivos entre ambos números, incluyéndolos.
```r
v[1:5]  ## [1]  3 10 21 25 33
```
Por último, es posible sub seleccionar elementos de un vector mediante un vector lógico del mismo tamaño, donde los elementos serán seleccionados si hay un `TRUE`. Y dado que al aplicar una operación lógica sobre un vector se obtiene un vector lógico, se puede utilizar directamente para filtrar los elementos de un vector utilizando una expresión lógica.
```r
# mayores a 25
v[v > 25]  ## [1] 33 41 55
# pares
v[v %% 2 == 0]  ## [1] 10
```

## Matrices

## Listas