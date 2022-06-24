---
  layout: single
  title:  "What is RSA Classic Cryptosystem?"
  date:   2022-03-13
   
--- 

*This is a brief introduction for the RSA Encryption and Decryption Algorithm*

RSA (Rivest–Shamir–Adleman) is a public-key cryptosystem that is widely used for secure data transmission. It is also one of the oldest. The acronym "RSA" comes from the surnames of Ron Rivest, Adi Shamir and Leonard Adleman, who publicly described the algorithm in 1977. An equivalent system was developed secretly in 1973 at GCHQ (the British signals intelligence agency) by the English mathematician Clifford Cocks. That system was declassified in 1997.

**How does RSA work?**

The core idea is to find the least natural number that satisfies the following:

$$x^r = (mod  \;N) $$ (This is extremely difficult to find and computational expensive for the plain-search decription)

Modular exponentiation is the remainder when an integer b (the base) is raised to the power e (the exponent), and divided by a positive integer m (the modulus); that is:

$$ c = b^{e} mod(m) $$

Modular exponentiation is efficient to compute, even for very large integers. On the other hand, computing the modular discrete logarithm – that is, finding the exponent e when given b, c, and m – is believed to be difficult. This one-way function behavior makes modular exponentiation a candidate for use in cryptographic algorithms.

Then, the above can be re-written as: 

$$x^r - 1 = (x^{r/2}+1)(x^{r/2}-1) = 0 (mod \;N)$$

We can find the keys using the greatest common divisor:

$$gcd(X1, N) = a1;$$\
$$gcd(X2, N) = a2;$$

So, we can find: $$N = a1 * a2$$

Where:\
$$(x^{r/2}+1)=X_1$$\
$$(x^{r/2}-1)=X_2$$

**Algorithm:**

1.Generating the keys
Select two large prime numbers, x and y. The prime numbers need to be large so that they will be difficult for someone to figure out. 

2.Calculate:
 
$$n = x * y $$
 
3.Calculate the totient function 

$$\phi(n) = (x-1)(y-1)$$

4.Select an integer $$e$$, such that $$e$$ is co-prime to $$\phi(n)$$ ϕ(n) and $$1 < e < \phi(n)$$
. The pair of numbers (n,e) makes up the public key.
**Note: Two integers are co-prime if the only positive integer that divides them is 1.**

5.Calculate d such that $$e.d = 1 mod(\phi(n))$$
d can be found using the extended euclidean algorithm. The pair (n,d) makes up the private key.

**Encryption**
Given a plaintext P, represented as a number, the ciphertext C is calculated as:

$$C = P^{e} mod(n)$$

**Decryption**
Using the private key (n,d), the plaintext can be found using:

$$P = C^{d} mod(n)$$

**Pseudocode**

>int x = 61, int y = 53;\
>int n = x * y;\
>// n = 3233.\
>// compute the totient, phi\
>int phi = (x-1)*(y-1);\
>// phi = 3120.\
>int e = findCoprime(phi);\
>// find an 'e' which is > 1 and is a co-prime of phi.\
>// e = 17 satisfies the current values.\
>// Using the extended euclidean algorithm, find 'd' which satisfies this equation:\ 
>d = (1 mod (phi))/e;\
>// d = 2753 for the example values.\
>public_key = (e=17, n=3233);\
>private_key = (d=2753, n=3233);\
>// Given the plaintext P=123, the ciphertext C is :\
>C = (123^17) % 3233 = 855;\
>// To decrypt the cypher text C:\
>P = (855^2753) % 3233 = 123;
