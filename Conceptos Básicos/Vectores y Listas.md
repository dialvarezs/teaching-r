El contar con un único valor por variable es una limitante a la hora de abordar problemas que involucren datos reales, ya que es común que existan múltiples mediciones, o que los datos puedan estar compuestos por múltiples atributos. Para estos casos son útiles las **colecciones**, que permiten agrupar datos y asignarlos a una variable determinada.

## Vectores
Un vector es una colección unidimensional con datos del mismo tipo. Para crear un vector se utiliza la función `c()`, pasándole como argumentos los elementos que queremos incluir.
```r
# vector de números enteros
c(1, 2, 3, 5, 8, 13) 
# vector de strings
animales <- c("gato", "perro", "vaca", "serpiente", "gallina")
```
Igualmente podemos utilizar la función `c()` para añadir elementos a un vector o combinar vectores.
```r
nuevos_animales <- c(animales, "cangrejo", "rana")

nombres_grupo_1 <- c("Luis", "Nataly", "Andrea")
nombres_grupo_2 <- c("Karen", "Rodrigo", "Carlos")
nombres_curso <- c(nombres_grupo_1, nombres_grupo_2)
```