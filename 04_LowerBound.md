# Lower Bound

Problema di ordinamento x confronto.

$a_0,a_1,...,a_{n-1}\rightarrow a_0' \leq a_1' \leq ... \leq a_{n-1}'$

esempio:\
$1, \underbrace{4, 3}_\textrm{4?3}, 7 \rightarrow 1, 3, 4, 7$ 

quello che otteniamo è una permutazione dei numeri di partenza.

Grazie ad ogni permutazione siamo in grado di scartarne alcune.\
#permutazioni di n numeri = n!

**1° Confronto**

$
a_i?a_j
\begin{cases}
   A \rightarrow \text{permutazione compatibile con il risultato del confronto}\\
   B \rightarrow \text{non compatibili con il risultato del confronto}
\end{cases}
$

$|A| + |B| = n!$

se a + b = c\
*  a $\geq \frac{c}{2}$
*  b $\geq \frac{c}{2}$

caso peggiore $|A| \geq \frac{n!}{2}$

Quindi il numero di permutazioni compatibili è $\geq \frac{n!}{2}$

**2° Confronto**

n° permutazioni compatibili $\geq \frac{n!}{4}$\
. . . 

$logn! = ?$\
$n! = n(n-1)(n-2)...2\cdot 1 \geq n(n-1)(n-2)...\frac{n}{2}\geq \frac{n}{2}\cdot \frac{n}{2}...\frac{n}{2} = (\frac{n}{2})^{n/2}$\
$logn! \geq log(\frac{n}{2})^{n/2} = \underbrace{\frac{n}{2}log\frac{n}{2}}_{\geq c\cdot n\cdot logn} \in \Omega(nlogn)$

Il numero di confronti minimo che il problema deve fare l'algoritmo basandosi solo sui confronti è nlogn.\
Il merge sort quindi per il nostro problema è ottimo, ma è ricorsivo e di conseguenza **pesante**.