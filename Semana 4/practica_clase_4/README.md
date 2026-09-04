# Práctica de clase 4

> **Nota:** Profesor, disculpe que esta práctica se agregue después. No me había dado cuenta de que también había que realizar la Práctica de clase 4 y pensé que solamente correspondía la práctica anterior. Cuando lo noté realicé los incisos A y B y agregué los resultados al repositorio.

## Inciso A - Biblioteca estática

Se compiló y ejecutó la versión utilizando una biblioteca estática.

```bash
make -C libraries all
./libraries/build/bin/bench-static 1000000 1000 1.0 2.0
```

Se realizaron tres pruebas con los mismos parámetros.

| Corrida | fill A (us) | fill B (us) | add (us) | Total (us) |
|---:|---:|---:|---:|---:|
| 1 | 654929.336 | 649707.457 | 1173535.895 | 2478173.464 |
| 2 | 611535.622 | 578911.626 | 1215812.277 | 2406260.240 |
| 3 | 711617.360 | 698777.480 | 959483.425 | 2369878.979 |
| **Promedio** | **659360.773** | **642465.521** | **1116277.199** | **2418104.228** |

Tamaño de la biblioteca:

```text
libvectorops.a = 1.8 KB
```

Tiempo promedio total: **2.42 s**

## Inciso B - Biblioteca dinámica

Se ejecutó el mismo programa utilizando la biblioteca dinámica.

```bash
./libraries/build/bin/bench-dynamic 1000000 1000 1.0 2.0
```

También se realizaron tres pruebas.

| Corrida | fill A (us) | fill B (us) | add (us) | Total (us) |
|---:|---:|---:|---:|---:|
| 1 | 1575689.623 | 1626466.175 | 1801756.007 | 5003912.583 |
| 2 | 1382223.743 | 1185751.405 | 1463652.158 | 4031627.990 |
| 3 | 1649130.160 | 1366195.074 | 1319226.509 | 4334552.556 |
| **Promedio** | **1535681.175** | **1392804.218** | **1528211.558** | **4456697.710** |

Tamaño de la biblioteca:

```text
libvectorops.so = 16 KB
```

Tiempo promedio total: **4.46 s**

## Comparación

| Versión | Tiempo promedio | Tamaño de biblioteca |
|---|---:|---:|
| Estática | 2.42 s | 1.8 KB |
| Dinámica | 4.46 s | 16 KB |

En estas pruebas la versión estática obtuvo menores tiempos que la dinámica. La biblioteca estática se enlaza directamente con el programa durante la compilación, mientras que la dinámica se mantiene como un archivo separado que se utiliza durante la ejecución.

