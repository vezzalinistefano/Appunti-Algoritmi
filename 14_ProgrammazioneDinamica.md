# Programmazione dinamica

Si applica ai problemi di ottimizzazione

## Shortest Paths On DAG

![](\images/pd_dag.png)

Se mi metto nel nodo 1 da dove può arrivare il cammino più breve per arrivare a 1?  
Devo guardare qual è il migliore tra gli archi entranti

$
\text{Tengo il più piccolo}\begin{cases}
   w(s, 1) + \text{cammino minimo(s)} = x\\
   w(3, 1) + \text{cammino minimo(3)} = y
\end{cases} 
$

Seguendo l'ordine topologico ho tutti i dati necessari appena ne ho bisogno.

      SPD_PD(G, s)
         for all v ∈ V
            dist[v] := +∞
         dist[s] := 0
         for all v ∈ V \{s} in ordine topologico
            dist[v] := min (u,v)⊂E {w(u, v) + dist[u]}

Pago $O(n)$

## Longest increasing subsequence

< 5, 2, 8, 6, 3, 6, 9, 7>

*Input*: sequenza di n interi $a_1,..., a_n$  
*Output*: la più lunga sottosequenza che contiene elementi crescenti

ci sono $2^n$ sottoinsiemi possibili  
$\rightarrow$ faccio diventare un nodo ogni numero della mia sequenza e eseguo una linearizzazione.


L[j] = lunghezza della sottosequenza più lunga che termina in j  
j = 1, ..., n  
$L[j] = 1 + max_{(i, j)\in E} \{L[i]\}$ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; $prev[j]$ = indice i che massimizza

Perchè invece della programmazione dinamica non uso la ricorsione?  
$\rightarrow$ calcolerei le stesse cose moltissime volte!

**ESEMPIO**

<30, 34, 11, 34, 11, 34, 5, 60, 17, 13>

| <br> | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   |
| ---- | --- | --- | --- | --- | --- | --- | --- | --- |
| L    | 1   | 2   | 1   | 2   | 1   | 3   |
| prev | /   | 1   | /   | 1   | /   | 4   |

## Problema Zaino (Knapsack) 

>Sei un ladro devi mettere più roba di valore possibile all'interno dello zaino e scappare

**Input:** 
* Capacità zaino W in N
* n item 1, ..., n
* Item i: 
  * peso w $\in \N$ 
  * valore v$_i \in \N$

**Output:** selezione di item che sta nello zaino ($\sum w_i \leq W$) che massimizzi il profitto ($\sum w_i$ massima).

### Con ripetizione

>Una soluzione possibile è una combinazione di oggetti (lista di valori)  
>Tentando ogni possibile combinazione otterremmo una soluzione di ordine $O(n^n)$

Utilizziamo quindi la programmazione dinamica.

Definiamo `K[w]=` massimo profitto ottenibile con uno zaino di capacità w $\in$ W
>w = 0, ..., W

Voglio trovare la migliore tra le soluzioni con uno zaino ancora più piccolo e combinarle con dimensioni più grandi

Se sapessimo che i appartiene alla soluzione ottima  
`K[w] = vi + K[w - wi]`  
purtroppo però non so se i appartiene alla soluzione ottima

`K[w] = max{vi + K[w - wi]}` (*)

>Problema più piccolo: `K[0] = 0`

L'obbiettivo è trovare `K[W]`.  
Mi creo un array di dimensione W (w grande) che comincio a riempire e in ogni casella scrivo cosa ottengo in questo modo (*).  
Così facendo pago O(nW) 
>ATTENZIONE: quando nel costo computazionale appare uno dei valori dell'input il costo potrebbe diventare impraticambile molto facilmente

Per questo probelma però non siamo in grado di dare una soluzione migliore, ma non è nemmeno dimostrato che non possa esserci.

 | Item | w$_i$ | v$_i$ |
 | ---- | ----- | ----- |
 | 1    | 4     | 18    |
 | 2    | 5     | 22    |
 | 3    | 3     | 20    |
 | 4    | 4     | 15    |
 | 5    | 4     | 20    |

W = 10


| w     | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  |
| ----- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| K     | 0   | 0   | 0   | 20  | 20  | 22  | 40  | 40  | 42  | 60  | 60  |
| Items | /   | /   | /   | 3   | 3   | 2   | 3   | a   | b   | c   | d   |

In ogni casella itemi scrivo qual è l'item con cui ho massimizzato

## Senza ripetizione

Ogni oggetto si prende una volta sola