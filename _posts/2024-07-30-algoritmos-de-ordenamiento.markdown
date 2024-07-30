---
title:  "Algoritmos de ordenamiento"
date:   2024-07-30 11:00:00 -0500
categories: [Fuerza bruta, Divide y vencerás, Algoritmo recursivo, Algoritmo de ordenamiento, Ordenamiento por inserción, Ordenamiento por selección, Ordenamiento burbuja, Ordenamiento por mezcla, Ordenamiento Rápido]
tags: [fuerza-bruta, divide-y-vence, algoritmo-recursivo, sort, insertion-sort, selection-sort, bubble-sort, merge-sort, quick-sort] 
author: ok
---

## Algoritmo de Fuerza Bruta

> El algoritmo de **fuerza bruta** es una técnica simple pero poderosa para resolver problemas mediante la enumeración exhaustiva de todas las posibles soluciones y la evaluación de cada una de ellas para encontrar la solución óptima. Este enfoque se basa en probar todas las combinaciones posibles hasta encontrar una solución que satisfaga las condiciones del problema.
{: .prompt-tip }

### Características Principales

1. **Simplicidad**: La fuerza bruta es fácil de entender e implementar, ya que no requiere conocimientos avanzados de algoritmos o estructuras de datos complejas.
2. **Exhaustividad**: Explora todas las posibles soluciones sin descartar ninguna, lo que garantiza encontrar la solución correcta si existe.
3. **Costo Computacional**: A menudo tiene un costo computacional alto, especialmente para problemas con grandes espacios de búsqueda, ya que puede implicar evaluar un número exponencial de posibilidades.

#### Ejemplos Comunes

- **Búsqueda de patrones**: Encontrar todas las ocurrencias de una subcadena dentro de una cadena más grande.
- **Problemas combinatorios**: Resolver problemas como el de la mochila (knapsack), el viajante de comercio (traveling salesman), o la generación de permutaciones y combinaciones.
- **Búsqueda en espacios discretos**: Encontrar el mínimo o máximo en un conjunto de datos sin usar técnicas avanzadas de optimización.

### Ventajas y Desventajas

> **Ventajas**:
> - Fácil de implementar.
> - Garantiza encontrar la solución correcta si se ejecuta hasta el final.
{: .prompt-info }

> **Desventajas**:
> - Ineficiente para problemas de gran tamaño debido al alto costo computacional.
> - A menudo no es práctico para problemas con grandes espacios de búsqueda.
{: .prompt-danger }

### Conclusión

El algoritmo de fuerza bruta es una herramienta fundamental en la caja de herramientas de cualquier programador, especialmente útil para resolver problemas pequeños o como punto de partida para entender un problema antes de aplicar técnicas más avanzadas y eficientes. Aunque puede ser ineficiente, su simplicidad y exhaustividad lo hacen valioso en una variedad de contextos.

---

## Algortimo de ordenamiento

> **Definición:** Un **algoritmo de ordenamiento** es un procedimiento paso a paso que toma una lista o arreglo de elementos que son "ordenables" y los reorganiza en un orden específico, ya sea en orden ascendente o descendente.
{: .prompt-warning }

> **Observación:** Los algoritmos de ordenamiento son fundamentales en la informática y se utilizan en una amplia variedad de aplicaciones, desde la organización de datos en bases de datos hasta la optimización de búsquedas y la mejora del rendimiento de otros algoritmos.
{: .prompt-info }

Existen varios tipos de algoritmos para ordenar, entre ellos vamos a abordar:

1. **Fuerza bruta:**
   - Ordenamiento por inserción (insertion-sort),
   - Ordenamiento por selección (selection-sort),
   - Ordenamiento burbuja (bubble-sort).
2. **Algoritmos recursivos:**
   - Ordenamiento por mezcla (merge-sort),
   - Ordenamiento rápido (quick-sort).

---

### Algoritmos de ordenamiento de fuerza bruta

---

#### Ordenamiento por inserción

> **Estrategia:**
>
> 1. **Inicia en el segundo elemento:** Considera el segundo elemento del arreglo como el primer candidato para ser insertado en su posición correcta.
> 2. **Compara e Inserta:** Compara este elemento con los elementos antes de él y muévalo hasta encontrar su lugar correcto.
> 3. **Repite:** Continúa con el siguiente elemento y repite el paso 2 hasta que todos los elementos en el arreglo estén ordenados.
{: .prompt-warning }

##### Algoritmo ordenamiento por inserción en arreglo de enteros

```cpp
#include<iostream>
using namespace std;

void insertionSort(int arr[], int n) {
    for(int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i-1;
        while(j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}
```
{: file="insertionSort.cpp" }

---

#### Ordenamiento por selección

> **Estrategia:**
>
> 1. **Encuentra el mínimo:** Recorre el arreglo para encontrar el elemento más pequeño.
> 2. **Intercambia:** Intercambia este elemento con el primer elemento del arreglo.
> 3. **Subarreglo restante:** Considera el subarreglo que empieza desde la segunda posición y repite el proceso, encontrando el elemento más pequeño en el subarreglo y colocándolo en la primera posición de este subarreglo.
> 4. **Repite:** Continúa hasta que todos los elementos hayan sido colocados en su posición correcta en el arreglo.
{: .prompt-warning }

##### Algoritmo ordenamiento por selección en arreglo de enteros

```cpp
#include <iostream>
using namespace std;
  
void selectionSort(int arr[], int n) { 
    int i, j, min_idx; 
  
    for (i = 0; i < n - 1; i++) { 
        min_idx = i; 
        for (j = i + 1; j < n; j++) 
            if (arr[j] < arr[min_idx]) 
                min_idx = j; 

        int temp = arr[min_idx]; 
        arr[min_idx] = arr[i]; 
        arr[i] = temp; 
    } 
} 
```
{: file="selectionSort.cpp" }

---

#### Ordenamiento Burbuja (Bubble Sort)

> **Estrategia:**
>
> 1. **Comienza en el primer elemento:** Considera los dos primeros elementos del arreglo.
> 2. **Compara y cambia:** Si el primer elemento es mayor que el segundo, intercámbialos.
> 3. **Avanza y repite:** Avanza al siguiente par de elementos y repite el paso 2. Repite este paso hasta llegar al final del arreglo.
> 4. **Repite todo otra vez:** Repite los pasos 1, 2 y 3 tantas veces como el número de elementos en el arreglo.
{: .prompt-warning }

##### Algoritmo ordenamiento burbuja en arreglo de enteros

```cpp
#include <iostream>
using namespace std;

void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}
```
{: file="bubbleSort.cpp" }

---

## Continuara...

---

**¡Gracias por leer este post!**

---
