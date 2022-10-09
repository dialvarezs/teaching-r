El paquete `tidyr` también es parte de `tidyverse`, y tiene funciones que se centran principalmente en la "limpieza" y transformación de datos en un dataframe.

### Reestructuración de datos
Dependiendo del origen de un conjunto de datos, éste puede estar en formato "largo" o "ancho".
En el formato largo cada columna es una variable y cada fila es una observación. En cambio, en el formato ancho cada fila es un registro completo, y las columnas normalmente son las variables.
![[wide_vs_long.png]]

Dependiendo el uso que se le quiera dar al dataframe puede ser necesario cambiar entre una y otra representación. Por ejemplo, para graficar con `ggplot2` es necesario que el conjunto de datos se encuentre en formato largo, pero para visualizar el conjunto de datos seguramente es más conveniente tener un formato ancho. Además, algunas operaciones de manipulación de datos pueden ser más fáciles de realizar en un formato que en otro.

#### Ancho a largo
Para pasar del formato ancho al largo, se utiliza la función `pivot_longer()`, donde los parámetros relevantes son:
- `cols`: la selección de columnas a la cual se aplicará la operación (o también se pueden excluir las columnas que se quieren conservar en su forma actual).
- `names_to`: el nombre que tendrá la columna que contendrá los nombres de las columnas que se pasaron a formato largo.
- `values_to`: el nombre de la columna que contendrá los valores.
Existen otros parámetros adicionales que pueden ayudar en ciertos casos más específicos.
```r
# suponiendo que data_wide contiene datos de ventas mensuales,
# en cada fila un año y en cada columna cada mes
data_long <- data_wide %>%
	pivot_longer(cols=-año, names_to="mes", values_to="ventas")
# el resultado será un dataframe con 3 columnas: año, mes y ventas,
# con cada fila representando las ventas de un mes
```

#### Largo a ancho
Para pasar de formato largo a ancho, se utiliza la función `pivot_wider()`, cuyos parámetros más relevantes son:
- `id_cols`: columna(s) que contienen los campos que pueden considerarse ID, es decir, columnas que se mantendrán de la misma manera en la que están representadas.
- `names_from`: columna que contiene los nombres de las variables que serán expandidas a columnas.
- `values_from`: columna que contiene los valores asociados a las variables.
```r
# suponiendo que data_long contiene datos de inventario que están separados
# por bodega (5 bodegas diferentes), el dataframe tiene las columnas
# id, nombre, bodega, cantidad
data_wide <- data_long %>%
	pivot_wider(id_cols=c(id, nombre), names_from=bodega, values_from=cantidad)
# el resultado será un dataframe con las columnas
# id, nombre, bodega1, bodega2, etc
```

### Manejo de valores nulos
Algunas funciones que provee `tidyr` para tratar con valores nulos son:
- `drop_na()`: elimina filas que tengan valores nulos. Es posible especificar una o más columnas para aplicar la condición únicamente a ellas.
	```r
	# elimina filas que tengan NA en cualquiera de las columnas
	data %>%
		drop_na()
	# elimina filas que tengan NA en edad y género
	data %>%
		drop_na(c(edad, genero))
	```
- `replace_na()`: reemplaza los valores nulos con valores especificados. Recibe como argumento una lista indicando los nombres de las columnas y los valores que aplicarán en cada una de ellas.
	```r
	# reemplaza los NA en examenes_realizados por 0, y en contacto por "deconocido"
	data %>%
		replace_na(list(examanes_realizados = 0, contacto = "desconocido"))
	```

### Unión / separación de columnas
En algunos casos ciertas columnas pueden contener información que podría ser relevante separador (por ejemplo `<dia> / <mes> / <año>`). Para estos casos se puede utilizar la función `separate`, cuyos argumentos más importantes son:
- `col`: nombre de la columna a separar.
- `into`: nombres de las columnas que se generarán a partir de la separación.
- `sep`: carácter que se utilizará para separar la columna.
```r
# la columna fecha tiene formato dd/mm/aaaa, y se separará en día, mes y año
data %>%
	separate(col=fecha, into=c("dia", "mes", "año"), sep="/")
```

Análogamente, existe la función `unite()` que combina múltiples columnas en una.
```r
# combinar dia, mes y año a fecha
data %>%
	unite("fecha", c(dia, mes, año), sep="/")
```

---
⬅️ [[Manipulación de dataframes con dplyr]]

---
