Las funciones son bloques de código que contienen un conjunto de instrucciones que convierte inputs en outputs. La creación de funciones permite reutilizar código de manera simple y elegante. Las funciones pueden estar compuestas de los siguientes elementos:
- **Inputs (argumentos o parámetros):** Una función puede no recibir ningún argumento, como también puede recibir múltiples argumentos. Se pueden definir valores por defecto en caso de inputs no requeridos.
- - **Cuerpo (instrucciones):** Son el conjunto de instrucciones que transforman las entradas en las salidas.
- **Salida (output):** Son el resultado de la función, puede ser un número, una lista, un mensaje o el objeto que se desee. Podemos almacenar el resultado en una variable para utilizarla más adelante

La estructura básica de una función es la siguiente: 
```r
nombre_funcion <- function(input1, input2, ...)
{
	(instrucciones)
	return(output)
}
```

Ejemplo de una función que suma dos números y retorna su resultado
```r
suma_dos_numeros <- function(x, y)
{
	suma <- x + y 
	return(suma)
}
```

Para utilizar la función debe llamar a la función utilizando el nombre que se le asignó y pasarle los argumentos requeridos. Los parámetros deben ser pasados en el mismo orden indicado en la definición de la función:
```r
valor_suma <- suma(4,7)
## Ahora la variable suma almacenara el valor 11.
```
También se puede llamar a las funciones e indicarle los parámetros mediante su nombre. En este caso, da igual el orden de los parámetros ingresados.
```r
valor_suma <- suma(x=4,y=7)
valor_suma <- suma(y=7,x=4)
```

Podemos también crear una función que tenga argumentos por defecto en caso de que al llamar la función no se ingrese el valor.
```r
perimetro_circunferencia <- function(r,pi=3.14){
	perimetro <- 2*pi*r
	cat("El perimetro es", perimetro)
}

perimetro_circunferencia(5)
##Imprimira "El perimetro es 31.4"
```

R proporciona un amplio conjunto de funciones y constantes predeterminadas, por lo que aquellas funciones matemáticas o estadísticas ya se encuentran desarrolladas y no es necesario crearlas.
Algunas funciones que tiene incluído R:
- **mean:** Calcula el promedio del vector.
- **median:** Ordena el vector y retorna el valor que se encuentra en el centro.
- **sum:** Suma los elementos del vector argumento.
- **max:** Retorna el valor máximo entre los números ingresados como parámetros. Se puede también pasar un vector como argumento.
- **min:** Retorna el valor mínimo entre los números ingresados como parámetros. Se puede también pasar un vector como argumento.
- **abs:** Retorna el valor absoluto del número pasado como parámetro.

```r
mean(c(3,5,9,0)) ## 4.25
abs(-7)          ## 7
min(c(3,5,9,0))  ## 0
min(3,5,9,0)     ## 0
sqrt(36)         ## 6
```

También podemos encontrar constantes definidas, como el valor de pi, por lo cual no sería necesario definirlo como en el ejemplo de más arriba y podría solamente utilizarse

```r
perimetro_circunferencia <- function(r){
	perimetro <- 2*pi*r
	cat("El perimetro es", perimetro)
} ## La función esta utilizando el valor de pi definido por el sistema.

print(pi) ##3.141593

perimetro_circunferencia(5)
##Imprimira "El perimetro es 31.41593"
```

