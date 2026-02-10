---
tags:
  - source/video
time: 2026-02-10 11:49
status: done
---
# References
- [[@csZiXueSheQu16CombinationalLogic_BiLiBiLi_bilibili]]

# Boolean Algebra for logical gate
In Boolean algebra, we denote *AND* as a multiplication sign, which is $\cdot$  . And we denote  *OR* as *+*, while *NOT* as $\bar{x}$. We can use boolean algebra to simplify the circuit and to tell whether two circuit are same or not.

The following is some properties of boolean algebra, which can be used to simplify some boolean expressions.
1. Complementary: $x + \bar{x} = 1$, $x \cdot \bar{x} = 0$.
2. Laws of $0$'s and $1$'s: $x \cdot 0=0$, $x+1=1$.
3. Identities: $x \cdot 1=x$, $x+ 0=x$.
4. Idempotent law: $x \cdot x=x$, $x + x=x$.
5. Communicative law: $x \cdot y= y \cdot x$, $x+y = y +x$.
6. Associativity: $(xy)z=x(yz)$, $(x+y)+z = x+(y+z)$.
7. Distribution: $x(y+z)=xy+xz$, $x+yz=(x+y)(x+z)$.
	1. $(x+y)(x+z)=x \cdot x + x \cdot z + x \cdot y + y \cdot z = x+yz$.
8. Uniting Theorem: $xy+x=x$, $(x+y)x=x$.
9. De Morgan's Law: $\overline{x \cdot y} = \bar{x}+\bar{y}$, $\overline{x+y}=\bar{x} \cdot \bar{y}$.