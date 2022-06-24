---
  layout: single
  title:  "The core of FFT based Image Correlation - The Theory."
  date:   2022-06-23
   
--- 

*This is a brief theory introduction for the FFT for image correlation*

**How does FFT-phase correlation work?**

The method is based on the Fourier shift theorem.

Multiplying $$ x_n $$ by a linear phase $$ e^{\frac{i2\pi(n-1)}{N}m}$$ for some integer m corresponds to a circular shift of the output $x_k$ : $x_k$ is replaced by $x_{k-m}$, where the subscript is interpreted modulo N.\
Similarly, a circular shift of the input $x_n$ corresponds to multiplying the output $x_k$ by a linear phase.

Mathematically, if ${x_n}$ represents the vector x then:

if $F({x_n})_k = X_k$, then\

$F({x_n * e{\frac{i2\pi(n)}{N}m}})_k = X_{k-m}$  


