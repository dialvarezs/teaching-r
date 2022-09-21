R es un lenguaje que de base incluye una gran cantidad de funciones típicas ya implementadas y listas para su uso. Sin embargo, es imposible abarcar todos los casos de uso, sobre todo los más específicos. Por esta razón, es que existe un repositorio de paquetes creados por la comunidad llamado [CRAN](https://cran.r-project.org/web/packages/index.html), que son revisados y aprobados por miembros del comité que gestiona el repositorio. Dentro de este repositorio se puede encontrar paquetes para diversas funciones, como producción de gráficos, manipulación de datos de áreas específicas, realización de pruebas estadísticas más específicas, etc. También existe un repositorio especializado en manejo de datos bioinformáticos llamado [Bioconductor](https://www.bioconductor.org/).

La instalación de paquetes de CRAN se puede realizar mediante la interfaz de [[Instalación de R y RStudio|RStudio]], así como también mediante la línea de comandos de R, mediante la función `install.packages()`.
```r
# un paquete
install.packages("dplyr")
# múltiples paquetes
install.packages(c("dplyr", "readxl"))
```

Una vez instalado el paquete, éste quedará disponible para ser utilizado en cualquier programa, y puede ser cargado en el entorno de trabajo actual mediante la función `library()`.

Los paquetes suelen incluir tutoriales de uso, los que son llamados _vignettes_. Se puede acceder a éstos con la función `vignette()` que recibe como primer argumento el nombre de la vignette, la cual abrirá la vignette en el panel de ayuda de RStudio. En algunos casos, el nombre de la vignette puede ser el mismo paquete, y en otros no, por lo que para revisar qué vignettes tiene un paquete puede utilizarse el parámetro `package`.
```r
# revisar las vignettes que tiene el paquete readxl
vignette(package="readxl")

## Vignettes in package ‘readxl’:
## cell-and-column-types             Cell and Column Types (source, html)
## sheet-geometry                    Sheet Geometry (source, html)

# abrir una vignette específica de readxl
vignette("sheet-geometry")
# abrir la vignette de dplyr
vignette("dplyr")
```

Además cabe recordar que se puede buscar la ayuda de cualquier función (incluso de las de paquetes instalados) utilizando el panel "Help" de RStudio, o ejecutando la función precedida de un símbolo de pregunta (`?`).
```r
# cargar ayuda de read.csv
?read.csv
```

---
⬅️ [[Números Aleatorios]]

---