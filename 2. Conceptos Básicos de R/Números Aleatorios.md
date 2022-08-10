La generación de números aleatorios es una tarea común cuando se desea crear valores para probar un fragmento de código. Es posible controlar el tipo de este número aleatorio e incluso el rango y la distribución en la cual se genera.


## Números aleatorios en distribución uniforme
La forma más sencilla es utilizar la función `runif()`, que recibe 3 parámetros:
- cantidad de números a generar
- `min`: valor mínimo (por defecto 0)
- `max`: valor máximo (por defecto 1)
Estos números son obtenidos generados a partir de una **distribución uniforme** en los valores mínimo y máximo, y dado que genera múltiples números al mismo tiempo, la función retorna un vector.
```r
# genera 5 números aleatorios entre 0 y 1
runif(5)

# genera 100 números aleatorios entre 0 y 100
runif(100, min = 0, max = 10)
```

Si queremos generar números enteros (sin decimales), es posible utilizar la función `sample()`, pasando un rango como primer argumento y la cantidad de valores deseados como segundo argumento. Además, es posible controlar si se desean elementos únicos o si es posible repetirlos con el parámetro `replace` (el cual por defecto es `FALSE`). 
```r
# genera 10 números aleatorios entre 1 y 1000, con la posibilidad de que estén repetidos
sample(1:1000, 10, replace = TRUE)

# genera 20 números aleatorios entre 1 y 100, sin repetición
sample(1:100, 20, replace = FALSE)
```

Algo interesante de la función `sample()` es que el primer argumento puede ser un vector con los posibles valores (los cuales no necesariamente tienen que ser numéricos).
```r
# genera 10 valores aleatorios entre números los presentes en el vector
sample(c(1, 6, 7, 13), 10, replace = TRUE)

# genera 15 opciones de Verde / Rojo / Amarillo
sample(c("Verde", "Rojo", "Amarillo"), 15, replace = TRUE)
```

## Números aleatorios en distribución normal
Para generar números aleatorios en una distribución normal, se utiliza la función `rnorm()`, con los siguientes parámetros:
- cantidad de números a generar
- `mean`: promedio de la distribución (por defecto 0)
- `sd`: desviación estándar de la distribución (por defecto 1)

---
⬅️ [[Funciones]]

---
