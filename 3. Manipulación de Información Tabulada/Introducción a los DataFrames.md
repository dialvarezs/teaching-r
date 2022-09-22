Los dataframes son una estructura de R que puede almacenar datos en una estructura que representa una tabla de datos compuesta por variables y registros. Las variables corresponden a las columnas, donde cada una tiene un tipo de dato, mientras que los registros corresponden a las filas.

RStudio provee soporte para visualización de dataframes como tabla, mediante un botón que se puede encontrar  en el panel de variables, el cual abre una vista en el panel de archivos abiertos.
![[rstudio_open_dataframe.png]]

## Creación de dataframes

### Creación a partir vectores ya definidos
Se puede crear un dataframe mediante la función `data.frame()`, pasando como argumento las columnas y los vectores con los datos de éstas (todos los vectores deben ser del mismo tamaño).
```r
nombres <- c("Pedro", "Pablo", "Mariana")
edades <- c(21, 22, 30)
ciudades <- c("Punta Arenas", "Puerto Natales", "Santiago")

personas <- data.frame(nombre=nombres, edad=edades, ciudad=ciudades)

##    nombre edad         ciudad
## 1   Pedro   21   Punta Arenas
## 2   Pablo   22 Puerto Natales
## 3 Mariana   30       Santiago
```

### Carga de dataframes desde archivos
Es común que queramos cargar datos que estén en algún archivo externo, comúnmente una planilla de Microsoft Excel o un formato similar.
En R es posible cargar una tabla desde un archivo delimitado mediante la función `read.table()`, que recibe múltiples parámetros para controlar cómo cargar la tabla. Existen además funciones derivadas de esta como `read.csv()` que viene preconfigurada para cargar archivos tipo CSV (delimitados por comas) y `read.delim()` para cargar archivos TSV.
```r
# cargar un CSV (delimitado por comas)
df <- read.csv("mis_datos.csv")
# cargar un TSV (delimitado por tabulaciones)
df <- read.delim("mis_datos.tsv")
# cargar un archivo tabulado delimitado por ;
df <- read.table("mis_datos.csv", sep=";")
```

R no soporta nativamente la carga de archivos tipo Excel, pero se puede instalar el paquete `readxl` para este propósito.  Este paquete provee la función `read_excel()`, que permite seleccionar la hoja deseada o incluso el rango de filas o columnas a cargar desde el archivo.
```r
# instalar readxl (sólo es necesario una vez)
install.packages("readxl")
# cargar reaxl (una vez por cada sesión)
library(readxl)
# cargar un excel, por defecto toma la primera hoja
df <- read_excel("datos_diciembre_2022.xlsx")
# cargar una hoja y un rango de celdas específicos
df <- read_excel("datos_2022.xlsx", sheet = "Junio", range = "B3:D87")
```


## Manipulación de dataframes
En gran parte los dataframes se comportan como listas, pero poseen ciertas funciones asociadas específicamente. Algunas operaciones comunes son
```r
colnames(df)  # nombres de columnas
rownames(df)  # nombres de filas
nrow(df)      # número de filas
```

### Selección de datos en dataframes
Los dataframes internamente son listas de vectores, por lo que se pueden utilizar las mismas operaciones que se utilizarían para esa estructura.
```r
# obtener una columna del dataframe mediante su nombre
personas$edad
# obtener una columna mediante su posición
personas[[1]]
# obtener la primera ciudad
personas$ciudad[1]
```

Adicionalmente, los dataframes permiten hacer filtros en columnas y filas de forma simultánea mediante la notación  `df[x, y]`, donde `x` se utiliza para filtrar filas e `y` para las columnas. Ambas componentes pueden ser cualquiera de las formas utilizadas para filtrar vector (un valor numérico, un vector de valores numéricos, o una condición), y dado que las columnas tienen nombre, se puede utilizar un vector con sus nombres para seleccionarlas. Se puede omitir cualquiera de los dos filtros dejando vacía la sección.
```r
# primera fila del dataframe
df[1, ]
# columas nombre y edad
df[, c("nombre", "edad")]
# filas de registros con ciudad "Santiago"
df[df$ciudad == "Santiago", ]
# filtrar por edad y luego seleccionar nombre y ciudad
df[df$edad > 21, c("nombre", "ciudad")]
```

### Manipulación de columnas de un dataframe
Es posible crear nuevas columnas en un dataframe mediante un valor constante o un vector (que puede ser el resultado de operaciones que involucren otras columnas del dataframe). Al momento de asignarla debe indicarse el nombre de esta nueva columna. Igual es posible eliminar una columna del dataframe asignándole `NULL`.
```r
# nueva columna con un valor fijo
df$habilitado <- TRUE
# nueva columna a partir de un vector externo (debe ser del mismo tamaño)
df$altura <- c(1.81, 1.77, 1.60)
# nueva column a partir de las columnas ya existentes
df$z <- df$x + df$y / 2
# elminar la columna edad
df$edad <- NULL
```

Es posible realizar más operaciones con dataframe (como ordenar o aplicar filtros más avanzados), pero para este tipo de operaciones haremos uso de las librerías de la colección `tidyverse`, que proveen una sintaxis más sencilla y flexible para manipular los datos.

---
➡️ [[La colección tidyverse]]

---
