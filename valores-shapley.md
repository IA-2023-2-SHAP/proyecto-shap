# Valor de Shapley

## Juegos cooperativos TU

Un juego se puede pensar como una secuencia de movimientos. En cada uno de ellos, uno de los jugadores decide su actuación entre distintas posibilidades. Al final del juego se asigna un pago a los jugadores que depende de las decisiones que todos ellos hayan tomado. Podemos, por tanto, describir un juego como una función que asigna un pago a cada "posición final" posible en el mismo. En el caso de los juegos **utilidad transferible** o **TU** por sus siglas en ingles, se pueden formar grupos de jugadores (que denominaremos **coaliciones**) que fuercen determinados repartos. Así pues, un juego TU puede ser definido mediante una función que asigna a cada coalición
posible un número real que indica el pago asociado a dicha coalición[^2].

> Un juego TU es un par $(N, v)$ donde $N$ es el conjunto finito de jugadores y $v : \mathcal{P}(N) \to \mathbb{R}$ es una función que cumple que $v(∅) = 0$.

Un juegos TU también es conocido como un **juego cooperativo** o **juego de coalición**.

Uno de los principales problemas que plantea la teoría de juegos cooperativos TU es cómo repartir la ganancia total $v(N)$ entre todos los jugadores de manera equitativa y acorde con la participación individual de cada jugador. Una de las técnicas más utilizadas para dar solución a este problema
es el valor de Shapley[^3].

## Función característica

La función $v$ se llama función característica. La función $v$ tiene el siguiente significado: si $S$ es una coalición de jugadores, entonces $v(S)$, llamado el **valor de la coalición** $S$, describe la suma total esperada de pagos que los miembros de $S$ pueden obtener mediante la cooperación.

> La función característica $v$ de un juego TU es una función $v : \mathcal{P}(N)  \to \mathbb{R}$ que cumple que $v(∅) = 0$.

Su dominio es el conjunto de partes de $N$, es decir, conjunto de todos los subconjuntos de $N$, que denotamos por $\mathcal{P}(N)$ ó $2^N$. Dada una coalición $S ⊂ N$, $v(S)$
representa el pago asegurado por los jugadores de $S$, independientemente de las estrategias del resto de jugadores. Se denotará por $G(N)$ el conjunto de todos los **juegos TU**
con conjunto de jugadores $N$, y por $n$ la cardinalidad de $N$. Por simplicidad, en general identificaremos $(N, v)$ con su función característica $v$.

## Coalición

Se denomina **Coalición** a cualquier subconjunto no vacío de $N$. Para cada coalición $S ⊂ N$ está asociado un número $v(S)$ el cual representa el pago que se puede asegurar a los jugadores que forman parte de $S$, independientemente de lo que hagan los demás jugadores. El **valor de una coalición** se puede considerar como la cantidad mínima que puede obtener una coalición si todos los jugadores que forman parte de ella se asocian y juegan en equipo. En el caso de la fórmula de Shapley se denomina **Coalición** a cualquier subconjunto no vacío de $N \setminus \{i\}$, es decir, a cualquier subconjunto de jugadores que no contenga al jugador $i$.


## Valor de Shapley

El valor de Shapley es una forma de distribuir las ganancias totales a los jugadores, suponiendo que todos colaboran. Es una distribución "justa" en el sentido de que es la única distribución con ciertas propiedades deseables que se enumeran a continuación. 

Shapley, analizó durante mucho tiempo los juegos cooperativos y en 1953 propuso el concepto de valor de un juego $(N, v)$ dado para cada jugador $i ∈ N$ a través de la siguiente expresión [^4]: 

$$
\varphi_i(N,v)=\sum_{S \subseteq N \setminus
\{i\}} \frac{s!\;(n-s-1)!}{n!}(v(S\cup\{i\})-v(S))
$$


donde $n$ es el número total de jugadores $N$, $s$ es el numero de jugadores en la coalición $S$ y la suma se extiende sobre todos los subconjuntos $S$ de $N$ que no contienen al jugador $i$. 

