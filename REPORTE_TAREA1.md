En este trabajo se planteó el problema de encontrar rutas óptimas en una red de estaciones, considerando tanto el tipo de producto transportado como los certificados necesarios en cada estación. Cada nodo de la red representa una estación con atributos de costo y certificado, mientras que las acciones corresponden a los desplazamientos válidos entre estaciones conectadas. El objetivo es llegar desde la estación inicial (E1) hasta la estación final (E23), minimizando el costo total y respetando las restricciones de cada producto.

Para modelar el problema se utilizó una lista de pares de adyacencias junto con otra lista de representación de los atributos de cada estación. Esta elección permitió manejar el grafo de manera flexible, eficiente y con una visualización clara. Aunque en teoría el espacio de estados incluye todas las combinaciones posibles entre estaciones y productos, las restricciones de certificado reducen el espacio efectivo. Además, el factor de ramificación está acotado: en el peor caso, un nodo puede tener hasta seis vecinos.

Se implementaron tres algoritmos de búsqueda: DFS, BFS y UCS. DFS  encuentro mas rapido un camino válido, aunque no garantiza que sea el más barato. BFS permitió hallar el recorrido más corto en número de pasos, mientras que UCS aseguró la minimización del costo total. La implementación se apoyó en estructuras simples y claras (clases, listas), y se complementó con funciones de validación y visualización paso a paso que facilitaron el análisis.

Los resultados se resumen en la siguiente tabla:

Algoritmo	Producto	Camino encontrado	Costo total

DFS	Sanitaria	E1 → E12 → E15 → E18 → E22 → E23	38.3

DFS	Temperatura	E1 → E2 → E5 → E8 → E10 → E23	49.4

BFS	Sanitaria	E1 → E14 → E20 → E23	19.0

BFS	Temperatura	E1 → E3 → E8 → E23	21.5

UCS	Sanitaria	E1 → E14 → E20 → E23	19.0

UCS	Temperatura	E1 → E3 → E8 → E23	21.5

El análisis muestra que DFS encuentra soluciones válidas, pero a un costo mucho mayor. BFS y UCS coinciden en este caso porque el camino con menos pasos también resulta ser el más barato, lo que no siempre ocurre en otros problemas. Así, UCS se confirma como el algoritmo más confiable cuando el criterio principal es minimizar el costo, mientras que BFS es útil cuando solo interesa el número de pasos y los costos son uniformes. DFS, en cambio, puede servir en grafos pequeños o para obtener una solución rápida, pero no es recomendable si se busca optimalidad.

Entre las limitaciones se encuentra que el modelo no incorpora dinámicas de cambio en los costos ni restricciones adicionales que podrían aparecer en escenarios más realistas. Ademas tampoco tiene forma de saber si se esta acercando o alejando del estado objetivo. Asimismo, BFS y UCS pueden requerir mucha memoria en grafos grandes, aunque en el caso de UCS esto se puede mitigar con estructuras más eficientes, como colas de prioridad.

El trabajo se desarrolló de manera colaborativa, donde cada integrante se encargó de implementar uno de los algoritmos: Pablo Tapia trabajó en BFS, Bryan Alburquenque en DFS y Joaquín Urrutia en UCS. Finalmente, se añadieron funciones de visualización en el notebook, que permiten observar el grafo con los caminos resaltados y comparar de forma intuitiva las soluciones encontradas.