# CURSO DE COMPILADORES
## Integrantes
* NOA LLASCCANOA, Eliazar
## Tema: Proyecto de Compiladores
Este proyecto de la asignatura de compiladores consiste en la implementacion de un compilador completamente funcional en el lenguaje de programacion Python el cual mantine muchas de as caracteristicas de un compilador  como el Lexer y el conjuntod de Token similar a muchos programas. Ademas de manter el tipo de programacion Orientado a Objetos tipado estatico y manejo de memoria.

# Fase del Análisis Léxico

![image](https://user-images.githubusercontent.com/108890838/188966013-5f581d4f-e9b7-467e-932f-36a92cd72ad3.png)

El proyecto de Compilación será recogido y evaluado únicamente a través de Github. Es imprescindible tener una cuenta de Github para cada participante, y que su proyecto esté correctamente alojado en esta plataforma. A continuación le damos las instrucciones mínimas necesarias para ello

## 1.- Lenguaje de Programacion
El Lenguaje de programación a utilizar Python 3.8.10 'https://www.python.org/downloads/'
* Instalar el programa Python del siguiente enlace: 'https://www.python.org/downloads/' 
* Comprobar la versión python –version
* 
![image](https://user-images.githubusercontent.com/108890838/188966547-00965210-0c0f-42f6-a97d-b8e84de1949f.png)

## 2.- Crear Entorno Virtual
1. Instalar Ambiente Virtual

![image](https://user-images.githubusercontent.com/108890838/188967992-1d4dc9e8-112d-4d99-8f33-93ddc54b0bf2.png)

2. Verificar que se instalo Conrrectamente

![image](https://user-images.githubusercontent.com/108890838/188968195-79decc63-1253-422d-b5da-c82516b0e09e.png)

3. Creamos nuestro entorno virtual en una carpeta
Para esto ponemo el comando `python -m venv name_env`

![image](https://user-images.githubusercontent.com/108890838/188968923-32980901-dd03-45fb-939d-5c3acd91398b.png)

4. Activar el entorno virtual

![image](https://user-images.githubusercontent.com/108890838/188969432-3214e89f-3875-4510-964d-f70b96d00ffc.png)

## 3. - Instalar dependencias
### Nose
https://pypi.org/project/nose/

Nose extiende *unittest* para facilitar las pruebas, correr los test.

*unittest* — Marco de pruebas unitarias

Está librería que se requiere instalar nose, para evaluar los test.
En la mayoría de los sistemas tipo UNIX, probablemente necesitará ejecutar
estos comandos como root o usar sudo.

### Mypy
https://pypi.org/project/mypy/

Agregue anotaciones de tipo a sus programas de Python y use mypy
para escribirlos.

Mypy puede detectar muchos errores de programación al analizar su
programa, sin tener que ejecutarlo. Mypy tiene un potente sistema de
tipos con funciones como inferencia de tipos, tipos graduales,
genéricos y tipos de unión.

### Instalar los paquetes o librerias necesarias
* Para esto tenemos que generar una archivo `requirements.txt` dentro de la carpeta seleccionada, donde esta nuetsro entorno virtual
* Luego colocar la siguiente informacion
1   nose==1.3.7
2   mypy==0.782
![image](https://user-images.githubusercontent.com/108890838/188970574-4f9afeeb-ae11-4ccf-85ef-4cee6d69577e.png)

* Luego coloca el siguiente comando para instalar las librerias
`pip3 install -r requirements.txt`
![image](https://user-images.githubusercontent.com/108890838/188973379-66f6754c-200b-4eef-bb3f-c8af481d2946.png)


*   Verificar que esten instalados
![image](https://user-images.githubusercontent.com/108890838/188971339-3db9555e-7f8a-49bd-a802-8a6a4154a7fa.png)

* verifica que funciona nosetests
![image](https://user-images.githubusercontent.com/108890838/188971664-7e390f0f-9f34-4e8a-988a-31de3a99fa08.png)


## 4.- Simbolos para el Token

Enlace al código fuente: 
https://github.com/cayoss777/Compiler

### *Enum*.- Es una enumeración es un conjunto de nombres simbólicos
(miembros) vinculados a valores únicos y constantes. Dentro de una
enumeración, los miembros se pueden comparar por identidad, y la
enumeración en sí se puede iterar.

Este módulo define cuatro clases de enumeración que se pueden usar
para definir conjuntos únicos de nombres y valores: Enum, IntEnum,
Flag, and IntFlag. También define un decorador, unique(), y un
ayudante, auto.

- *class enum.Enum*

Clase base para crear constantes enumeradas. Consulte la
sección API Funcional para obtener una sintaxis de construcción
alternativa.

- *class enum.IntEnum*

Clase base para crear constantes enumeradas que también son
sub clases de int.

- *class enum.IntFlag*

Clase base para crear constantes enumeradas que se pueden
combinar usando los operadores bitwise sin perder su membresía
`IntFlag`. Los miembros de `IntFlag` también son subclases de int.

- *class enum.Flag*

Clase base para crear constantes enumeradas que se pueden
combinar utilizando las operaciones bitwise sin perder su
membresía `Flag`.

- *enum.unique()*

El decorador de clase Enum que garantiza que solo un nombre
esté vinculado a cualquier valor.

- *class enum.auto*

Las instancias se reemplazan con un valor apropiado para los
miembros de Enum. El valor inicial comienza en 1.
**Typing**

Una de las características del lenguaje Python es que el tipado
que usa es dinámico, es decir, permite que una variable pueda
cambiar su tipo durante la ejecución de un programa. La razón es
que los tipos dependen del valor que tenga asignado dicha variable
en un momento dado, no de una propiedad de la variable en sí.

https://docs.python.org/3/library/typing.html

En tiempo de ejecución, Python no impone las anotaciones de
tipado en funciones y variables. Pueden ser utilizadas por
herramientas de terceros como validadores de tipado, IDEs, linters,
etc.

Lista de token, predefinidos por python

https://docs.python.org/es/3/library/token.html

En programación, EOF es un concepto para determinar el final de
un archivo. Muchos lenguajes de programación tienen formas de
detectar el final de archivo como condicionante para la lectura de
un flujo de datos.

https://github.com/python/cpython/blob/3.10/Lib/token.py

## 5.- Paquetes de Python
El archivo __init__.py se utiliza para realizar configuraciones de importación.
Algo que se utiliza mucho en este archivo es la importación de clases,
funciones, etc, para que puedan ser utilizadas en otros paquetes.
El archivo __init__.py es utilizado para inicializar paquetes de Python.

![image](https://user-images.githubusercontent.com/108890838/188976677-1f2e67c5-a27f-42de-abda-999609ca6253.png)


## 6.- Ejecutando python.
¿Qué es el código de bytes en Python?
El código de bytes es una representación independiente de la plataforma de
bajo nivel de su código fuente, sin embargo, no es el código binario de la
máquina y no puede ser ejecutado directamente por la máquina de destino.
De hecho, es un conjunto de instrucciones para una máquina virtual que se
llama Python Virtual Machine (PVM)
__pycache__ es un directorio que contiene archivos de caché de bytecode
que son generados automáticamente por python

Cuando ejecutas un programa en python, el intérprete lo compila primero a
bytecode (esto es una simplificación excesiva) y lo almacena en la carpeta
__pycache__

![image](https://user-images.githubusercontent.com/108890838/188976968-ea7c5260-6d2f-4188-9e09-46ff7eecbcf6.png)


## 7.-Desarrollo guiado por pruebas (Test-driven development)
Desarrollo guiado por pruebas de software, o Test-driven development es una
práctica de ingeniería de software que involucra otras dos prácticas: Escribir
las pruebas primero y Refactorización. Para escribir las pruebas
generalmente se utilizan las pruebas unitarias.

![image](https://user-images.githubusercontent.com/108890838/188976399-3a56cc29-0ac2-4b75-9edf-a8b172ae5a34.png)


Prueba unitaria de Python - función assertEqual ()

assertEqual() en Python es una función de biblioteca de prueba unitaria que se
usa en pruebas unitarias para verificar la igualdad de dos valores. Esta función
tomará tres parámetros como entrada y devolverá un valor booleano
dependiendo de la condición de afirmación. Si ambos valores de entrada son
iguales, assertEqual() devolverá verdadero; de lo contrario, devolverá falso.

Syntax: assertEqual(firstValue, secondValue, message)

Parámetros: assertEqual() acepta tres parámetros que se enumeran a
continuación con una explicación:

firstValue variable de cualquier tipo que se utiliza en la comparación por
función
secondValue: variable de cualquier tipo que se utiliza en la comparación por
función
mensaje: una oración de cadena como un mensaje que se mostró cuando el
caso de prueba falló.

## 6.- Descargar el Repositorio
- descarga del repositorio https://github.com/cayoss777/Compiler todo el archivo
- solo necesitamos PLHL asi que ese es el que copiaremos dentro de nuestra carpeta de trabajo, no dentro del entorno virtual

![image](https://user-images.githubusercontent.com/108890838/188977594-b8d2a115-61ee-4f79-b0b4-1dd9a3ade425.png)

ingresamos para verificar algunos aspectos

`cd PLHL/`

`ll`

salimos de ese directorio a la carpeta de trabajo y colocamos este comando

## 7.- Pruebas Unitarias Para realizar las purbas unitarias escribimos el siguiente comando

``mypy . && py -m unittest discover -p "*_test.py"´´

![image](https://user-images.githubusercontent.com/108890838/188978300-c421628a-fe0c-439a-b6d3-4a815f6d833d.png)

## 8.- Superando los Errores

https://github.com/cayoss777/Compiler/blob/RamaLexica_1/PRUEBAS/lexer_test.py

![image](https://user-images.githubusercontent.com/108890838/188978588-bcd2d787-f65d-4e49-aef8-bebb7cf200ba.png)


![image](https://user-images.githubusercontent.com/108890838/188978673-f8b8ed27-a169-4478-a45c-c062a9886337.png)