$$
\varphi_i(N,v)= \sum_{S \subseteq N \setminus
\{i\}} {n \choose 1, s, n - s - 1}^{-1} (v(S\cup\{i\})-v(S))
$$

También tenga en cuenta que ${n \choose a, b, c}$ es el coeficiente multinomial. 

Aquí, los términos clave son:

- $\varphi_i(v)$: Es el Shapley value del jugador $i$ en el juego representado por la función de valor $v$.

- $N$: Es el conjunto de todos los jugadores (en nuestro caso, todas las características).

- $S \subseteq N \setminus \{i\}$: $S$ es una coalición que no contiene al jugador $i$ [^1].

- $|S|$ o $s$: Representa el número de jugadores en la coalición $S$.

- $|N|$ ó $n$: Es el número total de jugadores (características).

- $v(S \cup \{i\})$: Es el valor de la función $v$ cuando la coalición es ampliada para incluir al jugador $i$.

- $v(S)$: Es el valor de la función $v$ cuando solo consideramos la coalición $S$.

Muchas veces un juego TU denotado como $(N,v)$ se expresa tan solo como $v$ por practicidad. por lo que podemos tambien encontrar $\varphi_i(N,v)$ que seria equivalente a $\varphi_i(v)$

Esta fórmula puede parecer compleja, pero es esencialmente una suma ponderada de las diferencias en la contribución de la característica $i$ cuando se agrega a diferentes coaliciones. El término $\frac{s!(n - s - 1)!}{n!}$ representa la ponderación de las diferentes permutaciones posibles de las coaliciones.

Una fórmula equivalente alternativa para el valor de Shapley es:

$$
\varphi _{i}(v)={\frac {1}{n!}}\sum _{R}\left[v(P_{i}^{R}\cup \left\{i\right\})-v(P_{i}^{R})\right]
$$

donde la suma recorre todos los órdenes posibles de $n!$ jugadores $R$ y $P_i^R$ es el conjunto de jugadores en $N$ que preceden (estan antes de) a $i$ en el orden $R$. 


Finalmente, también se puede expresar como

$$
\varphi _{i}(v)={\frac {1}{n}}\sum _{S\subseteq N\setminus \{i\}}{\binom {n-1}{s}}^{-1}(v(S\cup \{i\})-v(S))
$$


que se puede interpretar como

$$
\varphi _{i}(v)={\frac {1}{\text{número de jugadores}}}\sum _{{\text{coalitions incluyendo }}i}{\frac {{\text{contribución marginal de }}i{\text{ a la coalición}}}{{\text{número de coaliciones excluyendo }}i{\text{ de este tamaño}}}}
$$

## Contribución marginal

El valor de Shapley, puede interpretarse como la
contribución marginal esperada del jugador $i$ o como un promedio de las contribuciones marginales $[v(S) − v(S − i)]$ de dicho jugador a todas las coaliciones no vacías 
$S ∈ \mathcal{P}(N)$, considerando que la coalición del jugador sea
equiprobable en tamaño $(1 ≤ s ≤ n)$ y que todas las coaliciones de tamaño $S$ tienen la misma probabilidad.

## Propiedades del valor de Shapley

El valor de Shapley tiene las siguientes propiedades deseables:

**1. Eficiencia**: La ganancia total se distribuye:
$$
\sum_{i\in N}\varphi _i(v) = v(N)
$$

**2. Simetría**: si i y j son dos actores que son equivalentes en el sentido de que:
$$
v(S\cup\{i\}) = v(S\cup\{j\})
$$
para cada subconjunto $S$ de $N$ que no contiene $i$ ni $j$, entonces $\varphi _i(v) = \varphi _j(v)$.

**3. Linealidad**: Si dos juegos cooperativos descritos por las
funciones de ganancia $v$ y $w$ son combinados, entonces la ganancia distribuida debería corresponder a la ganancia derivada de $v$ y $w$:

