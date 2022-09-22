La librería `dplyr` provee un conjunto de funciones que en algunos casos reemplazan a funciones que existen en R, por lo que en muchos casos no es necesario utilizar las funciones nativas de R.

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

### Selección / renombrado de columnas
Para seleccionar columnas se utiliza la función `select()`, que recibe como primer argumento el dataframe y como siguientes argumentos las columnas. Es posible descartar columnas anteponiendo un signo `-` antes del nombre.
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

### Filtrado de registros


###  Ordenamiento de registros


### Creación / modificación de columnas


### Agrupamiento de datos
