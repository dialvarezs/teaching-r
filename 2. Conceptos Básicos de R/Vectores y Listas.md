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
# "gato"      "perro"     "vaca"      "serpiente" "gallina"   "cangrejo"  "rana"

nombres_grupo_1 <- c("Luis", "Nataly", "Andrea")
nombres_grupo_2 <- c("Karen", "Rodrigo", "Carlos")
nombres_curso <- c(nombres_grupo_1, nombres_grupo_2)
# [1] "Luis"    "Nataly"  "Andrea"  "Karen"   "Rodrigo" "Carlos" 
```

### Operaciones sobre vectores
Una de las características de R es que puede trabajar con vectores de forma natural, lo que quiere decir que la mayoría de las funciones y operaciones funcionan directamente esperando un vector como entrada. Ejemplo de esto son las operaciones matemáticas, donde al realizar una operación matemática que involucre, esta se realizará por cada uno de sus elementos.
```r
v1 <- c(1 , 3, 5, 7, 11, 13, 17)
v2 <- c(2, 4, 6, 8, 10, 12, 14)

v1 + 5   ## 6 8 10 12 16 18 22
v1 * 2   ## 2 6 10 14 22 26 34
v1 + v2  ## 3 7 11 15 21 25 31
v2 / v1  ## 2.0 1.3 1.2 1.1 0.9 0.9 0.8
```
También se pueden evaluar operaciones lógicas en vectores, donde la operación será aplicada a cada elemento y será entregado un valor lógico dependiendo del resultado para cada elemento.
```r
v1 > 7  ## FALSE FALSE FALSE FALSE TRUE TRUE TRUE
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
v[c(1, 2, 5, 6)]  ##  3 10 33 41
```
En muchos casos nos interesará sub seleccionar múltiples elementos en posiciones consecutivas, y si bien es posible escribir el vector con todas las posiciones, se puede escribir de una forma mucho más conveniente mediante el uso de rangos. Un rango consiste en dos números separados por dos puntos (por ejemplo `1:10`), que se traduce como un vector con todos los valores consecutivos entre ambos números, ambos inclusive.
```r
v[1:5]  ##  3 10 21 25 33
```
Por último, es posible sub seleccionar elementos de un vector mediante un vector lógico del mismo tamaño, donde los elementos serán seleccionados si hay un `TRUE`. Y dado que al aplicar una operación lógica sobre un vector se obtiene un vector lógico, se puede utilizar directamente para filtrar los elementos de un vector utilizando una expresión lógica.
```r
# mayores a 25
v[v > 25]  ## 33 41 55
# pares
v[v %% 2 == 0]  ## 10
```

## Matrices
Las matrices son esencialmente vectores en dos dimensiones útiles para almacenar ciertos tipos de información, y su uso es requerido para ciertas operaciones matemáticas. Se puede crear una matriz a partir de un vector o rango mediante la función `matrix()`, en la que podemos indicar el número de filas (`nrow`) y columnas (`ncol`) que queremos que tenga nuestra matriz. Se puede indicar solo uno de los dos parámetros y el otro será calculado automáticamente en base a la cantidad de elementos. Otro punto relevante a considerar es que por defecto la matriz se llena por columnas, pero eso puede ser cambiado mediante el parámetro `byrow`.
```r
# al no especificar cantidad de filas ni de columnas
# se crea una matriz de una única columna
mat <- matrix(1:20)

# matriz de 5 columnas y 4 filas
mat <- matrix(1:20, ncol=5, nrow=4)
#    1    5    9   13   17
#    2    6   10   14   18
#    3    7   11   15   19
#    4    8   12   16   20
```
A la hora de extraer elementos de una matriz, hay que tener en consideración que existen dos dimensiones, que se pueden indicar dentro del mismo par de corchetes (`[c, r]`, `c`: columna, `r`: fila). Se puede omitir uno de los dos valores para extraer la columna o fila completa.
```r
mat[3, 4]  ## 15 (columna 3, fila 4)
mat[2,]    ##  2  6 10 14 18 (fila 2 completa)
mat[,4]    ## 13 14 15 16 (columna 4 completa)
```

## Listas
Las listas son colecciones que contienen múltiples elementos en una sola dimensión, como los [[#Vectores|vectores]], con la principal diferencia pueden contener elementos de diferentes tipos en la misma colección, incluso vectores o hasta otras listas. Para crear una lista se sigue un método similar al de un vector, pero utilizando la función `list()`.
```r
lista_1 <- list("el1", 2, 3)
lista_2 <- list("¡hola!", 123, 1:10, lista_1, FALSE)
```
Para acceder a los elementos de una lista, se debe utilizar doble corchete (`[[]]`), es importante tener en cuenta esto, ya que al usar un par de corchetes no habrá un error, sino que se creará una lista con el elemento seleccionado como único elemento.
```r
lista_1 <- list("uno", "dos", "tres")

lista_1[1]  ## [[1]] [1] "dos" (retorna una lista)
lista_1[[1]]  ## [1] "dos" (retorna el elemento)
```
Al igual que con los vectores, se pueden sub seleccionar los elementos para crear una nueva lista, y en este caso debe utilizarse solo un par de corchetes.
```r
# crea lista_2, usando el primer y el tercer elemento de lista_1
lista_2 <- lista_1[c(1, 3)]
```
Otra característica conveniente en las listas es que se les puede asignar un nombre a sus elementos, el cual puede utilizarse posteriormente para obtener dicho elemento usando el símbolo `$`.
```r
# se crea la lista con los atributos por nombres
persona <- list(nombre="Juan", apellido="Pérez", edad=30, peso=76.8, soltero=TRUE)

# obtener la edad por nombre
persona$edad   ## 30
# sigue funcionando acceder por posición
persona[[3]]   ## 30
```

---
⬅️ [[Variables y Tipos]] / ➡️ [[Control de Flujo]]

---
