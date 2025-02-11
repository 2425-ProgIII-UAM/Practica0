# Práctica 0

EL objetivo de esta práctica es proporcionar una primera aproximación a la programación concurrente. Pretende ilustrar algunos de los conceptos y retos más importantes.

## Programación secuencial vs concurrente

1. Programa una función `num` que reciba como parámetro un entero y lo muestre por pantalla.

2. Llama a dicha función en el programa con los parámetros del 0 al 9, es decir:

```python
num(0)
num(1)
...
num(9)
```

No es sorprendente que la salida de ese programa sea la secuencia de números del 0 al 9 ordenada por orden de llamada a las funciones.

2.1. ¿Se te ocurre alguna forma de que pudiéramos llamar simultáneamente a cada una de las funciones de forma que no pudiéramos predecir el orden de ejecución?

2.2. Escribe al menos tres ventajas que pueda tener ejecutar software de forma simultánea.

### Hilos de ejecución y programación concurrente en Python

La programación concurrente permite realizar distintas tareas de forma aparentemente simultánea. Podemos imaginar un programa que lance "a la vez" las diez llamadas a la función `num` de forma que no podamos predecir el orden de los números en la salida al no saber qué función se ejecutará antes. Los hilos de ejecución o 'threads' son un recurso para realizar estas ejecucciones aprentemente simultáneas en muchos lenguajes como python.

Una de las ventajas de la programación concurrente es que nos permite ejecutar programas intensivos en uso del procesador simultáneamente en distintos núcleos de la CPU (en el caso de que nuestro ordenador los tenga).

## **Ejercicio Entregable:** El `Hash` Dorado

_Nota: El ejercicio se entregará como archivo de Jupter Notebooks con el código y los comentarios necesarios para explicar vuestro enfoque, incluidas las respuestas a las preguntas planteadas. Deberá entregarse la semana del 17 de febrero_

### Introducción

Una función de `hash` es una función que devuelve una huella digital para cada conjunto de datos. En python, podemos usar el método `hash` para obtener estas huellas digitales. No existen formas eficientes de predecir cuál será la huella digital de unos datos, por lo que si queremos encontrar unos datos cuya huella digital tenga ciertas características. Por ejemplo, podemos decir que un hash es dorado si sus últimas 6 cifras son iguales a 0. Si queremos encontrar un hash dorado, deberemos probar on datos diferentes hasta que encontremos aquellos que buscábamos.

Este ejercicio pretende utilizar la programación concurrente para mejorar el rendimiento de un programa intensivo en CPU como es la búsqueda de hashes.

### La excavadora

Primero, programa una función `excavadora`, que reciba por parámetro unas coordenadas en forma de tupla de dos elementos y devuelva otra tupla "cercana" cuyo hash termine por 6 ceros. Antes de terminar, la función excavadora imprimirá por consola el número de iteraciones realizadas. Si la función excavadora ha realizado `n` comprobaciones, la distancia `Manhattan` entre las coordenadas de origen y las devueltas por la función no deben ser superiores a `n`. Es decir, si '(a,b) = '

es decir, una función tal que si `(a,b) = excavadora((c,d))` entonces `1000000 % hash((a,b))` es igual a `0` y `abs(a-c) + abs(b-d)` es menor o igual al número de ciclos que se han ejecutado.

### Las excavadoras

Escribe primero un programa que ejecute de forma secuencial 8 excavadoras a la vez, empezando por coordenadas separadas.

Después, utilizando hilos de ejecución, haz un programa que ejecute las 8 excavadoras de forma concurrente.

**Pregunta** ¿hay alguna mejora en el rendimiento?

### El concurso

Haz un programa concurrente que "lance" 8 excavadoras a la vez y termine en cuanto una excavadora encuentre un hash dorado.

**Pregunta** De media, ¿tarda más o menos este programa en encontrar un hash dorado que cuando teníamos una sola excavadora? ¿por qué?

## Recursos

- [Ejecucción Concurrente - Documentación oficial de Python](https://docs.python.org/3/library/concurrency.html)
- [Hilos en Python - pythontutorial.net](https://www.pythontutorial.net/python-concurrency/python-threading/)
