Las estructuras de control nos permiten añadir flexibilidad a las tareas que se realizan en nuestro código, al hacer posible ejecutar bloques de código de forma condicional o de forma repetitiva.

## Condicionales

### `if-else`
Se evalúa una pregunta **lógica** (condición), y si su resultado es evaluado como verdadero, se ejecuta la acción especificada en el bloque. Adicionalmente, puede especificarse una acción alternativa mediante la instrucción `else`, que se ejecutará si es que la condición indicada en el `if` es evaluada como falsa.
```r
if (condicion) {
	# este bloque se ejecuta si "condición" es evaluada como TRUE
	instructiones
} else {
	# este bloque se ejecuta si "condición" es evaluada como FALSE
	instrucciones
}
```

El uso de `else` es opcional, por lo que se puede tener un bloque que se ejecuta o no simplemente dependiendo de la condición.
```r
if (numero > 10) {
	print("El número es mayor a 10")
}
```

Igual es posible encadenar un nuevo `if` luego del `else`, y con esto se puede lograr bloques condicionales con más de dos "caminos".
```r
if (numero > 0) {
	print("El número es positivo")
} else if (numero < 0) {
	print("El número es negativo")
} else {
	print("El número es 0")
}
```

## Ciclos
Los ciclos o bucles sirven para abordar tareas que son repetitivas, donde la cantidad de veces que se realizará una acción está determinada por alguna variable propia de la operación.

### `while`
Un ciclo `while` tiene como parte de su definición una condición **lógica**, y mientras esta se evalúe como verdadera, el bloque de código asociado al `while` seguirá siendo ejecutado. Dentro del bloque de código debe realizarse alguna operación para afectar la(s) variable(s) que involucran la condición, dado que se necesita que el valor de la condición cambie a `FALSE` para que se pueda terminar el ciclo.

```r
while (condicion) {
	instructiones
}
```

Ejemplo
```r
# aumenta el valor de un número en 2 y lo imprime mientras sea menor a 10
numero <- -3
while (numero < 10) {
	print(numero)
	numero <- numero + 2
}
```

### `for`
El ciclo de tipo `for` está especialmente diseñado para su uso en [[Vectores y Listas|colecciones]]. A diferencia del ciclo de tipo `while`, no hay una condición para determinar su continuidad, sino que simplemente se ejecuta una vez por cada elemento en la colección, y se termina cuando se llega al último elemento. La operación de recorrer una colección mediante un ciclo `for` también es denominada "iterar", y el elemento sobre el cual itera, se llama denomina "iterable".

```r
for (i in iterable) {
  instructiones
}
```

Ejemplo
```r
# vector con los primeros 10 números primos
numeros_primos <- c(1, 3, 5, 7, 11, 13, 17, 19, 23, 29)

# se itera el vector, imprimiendo cada número y multiplicándolos entre sí
mult = 1
for(num in numeros_primos) {
    print(num)
    mult = mult * num
}
print(mult)
```

---
Anterior: [[Vectores y Listas]]
Siguiente: [[Funciones]]