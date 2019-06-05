# Compressione

FILE n caratteri $\underbrace{\sum}_\text{alfabeto} = \{a, b, c, d, e, f\}$

$
   a = 01100001\\
   b=01100010\\
   c = 01100011\\
   ...
$

$\text{dimensione file: } 8 \cdot \text{n}$

Ho solo 6 lettere quindi posso usare una codifica diversa

$
\begin{alignedat}
   000, 001, 010, 011, 100, 101 \rightarrow &\text{nuova dimensione= } 3 \cdot \text{n° bit}\\
   &\text{k bit} \rightarrow 2^k
\end{alignedat} 
$

Codici a lunghezza fissa, decodifica facile da fare  
$\sum = \{a, b, c, d, e, f\}$

Più una lettera compare meno bit gli assegno  
Percentuale di apparizioni delle lettere sul totale (esempio):  
$
   a \rightarrow \text{45\%} \rightarrow 0\\
   a \rightarrow \text{13\%} \rightarrow 100\\
   a \rightarrow \text{12\%} \rightarrow 101\\
   a \rightarrow \text{16\%} \rightarrow 111\\
   a \rightarrow \text{9\%} \rightarrow 110\\
   a \rightarrow \text{5\%} \rightarrow 1101
$

$1 \cdot 0.45n + 3 \cdot 0.13n + ... + 4 \cdot 0.05n = 2.24n$ ho un guadagno ulteriore rispetto alla semplice codifica a lunghezza fissa

Esempio:  
$\underbrace{100}_b|\underbrace{0}_a|\underbrace{100}_b|\underbrace{0}_a|\underbrace{101}_c|\underbrace{0}_a$

ma non sempre sarà così facile eseguire la codifica, molto spesso può succedere che ci sia ambiguità.  
Per togliere ambiguità il nostro codice deve rispettare una regola detta **codice a prefisso**: nessun codice deve essere prefisso di un altro.

$\underbrace{1011}_\text{Prefisso}1001$

## Albero di decodifica

- Albero binario
- Foglia $\rightarrow$ 1 carattere di $\sum$

![albero di decodifica](\images/albero-di-decodifica.png)

L'albero mi permette di decodificare il file