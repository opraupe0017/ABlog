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

## Ejemplo de árbol binario de búsqueda por edad de personas

Usando la clase `Persona` y la clase `Node` que se encuentran en el artículo [Representación de datos, comprensión de estructuras y Nodo en `C++`](https://opraupe0017.github.io/ABlog/posts/data-dummies/), considere el siguiente árbol binario de búsqueda capaz de almacenar las personas usando sus edades como orden.

{::options parse_block_html="true" /}
<details><summary markdown="span">Código de cabecera para la clase de árbol binario de búsqueda `bst.h`</summary>
```cpp
#ifndef BST_H
#define BST_H

#include "node.h"
#include <iostream>
#include <vector>    // Incluye la librería vector para usar vectores

using namespace std;

class BST {
private:
    Node *root;
    BST *L;
    BST *R;
    int size;

public:
    BST();                         // Constructor por defecto
    ~BST();                        // Destructor para liberar la memoria

    // Métodos para manipular el árbol binario de búsqueda
    void insert(Node &node);            // inserta un nodo en el árbol      
    bool isEmpty() const;               // verifica si el árbol está vacío
    // Node getRoot() const;               // Entrega el nodo raiz del árbol si existe
    // BST* getL() const;                  // Entrega el apuntador a subárbol izq del árbol si existe
    // BST* getR() const;                  // Entrega el apuntador a subárbol der del árbol si existe
    Node search(const int edad) const;  // busca un nodo en el árbol que coincida con la edad
    // void update(const Node &node);      // actualiza un nodo en el árbol
    // void remove(const Node &node);      // Busca un nodo y lo elimina del árbol
    void printInOrden() const;          // imprime el árbol en inorden
    // void printPreOrder() const;         // imprime el árbol en preorden
    // void printPostOrder() const;        // imprime el árbol en postorden
    // vector<Node *> getInOrder() const;  // retorna un vector con los nodos del árbol en orden ascendente (Inorden)
    // vector<Node *> getPreOrder() const; // retorna un vector con los nodos del árbol en preorden
    // vector<Node *> getPostOrder() const;// retorna un vector con los nodos del árbol en postorden
    int getSize() const;                // retorna el tamaño del Array
};

#endif // BST_H
```
{: file="bst.h"  .shadow }
</details>

<details><summary markdown="span">Código de para la clase de árbol binario de búsqueda `bst.cpp`</summary>
```cpp
#include "bst.h"
#include <stdexcept> // Para std::invalid_argument

BST::BST() {
    root = nullptr;
    L = nullptr;
    R = nullptr;
    size = 0;
}

BST::~BST() {
    delete L;
    delete R;
}

void BST::insert(Node &node) {
    if (size == 0) root = &node;
    else if (node.getData() < root->getData() || node.getData() == root->getData()) {
        if (L == nullptr) L = new BST();
        L->insert(node);
    }
    else if (node.getData() > root->getData()) {
        if (R == nullptr) R = new BST();
        R->insert(node);
    }
    size++;
}

bool BST::isEmpty() const {
    if (size == 0) {
        return true;
    }
    else {
        return false;
    }
}

Node BST::search(const int edad) const {
    Node nodo_vacio = Node();

    if (size == 0) {
        return nodo_vacio;
    }

    if (edad == root->getData().getEdad()) {
        return *root;
    }
    else if (edad < root->getData().getEdad()) {
        if (L == nullptr) {
            return nodo_vacio;
        }
        return L->search(edad);
    }
    else {
        if (R == nullptr) {
            return nodo_vacio;
        }
        return R->search(edad);
    }
}

void BST::printInOrden() const {
    if (L != nullptr) L->printInOrden();                // Llamada recursiva al operador << para el subárbol izquierdo
    cout << "(" << root->getData() << "), ";
    if (R != nullptr) R->printInOrden();                // Llamada recursiva al operador << para el subárbol derecho
}

int BST::getSize() const {
    return size;
}

```
{: file="bst.cpp"  .shadow }
</details>

<details><summary markdown="span">Código de prueba para árbol binario de búsqueda `main.cpp`</summary>
```cpp
#include "bst.h"     // Incluye el archivo de cabecera bst.h
#include <cstdlib>    // Para std::rand y std::srand
#include <string>     // Para trabajar con cadenas de texto
#include <vector>     // Para trabajar con arreglos dinámicos

int main() {
    // Inicializar el generador de números aleatorios con el tiempo actual
    std::srand(0);

    // Crear vector de nombres
    std::vector<std::string> nombres = {"Hugo", "Paco", "Luis", "Rosita"};

    // Crear un vector de objetos Node
    std::vector<Node> nodos;

    // Genera pregunta en consola de cuántas personas quiere generar
    int numPersonas;
    std::cout << "Ingrese el número de personas que desea generar: ";
    std::cin >> numPersonas;

    // Generar nodos con personas de nombres y edades aleatorias
    for (int i = 0; i < numPersonas; ++i) { // Generar numPersonas nodos como ejemplo
        std::string nombreAleatorio = nombres[std::rand() % nombres.size()]; // Nombre aleatorio de la lista
        int edadAleatoria = std::rand() % 101; // Edad aleatoria entre 0 y 100
        Persona personaAleatoria(nombreAleatorio, edadAleatoria);
        nodos.emplace_back(personaAleatoria);
    }

    // Imprimir los datos de cada nodo
    for (const auto& nodo : nodos) {
        std::cout << nodo.getData() << std::endl;
    }

    // Crear un árbol binario de búsqueda
    BST arbol = BST();

    // Insertar cada nodo en el árbol
    for (auto& nodo : nodos) {
        arbol.insert(nodo);
    }
    
    std::cout << "\n-----------------------------\n";

    // Imprimir el árbol en inorden
    arbol.printInOrden();

    std::cout << "\n-----------------------------\n";

    // Preguntar el tamaño del árbol
    cout << arbol.getSize() << endl;

    std::cout << "\n-----------------------------\n";

    // Preguntar el tamaño del árbol
    cout << arbol.search(66).getData() << endl;

    return 0;
}
```
{: file="main.cpp"  .shadow }
</details>
{::options parse_block_html="false" /}

---

## Actividad

> **Actividad:** Implementar en `C++` los métodos faltantes que se sugieren en `bst.h` y hacer pruebas de ellos.
{: .prompt-danger .shadow }

---

**!Gracias por leer este artículo!**