$$
\varphi _i(v+w) = \varphi _i(v) + \varphi _i(w)
$$

por cada $i$ en $N$.

También, por cada número real $a$:

$$
\varphi _i(a v) = a \varphi _i(v)
$$ 

por cada $i$ en $N$.

**4. Zero Player** (Jugador Nulo): El valor de Shapley $\varphi _i(v)$ de un jugador nulo $i$ en un juego v es cero. Un jugador $i$ es nulo en v si $v$ if $v(S\cup \{i\}) = v(S)$ para todas las coaliciones $S$.

De hecho, dado un conjunto de $N$ jugadores, el valor de Shapley es el único mapa a partir del conjunto de todos los juegos de vectores de ganancias que satisface todas las cuatro propiedades aquí mencionadas.

## Dividendos Harsanyi

La fórmula del valor de Shapley utiliza los Dividendos Harsanyi para calcular la contribución promedio de cada jugador a la sinergia de todas las coaliciones de las que es miembro.

John Charles Harsanyi, en colaboración con John Forbes Nash and Reinhard Selten, propusieron en 1959 [^6] la formula alternativa:
$$
\varphi_i(v) = \sum_{i \in S \subseteq N }{\frac{d_v(S)}{s}}
$$

donde $d_v(T)$ son los llamados **dividendos Harsanyi** $d_v \colon \mathcal{P}(N) \to \mathbb{R}$ el cual se define como[^7]:


$$
\begin{aligned}
d_{v}(\{i\})&=v(\{i\})\\
d_{v}(\{i,j\})&=v(\{i,j\})-d_{v}(\{i\})-d_{v}(\{j\})\\
d_{v}(\{i,j,k\})&=v(\{i,j,k\})-d_{v}(\{i,j\})-d_{v}(\{i,k\})-d_{v}(\{j,k\})-d_{v}(\{i\})-d_{v}(\{j\})-d_{v}(\{k\})\\
&\vdots \\
d_{v}(S)&=v(S)-\sum _{T\subsetneq S}d_{v}(T)
\end{aligned}
$$

El dividendo Harasanyi identifica el excedente que se crea por una coalición de jugadores en un juego cooperativo. Para especificar este superávit, el valor de esta coalición se corrige por el superávit que ya crean las subcoaliciones.


Una formula explicita para $d_v(T)$ es:

$$
d_v(T) = \sum_{T \subseteq S }{(-1)^{|S| - |T|}  v(T)}
$$

Podemos recuperar $v$ de $d_v$ con la ayuda de la formula
$$
v(S) = d_v(S) + \sum_{T \subseteq S }{d_v(T)}
$$

> En otras palabras, el "valor total" de la coalición $S$ proviene de sumar las *divisiones* de cada subconjunto posible de $S$. 

**Nota:** Los dividendos de Harsanyi pueden encontrarse en algunas literaturas como **sinergia**.

## Resumen de términos clave

* **Juego cooperativo**: Hay un conjunto $N$ (de $n$ jugadores) y una función $v$ que mapea subconjuntos de jugadores a los números reales: $v \colon 2^N \to \mathbb{R}$, con $v (\emptyset ) = 0$.
* **Función característica**: si $S$ es una coalición de jugadores, entonces $v(S)$, llamado el valor de la coalición $S$, describe la suma total esperada de pagos que los miembros de $S$ pueden obtener mediante la cooperación.
* **Coalición**: Un subconjunto de jugadores.
* **Sinergia**: La contribución de una coalición a la función de valor.

## Ejemplos

### Ejemplo simple

Consideremos el siguiente juego $(N,v)$ de dos jugadores:

$$
N = \{A, B\}
$$

$$
\begin{align*}
v(\{A\}) &= 10 \\
v(\{B\}) &= 10 \\
v(\{A, B\}) &= 20 \\
\end{align*}
$$

En este juego, el valor total del juego es $v(N) = 20$.

