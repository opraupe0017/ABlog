---
title:  "Algoritmos de ordenamiento"
date:   2024-07-30 23:01:00 -0500
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

## Algoritmos recursivos

> **Definición:** Un **algoritmo recursivo** es aquel que se llama a sí mismo para resolver **subproblemas más pequeños** del mismo problema. La recursión se basa en el principio de que un problema puede ser dividido en subproblemas más pequeños y manejables, y luego combinar las soluciones de estos subproblemas para obtener la solución del problema original.
{: .prompt-warning }


> **Componentes de la Recursión:**
> 1. **Caso Base:** Es la condición que detiene la recursión. Cuando se cumple esta condición, la función recursiva deja de llamarse a sí misma y retorna un valor.
> 2. **Caso Recursivo:** Es la parte del algoritmo en la que la función se llama a sí misma con una versión más pequeña del problema original.
{: .prompt-tip }

### Ejemplo

El factorial de un número  $n$ (representado como $ n! $) puede definirse recursivamente de la siguiente manera:

$$ n! = \begin{cases} 
1 &,\ \text{si}\ n = 0 \\
n \times (n - 1)! &,\ \text{si}\ n > 0 
\end{cases} $$

### Actividad

Implementar la función `calcularFactorial(int n)` en `C++` sin importar bibliotecas, salvo `iostream`.

---

### Estrategia Divide y Vencerás

> **Definición:** **Divide y vencerás** es una estrategia de diseño de algoritmos que consiste en dividir un problema en subproblemas más pequeños y resolver cada uno de esos subproblemas por separado. Una vez resueltos los subproblemas, las soluciones se combinan para resolver el problema original.
{: .prompt-warning }

> **Pasos de Divide y Vencerás:**
> 1. **Dividir:** Dividir el problema en subproblemas más pequeños que sean similares al problema original.
> 2. **Vencer:** Resolver cada subproblema recursivamente. Si el subproblema es lo suficientemente pequeño, resolverlo directamente (caso base).
> 3. **Combinar:** Combinar las soluciones de los subproblemas para obtener la solución del problema original.
{: .prompt-tip }


> **Observación:** Esta combinación de algoritmos recursivos y la estrategia divide y vencerás es poderosa para resolver problemas complejos de manera eficiente y estructurada.
{: .prompt-info }

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

![insertion-sort](https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif)
_Ejemplo de ordenamiento por inserción._

##### Algoritmo ordenamiento por inserción en arreglo de enteros

```cpp
#include<iostream>
using namespace std;

void insertionSort(int arr[], int n) {
    int key, j;

    for(int i = 1; i < n; i++) {
        key = arr[i];
        j = i - 1;
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

![selection-sort](https://upload.wikimedia.org/wikipedia/commons/9/94/Selection-Sort-Animation.gif)
_Ejemplo de ordenamiento por selección._

##### Algoritmo ordenamiento por selección en arreglo de enteros

```cpp
#include <iostream>
using namespace std;
  
void selectionSort(int arr[], int n) { 
    int i, j, min_idx, tmp; 

    for (i = 0; i < n - 1; i++) { 
        min_idx = i; 
        for (j = i + 1; j < n; j++) 
            if (arr[j] < arr[min_idx]) 
                min_idx = j; 

        tmp = arr[min_idx]; 
        arr[min_idx] = arr[i]; 
        arr[i] = tmp; 
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

![bubble-sort](https://upload.wikimedia.org/wikipedia/commons/c/c8/Bubble-sort-example-300px.gif)
_Ejemplo de ordenamiento burbuja._

##### Algoritmo ordenamiento burbuja en arreglo de enteros

```cpp
#include <iostream>
using namespace std;

void bubbleSort(int arr[], int n) {
    int tmp;

    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                tmp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = tmp;
            }
        }
    }
}
```
{: file="bubbleSort.cpp" }

---

#### Ordenamiento por mezcla (Merge Sort)

> **Estrategia:**
>
> 1. **Divide:** Si la lista tiene más de un elemento, divide la lista de elementos a la mitad.
> 2. **Ordena:** Ordena ambas mitades de la lista por separado. Hazlo recursivamente utilizando el algoritmo de ordenamiento por mezcla.
> 3. **Mezcla:** Combina las dos mitades ordenadas en una única lista ordenada.
{: .prompt-warning }

![merge-sort](/assets/img/0008_mergesort.gif)
_Ejemplo de ordenamiento por mezcla._

##### Algoritmo ordenamiento por mezcla en arreglo de enteros

Este algoritmo necesita tanto la fase de divide y vencerás como la fase de mezcla, este es el script que corresponde a la mezcla.

```cpp
#include <iostream>
using namespace std;

void merge(int arr[], int p, int q, int r) {
    int n1 = q - p + 1;
    int n2 = r - q;
    int L[n1], R[n2];

    for (int i = 0; i < n1; i++)
        L[i] = arr[p + i];
    for (int j = 0; j < n2; j++)
        R[j] = arr[q + 1 + j];

    int i, j, k;
    i = 0;
    j = 0;
    k = p;

    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k] = L[i];
            i++;
        }
        else {
            arr[k] = R[j];
            j++;
        }
        k++;
    }

    while (i < n1) {
        arr[k] = L[i];
        i++;
        k++;
    }

    while (j < n2) {
        arr[k] = R[j];
        j++;
        k++;
    }
}
```
{: file="mergeSort.cpp" }

Este es el script que corresponde a la mezcla.

```cpp
void mergeSort(int arr[], int l, int r) {
    if (l < r) {
        int m = l + (r - l) / 2;

        mergeSort(arr, l, m);
        mergeSort(arr, m + 1, r);

        merge(arr, l, m, r);
    }
}
```
{: file="mergeSort.cpp" }

---

#### Ordenamiento rápido (Quick Sort)

> **Estrategia:**
>
> 1. **Elige un pivote:** Selecciona el último elemento del arreglo para ser el pivote.
> 2. **Partición:** Pasa todos los elementos que son menores que el pivote a su izquierda y los mayores a su derecha.
> 3. **Recursión:** Aplica los mismos pasos de forma recursiva para las dos mitades del arreglo.
{: .prompt-warning }

![quick-sort](/assets/img/0009_quicksort.gif)
_Ejemplo de ordenamiento rápido_

##### Algoritmo ordenamiento rápido en arreglo de enteros

Para este algoritmo requerimos hacer en repetidas ocasiones *intercambios* con `swap`, una función que nos ubique en la posición correspondiente el valor en un arreglo con `partition` y la función `quickSort`.

```cpp
#include <iostream>
using namespace std;

void swap(int *a, int *b) {
    int t = *a;
    *a = *b;
    *b = t;
}
```
{: file="quickSort.cpp" }

```cpp
int partition(int array[], int low, int high) {
    int pivot = array[high];
    int i = low - 1;

    for (int j = low; j < high; j++) {
        if (array[j] <= pivot) {
            i++;
            swap(&array[i], &array[j]);
        }
    }
  
    swap(&array[i + 1], &array[high]);

    return (i + 1);
}
```
{: file="quickSort.cpp" }

```cpp
void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int pivote = partition(arr, low, high);

        quickSort(arr, low, pivote - 1);
        quickSort(arr, pivote + 1, high);
    }
}
```
{: file="quickSort.cpp" }

---

**¡Gracias por leer este post!**

---
