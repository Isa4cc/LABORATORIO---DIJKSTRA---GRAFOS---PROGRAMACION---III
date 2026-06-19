# Laboratorio: Algoritmo de Dijkstra - Optimización de Consumo Energético

## Objetivo

Implementar el algoritmo de Dijkstra para resolver un problema real de optimización: encontrar la ruta de **menor consumo energético** para un vehículo eléctrico que se desplaza por la red vial de Quito, desde el **Valle de los Chillos** hasta **UDLA Park**.

## Resumen de la Actividad

Se modeló la red vial de Quito como un **grafo ponderado no dirigido** donde:
- Los **vértices** representan puntos importantes de la ciudad (6 ubicaciones reales)
- Las **aristas** representan vías de conexión (8 tramos bidireccionales)
- Los **pesos** representan el consumo energético aproximado en **Wh** (vatios-hora)

El algoritmo de Dijkstra encuentra automáticamente la ruta óptima minimizando el consumo total de energía.

### Conceptos Evaluados

| # | Concepto | Componente |
|---|----------|------------|
| 1 | Implementar `compareTo()` | `NodoPrioridad` - Comparable y PriorityQueue |
| 2 | Completar el cálculo de `nuevoCosto` | `Grafo` - Modificación de aristas |
| 3 | Actualizar distancias y predecesores | `Grafo` - Núcleo de Dijkstra |
| 4 | Gestionar nodos visitados | `Grafo` - Optimización del algoritmo |
| 5 | Reconstruir la ruta final | `Grafo` - Manipulación de estructuras dinámicas |
| 6 | Responder preguntas de reflexión | Comprensión conceptual |

## Estructura Base del Proyecto

```
LABORATORIO---ALGORITMOS-DE-ORDENAMIENTO---PROGRA---III/
├── Arista.java           # Clase que representa una conexión (arista) con peso en Wh
├── NodoPrioridad.java    # Nodo para la PriorityQueue, implementa Comparable
├── Grafo.java            # Grafo ponderado + implementación de Dijkstra
├── ResultadoRuta.java    # Clase de resultado: ruta + consumo total
├── Main.java             # Punto de entrada con el escenario de Quito
├── README.md             # Este archivo
└── out/                  # Archivos compilados (.class)
```
## Grafo del Problema

### Vértices (6 nodos)

| Nodo | Ubicación Real |
|------|----------------|
| Valle de los Chillos | Zona sur de Quito |
| El Trébol | Intersección vial principal |
| La Marín | Centro histórico |
| La Carolina | Zona norte comercial |
| Granados | Zona residencial |
| UDLA Park | Universidad de Las Américas |

### Aristas (8 tramos bidireccionales)

| Origen | Destino | Consumo (Wh) |
|--------|---------|:------------:|
| Valle de los Chillos | El Trébol | 120 |
| El Trébol | La Marín | 80 |
| El Trébol | Granados | 160 |
| La Marín | La Carolina | 100 |
| La Carolina | UDLA Park | 70 |
| Granados | UDLA Park | 90 |
| Valle de los Chillos | Granados | 300 |
| La Marín | UDLA Park | 150 |

### Resultado del Algoritmo

```
Ruta óptima: Valle de los Chillos → El Trébol → La Marín → La Carolina → UDLA Park
Consumo total: 370 Wh
```

**Comparación con rutas alternativas:**

| Ruta | Consumo |
|------|:-------:|
| Valle → Trébol → Marín → Carolina → UDLA | **370 Wh** ✓ |
| Valle → Trébol → Marín → UDLA | 350 Wh |
| Valle → Trébol → Granados → UDLA | 370 Wh |
| Valle → Granados → UDLA | 390 Wh |

## Análisis de Complejidad

| Operación | Complejidad |
|-----------|:-----------:|
| Inicialización | O(V) |
| Extracción de mínimo (cada nodo) | O(log V) × V = O(V log V) |
| Relaxación de aristas (cada arista) | O(log V) × E = O(E log V) |
| Reconstrucción de ruta | O(V) |
| **Total** | **O((V + E) log V)** |

Donde V = número de vértices y E = número de aristas.

## Impacto Ambiental

La optimización de rutas para vehículos eléctricos tiene un impacto ambiental significativo:

- **Reducción del consumo energético:** Encontrar rutas óptimas reduce el consumo de electricidad, lo que indirectamente reduce la demanda energética y las emisiones de CO₂ asociadas a la generación eléctrica
- **Extensión de autonomía:** Rutas eficientes permiten recorrer mayor distancia con la misma carga de batería
- **Reducción del tráfico:** Rutas óptimas distribuyen mejor el flujo vehicular
- **Promoción de la movilidad eléctrica:** Demostrar que la tecnología permite optimizar rutas incentiva la adopción de vehículos eléctricos

En el contexto de Quito, donde la geografía montañosa afecta significativamente el consumo energético, este tipo de optimización es especialmente relevante.

## Conclusiones

1. El algoritmo de Dijkstra es una herramienta poderosa para resolver problemas de caminos mínimos en grafos ponderados
2. La implementación eficiente requiere el uso de `PriorityQueue` y `HashSet` para garantizar la complejidad O((V + E) log V)
3. El modelo de grafo permite representar de forma fiel la red vial de una ciudad
4. Los pesos del grafo pueden modelar diferentes criterios de optimización (consumo, tiempo, distancia)
5. La comprensión de las estructuras de datos es fundamental para implementar algoritmos correctamente

---
*Laboratorio de Programación III - Universidad de Las Américas (UDLA)*


