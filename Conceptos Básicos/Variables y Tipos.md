## Variables
Una variable es un objeto el cual almacena un valor, el cual puede ser accedido y modificado durante la ejecución del programa.

El proceso para crear estas variables se denomina "declaración", y utiliza como sintaxis un nombre para la variable seguido del símbolo `<-` (asignación) y finalmente el valor a asignar.
```r
nombre <- "Diego"
```
Es posible cambiar el valor de las variables utilizando la misma operación
```r
naranjas_restantes <- 4
# alguien se comió una
naranjas_restantes <- 3
```

Al nombrar variables deben tener las siguientes consideraciones:
- Pueden ser una combinación de letras, dígitos, puntos (`.`), y guiones bajos (`_`). No pueden comenzar con dígitos o guiones bájos, y en caso de empezar con un punto, no puede ser seguido por un dígito.
- Los nombres de variables son sensibles al uso de mayúsculas y minúsculas (`edad`, `Edad` y `EDAD` son variables diferentes).
- No se pueden utilizar las palabras reservadas como nombres de variables (`if`, `while`, `FALSE`, etc).

En términos generales es recomendable utilizar nombres de variables **claros, no ambiguos y descriptivos**. Y concretamente, se podría considerar un buen esquema el uso de palabras en minúsculas separadas por guiones bajos.

## Tipos de datos en R
#### `numeric`
Para valores numéricos, tanto enteros como decimales. Es posible utilizar notación científica.
```r
temperatura_ambiente <- -3.5
pi <- 3.14159265359
precio_pantalon <- 20000
cantidad_de_estudiantes <- 7
velocidad_de_la_luz_kms <- 3e6
```

#### `character` 
Cadenas de texto.
```r
mensaje <- "¡Hola a todos!"
nombre <- "Jacqueline"
cadena_de_adn <- "ATGTTGGAAATGTGGTAG"
```

#### `logical`
Para almacenar valores lógicos, verdadero (`TRUE` o `T`) o falso (`FALSE` o `F`).
```r
compra_recibida <- FALSE
agua_ha_hervido <- T
```

#### `factor`
***Nota**: esto tendrá más sentido después de haber leído la sección [[Vectores y Listas]].*
Los factores son tipos especialmente útiles cuando se poseen categorías definida (por ejemplo sexo). El tipo factor permite definir las opciones (o niveles) para un valor determinado, los que son asociados a un valor entero. Esto entrega ciertas ventajas como la de controlar el orden de los elementos de forma arbitraria.
Los factores pueden ser creados directamente a partir de vectores (generalmente de tipo `character`).
```r
colores <- c("azul", "amarillo", "azul", "azul", "rojo", "rojo")
colores <- factor(colores)
print(colores)
# [1] azul     amarillo azul     azul     rojo     rojo    
# Levels: amarillo azul rojo
```

### Transformación de tipos en variables
Existen funciones para cambiar de tipo una variable, las cuales comienzan con el prefijo `as.`. Naturalmente, para que este proceso sea exitoso debe tener sentido (no podemos tranformar a valor numérico un texto que no pueda ser interpretado como un número).
```r
# de character a numeric
texto_numerico <- "1111234185809"
as.numeric(texto_numerico)
# de numeric a logical (sólo funcionará con 0 y 1)
valores_binarios <- c(1, 0, 1, 1)
as.logical(valores_binarios)
```