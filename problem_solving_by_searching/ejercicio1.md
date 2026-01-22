# 🗺️ Ejercicio 1: Búsqueda de Rutas (NPC)

## 1. Definición del Problema

Queremos llevar a un NPC desde un punto de inicio hasta una meta en un tablero con muros, minimizando costes o pasos según el algoritmo.

* **Mapa:** Cuadrícula de $6 \times 5$.
* **Estado Inicial ($S_0$):** Casilla `(5, 4)`.
* **Metas posibles:** `(2, 3)` y `(4, 1)`.
* **Movimientos:** `{Arriba, Abajo, Izquierda, Derecha}`.
* **Costes:**
  * ↕️ Vertical: **1**
  * ↔️ Horizontal: **2**

![Mapa del Ejercicio](./mapa_ejercicio_1.png)

---

## 2. Algoritmos Aplicados

###      2.1. Búsqueda en Anchura (BFS)

El algoritmo explora el mapa por "capas" o niveles de profundidad. Utiliza una **Cola (FIFO)** para gestionar la frontera.

**Datos de ejecución:**
* **Estrategia:** Expandir nodos superficiales primero.
* **Orden de operadores:** Arriba, Abajo, Izquierda, Derecha.
* **Ignora costes:** Busca el camino con menor número de pasos.

>
> ![Árbol BFS](./anchura_docs/1.png)
> ![Árbol BFS](./anchura_docs/2.png)
> ![Árbol BFS](./anchura_docs/3.png)
> ![Árbol BFS](./anchura_docs/4.png)
> ![Árbol BFS](./anchura_docs/5.png)
> ![Árbol BFS](./anchura_docs/6.png)
> ![Árbol BFS](./anchura_docs/7.png)

#### 🏆 Solución Final (BFS)

* **Camino encontrado:** `(5,4) → (4,4) → (4,5) → (3,5) → (2,5) → (2,4) → (2,3)`
* **Profundidad:** 6 pasos.
* **Coste Acumulado ($g$):** 9 (Calculado como: $1+2+1+1+2+2$).


---

### 2.2. Búsqueda en Profundidad (DFS)
🚧 **En construcción...**

---

###  2.3. Búsqueda de Coste Uniforme (UCS)
🚧 **En construcción...**


---

### 2.4. Algoritmo A*
🚧 **En construcción...**



---