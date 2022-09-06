CURSO DE COMPILADORES
integrantes
NOA LLASCCANOA, Eliazar
Tema: Crear un compilador 
Para describir el sonido con métodos simples de Machine Learning se hará uso de una API "Freesound" para cargar descriptores de sonido precomputados y desarrollar agrupación y clasificación de sonidos.

Este tema consistirá en cuatro partes: 1) Descarga de sonidos y descriptores desde Freesound , 2) Seleccionar dos descriptores para una buena agrupación de sonido, 3) Agrupar sonidos usando k-means , y 4) Clasificar sonidos usando k-NN .

Conceptos Relevantes
API de sonido libre
Con la API de Freesound podremos navegar, buscar y recuperar información desde Freesound . Nosotros tambien podemos desarrollar consultas avanzadas combinando contenido de analisis de caracteristicas otros metadatos (etiquetas, etc...). Con la API podemos hacer una búsqueda de texto similar a como hacemos en buscador avanzado en el sitio https://freesound.org/search/?q , excepto implementar las consultas en software.

Descriptores de sonido
En este ejercicio, usaremos descriptores de sonidos que han sido pre-computados con Essentia , https://essentia.upf.edu y son almacenados en la base de datos de Freesound junto con el sonido correspondiente. Muchos descriptores de sonidos pueden ser extraidos usando Essentia y en Freesound, un numero de ellos son usados.

Distancia euclidiana
La distancia Euclidiana es la distancia de una linea recta entre dos puntos en un espacio n-dimensional, asi la distancia entre dos puntosyes la longitud del segmento de linea que los conecta. Siyson dos puntos en el n-espacio Euclidiano, luego la distancia,, desdea, o desdeaeste dado por la formula de pitagoras:


Agrupamiento k-means (k-means)
El agrupamiento k-means es un metodo de cuantificacion vectorial que es popular en el analisis de agrupamiento en la mineria de datos. el agrupamiento k-means tiene como objetivo dividir enobservaciones dentro degrupos en el cual cada observación pertenece a un grupo con el significado más cercano, sirviendo como un prototipo de grupos. el problema es computacionalmente dificil (NP-hard), sin embargo, los algoritmos euristicos eficientes convergen rapidamente al optimo local.

Dado un conjunto de observaciones, donde cada observacion es un vector real d-dimesional, el agrupamiento k-means tiene como dividir objetivo lasobservaciones esconjuntosasi minimizar la suma de cuadrados de los clusters internos, el objetivo es encontrar:

 
  
 
, dondees el significado de los puntos.

desarrollo del ejercicio
Parte 1: Descarga de sonidos y descriptores desde Freesound
Descarga una colección de sonidos de instrumentos y sus descriptores desde Freesound unsando la API Freesound.

Primero.- DEBEMOS obtener una llave de la API Freesound (Freesound API key) para hacer uso de esta. En caso de que no tengamos una cuenta de Freesound debemos crear uno, para ello ingresamos al siguiente enlace https://www.freesound.org/apiv2/apply/ . Una vez creada una cuenta ingresamos nuevamente al enlace anterior, si es la primera vez que hacemos uso de esta API, nos pedirá generar una clave API para lo cual nos pedirá ciertos datos del proyecto en el cual estamos trabajando. Cumplido con lo pedido se generara la clave API .

Segundo.- Dentro del directorio (nuestro espacio de trabajo) en el cual se encuentra nuestro cuaderno "00.Sound-and-music-description.ipynb" creamos dos directorios con los nombres testDownloady oneSoundpara almacenar los sonidos y descriptores.

Tercero.- En seguida debemos instalar el cliente python para Freesound API. Parra ello debemos clonar el repositorio https://github.com/MTG/freesound-python , dentro de nuestro espacio de trabajo. Al clonar el repositorio, dentro de nuestro espacio de trabajo se creara un directorio freesound-pytho. La estructura de nuestro espacio de trabajo será la siguiente:

 |-- workspace (nuestro espacio de trabajo)
    |-- 0.0Sound-and-music-description.ipynb
    |-- testDownload/
    |-- oneSound/
    |-- freesound-python/
