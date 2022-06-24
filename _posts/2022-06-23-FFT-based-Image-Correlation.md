---
  layout: single
  title:  "The core of FFT based Image Correlation - The Theory."
  date:   2022-06-23
   
--- 

*This is a brief theory introduction for the FFT for image correlation*

**How does FFT-phase correlation work?**

The method is based on the Fourier shift theorem.

Multiplying {\displaystyle x_{n}}x_{n} by a linear phase {\displaystyle e^{{\frac {i2\pi (n-1)}{N}}m}}{\displaystyle e^{{\frac {i2\pi (n-1)}{N}}m}} for some integer m corresponds to a circular shift of the output {\displaystyle X_{k}}X_{k}: {\displaystyle X_{k}}X_{k} is replaced by {\displaystyle X_{k-m}}X_{k-m}, where the subscript is interpreted modulo N (i.e., periodically). Similarly, a circular shift of the input {\displaystyle x_{n}}x_{n} corresponds to multiplying the output {\displaystyle X_{k}}X_{k} by a linear phase. Mathematically, if {\displaystyle \{x_{n}\}}\{x_{n}\} represents the vector x then

if {\displaystyle {\mathcal {F}}(\{x_{n}\})_{k}=X_{k}}{\mathcal {F}}(\{x_{n}\})_{k}=X_{k}
then {\displaystyle {\mathcal {F}}\left(\left\{x_{n}\cdot e^{{\frac {i2\pi }{N}}nm}\right\}\right)_{k}=X_{k-m}}{\displaystyle {\mathcal {F}}\left(\left\{x_{n}\cdot e^{{\frac {i2\pi }{N}}nm}\right\}\right)_{k}=X_{k-m}}:
and {\displaystyle {\mathcal {F}}\left(\left\{x_{n-m}\right\}\right)_{k}=X_{k}\cdot e^{-{\frac {i2\pi }{N}}km}}{\displaystyle {\mathcal {F}}\left(\left\{x_{n-m}\right\}\right)_{k}=X_{k}\cdot e^{-{\frac {i2\pi }{N}}km}}


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
