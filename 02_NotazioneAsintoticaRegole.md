## **IN GENERALE**

* *Somma dei primi n numeri*

$$
   \sum_{i=1}^n i = \frac{n(n+1)}{2} \in \Theta(n^2)
$$

* *Somma dei primi n quadrati*

$$
   \sum_{i=1}^n i^2 = \frac{n(n+1)(2n+1)}{6} \in  \Theta(n^3)
$$

* *Somma parziale n-esima della serie geometrica: per x $\neq$ 1*
  $$
   \sum_{i=1}^n x^i = \frac{1-x^{n+1}}{1-x}
   $$
   
   * Quando 0 < x < 1 abbiamo che 
     $$
      \sum_{i=1}^n x^i \in \Theta(1)
     $$
   
   * Quando x = 2 abbiamo
     $$
      \sum_{i=1}^n x^i = 2^{n+1}-1 \in \Theta(2^n)   
     $$
   
   * Quando x > 1 abbiamo
     $$
      \sum_{i=1}^n x^i = \frac{1}{x-1}(x^{n+1}-1) \in \Theta(x^n)  
     $$ 

