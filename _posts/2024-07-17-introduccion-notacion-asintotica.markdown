---
layout: post
title:  "Análisis asintótico de algoritmos"
date:   2024-07-17 12:00:00 -0500
categories: algorithms
author: Oscar García
---

EL **análisis asintótico de algoritmos** es una herramienta fundamental en el análisis de algoritmos, ya que nos permite describir el comportamiento de un algoritmo a medida que el tamaño de la entrada crece. En este post, exploraremos las tres notaciones más comunes: **Big $\mathcal{O}$**, **Big $\Omega$** y **Big $\Theta$**, y su aplicabilidad en la **complejidad temporal**, **espacial**, **energética** y de **latencia en red**. Además, mencionaremos el **teorema maestro**, una herramienta útil para analizar algoritmos recursivos.

## Contenidos
{:.no_toc}

* TOC
{:toc}

## Definición: Complejidad del Algoritmo

La **complejidad del algoritmo** es una medida de la cantidad de recursos que requiere un algoritmo para resolver un problema. Estos recursos pueden ser:

- **Tiempo** en función del tamaño $n$ de la entrada, denotado por $T(n)$.
- **Espacio de almacenamiento** requerido para procesar un tamaño $n$ de entrada, denotado por $E(n)$.
- **Consumo de energía**.
- **Ancho de banda**, entre otros.

### Ejemplo: Algunas Complejidades en Algoritmos

**Registrar el signo de los elementos de una lista de números**: El algoritmo recorre la lista una vez uno por uno. Por lo tanto para algún tiempo $c\geq 0$ y espacio $k\geq 0$ que son *constantes de que dependen del computador que se está utilizando para ejecutar el algoritmo*
- $T(n) = cn$, es decir el algoritmo realiza $n$ operaciones que tardan máximo un tiempo $c$ cada una.
- $E(n) = kn$, es decir el algoritmo ocupa $n$ espacios de memoria de tamaño máximo $k$ cada una.

**Búsqueda binaria**: El algoritmo divide repetidamente la lista en dos y verifica en qué mitad se encuentra el elemento buscado. Por lo tanto para algún tiempo $c\geq 0$ y espacio $k\geq 0$
- $T(n) = c \log n$
- $E(n) = k$

**Suma de matrices cuadradas**: El algoritmo suma los elementos correspondientes de dos matrices de tamaño $n \times n$. Por lo tanto para algún tiempo $c\geq 0$ y espacio $k\geq 0$
- $T(n) = cn^2$
- $E(n) = k$

## Notación Asintótica

Contamos con $3$ notaciones especiales:

- **Big $\mathcal{O}$:** Para los peores casos.
- **Big $\Omega$:** Para el mejor de los casos.
- **Big $\Theta$:** Para los casos que son mejores y peores al mismo tiempo, es decir la complegidad es "la misma" para cualquier entrada que procese el algoritmo.

**Límites superiores e inferiores:**

Podemos analizar el comportamiento del algoritmo utilizando límites superiores e inferiores. Un límite superior describe el valor máximo que puede alcanzar el tiempo de ejecución del algoritmo para entradas suficientemente grandes. Por otro lado, un límite inferior establece el valor mínimo que no puede ser menor el tiempo de ejecución del algoritmo.

**Ejemplo: Análisis del tiempo de ejecución de la búsqueda binaria**

Consideremos el algoritmo de búsqueda binaria, utilizado para encontrar un elemento específico en una lista ordenada. El tiempo de ejecución de la búsqueda binaria se puede expresar en términos del número de elementos ($n$) de la lista.

**Límite superior:** El tiempo de ejecución máximo de la búsqueda binaria se produce cuando el elemento buscado no se encuentra en la lista. En este caso, el algoritmo recorre toda la lista, realizando comparaciones hasta llegar al final. El límite superior del tiempo de ejecución en este caso es $c\log n$.

**Límite inferior:** El tiempo de ejecución mínimo de la búsqueda binaria se produce cuando el elemento buscado se encuentra en el centro exacto de la lista. En este caso, el algoritmo realiza solo una comparación y encuentra el elemento de inmediato. El límite inferior del tiempo de ejecución en este caso es $c$ que corresponde al tiempo de hacer sólo una comparación.

**Ventajas del análisis asintótico de los algoritmos:**

* **Precisión:** Los límites superior e inferior proporcionan una descripción más precisa del comportamiento del algoritmo.
* **Facilidad de comprensión:** Estimando con las notaciones asintóticas la complegidad de los algoritmos podemos determinar de manera fácil y sencilla si el algoritmo que estamos desarrollando es suficientemente eficiente para utilizarlo en nuestros desarrollos.

### Notación Big $\mathcal{O}$

La notación **big $\mathcal{O}$** se utiliza para describir un **límite superior** en la complejidad del algoritmo que requerido por un algoritmo en el peor de los casos.

