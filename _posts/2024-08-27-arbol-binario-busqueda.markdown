---
title: "Árbol binario de búsqueda (ABB)"
date: 2024-08-27 08:30:00 -0500
categories: [Árbol binario de búsqueda]
tags: [abb]
author: ok
---

Un **árbol binario de búsqueda** (**ABB**) es un tipo especial de árbol binario en el que cada nodo tiene un valor mayor que todos los valores en su subárbol izquierdo y menor que todos los valores en su subárbol derecho. Esto permite realizar búsquedas eficientes en el árbol.

> **Definición:** Árbol binario de búsqueda (ABB).
>
> Sea $A$ un árbol binario con raíz $R$ e hijos izquierdo y derecho (posiblemente nulos) $H_I$ y $H_D$, respectivamente.
>
> Decimos que $A$ es un **árbol binario de búsqueda (ABB)** si y solo si se satisfacen ambas condiciones al mismo tiempo:
>
> 1. $H_I$ es vacío **o** ("$R$ es mayor que todo elemento de $H_I$" **y** "$H_I$ es un ABB").
> 2. $H_D$ es vacío **o** ("$R$ es menor que todo elemento de $H_D$" **y** "$H_D$ es un ABB").
{: .prompt-warning .shadow }

---

## Ejemplo de árbol binario de búsqueda

![arbol-binario-busqueda](https://upload.wikimedia.org/wikipedia/commons/d/da/Binary_search_tree.svg)
_Ejemplo de árbol binario de búsqueda_

---

## Operaciones básicas

Las operaciones básicas en un ABB son:

* **Búsqueda:** Encontrar un elemento específico en el árbol.
* **Inserción:** Agregar un nuevo elemento al árbol.
* **Borrado:** Eliminar un elemento del árbol.
* **Recorrido:** Visitar todos los elementos del árbol en un orden específico.

## Tipos de recorridos

Existen diferentes tipos de recorridos en un ABB:

* **Inorden:** Se el subárbol izquierdo, luego la raiz y finalmente el subárbol derecho.
* **Preorden:** Se visita la raíz, luego el subárbol izquierdo y finalmente el subárbol derecho.
* **Postorden:** Se visitan primero los subárboles izquierdo y derecho, y finalmente la raíz.

## Aplicaciones

Los ABBs se utilizan en una amplia variedad de aplicaciones, incluyendo:

* **Bases de datos:** Para almacenar y recuperar datos de manera eficiente.
* **Diccionarios:** Para almacenar y buscar palabras.
* **Sistemas de recomendación:** Para recomendar productos o servicios a los usuarios.

## Conclusión

Los ABBs son una estructura de datos fundamental en informática con una amplia gama de aplicaciones. Su simplicidad, eficiencia y versatilidad los convierten en una herramienta poderosa para resolver problemas de búsqueda y ordenamiento.

---

**!Gracias por leer este artículo!**
