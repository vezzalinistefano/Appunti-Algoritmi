### Esempi:
1. Ciclo semplice:

        for i = 0 to n - 1 
            c := c + 1
            d := d + c
        c := c + d
    All'interno del ciclo for sono presenti 2 operazioni, il ciclo for esegue n iterazioni, quindi:<br> $\# op. = 2 \cdot iterazioni$<br>
    > $T(n) = 2n + 1 \in O(n)$ 


2. Ciclo annidato

        for i = 0 to n - 1 
            for j = i to n - 1
                x := x + 1
            y := y + 1

    > $T(n) = n + \frac{n(n + 1)}2 \in O(n^2)$ 
 
    $n \rightarrow$ `y := y+ 1`

    | i     | j           | # iterazioni ciclo <br> interno |
    | ----- | ----------- | ------------------------------- |
    | 0     | 0 - n-1     | n                               |
    | 1     | 1 ... n-1   | n-1                             |
    | 2     | 2 ... n-1   | n-2                             |
    | k     | k... n-1    | n-k                             |
    | n - 1 | n-1 ... n-1 | 1                               |

    $\hookrightarrow n + (n - 1) + (n - 2) + ... + 2 + 1$<br>Sto sommando i primi n numeri naturali

     = $n(n + 1) \over 2$ 

## Upper Bound

Diremo che: 

$$f(n)\in O(g(n)) \text{ se esistono delle costanti positive c e }n_0: 0 \leq f(n) \leq c\cdot g(n) \text{ }\forall n\geq n_0 $$

Notiamo che la notazione $f(n)\in \Theta(g(n))$ implica $f(n)=O(g(n))$, in quanto la notazione $\Theta$ è più forte della notazione $O$.\
Qualsiasi funzione quadratica $an^2 + bn + c$, con $a > 0$, è in $\Theta(n^2)$ implica anche che tali funzioni quadratiche siano tutte in $O(n^2)$.

| Espressione O()         | Nome         |
| ----------------------- | ------------ |
| O(1)                    | Costante     |
| O($loglogn$)            | loglog       |
| O($\sqrt[c]{n}$, c > 1) | sublineare   |
| O(n)                    | lineare      |
| O(nlogn)                | nlogn        |
| O($n^2$)                | quadratica   |
| O($n^3$)                | cubica       |
| O($n^k$), k > 1         | polinomiale  |
| O($a^n$), a > 1         | esponenziale |
| O($n!$)                 | fattoriale   |

Più siamo in alto nella tabella più il nostro algoritmo sarà efficente.

### Esempio
> Vediamo un esempio. $Sia f(n) = 2n^2 + 3n + 6, g(n) = n^2$, e tentiamo di mostrare che $2n^2 + 3n + 6 = O(n^2)$.\
Occorrerà quindi provare che esistono costanti c > 0 e $n_0 \in \N$ per cui $2n^2 +3n+6 ≤ cn^2$, per ogni n ≥ n0.   
A tal fine osserviamo che $2n^2 + 3n + 6 ≤ 2n^2 + 3n^2 + 6 ≤ 2n2 + 3n^2 + n^2 = 6n^2$, per ogni valore di n per cui $n^2 ≥ 6$,
ovvero per ogni valore di n ≥ 3.  
Quindi, le costanti c e $n_0$ che cercavamo per provare che $2n^2 + 3n + 6 ≤ cn^2$,
per ogni $n ≥ n_0$, possono essere scelte come c = 6 e $n_0$ = 3. Ovviamente, possono esistere anche altri valori di c
e $n_0$ per cui la diseguaglianza $2n^2 + 3n + 6 ≤ cn^2$, per ogni $n ≥ n_0$, sia soddisfatta. Tuttavia, al fine di provare
che $2n^2 + 3n + 6 = O(n^2)$ ci basta aver provato che $c = 2 \text{ e } n_0 = 3$ vanno bene.

L'esempio descritto ammette una semplice generalizzazione, ovvero per ogni k costante 

**Generico polinomio di grado k:**

f(n) = a<sub>k</sub>n<sup>k</sup> + a<sub>k-1</sub>n<sup>k-1</sup> + ... + a<sub>1</sub>n<sup>1</sup> +a<sub>0</sub>n<sup>0</sup> $\in$ O(n<sup>k</sup>) 

Questa proprietà vale per tutti i polinomi
<br>La difficoltà sta nel definire f(n)

0 $\leq$ i $\leq$ k

a<sub>i</sub>n<sup>i</sup> $\leq$ |a<sub>i</sub>|n<sup>i</sup> $\leq$ |a<sub>i</sub>|n<sup>k</sup> ... $\leq$ |a<sub>k</sub>|n<sup>k</sup> + |a<sub>k-1</sub>|n<sup>k</sup> + ... + |a<sub>1</sub>|n<sup>k</sup> +|a<sub>0</sub>|n<sup>k</sup> = (|a<sub>k</sub>| + |a<sub>k-1</sub>| + ... + |a<sub>0</sub>|)n<sup>k</sup> = cn<sup>k</sup>

