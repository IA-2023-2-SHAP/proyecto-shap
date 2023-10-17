# Valor de Shapley

## Juego cooperativo
Formalmente, un **juego cooperativo** se define como: Hay un conjunto $N$ (de $n$ jugadores) y una función $v$ que mapea subconjuntos de jugadores a los números reales: $v \colon 2^N \to \mathbb{R}$, con $v (\emptyset ) = 0$, donde $\emptyset$ denota el conjunto vacío. 

## Función caractterística
La función $v$ se llama función característica. La función $v$ tiene el siguiente significado: si $S$ es una coalición de jugadores, entonces $v(S)$, llamado el valor de la **coalición** $S$, describe la suma total esperada de pagos que los miembros de $S$ pueden obtener mediante la cooperación.


## Valor de Shapley
El valor de Shapley es una forma de distribuir las ganancias totales a los jugadores, suponiendo que todos colaboran. Es una distribución "justa" en el sentido de que es la única distribución con ciertas propiedades deseables que se enumeran a continuación. 

Según el valor de Shapley, la cantidad que se le da al jugador $i$ en un juego cooperativo $( v, N)$ es:

$$\varphi_i(v)=\sum_{S \subseteq N \setminus
\{i\}} \frac{|S|!\; (n-|S|-1)!}{n!}(v(S\cup\{i\})-v(S))$$

$$\quad \quad \quad = \sum_{S \subseteq N \setminus
\{i\}} {n \choose 1, |S|, n - |S| - 1}^{-1} (v(S\cup\{i\})-v(S))$$

donde $n$ es el número total de jugadores y la suma se extiende sobre todos los subconjuntos $S$ de $N$ que no contienen al jugador $i$. También tenga en cuenta que ${n \choose a, b, c}$ es el coeficiente multinomial. 

Una pequeña variante e:

$$
\phi_i(v) = \sum_{S \subseteq N \setminus \{i\}} \frac{|S|!(|N| - |S| - 1)!}{|N|!} \left[v(S \cup \{i\}) - v(S)\right]
$$

Aquí, los términos clave son:

- $\phi_i(v)$: Es el Shapley value del jugador $i$ en el juego representado por la función de valor $v$.

- $N$: Es el conjunto de todos los jugadores (en nuestro caso, todas las características).

- $S \subseteq N \setminus \{i\}$: $S$ es una coalición que no contiene al jugador $i$ [^1].

- $|S|$: Representa el número de jugadores en la coalición $S$.

- $|N|$ ó $n$: Es el número total de jugadores (características).

- $v(S \cup \{i\})$: Es el valor de la función $v$ cuando la coalición es ampliada para incluir al jugador $i$.

- $v(S)$: Es el valor de la función $v$ cuando solo consideramos la coalición $S$.

Esta fórmula puede parecer compleja, pero es esencialmente una suma ponderada de las diferencias en la contribución de la característica $i$ cuando se agrega a diferentes coaliciones. El término $\frac{|S|!(|N| - |S| - 1)!}{|N|!}$ representa la ponderación de las diferentes permutaciones posibles de las coaliciones.

Una fórmula equivalente alternativa para el valor de Shapley es:

$$
\varphi _{i}(v)={\frac {1}{n!}}\sum _{R}\left[v(P_{i}^{R}\cup \left\{i\right\})-v(P_{i}^{R})\right]
$$

donde la suma recorre todos los órdenes posibles de $n!$ jugadores $R$ y $P_i^R$ es el conjunto de jugadores en $N$ que preceden (estan antes de) a $i$ en el orden $R$. 


Finalmente, también se puede expresar como

$$
\varphi _{i}(v)={\frac {1}{n}}\sum _{S\subseteq N\setminus \{i\}}{\binom {n-1}{|S|}}^{-1}(v(S\cup \{i\})-v(S))
$$


que se puede interpretar como

$$
\varphi _{i}(v)={\frac {1}{\text{número de jugadores}}}\sum _{{\text{coalitions incluyendo }}i}{\frac {{\text{contribución marginal de }}i{\text{ a la coalición}}}{{\text{número de coaliciones excluyendo }}i{\text{ de este tamaño}}}}
$$

## En términos de sinergia

A partir de la **función característica** $v$, se puede calcular la *sinergia* que proporciona cada grupo de jugadores. La sinergia es la función única $w \colon 2^N \to \mathbb{R}$, tal que

