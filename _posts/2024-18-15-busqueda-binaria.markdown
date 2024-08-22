---
title: "Búsqueda Binaria"
date: 2024-08-15 10:30:00 -0500
categories: [Algoritmos de búsqueda, Complejidad computacional]
tags: [búsqueda-binaria, divide-y-vence]
author: ok
---

> **Definición:** La búsqueda binaria es un algoritmo de búsqueda eficiente que localiza la posición de un valor en un arreglo **ordenado**. Compara el valor objetivo con el elemento en el medio del arreglo, y si no son iguales, elimina la mitad en la que el valor no puede estar y continúa la búsqueda en la mitad restante hasta encontrar el valor o determinar que no está presente.
{: .prompt-warning }

## Complejidad

La búsqueda binaria tiene una complejidad temporal de $\mathcal{O}(\log n)$ en el peor de los casos, donde $n$ es el número de elementos en el arreglo. En cuanto al espacio, requiere solo $\mathcal{O}(1)$, ya que el espacio necesario es constante sin importar la cantidad de elementos.

## Estrategia

1. Comenzar con los límites izquierdo ($L$) y derecho ($R$) en los extremos del arreglo.
2. Calcular el índice del elemento medio ($m$) como:  
   $$ m = \left\lfloor \frac{L + R}{2} \right\rfloor $$
3. Si el valor buscado ($T$) es igual a $A[m]$, la búsqueda termina.
4. Si $T$ es menor que $A[m]$, continuar la búsqueda en la mitad izquierda.
5. Si $T$ es mayor que $A[m]$, continuar la búsqueda en la mitad derecha.
6. Repetir hasta encontrar el valor o hasta que $L > R$, en cuyo caso el valor no está presente.

## Algoritmo

```bash
Función busquedaBinaria(arreglo, inicio, fin, valor_a_buscar)
    Si inicio es mayor que fin
        Retornar -1  // Elemento no encontrado

    medio <- inicio + (fin - inicio) / 2

    Si arreglo[medio] es igual a valor_a_buscar
        Retornar medio

    Si arreglo[medio] es menor que valor_a_buscar
        Retornar busquedaBinaria(arreglo, medio + 1, fin, valor_a_buscar)

    Sino
        Retornar busquedaBinaria(arreglo, inicio, medio - 1, valor_a_buscar)
    Fin Si
Fin Función
```

{::options parse_block_html="true" /}
<details><summary markdown="span">Código en `search.h`</summary>
```cpp
#ifndef SEARCH_H // Comienza una guardia de inclusión para evitar inclusiones múltiples del archivo
#define SEARCH_H // Define la macro SEARCH_H

long long linearSearch(long long arr[], long long n, long long value);

long long binarySearch(long long arr[], long long l, long long r, long long value);

#endif // SEARCH_H
```
{: file="search.h" }
</details>
{::options parse_block_html="false" /}

{::options parse_block_html="true" /}
<details><summary markdown="span">Código en `search.cpp`</summary>
```cpp
#include "search.h"

long long linearSearch(long long arr[], long long n, long long value) {
  for (long long i = 0; i < n; i++) {
    if (arr[i] == value) {
      return i;
    }
  }
  return -1;
}

long long binarySearch(long long arr[], long long l, long long r, long long value) {
    if (l > r) {
        return -1;
    }

    long long mid = l + (r - l) / 2;

    if (arr[mid] == value) {
        return mid;
    } else if (arr[mid] < value) {
        return binarySearch(arr, mid + 1, r, value); // Search in the r half
    } else {
        return binarySearch(arr, l, mid - 1, value); // Search in the l half
    }
}
```
{: file="search.h" }
</details>
{::options parse_block_html="false" /}

{::options parse_block_html="true" /}
<details><summary markdown="span">Código en `search_test.cpp`</summary>
```cpp
#include <iostream>
#include <chrono>
#include "search.h"

using namespace std;

int main() {
    long long n;
    cout << "Ingrese el tamaño del arreglo: ";
    cin >> n;

    long long arr[n];
    for (long long i = 0; i < n; i++) {
        arr[i] = 2 * i;
    }

    long long value;
    cout << "Ingrese el número entero a buscar: ";
    cin >> value;

    // Medir el tiempo de búsqueda lineal
    auto start_linear = chrono::high_resolution_clock::now();
    long long linear_result = linearSearch(arr, n, value);
    auto end_linear = chrono::high_resolution_clock::now();
    chrono::duration<double> elapsed_linear = end_linear - start_linear;

    // Medir el tiempo de búsqueda binaria
    auto start_binary = chrono::high_resolution_clock::now();
    long long binary_result = binarySearch(arr, 0, n - 1, value);
    auto end_binary = chrono::high_resolution_clock::now();
    chrono::duration<double> elapsed_binary = end_binary - start_binary;

    cout << "Resultado de búsqueda lineal: " << linear_result << endl;
    cout << "Tiempo de búsqueda lineal: " << elapsed_linear.count() << " segundos" << endl;

    cout << "Resultado de búsqueda binaria: " << binary_result << endl;
    cout << "Tiempo de búsqueda binaria: " << elapsed_binary.count() << " segundos" << endl;

    return 0;
}
```
{: file="search.h" }
</details>
{::options parse_block_html="false" /}


## Variaciones

Existen variaciones como la búsqueda binaria para coincidencias aproximadas y la "cascada fraccional", que acelera la búsqueda en múltiples arreglos para un mismo valor.

## Actividad

> **Actividad:** Implementar en `C++` el algoritmo de búsqueda binaria
> 1. Exacta para enteros.
> 2. Aproximada para flotantes.
> 3. Para estructuras más complejas como un arreglo de personas y buscar por el nombre.
{: .prompt-danger }

---

**¡Gracias por leer este artículo!**

---