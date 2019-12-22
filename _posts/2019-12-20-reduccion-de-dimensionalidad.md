---
layout: post
title: "Reducción de dimensionalidad"
post_url: "2019-12-20-reduccion-de-dimensionalidad"
categories:  [Algoritmos]
tags: [Machine Learning, Reducción de dimensionalidad, Algoritmos, Preprocesamiento]
[//]: # (author: "María García Gumbao")
[//]: # (description: "Una introducción al concepto de reducción de dimensionalidad, por qué y los tipos de técnicas existentes")
---

¿Qué es?
-------------

Las técnicas de reducción de dimensionalidad son métodos que se utilizan para reducir el número de variables de nuestros datos.

¿Por qué querríamos reducir la dimensionalidad?
----------------

Hay varios motivos y situaciones en los que conviene hacer esto:
1. La maldición de la dimensionalidad (_curse of dimensionality_). El principal motivo de reducir la dimensionalidad es que hay varios problemas que surgen cuando los datos tienen unas dimensiones muy altas. Entre ellos que necesitamos más datos para entrenar el modelo y que es más probable que nuestro modelo acabe produciendo un sobre-ajuste (_overfitting_).

   Siempre oímos que los modelos de _machine learning_ funcionan mejor cuantos más datos tengamos, sobre todo cuando se habla de algoritmos complejos como las redes neuronales, ¿por qué vamos a querer reducir el número de variables? Lo cierto es que cuando se habla de la cantidad de datos se hace referencia al número de muestras, o sea, el número de filas, y no tanto del número de variables. En realidad cuantas más variables (columnas) tengamos, más muestras necesitaremos para ser capaces de producir un modelo que de buenos resultados. 

   Por ejemplo, una simple recta en dos dimensiones se puede ajustar simplemente conociendo dos puntos en el espacio: $$A(x_A,y_A)$$ y $$B(x_B,y_B)$$
   
   $$y\ =\ m x+b → \left\{
      \begin{array}{l}
         m = \dfrac{y_B-y_A}{x_B-x_A}\\
         b= y_A - \dfrac{y_B-y_A}{x_B-x_A}·x_A
      \end{array}
   \right.$$

   Sin embargo, si nos vamos a la ecuación de la recta en 3-dimensiones $$(z= m_x  x+m_y  y+b)$$, no es posible resolverla únicamente con dos puntos, ya que el número de coeficientes a determinar es 3 $$(m_x,m_y,b)$$.

   Lo mismo ocurre cuando nuestro modelo se vuelve más complejo, así que podéis imaginaros cómo sería ajustar algo así en unos datos con unas 100 variables (y aun peor cuando nuestros datos no representan una recta, sino algo más complejo).

2. Eliminar variables irrelevantes y ruido. No todas las variables van a ser importantes para nuestro modelo, no porque tengamos acceso a ellas significa que debamos incluirlas si sabes que no hay ningún tipo de relación, sólo introducirían ruido y harían más difícil obtener un modelo preciso.
	
3. Reducir el tiempo de computación y el espacio de almacenamiento. Obviamente, cuantas menos columnas tengamos, menos cantidad de datos tendremos que manejar, y más fácil le será a nuestro ordenador hacer las operaciones necesarias.
	
4. Eliminar dependencias entre variables. Esto ayuda a la interpretación de los modelos, cuando dos variables son muy dependientes entre sí el modelo puede llegar a la conclusión de que sólo una de ellas es importante. Por ejemplo, imaginemos que tenemos un modelo de clasificación para ver si alguien es jugador de baloncesto o no, y dos de las variables de entrada son la altura de la persona en metros y en pulgadas. El modelo puede utilizar sólo una de esas variables para llegar a la conclusión final, pero ¿significa eso que la otra variables no es importante? Claro que no, tienen exactamente la misma importancia, pero como la información que aportan es la misma, el modelo no necesita utilizar ambas columnas.
	
5. Facilitar la visualización de los datos, especialmente cuando reducimos a 2 o 3 dimensiones.

Técnicas 
-----------

Hay dos tipos de métodos para reducir el número de variables:
* Selección de variables: Se trata de seleccionar sólo las variables más importantes para nuestro modelo.
* Extracción de características: Tratan de reducir la dimensionalidad a base de crear nuevas variables que combinen la información de las variables iniciales.

### Selección de variables 
La selección de variables consiste en identificar qué columnas son realmente relevantes para nuestro modelo objetivo, y deshacernos de todas las demás. Los algoritmos para realizar la selección se pueden clasificar en tres tipos:
* Métodos de filtrado: Basándose en alguna medida estadística se le asocia un valor a cada variable que permita ordenarlas y así seleccionar con cuáles te quedas o no.
Generalmente estudian las variables de manera independiente (univariante), o en relación con la variable objetivo únicamente.

* Métodos _wrapper_: Evalúan subconjuntos de variables para ver qué subconjunto produce mejores resultados en el modelo. Esta técnicas permiten detectar interacciones entre las variables, pero también pueden llevar a un sobreajuste de los datos (además de ser computacionalmente caras).
	
* Métodos embebidos: Buscan cómo contribuye cada variable a la precisión del modelo mientras este se está creando. Los más comunes son los métodos de regularización, que imponen restricciones extras al modelo.

### Extracción de características 
En lugar de usar los datos tal y como los tenemos este tipo de algoritmo intenta hacer una representación de los datos con menos dimensiones, siendo estas dimensiones nuevas variables que combinen la información de las variables originales de los datos.
Algunos ejemplos son:

* Análisis de componentes principales (PCA)
* Análisis de componentes independientes (ICA)
* Análisis discriminante lineal (LDA)
* Embebido Local Lineal (LLE)
* t-SNE
* UMAP
* Autoencoders

-------------------
Soy consciente de que algunos temas se han tratado de manera muy general, pero cada uno de los temas mencionados da para un post en sí mismo (o varios), por lo que es imposible contarlo todo. Si os interesa que profundice más en algún tema en concreto dejármelo en los comentarios. Tengo planeado profundizar en PCA, t-SNE y UMAP en un futuro, añadiré los links en este post en cuanto los haya publicado.

## Referencias
* [Geeks for Geeks - Introduction to Dimensionality Reduction](https://www.geeksforgeeks.org/dimensionality-reduction/)
* [Towars Data Science - Dimensionality Reduction for Machine Learning](https://towardsdatascience.com/dimensionality-reduction-for-machine-learning-80a46c2ebb7e)
* [Towards Data Science - Feature Extraction Techniques](https://towardsdatascience.com/feature-extraction-techniques-d619b56e31be)
* [Wikipedia - Dimensionality Reduction](https://en.wikipedia.org/wiki/Dimensionality_reduction#:~:targetText=In%20statistics%2C%20machine%20learning%2C%20and,feature%20selection%20and%20feature%20extraction.)
* [Wikipedia - Curse of dimensionality](https://en.wikipedia.org/wiki/Curse_of_dimensionality)

