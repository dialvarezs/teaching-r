## Definición de funciones

Las funciones son bloques de código que contienen un conjunto de instrucciones que convierte inputs en outputs. El objetivo que se persigue al crear funciones es hacer más modular nuestro código, que puede ayudar a la facilidad de la lectura en el código, además de que si una función está correctamente definida, es posible copiarla a otro proyecto y debería funcionar sin problemas. Una función está compuesta de los siguientes elementos:
- **Entradas (argumentos o parámetros):** una función puede recibir múltiples argumentos, o también puede no recibir ninguno. Se pueden definir valores por defecto para hacer que el uso del argumento sea opcional.
- **Cuerpo (instrucciones):** la parte más importante de la función, en que se especifica el proceso que realizará la función.
- **Salida (output):** el resultado de la función, que puede ser una variable de cualquier tipo (incluyendo colecciones). También puede no haber valor de retorno, y la función puede mostrar un mensaje o guardar un archivo en lugar de eso.

La sintaxis para definir una función es la siguiente: 
```r
nombre_funcion <- function(input1, input2, ...) {
	(instrucciones)
	return(output)
}
```

Ejemplo de una función que suma dos números y retorna su resultado
```r
suma_dos_numeros <- function(x, y) {
	suma <- x + y 
	return(suma)
}
```

Para utilizar la función debe llamar a la función utilizando el nombre que le fue asignado y pasarle los parámetros requeridos  en el mismo orden indicado en la definición de la función. Si la función retorna explícitamente un valor, este puede ser almacenado mediante una variable.
```r
valor_suma <- suma(4, 7)
# ahora la variable suma almacenara el valor 11
```
También es posible llamar a las funciones e indicarle los parámetros mediante su nombre. En este caso, da igual el orden de los parámetros ingresados.
```r
valor_suma <- suma(x = 4, y = 7)
valor_suma <- suma(y = 7, x = 4)
```

Podemos también crear una función que tenga argumentos por defecto en caso de que al llamar la función no se ingrese el valor.
```r
# función con pi predefinido a 3.14
perimetro_circunferencia <- function(r, pi = 3.14){
	perimetro <- 2 * pi * r
	cat("El perimetro es", perimetro)
}

perimetro_circunferencia(5)  ## El perimetro es 31.4
```

## Funciones comunes

R proporciona un amplio conjunto de funciones predeterminadas en su librería base, lo que permite realizar operaciones comunes sin tener que implementar nuevas funciones para ello. El relevante recordar que R está diseñado desde su base para trabajar con vectores, por lo que la mayoría de las funciones también funcionan con vectores.
Algunas funciones de las funciones que incluye R son:
- `mean()` calcula el promedio de un vector.
- `median()` calcula la mediana de un vector (el elemento central al ordenar el vector).
- `sum()` calcula la suma de todos los elementos de un vector.
- `max()` calcula el valor máximo entre los números ingresados como parámetros, e igual es posible pasar como argumento un vector.
- `min()` análogo a `max()`, pero para el mínimo.
- `abs()` calcula el valor absoluto del parámetro (igual puede ser un vector).
- `sort()` ordena un vector (se puede cambiar el sentido con el parámetro `decreasing`).

```r
mean(c(3,5,9,0))       ## 4.25
abs(-7)                ## 7
min(c(3,5,9,0))        ## 0
min(3,5,9,0)           ## 0
sqrt(36)               ## 6
sort(c(3, 10, 2, -1))  ## -1  2  3 10
```

---
Anterior: [[Control de Flujo]]
Siguiente: [[Números Aleatorios]]