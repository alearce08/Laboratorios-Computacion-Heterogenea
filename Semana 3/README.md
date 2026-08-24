# Semana 3 - Laboratorio 2

## Vectorización SIMD con AVX2

En este laboratorio se implementaron diferentes operaciones utilizando SIMD con AVX2. Para las pruebas se trabajó con un tamaño de 2048 elementos. La idea principal fue utilizar operaciones vectorizadas para posteriormente aplicarlas en una multiplicación de matrices y comparar su tiempo de ejecución con una versión escalar.

## Desarrollo

Primero se implementó la multiplicación elemento a elemento entre dos vectores utilizando AVX2.

Después se realizó una reducción para sumar los valores obtenidos en los registros vectoriales. Con estas dos operaciones se pudo implementar el producto punto entre vectores.

Para la multiplicación de matrices se utilizó este producto punto vectorizado. También se realizó la transposición de la matriz B antes de hacer la multiplicación, para acceder a sus datos de una forma más conveniente durante el cálculo.

Además de la versión con AVX2, se utilizó una versión escalar para poder comparar los tiempos de ejecución.

## Resultados obtenidos

| Implementación | Tiempo (s) |
|----------------|-----------:|
| Escalar        | 7.229610 |
| AVX2           | 2.863350 |

Se verificó que ambas versiones produjeran los mismos valores en la matriz resultante.

Para comparar el rendimiento se calculó el speedup:

`Speedup = 7.229610 / 2.863350 = 2.53`

Por lo tanto, en esta ejecución la versión con AVX2 fue aproximadamente **2.53 veces más rápida** que la versión escalar.

## Observaciones

La versión con AVX2 obtuvo un menor tiempo porque permite realizar la misma operación sobre varios datos utilizando instrucciones vectoriales, en lugar de procesarlos uno por uno.

Aun así, la mejora del programa completo no depende solamente de la parte vectorizada. La multiplicación de matrices también incluye accesos a memoria, ciclos, la transposición de la matriz y otras operaciones que forman parte del tiempo total de ejecución.