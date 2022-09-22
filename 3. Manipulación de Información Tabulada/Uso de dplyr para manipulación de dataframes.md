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
    filter(nombre %in% c("Juan","María","Constanza","José"))

selected_names <-  c("Juan","María","Constanza","José")
df %>%
    filter(nombre %in% selected_names)
```

Se puede utilizar el operador `is.na()` para solo mantener aquellas filas que tengan valores en determinadas columnas
```r
df %>%
    filter( !is.na(edad))
```
###  Ordenamiento de registros
Para reordenar las filas en base a los valores de columnas se utiliza con la función `arrange()`. Se puede indicar a la función más de una columna, y por defecto, ordenará las filas por orden ascendente, en caso de querer un orden descendente se antepone el símbolo `-`.
```r
df %>%
    arrange(apellido, -edad)
```

### Creación / modificación de columnas
Se puede crear o modificar columnas con la función `mutate()`. Estas nuevas columnas pueden generarse a partir de la información presente en otras columnas del dataframe.

```r
df %>%
     mutate(IMC = (peso/(estatura**2))
```
Se puede también generar nuevas columnas en base a operadores lógicos.
```r
df %>% 
     mutate(mayor_de_edad = edad>=18)
```

En el ejemplo anterior se creará una nueva columna llamada `mayor_de_edad`, los valores de esta columna estarán dados por la condición `edad>=18`, es decir, en caso de que la edad sea mayor o igual a 18, la nueva columna tendrá un valor de `TRUE`, en el caso contrario, tendrá un valor `FALSE`.

Se pueden también encadenar varias expresiones en una misma sentencia, es decir, crear una nueva columna y utilizar la nueva columna para modificar o crear otra variable.
```r
df %>%
     mutate(IMC = (peso/(estatura**2), imc_normal = IMC >= 18.5 & IMC <= 24.9, obesidad = IMC >= 30)
```

### Agrupamiento de datos
Se pueden agrupar las filas dependiendo de sus valores específicos en determinadas columnas y realizar un conteo de estos con la función `count()`.
```r
df %>%
	count(edad)
```
El ejemplo anterior retornará un conteo de la cantidad de personas por edad presentes en el dataframe.

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