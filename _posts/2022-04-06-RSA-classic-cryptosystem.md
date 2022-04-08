---
  layout: single
  title:  "What is RSA Classic Cryptosystem?"
  date:   2022-03-13
   
--- 

*What is RSA*

RSA (Rivest–Shamir–Adleman) is a public-key cryptosystem that is widely used for secure data transmission. It is also one of the oldest. The acronym "RSA" comes from the surnames of Ron Rivest, Adi Shamir and Leonard Adleman, who publicly described the algorithm in 1977. An equivalent system was developed secretly in 1973 at GCHQ (the British signals intelligence agency) by the English mathematician Clifford Cocks. That system was declassified in 1997.

*How does RSA work?*

The core idea is to find the least natural number that satisfies the following:

$$x^r = (mod  \;N) $$

Then, the above can be re-written as: 

$$x^r - 1 = (x^{r/2}+1)(x^{r/2}-1) = 0 (mod \;N)$$

We can find the keys using the greatest common divisor:

$$gcd(X1, N) = a1;$$
$$gcd(X2, N) = a2;$$
So, we can find: $$N = a1 * a2$$

Where $$(x^{r/2}+1)=X_1 $$ , $$ (x^{r/2}-1)=X_2$$ 