El valor de Shapley de $A$ es:

$$
\begin{align*}
\varphi_A(v)&=\sum_{S \subseteq N \setminus
\{A\}} \frac{s!\;(n-s-1)!}{n!}(v(S\cup\{A\})-v(S)) \\
&= \frac{0!\;(2-0-1)!}{2!}(v(\emptyset\cup\{A\})-v(\emptyset))... \\
...&+ \frac{1!\;(2-1-1)!}{2!}(v(\{B\}\cup\{A\})-v(A)) \\
&= \frac{1}{2} \left( v(\{A\}) - v(\emptyset) \right) + \frac{1}{2} \left( v(\{A, B\}) - v(\{B\}) \right) \\
&= \frac{1}{2} \left( 10 - 0 \right) + \frac{1}{2} \left( 20 - 10 \right)\\
&= 8
\end{align*}
$$

El valor de Shapley de $B$ es:

$$
\begin{align*}
\varphi_B(v) &= \frac{1}{2} \left( v(\{B\}) - v(\emptyset) \right) + \frac{1}{2} \left( v(\{A, B\}) - v(\{A\}) \right) \\
&= \frac{1}{2} \left( 10 - 0 \right) + \frac{1}{2} \left( 20 - 10 \right) \\
&= 8
\end{align*}
$$

Por lo tanto, los jugadores $A$ y $B$ recibirán cada uno un pago de $8$.


### Ejempĺo del juego de los guantes

El juego de los guantes es un juego cooperativo en el que los jugadores tienen guantes de la mano izquierda y de la mano derecha y el objetivo es formar parejas. Sea

$$
N=\{1,2,3\}
$$

donde los jugadores 1 y 2 tienen guantes de la mano derecha y el jugador 3 tiene un guante de la mano izquierda.

La función de valor para este juego cooperativo es

$$
v(S)=\begin{cases}
1 & \text{si } S \in \{ \{1,3\},\{2,3\},\{1,2,3\} \} \\
0 & \text{de lo contrario }
\end{cases}
$$

La fórmula para calcular el valor de Shapley es

$$
\varphi _{i}(v)={\frac {1}{n!}}\sum _{R}\left[v(P_{i}^{R}\cup \left\{i\right\})-v(P_{i}^{R})\right]
$$

donde $R$ es un ordenamiento de los jugadores y $P_i^R$ es el conjunto de jugadores en $N$ que preceden (estan antes) a $i$ en el orden $R$.

La siguiente tabla muestra las contribuciones marginales del jugador 1 ($CM_1$).

| Orden $R$ | $CM_1 = v(P_{1}^{R}\cup \{1\})-v(P_{1}^{R})$ |
|-----------|----------------------------------------------|
| 1,2,3     | $v(\{1\})−v(∅)=0−0=0$                        |
| 1,3,2     | $v(\{1\})−v(∅)=0−0=0$                        |
| 2,1,3     | $v(\{1,2\})−v({2})=0−0=0$                    |
| 2,3,1     | $v(\{1,2,3\})−v({2,3})=1−1=0$                |
| 3,1,2     | $v(\{1,3\})−v({3})=1−0=1$                    |
| 3,2,1     | $v(\{1,3,2\})−v({3,2})=1−1=0$                |


Observe que

$$
\varphi _1(v)=\left(\frac{1}{6}\right)(1)=\frac{1}{6}.
$$

Por un argumento de simetría se puede demostrar que

$$
\varphi _2(v)=\varphi _1(v)=\frac{1}{6}.
$$

Debido al axioma de eficiencia, la suma de todos los valores de Shapley es igual a 1, lo que significa que

$$
\varphi _3(v)=\frac{4}{6}=\frac{2}{3}.
$$

### Ejemplo de negocio

Considera una descripción simplificada de un negocio. Un propietario, $o$, proporciona capital crucial en el sentido de que, sin él/ella, no se pueden obtener ganancias. Hay $m$ trabajadores $w_1, \dots ,w_m$, cada uno de los cuales contribuye con una cantidad $p$ a la ganancia total. Sea

