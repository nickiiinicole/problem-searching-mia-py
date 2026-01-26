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

El árbol de búsqueda generado sigue la siguiente lógica:

### Paso 1: Inicio en (5, 4)
* El algoritmo expande los vecinos válidos.
* Se identifican: `(5,3)` [Arriba], `(5,5)` [Abajo], `(4,4)` [Izquierda].
* **Decisión:** Debido a la prioridad **1. Arriba**, el algoritmo elige visitar inmediatamente `(5, 3)`. Los otros nodos quedan en espera en la Pila.

### Paso 2: Nodo (5, 3)
* Desde la nueva posición, se expanden vecinos.
* Se identifican: `(5,2)` [Arriba], `(4,3)` [Izquierda], `(6,3)` [Derecha]. (Abajo se descarta por estar en lista Cerrada).
* **Decisión:** Se elige **Arriba** nuevamente, moviéndose a `(5, 2)`.

### Paso 3: Nodo (5, 2)
* Se expanden vecinos.
* Se identifican: `(5,1)` [Arriba], `(6,2)` [Derecha].
* **Decisión:** Se prioriza **Arriba**, moviéndose a `(5, 1)`.

### Paso 4: Nodo (5, 1) - Punto de Giro
* El algoritmo intenta ir **Arriba**, pero choca con el límite del tablero.
* Intenta ir **Abajo**, pero el nodo `(5,2)` ya fue visitado.
* Intenta ir **Izquierda**, y encuentra el nodo `(4, 1)`.
* Intenta ir **Derecha**, y encuentra el nodo `(6, 1)`.
* **Decisión:** Por orden de prioridad (Izquierda antes que Derecha), se mueve a `(4, 1)`.

### Paso 5: Nodo (4, 1)
* **Verificación:** El algoritmo comprueba si este estado coincide con la Meta.
* **Resultado:** ¡Éxito! Se detiene la búsqueda.

## 4. Resultado Final
El camino encontrado por el algoritmo DFS :

**Ruta:** `(5, 4) → (5, 3) → (5, 2) → (5, 1) → (4, 1)`

* **Total de pasos:** 4
* **Nodos expandidos:** 5
* **Nodos generados pero no visitados:** `(5,5)`, `(4,4)`, `(4,3)`, `(6,3)`, `(6,2)`, `(6,1)`.
---
