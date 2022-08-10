R es un lenguaje interpretado, lo que hace que procese el código de forma interactiva, por lo que las instrucciones que se ejecuten son evaluadas de forma inmediata, obteniendo el resultado de la operación que estemos realizando en la misma consola. Esto entrega la ventaja de permitir evaluar rápidamente alguna operación o fragmento de código para determinar si el resultado obtenido es el esperado.

## Extensión
Los archivos que contienen código en R tienen la extensión `.r` o `.R`, y al tener esa extensión pueden ser reconocidos para ser abiertos directamente mediante [[Instalación de R y RStudio|RStudio]].

## Comentarios
Los comentarios son bloques de texto libre que son ignorados por el intérprete del lenguaje, por lo que cumplen la función de proveer información para el programador que está creando el código o cualquier persona que pueda estar interesada en leerla a futuro. Los comentarios deben comenzar con un `#`, lo que hace que todo lo que esté a la derecha de ese símbolo pase a ser un comentario, incluso código funcional de R que queramos que sea ignorado, pero no queremos borrarlo.
```r
# este es un comentario que contiene información importante
mensaje <- "¡Hola!"

condicion <- TRUE  # esto también es un comentario, pero en la misma línea
```

## Operadores matemáticos
R soporta todas las operaciones matemáticas básicas, lo que permite reproducir cualquier operación que podamos realizar en una calculadora sin problemas.
```r
a <- 10
b <- 20

a + b   # suma
a - b   # resta
a * b   # multiplicación
a / b   # división
a ** b  # exponenciación

# algo más complejo, requiere uso de paréntesis para garantizar
# que se realice la operación en el orden que esperamos
(a + b) / (a * b)
```

### Operador módulo
El operador módulo (`%%` en R) es un operador que entrega el resto de la división entera entre dos números. Esta operación es particularmente útil a la hora de determinar si un número es par (ya si es perfectamente divisible por dos quiere decir que es par), o al determinar si un número es primo.
```r
5 %% 2  ## 1, por lo tanto impar

27 %% 3 ## 0, por tanto 27 es divisible por 3
```

## Operadores lógicos
Los operadores lógicos permiten hacer una pregunta comparando dos valores y obtener una respuesta **lógica** ("verdadera" o "falsa") de esta expresión.
```r
a < b   # a menor que b
a <= b  # a menor o igual que b
a > b   # a mayor que b
a >= b  # a mayor o igual que b
a == b  # a igual a b
a != b  # a distinto de b
```
Es posible combinar múltiples preguntas entre dos valores para formular preguntas complejas. Para esto se puede utilizar
- `&&`: "y", verdadera solo si ambas preguntas son verdaderas.
- `||`: "o", verdadera si cualquiera de las preguntas es verdadera.
- `!`: "negación", cambia el valor de verdadero a falso y viceversa.
```r
x <- 3
y <- 5
z <- 15

z > 0                 ## TRUE
x >= y                ## FALSE
z == (x * y)          ## TRUE
(x < y) && (z < y)    ## FALSE
(x > 10) || (z > 10)  ## TRUE
```

---
➡️ [[Variables y Tipos]]

---