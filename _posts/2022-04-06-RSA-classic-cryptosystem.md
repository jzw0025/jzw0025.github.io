---
  layout: single
  title:  "Zero-knowledge Proof"
  date:   2022-03-13
   
--- 

*What is RSA*

RSA (Rivest–Shamir–Adleman) is a public-key cryptosystem that is widely used for secure data transmission. It is also one of the oldest. The acronym "RSA" comes from the surnames of Ron Rivest, Adi Shamir and Leonard Adleman, who publicly described the algorithm in 1977. An equivalent system was developed secretly in 1973 at GCHQ (the British signals intelligence agency) by the English mathematician Clifford Cocks. That system was declassified in 1997.

*How does RSA work?*
The core is to find the least natural number that satisfies the following:

$$x^r = (mod N)$$  e.g. 4^6 = 91 * 45 + 1 = 1 (mod 91)

Then, the core can be re-written as: 

x^r - 1 = (x^(r/2)+1)(x^(r/2)-1) = 0 (mod N)



