El paquete `dplyr` provee un conjunto de funciones que en algunos casos reemplazan a funciones que existen en R, por lo que en muchos casos no es necesario utilizar las funciones nativas de R.

### Consideraciones generales
Algo relevante de destacar es que al indicar una columna a una función de  `dplyr`, esta debe indicarse como si se tratara de una variable (aunque no esté definida explícitamente).
```r
# mal: pasar la columna como string
select(df, "nombre")
# bien: pasar la columna como si fuese una variable
select(df, nombre)
```

Otra consideración importante al trabajar con `dplyr` (y `tidyverse` en general), es que se añade un nuevo operador: `%>%`. Este operador permite aplicar operaciones directamente sobre la salida de otras (sin la necesidad de asignar variables intermedias), permitiendo "encadenar" las distintas funciones para lograr el resultado requerido. Concretamente, este operador pasa el resultado de la operación anterior como primer argumento de la siguiente función.
Es recomendable cambiar de línea al utilizar este operador, ya que ayuda a entender mejor cómo se realiza el proceso.
```r
# seleccionar columnas utilizando la función directamente
subset_df <- select(df, nombre, apellido, edad)

# ahora utilizando el operador %>%
subset_df <- df %>%
	select(nombre, apellido, edad)

# ...y aplicando un filtro por edad
filtered_df <- df %>%
	select(nombre, apellido, edad) %>%
	filter(edad >= 18)
```

### Seleccionar / renombrar columnas
Para seleccionar columnas se utiliza la función `select()`, que recibe como argumentos las columnas. Es posible descartar columnas anteponiendo un signo `-` antes del nombre.
```r
# selección de columnas
df %>%
	select(nombre, apellido, edad)
# decarte de columnas
df %>%
	select(-direccion, -telefono)
```
Para renombrar columnas se puede utilizar la función `rename()`, en la cual se pueden indicar mediante la sintaxis `nuevo_nombre = viejo_nombre` las columnas a renombrar.
```r
# renombrar "name" a "nombre" y "age" a "edad"
df %>%
	rename(nombre = name, edad = age)
```

### Filtrar registros
Para seleccionar solamente aquellas filas que cumplan una condición determinada se utiliza la función  `filter()`, a la cual se le indica la columna que se desea filtrar y la condición. Se puede indicar más de una columna en la función para así realizar múltiples filtros a nuestro dataframe.
```r
df %>%
    filter(nombre == "Juan")

df %>%
    filter(edad >= 29 & edad <= 50)

df %>%
    filter(nombre == "Juan", edad >= 29)
```

También se puede realizar filtros utilizando vectores en la condición:.
```r
df %>%
    filter(nombre %in% c("Juan", "María", "Constanza", "José"))

selected_names <-  c("Juan", "María", "Constanza", "José")
df %>%
	filter(nombre %in% selected_names)
```

Se puede utilizar el operador `is.na()` para solo mantener aquellas filas que tengan valores en determinadas columnas
```r
# elimina registros que no tienen el dato de edad
df %>%
	filter(!is.na(edad))
```

### Ordenar registros
Para reordenar las filas en base a los valores de columnas se utiliza con la función `arrange()`. Se puede indicar a la función más de una columna, y por defecto se ordenarán las filas por orden ascendente, en caso de querer un orden descendente se debe anteponer `-` al nombre. Al indicar múltiples condiciones para ordenar, serán evaluadas en el orden en el que se indiquen.
```r
# descendente por edad y luego ascendente por nombre
df %>%
	arrange(-edad, apellido)
```

### Crear / modificar columnas
Se puede crear o modificar columnas con la función `mutate()`. Estas nuevas columnas pueden generarse a partir de la información presente en otras columnas del dataframe.

```r
# nueva columna IMC de tipo numérica
df %>%
	mutate(IMC = peso / (estatura ** 2))

# nueva columna mayor_de_edad de tipo lógico
# si la edad es mayor a 18, entonces el valor es TRUE, de lo contrario es FALSE
df %>% 
	mutate(mayor_de_edad = edad >= 18)
```

Se pueden también crear múltiples columnas al mismo tiempo, incluso teniendo la posibilidad de definir columnas basadas en una columna que se declaró previamente en la misma operación.
```r
# al declarar IMC dentro del mutate, podemos utilizarla para
# calcular IMC_normal y obesidad
df %>%
	mutate(
	     IMC = (peso / (estatura ** 2),
	     IMC_normal = IMC >= 18.5 & IMC <= 24.9,
	     obesidad = IMC >= 30
	)
```

### Agrupar datos y generar variables resumen
Se pueden agrupar las filas dependiendo de sus valores específicos en determinadas columnas y realizar operaciones sobre estos grupos. Por ejemplo, se puede utilizar la función `count()` para contar el número de registros por grupo (que se encarga automáticamente de armar los grupos y obtener el resultado).
```r
# el resultado es una columna con la edad y
# otra columna indicando cuántos registros habían para cada edad
df %>%
	count(edad)
```

Se puede también hacer agrupaciones múltiples, incluyendo dos o más columnas en la función `count()`.
```r
df %>%
	count(edad, ciudad)
```

El ejemplo anterior retornará la cantidad de personas que posean un IMC y ciudad determinada, por ejemplo:
```r
edad  ciudad                n
16    Punta Arenas          2
16    Puerto Natales        3
16    Puerto Williams       1
18    Punta Arenas          20
18    Puerto Williams       7
20    Puerto Natales        47
20    Puerto Williams       16
20    Santiago              12
23    Santiago              5
```

De forma más general, se puede utilizar la función `group_by()`, la cual genera los grupos de registros en base a las columnas indicadas en los argumentos. Posterior a esto, se pueden calcular valores que resuman las filas utilizando funciones que permitan generar un único valor como resultado (por ejemplo `n()`, `mean()`, `min()`, `max()`). Para esto, existen dos opciones:
- Utilizar `mutate()`, lo cual añadirá las columnas indicadas al dataframe, pero conservando su estructura original.
	```r
	# conserva todas las filas y columnas existentes, añadiendo
	# dos nuevas columnas con los valores de edad mínimo y máximo
	# del grupo al que pertenece la fila
	df %>%
		group_by(ciudad, edad) %>%
		mutate(
			edad_min = min(edad),
			edad_max = max(edad)
		)
	```
- Utilizar `summarise()`, que conservará solamente las columnas que definen los grupos y una fila por cada grupo, agregando las columnas indicadas a la función.
	```r
	# sólo conserva una fila por cada grupo, con las columnas de resumen
	df %>%
		group_by(ciudad, edad) %>%
		summarise(
			edad_min = min(edad),
			edad_max = max(edad)
		)
	```
	
Usar `mutate()` o `summarise()` dependerá de qué es lo que queremos lograr: si añadir información a lo ya existente, o generar un resumen de la información, respectivamente.