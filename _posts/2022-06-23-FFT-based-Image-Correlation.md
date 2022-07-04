---
  layout: single
  title:  "The core of FFT based Image Correlation - The Theory."
  date:   2022-06-23
   
--- 

*This is a brief theory introduction for the FFT for image correlation*

**How does FFT-phase correlation work?**

The method is based on the Fourier shift theorem.

Multiplying $$ x_n $$ by a linear phase $$ e^{\frac{2\pi{i}(n-1)}{N}m}$$ for some integer m corresponds to a circular shift of the output $$x_k$$ : $$x_k$$ is replaced by $$x_{k-m}$$, where the subscript is interpreted modulo N.

Similarly, a circular shift of the input $$x_n$$ corresponds to multiplying the output $$x_k$$ by a linear phase.

Mathematically, if $${x_n}$$ represents the vector x then:

if $$F({x_n})_k = X_k$$, then:

$$F({x_n * e{\frac{i2\pi(n)}{N}m}})_k = X_{k-m}$$  

Let two images $$I_a$$ and $$ I_b $$ be circularly shifted version of each other:

$$I_b(x,y) = I_a((x-\Delta{x})Mod(M),(y-\Delta{y})Mod(N))$$, 

    where the images are M by N size.

Then, the discrete Fourier transforms of the images will be shifted relatively in phase:

$$ I_b(u,v) = I_a(u,v) e^{-2\pi{i}(\frac{u*\delta{x}}{M}+\frac{v*\delta{y}}{N})}$$

One can then calculate the normalized cross-power spectrum to factor out the phase differences:

$$ R(u,v) = \frac{I_a \cdot I_b^{*}}{|I_a \cdot I_b^{*}|}$$ 

$$ = \frac{I_a \cdot I_a^{*} \cdot e^{2 \pi{i}(\frac{u\delta{x}}{M}+\frac{v\delta{y}}{N})}}{|I_a \cdot I_a^{*}|} $$ 

$$ = e^{2\pi{i}(\frac{u\delta{x}}{M} + \frac{v\delta{y}}{N})} $$

Since the magnitude of an imaginary exponential is always one, and the phase of $$I_a \cdot I_a^{*} $$ is  always zero.

The inverse of Fourier of a complex exponential is Kronecker delta with the peak indicating the shifts of images at:

$$ r(x,y) = \delta{(x+\Delta{x}, y+\Delta{y})}$$ 

where $$\Delta{x} , \Delta{y} $$ are the shifts in X and Y directions between the images.
