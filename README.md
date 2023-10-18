# Creación de reportes reproducibles con Quarto
Un tutorial para la edición 2023 de [LatinR](https://latin-r.com/) a cargo de [Riva Quiroga](https://rivaquiroga.cl/).

## Descripción general
En este tutorial se hará una introducción a [Quarto](https://quarto.org/), un sistema de publicación científica y técnica que permite crear contenido dinámico usando R, Python, Julia y Observable. Durante la sesión se abordarán los aspectos generales de su uso para crear reportes con R, con especial énfasis en el trabajo en formato HTML. Para ello, se mostrará paso a paso cómo crear un reporte reproducible, cómo parametrizar su contenido, cómo editar su apariencia y cómo publicarlo utilizando GitHub Pages y Netlify.

Para poder seguir sin problema las actividades del tutorial, es necesario tener algún grado de experiencia con el operador “pipe” (en cualquiera de sus dos versiones: `%>%`o `|>`), con las funciones principales del paquete dplyr (como `filter`, `summarize` y `group_by`) y con el paquete ggplot2 (por ejemplo, tener una idea general de qué hacen las funciones `geom_*` o saber cómo modificar la escala del eje “y” de un gráfico). Para quienes tengan interés en la publicación de un reporte utilizando el servicio GitHub Pages, es necesario tener al menos un manejo inicial de git (saber cómo hacer commits y enviar cambios a un repositorio personal). De todos modos, se mostrarán otras alternativas para publicar un reporte.

## Preparación: ¿qué necesito tener instalado?

### Lo imprescindible

- La última versión estable de [Quarto (1.3.450)](https://quarto.org/docs/get-started/). 
- Una versión reciente de [R](https://cran.r-project.org/) (la más actual es 4.3.1).
- Una versión reciente de [RStudio](https://posit.co/download/rstudio-desktop/) (la más actual es 2023.09). Si bien es posible utilizar Quarto desde otros entornos de desarrollo como VS Code o desde un editor de texto, en el tutorial mostraremos las distintas opciones que nos entrega RStudio para trabajar con este formato.
- Los siguientes paquetes (todos están disponibles en CRAN, es decir, se pueden instalar con la función `install.pacakges`): **here**, **tidyverse**, **gt** y **datos**.
- Y algunos paquetes más: **gghighlight**, **ggsci**.

### Lo opcional
- Una cuenta en [Netlify](https://www.netlify.com/). Si bien es posible publicar un reporte en ese servicio sin crearse una cuenta, tenerla nos permite acceder a funcionalidades como editar la url de nuestro reporte o actualizar su contenido.

### Más opcional aún
- Si bien para las actividades que realizaremos durante el tutorial no es extrictamente necesario, para funcionalidades un poco más avanzadas de Quarto es útil saber cómo utilizar la línea de comandos (a la que a veces también se hace referencia como _terminal_, _bash_, _shell_, aunque no son exactamente lo mismo). Si usas Linux o Mac, ya tienes Bash instalado. Si usas una versión reciente de Windows, deberías tener Power Shell. Menciono esto acá como opcional, porque en un momento del tutorial usaré el terminal solo de forma demostrativa para ilustrar algunas funcionalidades que pueden seguir explorando en el futuro. 
  
### Solo si ya utilizas Git
- Git + una cuenta en GitHub conectada con tu computadora. Al finalizar la sesión mostraremos que es posible publicar nuestros reportes utilizando el servicio GitHub Pages. Esta parte del tutorial será una demostración de cómo puede hacerse y quedará un video para quienes quiera explorar esta opción en el futuro. Mostraremos otras dos opciones para compartir nuestros reportes que no requieren Git, así que si nunca lo has utilizado, no te preocupes. 

## Durante el tutorial

### Estructura de nuestro directorio de trabajo

El directorio de en que iremos guardando los materiales de la sesión tendrá cuatro subcarpetas: una para el código, otra para los datos, otra para figuras y otra para los reportes. Todo el código que escribamos asumirá esa estructura de carpetas (y que no se usó tilde en el nombre de la carpeta para el código). Para mantener todo en orden, convertiremos nuestro directorio de trabajo en un "proyecto" de RStudio. Crearemos esta estructura de carpetas durante la sesión, así que no es necesario que lo hagas con anticipación.

```
📂 tutorial-quarto-latinr
    |
    |-- 📁 codigo
    |-- 📁 datos
    |-- 📁 figuras
    |-- 📁 reportes
    |-- 🔵 tutorial-quarto-latinr.Rproj
```

### Enlaces y otros materiales que utilizaremos durante la sesión

Durante la sesión descargaremos cuatro archivos que nos van a servir para ilustrar algunas funcionalidades de Quarto. A continuación encontrarás los enlaces de descarga:

- 📄 un script de ejemplo: [01_procesamiento-datos.R](https://www.dropbox.com/scl/fi/1gduq3ayew0prshjehpb0/01_procesamiento-datos.R?rlkey=wkij0umzywopu4tgx1u4l3mlp&dl=0) 
- 📄 un set de datos de ejemplo: [desarrollo-sudamerica.csv](https://www.dropbox.com/scl/fi/j6ulgn05xmh9dpv78bt6l/desarrollo-sudamerica.csv?rlkey=4s0jyh1q9819vi0rys922iqo9&dl=0)
- 📄 los datos para la primera versión del reporte: [datos-reporte.csv](https://www.dropbox.com/scl/fi/hc2h0waaifcbv7vovb7g3/datos-reporte.csv?rlkey=phn9qw3j50e753l6vufmfwh6a&dl=0)
- 📄 los datos para la segunda versión: [datos-reporte-actualizados.csv](https://www.dropbox.com/scl/fi/ibddb3jhuwja71kp57uy1/datos-reporte-actualizados.csv?rlkey=259uk0aodq0t5tzayoor3kv23&dl=0)

El primero lo guardaremos en nuestro en la carpeta de código y los otros tres en la carpeta de datos.

```
📂 tutorial-quarto-latinr
    |
    |-- 📁 codigo
        |-- 📄 01_procesamiento-datos.R 
    |-- 📁 datos
        |-- 📄 desarrollo-sudamerica.csv
        |-- 📄 datos-reporte.csv
        |-- 📄 datos-reporte-actualizados.csv
    |-- 📁 figuras
    |-- 📁 reportes
    |-- 🔵 tutorial-quarto-latinr.Rproj
```


## Para el futuro: recursos y materiales complementarios

Esta sección la completaremos a partir de las preguntas que vayan anotando en nuestro [documento compartido](https://docs.google.com/document/d/1aG-ssbPPIe3HryaVlW2-ZPgbY1k1kjJ1N-_yf8I5C8w/edit?usp=sharing).