#### **Definición informal de Big $\mathcal{O}$**

Sería conveniente tener una forma de notación asintótica que signifique *"en el peor de los casos el algoritmo tarda ..."* ó *"el tiempo de ejecución crece a lo más por este tanto, pero puede crecer más lentamente"*. Usamos la **big $\mathcal{O}$** justo para estas ocasiones. 

Si un tiempo de ejecución es $T(n)$, entonces para $n$ suficientemente grande, el tiempo de ejecución es a lo más $cf(n)$ para alguna constante $c$. Aquí está cómo pensar acerca de un tiempo de ejecución que es $\mathcal{O}(f(n))$:

- **Ejemplo**: Si tenemos un algoritmo que haciendo el análisis asintótico **en el peor caso** identificamos $2$ etapas de 

  - $6n^2$ operaciones y
  - $100n + 300$ operaciones
  
  En total la complegidad total sería

  $$6n^2 + 100n + 300$$

  Podemos decir que el tiempo de ejecución es $\mathcal{O}(n^2)$. Usamos la notación big $\mathcal{O}$ para **cotas superiores asintóticas**, ya que acota el crecimiento del tiempo de ejecución por arriba para entradas suficientemente grandes.

#### **Definición formal de Big $\mathcal{O}$**

*Sean $f(n)$ y $g(n)$ funciones no negativas definidas sobre los números reales. Decimos que* 

$$f(n) = \mathcal{O}(g(n))$$

*si existen constantes positivas $a$ y $n_0$ tales que:*

$$
0 \leq f(n) \leq a \cdot g(n) \quad \text{para todo} \quad n \geq n_0
$$

<img src="/ABlog/assets/0001_big_o.png" alt="img: gráfica big o">

En otras palabras, $f(n)$ es $\mathcal{O}(g(n))$ si hay una constante multiplicativa $a$ que puede usarse para escalar $g(n)$ de modo que siempre sea mayor o igual a $f(n)$ para todos los valores de $n$ suficientemente grandes.

### Notación Big $\Omega$
La notación **Omega** se utiliza para describir un **límite inferior** de la complejidad que es requerido por un algoritmo en el mejor de los casos.

#### **Definición informal de Big $\Omega$**

Sería conveniente tener una forma de notación asintótica que signifique *"en el mejor de los casos el algoritmo tarda ..."* o *"el tiempo de ejecución crece al menos por este tanto, pero puede crecer más rápidamente"*. Usamos la **big $\Omega$** justo para estas ocasiones. 

Si un tiempo de ejecución es $T(n)$, entonces para $n$ suficientemente grande, el tiempo de ejecución es al menos $c \cdot f(n)$ para alguna constante $c$. Aquí está cómo pensar acerca de un tiempo de ejecución que es $\Omega(f(n))$:

- **Ejemplo**: En el caso de una **búsqueda lineal**, el **mejor caso** ocurre cuando el elemento buscado es el primer elemento de la lista. En este caso, el tiempo de ejecución es constante, ya que solo se verifica un elemento. Por lo tanto, podemos decir que $T(n) = \Omega(1)$.

Usamos la notación big $\Omega$ para **cotas inferiores asintóticas**, ya que acota el crecimiento del tiempo de ejecución por abajo para entradas suficientemente grandes.

#### **Definición formal de Big $\Omega$**

*Sean $f(n)$ y $g(n)$ funciones no negativas definidas sobre los números reales. Decimos que* 

$$f(n) = \Omega(g(n))$$

*si existen constantes positivas $b$ y $n_0$ tales que:*

$$
0 \leq b \cdot g(n) \leq f(n) \quad \text{para todo} \quad n \geq n_0
$$

<img src="/ABlog/assets/0002_big_omega.png" alt="img: gráfica big omega">

En otras palabras, $f(n)$ es $\Omega(g(n))$ si hay una constante multiplicativa $b$ que puede usarse para escalar $g(n)$ de modo que siempre sea menor o igual a $f(n)$ para todos los valores de $n$ suficientemente grandes.

### Notación Big $\Theta$
La notación big $\Theta$ proporciona una **acotación precisa** de una función, la cual nos permite describir un **límite superior e inferior al mismo tiempo**.

#### **Definición informal de Big $\Theta$**

Sería conveniente tener una forma de notación asintótica que signifique *"en promedio el algoritmo tarda ..."* o *"el tiempo de ejecución crece exactamente por este tanto, no más ni menos"*. Usamos la **big $\Theta$** justo para estas ocasiones. 

Si un tiempo de ejecución es $T(n)$, entonces para $n$ suficientemente grande, el tiempo de ejecución es "exactamente" $cf(n)$ para alguna constante $c$. Aquí está cómo pensar acerca de un tiempo de ejecución que es $\Theta(f(n))$:

