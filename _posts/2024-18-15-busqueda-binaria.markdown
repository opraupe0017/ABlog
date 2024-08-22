---
title: "Búsqueda Binaria"
date: 2024-08-15 10:30:00 -0500
categories: [Algoritmos de búsqueda, Complejidad computacional]
tags: [búsqueda-binaria, divide-y-vence]
author: ok
---

> **Definición:** La búsqueda binaria es un algoritmo de búsqueda eficiente que localiza la posición de un valor en un arreglo **ordenado**. Compara el valor objetivo con el elemento en el medio del arreglo, y si no son iguales, elimina la mitad en la que el valor no puede estar y continúa la búsqueda en la mitad restante hasta encontrar el valor o determinar que no está presente.
{: .prompt-warning .shadow }

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

cpp
```bash
Función binarySearchRecursive(arreglo, inicio, fin, objetivo)
    Si inicio es mayor que fin
        Retornar -1  // Elemento no encontrado

    medio <- inicio + (fin - inicio) / 2

    Si arreglo[medio] es igual a objetivo
        Retornar medio

    Si arreglo[medio] es menor que objetivo
        Retornar binarySearchRecursive(arreglo, medio + 1, fin, objetivo)

    Sino
        Retornar binarySearchRecursive(arreglo, inicio, medio - 1, objetivo)
    Fin Si
Fin Función
```

## Variaciones

Existen variaciones como la búsqueda binaria para coincidencias aproximadas y la "cascada fraccional", que acelera la búsqueda en múltiples arreglos para un mismo valor.

## Actividad

> **Actividad:** Implementar en `C++` el algoritmo de búsqueda binaria
> 1. Exacta para enteros.
> 2. Aproximada para flotantes.
> 3. Para estructuras más complejas como un arreglo de personas y buscar por el nombre.
{: .prompt-danger .shadow }

---

**¡Gracias por leer este artículo!**

---