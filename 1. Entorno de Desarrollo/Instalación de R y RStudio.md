RStudio es el entorno de desarrollo más completo que existe actualmente para R, que además de soportar una gran cantidad de características, tiene una interfaz amigable para trabajar con el lenguaje y su ecosistema.

## Instalación de R / RStudio

### R
En primer lugar es necesario instalar R (el lenguaje de programación), ya que el editor no lo trae integrado. La página de descarga de R es [https://cloud.r-project.org/](https://cloud.r-project.org/), donde se pueden encontrar instaladores tanto para Windows como para macOS. En cuanto a Linux, es prácticamente seguro que se encuentra empaquetado en los repositorios de la distribución.
Una vez se haya terminado de instalar R, se puede pasar a instalar RStudio.

### RStudio
Se puede descargar RStudio en [https://www.rstudio.com/products/rstudio/download/#download](https://www.rstudio.com/products/rstudio/download/#download), donde se encuentran los instaladores para todos los sistemas operativos soportados.

## Interfaz de RStudio
La interfaz de RStudio está compuesta por 4 paneles, que se pueden observar en la imagen.
![[rstudio.png]]
Estos paneles corresponden a:
1. **Scripts:** este panel en principio no se encontrará activado, y solamente se abrirá al crear un nuevo archivo. Aquí se encontrarán los archivos abiertos actualmente, que consistirán en los scripts y otros tipos de archivo, además de la visualización de dataframes.
    Dentro de un script el código no es ejecutado hasta que se haga explícitamente, mediante el botón **Run** presente en el panel (se puede seleccionar previamente para ejecutar solo una parte que nos interese). El objetivo de crear scripts es poder organizar nuestro código y tenerlo estructurado en un programa que permita realizar todos los pasos que requiera el proceso que queramos programar, de forma que podamos replicarlo siempre que sea necesario.
    Al crear un script nuevo, este será guardado en un lugar temporal, por lo que es recomendable utilizar la opción de guardar para tenerlo disponible en el lugar que queramos.
2. **Consola:** en este panel se encuentra la consola de R, donde se pueden ejecutar instrucciones de código directamente, que serán evaluadas de forma inmediata. Dentro de este panel se mostrará la salida de todas las instrucciones ejecutadas (también las desde el panel de scripts). También existe una pestaña para abrir una Terminal en el equipo.
3. **Entorno e historial:**
	- Environment: se pueden observar las variables presentes dentro de la sesión de trabajo actual y sus valores. Se puede activar a la visualización de listas y dataframes con el ícono que es como una tabla que sale en las variables de estos tipos.
	- History: registra todos los comandos ejecutados en la consola durante la sesión, para tener acceso a ellos de forma directa
4. **Archivos, gráficos, paquetes y ayuda:**
	- Files: permite navegar a través de los directorios dentro de nuestro equipo y realizar operaciones comunes asociadas. Una opción relevante es "Set As Working Directory" (en la sección More), que establece el directorio actual como la base para la sesión de R, lo que permite utilizarlo como directorio de trabajo para cargar y escribir archivos directamente.
	- Plots: en este panel se muestran los gráficos que se van generando en la sesión, hay opciones para visualizarlos en una ventana más grande, y también exportarlos.
	- Packages: este panel permite visualizar los paquetes instalados y activarlos en la sesión, buscar e instalar paquetes nuevos, y actualizar y/o eliminar paquetes instalados.
	- Help: en este panel puede visualizarse documentación de funciones, que pueden buscarse a través del campo de texto presente en la parte superior del panel.

> [!NOTA]
> Al cerrar y abrir nuevamente RStudio, éste recordará los archivos que teníamos abiertos, incluso los que tengan cambios sin guardar, e incluso guardará todo nuestro espacio de trabajo  (con variables incluídas) si es que seleccionamos la opción **Save** ante la pregunta "*Save workspace image to ...?*" .

---
Anterior: [[Lenguajes de Programación y Editores]]