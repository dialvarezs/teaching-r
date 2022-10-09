La colección [tidyverse](https://www.tidyverse.org/) está compuesta de un conjunto de paquetes diseñados para la manipulación de datos y producción de gráficos, que proveen una alternativa a las funciones que incluye R, pero complementando con más opciones y una sintaxis intuitiva y altamente legible, creando un ecosistema para manipulación y presentación de datos.

![[tidyverse.png]]

Concretamente, estos paquetes son:
- `dplyr`: manipulación (selección, filtro, alteración, ordenamiento y agrupación) de datos en formato dataframe.
- `tidyr`: transformación y organización de datos en formato dataframe.
- `tibble`: provee una implementación alternativa para la implementación de dataframes existente en R.
- `readr`: provee funciones alternativas para cargar archivos de datos tabulados, que generalmente son más rápidas y poseen más opciones que las nativas de R.
- `stringr`: manipulación de variables de tipo `string`.
- `forcats`: manipulación de variables de tipo `factor`.
- `ggplot2`: creación de gráficos.
- `purrr`: interfaz para aplicación de operaciones a datos en formato vectorial (programación funcional).

Es posible instalar cada uno de estos paquetes de forma independiente, o instalar `tidyverse` que los instalará todos. De igual manera, al cargar el paquete en la sesión con `library`, puede especificarse `tidyverse` para cargar todos los paquetes o puede cargarse uno o más de forma individual.

---
⬅️ [[Introducción a los DataFrames]]  /  ➡️ [[Manipulación de dataframes con dplyr]]

---