- **Ejemplo**: Si tenemos un algoritmo que imprima $n$ veces:

  ```sh
  Hello World!
  ```

  **Tanto en el peor como en el mejor de los casos** se deben hacer n repeticiones. Por lo tanto, podemos decir que $T(n) = \Theta(n)$.

Usamos la notación big $\Theta$ para **cotas asintóticas exactas**, ya que acota el crecimiento del tiempo de ejecución tanto por arriba como por abajo para entradas suficientemente grandes.

#### **Definición formal de Big $\Theta$**

*Sean $f(n)$ y $g(n)$ funciones no negativas definidas sobre los números reales. Decimos que* 

$$f(n) = \Theta(g(n))$$

*si existen constantes positivas $a$, $b$ y $n_0$ tales que:*

$$
0 \leq b \cdot g(n) \leq f(n) \leq a \cdot g(n) \quad \text{para todo} \quad n \geq n_0
$$

<img src="/ABlog/assets/0003_big_theta.png" alt="img: gráfica big theta">

En otras palabras, $f(n)$ es $\Theta(g(n))$ si hay constantes multiplicativas $a$ y $b$ que pueden usarse para escalar $g(n)$ de modo que siempre sea mayor o igual que $f(n)$ por abajo y menor o igual que $f(n)$ por arriba para todos los valores de $n$ suficientemente grandes.

## Complejidades de Algoritmos

- **Complejidad temporal $T(n)$:** mide el tiempo de ejecución de un algoritmo en función del tamaño de la entrada. Es crucial para determinar la eficiencia de un algoritmo.

- **Complejidad espacial $E(n)$:** mide la cantidad de memoria requerida por un algoritmo en función del tamaño de la entrada. Esto es importante para garantizar que el algoritmo pueda ejecutarse en un entorno con recursos limitados.

- **Complejidad energética:** mide la cantidad de energía consumida por un algoritmo. Esto es especialmente relevante en dispositivos móviles y sistemas embebidos donde el consumo de energía es una preocupación crítica.

- **Complejidad de latencia en red** mide el tiempo de respuesta de un algoritmo en un entorno de red. Es fundamental en aplicaciones distribuidas y en la optimización del rendimiento en redes.

- **Otras complejidades:** Dependiendo del propósito en que se realiza un algoritmo es posible que puedan presentarse otras complejidades que deban ser analizadas para garantizar eficiencia.

## Cálculo de complegidad temporal con el Teorema Maestro

El **teorema maestro** es una herramienta poderosa para resolver relaciones de recurrencia que aparecen en el análisis de algoritmos recursivos. Permite determinar la complejidad temporal de estos algoritmos de manera sencilla y directa. El teorema maestro aplica a relaciones de recurrencia de la forma:

$$ T(n) = aT\left(\frac{n}{b}\right) + f(n) $$

donde $a \geq 1$ y $b > 1$ son constantes, y $f(n)$ es una función asintótica positiva. El teorema maestro proporciona tres casos que cubren todas las posibles relaciones entre $f(n)$ y $n^{\log_b{a}}$, permitiendo una rápida evaluación de la complejidad temporal del algoritmo.

### Observaciones

El Teorema Maestro es **muy útil** para analizar el tiempo de ejecución de algoritmos recursivos que dividen un problema en subproblemas de tamaño $n/b$ y luego combinan las soluciones de los subproblemas en tiempo lineal $f(n)$.

### **Teorema Maestro**

*Dado un algoritmo con complejidad temporal asintótica:*

$$
T(n) = a T\left(\frac{n}{b}\right) + f(n)
$$

*La solución a la recurrencia está dada por:*

- *Si $f(n) = \mathcal{O}(n^{\log_{b} a - \epsilon})$ para algún $\epsilon > 0$, entonces*
  
  $$T(n) = \Theta(n^{\log_{b} a}).$$
- *Si $f(n) = \Theta(n^{\log_{b} a})$, entonces*
  
  $$T(n) = \Theta(n^{\log_{b} a} \log n).$$
- *Si $f(n) = \Omega(n^{\log_{b} a + \epsilon})$ para algún $\epsilon > 0$ y $a f\left(\frac{n}{b}\right) \leq c f(n)$ para algún $c < 1$ y para $n$ suficientemente grande, entonces*

  $$T(n) = \Theta(f(n)).$$

Este teorema proporciona una manera eficiente de determinar la complejidad temporal de muchos algoritmos recursivos comunes.

## Referencias

1. Cormen, Thomas H., Leiserson, Charles E., Rivest, Ronald L., & Stein, Clifford. (2022). *Introduction to Algorithms*. MIT Press.

2. Material sobre notación asintótica en [Khan Academy: Notación Asintótica](https://es.khanacademy.org/computing/computer-science/algorithms/asymptotic-notation/a/asymptotic-notation)

**¡Gracias por leer este post!**