$$
v(S) = \sum_{R \subseteq S } w(R)
$$

para cualquier subconjunto $S \subseteq N$ de jugadores. En otras palabras, el \'valor total\' de la coalición $S$ proviene de sumar las *sinergias* de cada subconjunto posible de $S$. $R$ es un grupo de jugadores que están contenidos en el grupo de jugadores $S$. Esto significa que el valor de la **función característica** de la coalición $S$ es igual a la suma de las sinergias de todos los subconjuntos posibles de $S$.

Por ejemplo, si tenemos un juego con tres jugadores, $N=\{A, B, C\}$, y la función característica del juego es $v$, entonces el valor de la coalición $S=\{A, B, C\}$, es igual a la suma de las sinergias de los siguientes subconjuntos:

* {A}
* {B}
* {C}
* {A, B}
* {A, C}
* {B, C}
* {A, B, C}

La fórmula del valor de Shapley utiliza la función sinergia para calcular la contribución promedio de cada jugador a la sinergia de todas las coaliciones de las que es miembro.

Dada una función característica $v$, la función sinergia $w$ se calcula a través de

$$
w(S) = \sum_{R \subseteq S } (-1)^{|S| - |R|}  v(R)
$$

utilizando el principio de inclusión-exclusión. En otras palabras, la sinergia de la coalición $S$ es el valor $v(S)$, que aún no ha sido contabilizado por sus subconjuntos.

Los valores de Shapley se dan en términos de la función sinergia por

$$
\varphi_i(v) = \sum_{i \in S \subseteq N } \frac{w(S)}{|S|}
$$

donde la suma es sobre todos los subconjuntos $S$ de $N$ que incluyen al jugador $i$.

Esto puede interpretarse como

$$
\varphi_i(v) = \sum_{\text{coaliciones incluyendo i}} \frac{\text{sinergia de la coalición}}{\text{miembros en la coalición}}
$$

En otras palabras, la sinergia de cada coalición se divide por igual entre todos los miembros.





## Resumen de términos clave

* **Juego cooperativo**: Hay un conjunto $N$ (de $n$ jugadores) y una función $v$ que mapea subconjuntos de jugadores a los números reales: $v \colon 2^N \to \mathbb{R}$, con $v (\emptyset ) = 0$.
* **Función característica**: si $S$ es una coalición de jugadores, entonces $v(S)$, llamado el valor de la coalición $S$, describe la suma total esperada de pagos que los miembros de $S$ pueden obtener mediante la cooperación.
* **Coalición**: Un subconjunto de jugadores.
* **Sinergia**: La contribución de una coalición a la función de valor.

## Ejemplos

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
\varphi _{i}(v)={\frac {1}{|N|!}}\sum _{R}\left[v(P_{i}^{R}\cup \left\{i\right\})-v(P_{i}^{R})\right]
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
La función de sinergia es una función que mide el valor adicional que se crea cuando se añade un jugador a una coalición. En este caso, la única sinergia que ocurre es entre el propietario y un trabajador individual. Por lo tanto, la función de sinergia $w$ es la siguiente:

$$
w(S)=\begin{cases}
p & \text{si } S=\{o,w_i\} \\
0 & \text{de lo contrario }
\end{cases}
$$

esta función de sinergia significa que la única sinergia que ocurre es entre el propietario y un trabajador individual. El valor de esta sinergia es igual a la contribución de un trabajador individual, que es igual a $p$.

En otras palabras, la función de sinergia se deduce de la función de valor al identificar las coaliciones que crean sinergia. En este caso, la única coalición que crea sinergia es la coalición que incluye al propietario y un trabajador individual.

Usando la fórmula anterior para el valor de Shapley en términos de $w$ calculamos

$$
\varphi _i(v) = \sum_{i \in S \subseteq N } \frac{w(S)}{|S|}
$$


$$
\varphi _{w_{i}}=\frac{w(\{o,w_i\})}{2}=\frac{p}{2}
$$

y

$$
\varphi _{w_{i}}=\sum_{i=1}^{m}{\frac{w(\{o,w_i\})}{2}=\frac{mp}{2}}
$$

---

La fórmula se deduce de la fórmula para el valor de Shapley en términos de la función de sinergia. Esta fórmula es la siguiente:

$$
\varphi_{i}(v)=\frac{w(\{i\})}{2}+\sum_{S\in \mathcal{F}(N)}\frac{(w(S)-w(S\setminus \{i\}))(-1)^{|S|-1}}{|S|!}
$$