$$
N=\{o,w_1,\dots,w_m\}
$$

La función de valor para este juego de coalición es

$$
v(S)=\begin{cases}
mp & \text{si } o\in S\\
0 & \text{de lo contrario }
\end{cases}
$$

donde $m$ es el número de trabajadores que no son el propietario, es decir $m=|S∖\{o\}|$. Calcular el valor de Shapley para este juego de coalición conduce a un valor de $mp/2$ para el propietario y $p/2$ para cada uno de los $m$ trabajadores. Esto se puede entender desde la perspectiva de la sinergia. 
La función de sinergia es una función que mide el valor adicional que se crea cuando se añade un jugador a una coalición. 

$$
d_{v}(S)=v(S)-\sum _{T\subsetneq S}d_{v}(T)
$$


En este caso, la única sinergia que ocurre es entre el propietario y un trabajador individual. Por lo tanto, la función de sinergia $w$ es la siguiente:


$$
d_{v}(S)=\begin{cases}
p & \text{si } S=\{o,w_i\} \\
0 & \text{de lo contrario }
\end{cases}
$$

esta función de sinergia significa que la única sinergia que ocurre es entre el propietario y un trabajador individual. El valor de esta sinergia es igual a la contribución de un trabajador individual, que es igual a $p$.

En otras palabras, la función de sinergia se deduce de la función de valor al identificar las coaliciones que crean sinergia. En este caso, la única coalición que crea sinergia es la coalición que incluye al propietario y un trabajador individual.

Usando la fórmula anterior para el valor de Shapley en términos de $w$ calculamos

$$
\varphi _i(v) = \sum_{i \in S \subseteq N } \frac{d_{v}(S)}{|S|}
$$


$$
\varphi _{w_{i}}=\frac{d_{v}(\{o,w_i\})}{2}=\frac{p}{2}
$$

y

$$
\varphi _o=\sum_{i=1}^{m}{\frac{d_{v}(\{o,w_i\})}{2}=\frac{mp}{2}}
$$


## Enlaces de interés

* 5.9 Valores de Shapley https://fedefliguer.github.io/AAI/shapley.html


# Referencias

[^1]: Colaboradores de los proyectos Wikimedia. (2022, March 04). Diferencia de conjuntos - Wikipedia, la enciclopedia libre. Retrieved from <https://es.wikipedia.org/w/index.php?title=Diferencia_de_conjuntos>

[^2]: Bamio Martínez, D. (2023). El valor de Shapley. Trabajo Fin de Grao, Universidad de Santiago de Compostela. [En línea]. Disponible en: <https://minerva.usc.es/xmlui/bitstream/handle/10347/26022/Bamio%20Mart%C3%ADnez,%20David.pdf>

[^3]: Vesga Ferreira, J. C., Granados Acuña, G., & Sierra Carrillo, J. E. (2015). El valor de shapley como estrategia de optimización de recursos sobre Power Line Communication (PLC). Disponible en: <http://www.scielo.org.co/pdf/ince/v11n22/v11n22a09.pdf>

[^4]: L. S. Shapley, “A value for n-persons games in Contributions to the Theory of Games II,” Annals of Mathematics Studies, no. 28, pp. 307–317, 1953. 

[5^]: Handbook of the Shapley Value. (2019). United Kingdom: CRC Press. Retrived from: <http://rguir.inflibnet.ac.in/bitstream/123456789/16159/1/Handbook%20of%20the%20Shapley%20Value.pdf>

[^6]: Harsanyi, J.C. (1959) A bargaining model for cooperative n-person games. In: Tucker, A.W., Luce, R.D. (eds) Contributions to the theory of games IV. Princenton University Press, Princenton, pp. 325-355

[^7]: Grabisch, M. (2016). Set Functions, Games and Capacities in Decision Making. Germany: Springer International Publishing.