Cuarto.- Ingresamos dentro de la carpeta freesound-pythony ejecutamos el siguiente comando.

$ python setup.py instalar

El comando anterior instalara todas las dependencias de freesound dentro de nuestro ambiente.

Quinto.- Ahora ya podremos hacer llamado a la función download-sounds-freesound()el cual tiene los siguientes parámetros:

queryText(string): Es una palabra simple una cadena de palabras sin espacios (hacer uso de guiones), es tipicamente el nombre del instrumento de cual se quiere obtener el sonido. Ejemplo (ej. "violín", "trompeta", "violonchelo", "fagot", etc.)
tag(string): Etiqueta para ser usado en el filtrado del sonido buscado. Ejemplo ("multimuestra", "nota simple", "velocidad", "tenuto", etc.)
duration(tupla de 2 numeros de punto flotante): minimo y maxima duracion (segundos) del sonido para filtrar. Ejemplo (0.2, 15).
API_Key(string): nuestra API key el cual fue optenido de https://freesound.org/apiv2/apply/ y tiene la siguiente estructura "7nCLWEwre4wsjWbZ0wDrersMCey48M7bj128cX3s"
outputDir(string): Ruta del directorio donde queremos que se almacene los sonidos y sus descriptores descargados, esta ruta puede ser absoluta o relativa; ser recomienda una ruta relativa respecto a nuestro espacio de trabajo en este caso podran ser ./testDownload o ./oneSound
topNResults(entero): Numero de resultados (sonidos) que queremos descargar el instrumento elegido.
featureExt(extensión de archivo): Extensión de archivo para los sonidos y descriptores almacenados (.json) generalmente usado.
Para llamar a la download_sound_freesound()funcion tendremos que elegir el queryText, tag, y duracion, para que nos retorne una nota singular de los sonidos del instrumento. Los 20 primeros resultados del query deben ser "buenos". Notar que tag puede estar vacío. Por ejemplo para obtener una nota singular de un violín podemos ejecutar la función de la siguiente menera:

download_sound_freesound(queryText="violin", API_Key=<tu key>, outputDir="./testDownload", topNResults=20, duration=(0, 8.5), tag="single-note")

Lo anterior retornara 20 notas sigulares de sonidos de violin y los scripts son almacenados en la ruta ./testDownload. Para este ejercicio debemos descargar 3 sonidos, para ello podemos elegir algunos de estos instrumentos (violín, guitarra, fagot, trompeta, clarinete, violonchelo, naobo).

Parte 2:Seleccione dos descriptores para un buen agrupamiento de sonido
Primero.- Instalamos dependencias que nos permitirán graficar con python, para ello instalamos las bibliotecas en nuestro ambiente virtual:

entumecido
matplotlib
espía
$ conda install numpy=1.21 matplotlib scipy

Segundo.- Para el uso de los módulos haremos uso del directorio testDownload, el cual le pasaremos como argumento del parámetro (inputDir) y el par de índices del descriptor (descInput). Asegurarnos que solo debe haber 3 sonidos de instrumentos dentro del directorio testDownload.

Tercero.- Eleccion de un buen par de descriptores para los sonidos que fueron descargados en parte 1. Un buen par de descriptores conduce a puntos de distribucion donde todos los sonidos de un instrumento se agrupan juntos, con una buena separacion de los otros agrupamientos de instrumentos Intentar diferentes combinaciones de pares de descriptores.

Cuarto.- Dentro del codigo modificamos las variables inputDiry descInput, segun la ruta de nuestro directorio donde se encuentran los sonidos descargados, y las el par de conbinaciones de descriptores respectivamente.

inputDir = "./testDownload"

descInput = (3, 6)

Quinto.- Analizar la grafica y ver con que par de descriptores se genera un mejor agrupamiento de los sonidos.
