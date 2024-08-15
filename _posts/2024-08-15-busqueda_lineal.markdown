---
title:  "Búsqueda Lineal"
date:   2024-08-15 09:00:00 -0500
categories: [Algoritmos de búsqueda, Estructuras de datos]
tags: [búsqueda-lineal]
author: ok
---

> La **búsqueda lineal** o **búsqueda secuencial** es un método para encontrar un valor objetivo dentro de una lista comprobando cada elemento secuencialmente hasta encontrar el objetivo o hasta que se hayan revisado todos los elementos.
{: .prompt-tip }

## Características Principales

1. **Complejidad del Peor Caso:** $\mathcal{O}(n)$
2. **Complejidad del Mejor Caso:** $\Omega(1)$
3. **Eficiencia:** Es el método más básico, pero se vuelve impráctico para listas grandes en comparación con algoritmos más avanzados como la búsqueda binaria o las tablas hash.

## Estrategia de la búsqueda lineal

El algoritmo recorre la lista secuencialmente buscando el objetivo:

1. **Iniciar en el primer elemento**.
2. **Comparar** el elemento actual con el objetivo.
3. Si coincide, **terminar** exitosamente.
4. Si no, avanzar al siguiente elemento y repetir.
5. Si se llega al final de la lista sin encontrar el objetivo, la búsqueda falla.

## Algoritmo

```bash
Función buscarLineal(arreglo, n, valor_a_buscar)
    Para cada índice desde 0 hasta n - 1
        Si el elemento en el arreglo en la posición índice es igual a valor_a_buscar
            Retornar el índice
        Fin Si
    Fin Para
    Retornar -1
Fin Función
```
{: file="Algoritmo de búsqueda lineal" }

## Aplicaciones

La búsqueda lineal es útil en casos donde:
- La lista es pequeña.
- Se realiza una única búsqueda en una lista no ordenada.
- El costo de preprocesamiento de la lista para otros métodos (como ordenar para búsqueda binaria) no justifica su uso.

## Limitaciones

Aunque la búsqueda lineal es simple, su rendimiento decrece rápidamente con listas más grandes. Para listas largas o con búsquedas frecuentes, métodos como la búsqueda binaria o el uso de estructuras como tablas hash son más eficientes.

## Actividad

> **Actividad:** Implementar en `C++` el algoritmo de búsqueda lineal
> 1. Para enteros.
> 3. Para estructuras más complejas como un arreglo de personas y buscar por el nombre.
{: .prompt-danger }

---

Gracias por leer este artículo.
