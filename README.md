# Optimización de programación quirúrgica mediante búsqueda tabú

Proyecto desarrollado en el curso **Ciencia y Tecnología**, utilizando Python y Google Colab.

## Descripción

Implementación de un algoritmo de optimización para resolver un problema de planificación de pacientes en un entorno hospitalario. El objetivo consiste en encontrar el orden de atención que minimice el tiempo total de operación (*makespan*), considerando tres etapas secuenciales: anestesia, cirugía y recuperación.

El problema incorpora restricciones de capacidad, tiempos de preparación y limpieza de salas, y una política de bloqueo sin buffer (*blocking no-wait buffer*), que provoca que la saturación de una etapa afecte el funcionamiento de las anteriores.

## Solución implementada

Se desarrolló una heurística basada en **búsqueda tabú (Tabu Search)**, que utiliza:

- **Solución inicial:** ordenamiento mediante la regla SPT (*Shortest Processing Time*).
- **Generación de vecinos:** movimiento de inserción, desplazando un paciente a otra posición de la secuencia.
- **Criterio de selección:** evaluación de múltiples soluciones vecinas y selección de la mejor alternativa admisible.
- **Memoria tabú:** registro de los últimos movimientos para evitar ciclos y escapar de óptimos locales.
- **Criterio de aspiración:** permite aceptar movimientos tabú cuando producen una solución que supera el mejor resultado global encontrado.

La búsqueda está limitada a 20.000 evaluaciones por instancia.

## Evaluación

El algoritmo se evaluó sobre 30 instancias de distintos tamaños (8, 12 y 16 pacientes), comparándolo con reglas clásicas de planificación y una implementación de búsqueda por escalada (*Hill Climbing*).

También se realizaron experimentos de convergencia, comparación estadística mediante Wilcoxon pareado con corrección de Holm y validación frente a soluciones óptimas obtenidas por enumeración exhaustiva en instancias pequeñas.

## Tecnologías

- Python
- NumPy
- Pandas
- Matplotlib
- Google Colab

**Resultado:** el método obtuvo un ratio promedio de 0,9256 respecto de la mejor regla clásica, equivalente a una reducción promedio del 7,44 % en el makespan.
