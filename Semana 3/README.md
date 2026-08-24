# Laboratorio 2 - Vectorización SIMD con AVX2

## Objetivo

Comparar el rendimiento de una multiplicación de matrices utilizando una versión escalar y una versión vectorizada con instrucciones SIMD y AVX2.

Para las pruebas se trabajó con matrices de tamaño `2048 x 2048`.

En la versión AVX2 se implementó la multiplicación de vectores y la reducción utilizando registros vectoriales. Estas operaciones se utilizaron posteriormente para realizar el producto punto necesario en la multiplicación de matrices.

También se realizó la transposición de la matriz B para facilitar el acceso a sus elementos durante la multiplicación.

## Resultados

| Implementación | Tiempo (s) |
|---------------|-----------:|
| Escalar | 7.229610 |
| AVX2 | 2.863350 |

Ambas implementaciones produjeron el mismo resultado, por lo que la vectorización no modificó el resultado de la multiplicación.

El speedup obtenido fue:

S = 7.229610 / 2.863350 = 2.53

Por lo tanto, en esta prueba la versión utilizando AVX2 fue aproximadamente **2.53 veces más rápida** que la versión escalar.

## Análisis

AVX2 permite trabajar con varios elementos al mismo tiempo utilizando registros de 256 bits. Esto permite realizar varias multiplicaciones en una misma operación en lugar de procesar cada elemento individualmente.

Sin embargo, esto no significa que todo el programa vaya a ser 8 veces más rápido, ya que también se realizan otras operaciones como accesos a memoria, reducción de los resultados parciales, transposición de la matriz y control de los ciclos.

En las pruebas realizadas se obtuvo una mejora de aproximadamente 2.53 veces con respecto a la versión escalar, por lo que se observa una mejora importante al utilizar SIMD con AVX2.