donde $i$ es un jugador, $\mathcal{F}(N)$ es el conjunto de todas las coaliciones posibles, y $|S|$ es la cardinalidad de la coalición $S$.

En este caso, la función de sinergia es la siguiente:

$$
w(S)=\begin{cases}
p & \text{si } S=\{o,w_i\} \\
0 & \text{de lo contrario }
\end{cases}
$$

Para el jugador $i$, la única coalición que es relevante es la coalición que incluye al propietario y al trabajador individual $i$. Por lo tanto, la fórmula para el valor de Shapley se reduce a la siguiente:

$$
\varphi_{w_{i}}=\frac{w(\{o,w_i\})}{2}
$$

Esta fórmula se deduce de la fórmula general para el valor de Shapley en términos de la función de sinergia al sustituir la función de sinergia en la fórmula.

Por lo tanto, la fórmula $$\varphi _{w_{i}}=\frac{w(\{o,w_i\})}{2}=\frac{p}{2}$$ se deduce de la fórmula general para el valor de Shapley en términos de la función de sinergia.

## Ejemplo juego simple

Supongamos que tenemos un juego cooperativo con tres jugadores: $A$, $B$ y $C$. La función de valor del juego está dada por la suma de los jugadores en la coalición:

$$ v(S) = \sum_{i \in S} i $$

Donde $S$ es una coalición de jugadores. Ahora, aplicamos la fórmula de Shapley para cada jugador. La fórmula es:

$$ \phi_i(v) = \sum_{S \subseteq N \setminus \{i\}} \frac{|S|!(|N| - |S| - 1)!}{|N|!} \left[v(S \cup \{i\}) - v(S)\right] $$

Vamos a calcular los valores de Shapley para $A$, $B$ y $C$:

1. Para $A$:

$$
\begin{align*}
\phi_A(v) &= \frac{1}{6}[(v(\{A\}) + v(\{A, B\}) + v(\{A, C\}) - v(\{\})) \\
&\quad+ (v(\{A, B, C\}) + v(\{A, B\}) + v(\{A, B, C\}) - v(\{B\})) \\
&\quad+ (v(\{A, B, C\}) + v(\{A, C\}) + v(\{A, B, C\}) - v(\{C\}))] \\
&= \frac{1}{6}[(1 + 3 + 4 - 0) + (6 + 3 + 6 - 1) + (6 + 4 + 6 - 3)] \\
&= \frac{1}{6}(22) = \frac{11}{3}
\end{align*}
$$

2. Para $B$:

$$
\begin{align*}
\phi_B(v) &= \frac{1}{6}[(v(\{B\}) + v(\{A, B\}) + v(\{B, C\}) - v(\{\})) \\
&\quad+ (v(\{A, B, C\}) + v(\{A, B\}) + v(\{B, C\}) - v(\{A\})) \\
&\quad+ (v(\{A, B, C\}) + v(\{A, B\}) + v(\{B, C\}) - v(\{C\}))] \\
&= \frac{1}{6}[(2 + 3 + 5 - 0) + (6 + 3 + 5 - 1) + (6 + 5 + 5 - 4)] \\
&= \frac{1}{6}(32) = \frac{16}{3}
\end{align*}
$$

3. Para $C$:

$$
\begin{align*}
\phi_C(v) &= \frac{1}{6}[(v(\{C\}) + v(\{A, C\}) + v(\{B, C\}) - v(\{\})) \\
&\quad+ (v(\{A, B, C\}) + v(\{A, C\}) + v(\{B, C\}) - v(\{A\})) \\
&\quad+ (v(\{A, B, C\}) + v(\{A, C\}) + v(\{B, C\}) - v(\{B\}))] \\
&= \frac{1}{6}[(3 + 4 + 5 - 0) + (6 + 4 + 5 - 2) + (6 + 5 + 5 - 3)] \\
&= \frac{1}{6}(39) = \frac{13}{2}
\end{align*}
$$

Estos son los valores de Shapley para cada jugador en este ejemplo particular. Indican cuánto contribuye cada jugador al juego cooperativo promediando sobre todas las posibles coaliciones. Ten en cuenta que este es un ejemplo simple y los valores de Shapley pueden variar según la función de valor y la estructura del juego.

# Referencias

[^1]: https://es.wikipedia.org/wiki/Diferencia_de_conjuntos