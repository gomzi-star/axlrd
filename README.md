# Modelo de Axelrod
En general supondremos una red cuadrada de largo $L$ , por ende $N=L^2$ nodos. Sin embargo, el modelo fue implementado sobre grafos, guiandonos por la libreria [NetworkX](https://networkx.org/documentation/stable/index.html), podemos decir entonces que una red cuadrada (triangular) es equivalente a un grafo regular de grado 4 (3). 

La definición del algoritmo y su implementación para las dsititntas topologias de redes y parámetros se puede encontrar en [Notebook Colab](https://colab.research.google.com/drive/1Rg4LpwvNVD4K7EktB4BHt4mPsKNZG9fS?usp=sharing). En la primera sección ***DEFINITIONS***  definimos la inicialización [***INIT***] de redes (regulares, completas y scale free) junto con un mapeo de colores para cada estado posible $Q^F$ y luego los pasos [***STEP***,***STEPUB***] tanto para interacciónes sin y con publicidad activa. 
> Nota: La cercanía en el mapeo de colores no siempre significa siempre la cercania entre vectores, en el sentido de carateristicas parecidas.

Mostramos a continuación los resultados obtenidos (en el mismo orden que la notebook)

## Red Cuadrada de largo $L=4$
Empezamos con $N=L^2=16$ nodos en un grafo regular de grado 4 , es decir 4 vecinos por nodo. 

Elegimos primero $F=Q=3$
<p align="center">
  <img src="images/Cuadrada(3-3).png" width="70%">
</p>

Luego $F=2,Q=5$
<p align="center">
  <img src="images/Cuadrada(2-5).png" width="70%">
</p>

Seguimos con $F=5,Q=3$
<p align="center">
  <img src="images/Cuadrada(5-3).png" width="70%">
</p>

Y por ultimo  $F=5,Q=5$
<p align="center">
  <img src="images/Cuadrada(5-5).png" width="70%">
</p>

## Red Cuadrada, Triangular y Grafo Completo sobre $F=10$
Fijamos ahora $F=10$, y variamos $L,Q$ y la topología de la red en grafos regulares de grado 4, 3 y grafos completos.

Primero para $L=4,Q=2$ comparamos sobre $t=600$ pasos.
<p align="center">
  <img src="images/F10(4-2)Cuadrada.png" width="70%">
</p>

<p align="center">
  <img src="images/F10(4-2)Triangular.png" width="70%">
</p>

<p align="center">
  <img src="images/F10(4-2)AllvAll.png" width="70%">
</p>

A continuación aumentamos el tamaño del sitema y las posibilidades  $L=6,Q=4$ y comparamos sobre $t=12000$ pasos.
<p align="center">
  <img src="images/F10(6-4)Cuadrada.png" width="70%">
</p>
<p align="center">
  <img src="images/F10(6-4)Triangular.png" width="70%">
</p>

<p align="center">
  <img src="images/F10(6-4)AllvAll.png" width="70%">
</p>

Manteniendo las posibilidades $Q=4$ con un mayor tamaño $L=8$ y comparamos sobre $t=30000$ pasos.
<p align="center">
  <img src="images/F10(8-4)Cuadrada.png" width="70%">
</p>

<p align="center">
  <img src="images/F10(8-4)Triangular.png" width="70%">
</p>

<p align="center">
  <img src="images/F10(8-4)AllvAll.png" width="70%">
</p>

Seguimos con $L=10,Q=5$
<p align="center">
  <img src="images/F10(10-5)Cuadrada.png" width="70%">
</p>
<p align="center">
  <img src="images/F10(10-5)Triangular.png" width="70%">
</p>
<p align="center">
  <img src="images/F10(10-5)AllvAll.png" width="70%">
</p>

Y por ultimo aumentamos masivamente el tamaño $L=18$ con la misma cantidad de opciones anterior $Q=5$
<p align="center">
  <img src="images/F10(18-5)Cuadrada.png" width="70%">
</p>
<p align="center">
  <img src="images/F10(18-5)Triangular.png" width="70%">
</p>
<p align="center">
  <img src="images/F10(18-5)AllvAll.png" width="70%">
</p>

No probamos para $Q\geq 6$, pues el mapeo de colores consume mas recursos de los disponibles.

## $Q$ vs $S_{max}$ en un Red Cuadrda
Comparamos ahora la proporicion de la población mayoritaria $100\cdot (S_{max}/N)$ según la cantidad de posibilidades $Q$, en grafos regulares de grado 4 para distintos valores de $L$ y $F$.

Primero para $F=2$ y tamaños $L=4$ (azul) y $L=10$ (naranja), variamos para los naturales $Q\in[1,15]$ y sobre cada uno de estos valores tomamos el promedio de $30$ evoluciones de $10000$ pasos.
<p align="center">
  <img src="images/QvSmax Cuadrada(4-2).png" width="40%">
  <img src="images/QvSmax Cuadrada(10-2).png" width="40%">
</p>

Luego para $F=10$ y tamaño $L=4$ (azul) variamos para los naturales $Q\in[1,100]$ y sobre cada uno de estos valores tomamos el promedio de $40$ evoluciones de $10000$ pasos. Por otro lado para tamaño $L=10$ (naranja) variamos para los naturales $Q\in[1,15]$ y sobre cada uno de estos valores tomamos el promedio de $30$ evoluciones de $20000$ pasos
<p align="center">
  <img src="images/QvSmax Cuadrada(4-10).png" width="40%">
  <img src="images/QvSmax Cuadrada(10-10).png" width="40%">
</p>

## Grafos Scale Free con y sin 'publicidad'
Para finalizar analizamos el modelo el grafos scale free, generados con el algoritmo [scale_free_graph](https://networkx.org/documentation/stable/reference/generated/networkx.generators.directed.scale_free_graph.html) con los parámetros de generación *alpha*,*beta* y *gamma* por default. Comparamos también con la variante donde a cada paso de interacción cultural, hay un agente 'externo' de publicidad que también interfiere en la red.

Elegimos primero $L=4,F=2,Q=2$
<p align="center">
  <img src="images/ScaleFree(4-2-2).png" width="70%">
</p>

<p align="center">
  <img src="images/ScaleFreePub(4-2-2).png" width="70%">
</p>

Y después $L=10,F=8,Q=2$
<p align="center">
  <img src="images/ScaleFree(10-8-2).png" width="70%">
</p>
<p align="center">
  <img src="images/ScaleFreePub(10-8-2).png" width="70%">
</p>

Por último graficamos $Q$ vs $100(S_{max}/N)$ en el tamaño 	$L=4$ con $F=10$.  Variamos para los naturales $Q\in[1,100]$ con promedio de $30$ evoluciónes por caso.

En el primer caso elegimos evoluciónes de $1000$ pasos y para el segundo de $10000$ pasos, mostando en verde los valores de la red sin publividad y en rojo los de la red con publicidad activa
<p align="center">
  <img src="images/QvSmax ScaleFree(4-10-1e3).png" width="40%">
  <img src="images/QvSmax ScaleFree(4-10-1e4).png" width="40%">
</p>