### Alcune proprietà:

1. $\text{Se } f(n) \in O(g(n)) allora: a \cdot f(n) \in O(g(n))\text{ } \forall a > 0$ costante  
*Esempio*:  
$7logn \in O(n)$

2. 

$$
Se
\begin{cases}
    f(n) \in O(g(n)),\\
    d(n) \in O(h(n))
\end{cases}
\rightarrow
\begin{alignedat}
    ff(n) + d(n) &\in O(g(n) + h(n))\\
    &\in O(max(g(n), h(n)))
\end{alignedat}
$$

3.

$$
Se
\begin{cases}
f(n) \in O(g(n)),\\
d(n) \in O(h(n))
\end{cases}\rightarrow
f(n) * d(n) \in O(g(n) * h(n))
$$

<div style="page-break-after: always;"></div>

4.

$$
Se
\begin{cases}
f(n) \in O(g(n)),\\
g(n) \in O(h(n))
\end{cases}\rightarrow
f(n) \in O(h(n))
$$

## Lower Bound

Diremo che $f(n) \in \Omega(g(n))$ se e solo se $\exists c > 0, n_0\geq0$  
per cui $f(n) \geq c \cdot g(n) \forall n \geq n_0$

| Espressione $\Omega$()         | Nome         |
| ------------------------------ | ------------ |
| $\Omega$(1)                    | Costante     |
| $\Omega$($loglogn$)            | loglog       |
| $\Omega$($\sqrt[c]{n}$, c > 1) | sublineare   |
| $\Omega$(n)                    | lineare      |
| $\Omega$(nlogn)                | nlogn        |
| $\Omega$($n^2$)                | quadratica   |
| $\Omega$($n^3$)                | cubica       |
| $\Omega$($n^k$), k > 1         | polinomiale  |
| $\Omega$($a^n$), a > 1         | esponenziale |
| $\Omega$($n!$)                 | fattoriale   |

L'ordine consta ancora ma stavolta è il contrario di prima.

## Tight Bound

Diremo che $f(n) \in \Theta(g(n))$  
se e solo se:  
$\hspace{1cm} \exists c1, c2 > 0, n_0\geq0$ per cui  
$\hspace{1cm} \forall n\geq n_0 \hspace{0.5cm} c1\cdot g(n)\leq f(n) \leq c2\cdot g(n)$

La definizione di $\Theta(g(n))$ richiede che ogni membro $f(n)\in \Theta(g(n))$ sia ***asintoticamente non negativo***, ovvero che $f(n)$ sia non negativa quando n è sufficentemente grande.

> *Stessa tabella di prima ma con $\theta$.*


## Problema

Un problema è trattabile se ha come U.B. un polinomiale  
ovvero: se $\exists$ un algrotimo A di tempo polinomiale

$$T(n)\in O(n^k)$$

Un problema è *intrattabile* se $\nexists$ un A polinomiale per risolverlo.  
Un problema potrebbe anche essere non risolvibile.  
Esiste anche una classe di problemi per cui non si è dimostrato se esiste o non esiste una soluzione, essi sono detti NP-compatibili.

<div style="page-break-after: always;"></div>

### Esempi

1) Input: 
    - Sequenza di numeri interi  

            A[0]...A[n-1]
    - $x \in N$
    
    Output: la posizione di c in A (se presente), altrimenti "non c'è"

        Cerca(A, x)
            i:= 0
            while i < n and A[i] != x
                i:=i+1
            
            if i=n
                then return "non c'è"
                else return i

2) Stesso problema ma stavolta la sequenza è ordinata in ordine non decrescente  

        A[0] <= A[1] <= ... <= A[n-1]
    
    Output: posizione di x in A

    #### **Ricerca binaria (Dicotomica)**
    
    Quand'è che non lo trovo? Quando la sequenza rimane vuota senza che io lo abbia trovato 

    Pseudo codice:

            Bin_Search(A, n, x)
                i:=0, j:=n-1
                while i <= J
                    k = int_floor((i+j)/2)
                    if A[k] = x then return k
                    if A[k] > x then j:=k-1
                                else then i:=k+1
                return "non c'è" 
    
    Quindi, ricapitolando:  
    Se A non è ordinato $\rightarrow$ O(n)  
    Se A  è ordinato $\rightarrow$ O(logn)

    | <br> | Algoritmo                                           | Problema                                                     |
    | ---- | --------------------------------------------------- | ------------------------------------------------------------ |
    | U.B. | Riesce a risolvere con<br>$T_a(n) \in O(\cdot)$     | Si può risolvere con<br>$T_p(n)\in O(\cdot)$                 |
    | L.B. | Non può fare meglio di<br>$T_a(n)\in \Omega(\cdot)$ | Non posso risolvere il problema<br>$T_p(n)\in \Omega(\cdot)$ |

