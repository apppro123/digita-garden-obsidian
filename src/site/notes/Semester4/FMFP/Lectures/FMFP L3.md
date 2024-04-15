---
{"dg-publish":true,"permalink":"/semester4/fmfp/lectures/fmfp-l3/"}
---

## Correctness
**What does it mean?**
- **Termination**: important for many, but not all, programs
- **Functional behavior**: function should return "correct" value. can be defined by another (mathematically defined) function or an input-output relation.
Correctness is rarely obvious => must be proven
### Termination
- if $f$ is defined in terms of functions $g_{1},\dots,g_{k}(g_{i}\ne f)$ and each $g_{i}$ terminates, then so does $f$. 
	- problem is recursion, when some $g_{i}=f$
- sufficient condition for termination: arguments are smaller along a **well-founded** order on functions domain
	- an order $>$ on a set $S$ is well-founded $\iff$ there is no infinite decreasing chain $x_{1}>x_{2}, \dots$ for $x_{i}\in S$
	- possible to construct new well-founded relations from existing ones
 ![Pasted image 20240228200253.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240228200253.png)
 ![Pasted image 20240228200206.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240228200206.png)
### Correctness
- examples for proving correctness on slides: mainly using **induction** 
#### Different reasoning strategies
- **equational reasoning** bc. functions are equations ![Pasted image 20240308102624.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240308102624.png)
- **reasoning by cases** ![Pasted image 20240308102827.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240308102827.png)
	- with inference rules
		- **Excluded Middle (TND)**: For all propositions $P$ holds $P\lor\lnot P$
		- **Case split** ($\lor$-E): Given $Q\lor R$ to prove any $P$ we must prove
			1. $P$ follows from $Q$ and 
			2. $P$ follows from $R$
- **proof by induction** ![Pasted image 20240308103155.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240308103155.png)