---
{"dg-publish":true,"permalink":"/semester4/fmfp/lectures/fmfp-l10/"}
---

## algebraic data types
- **data types** defines a **set of terms** for each type instance e.g. `Tree Int` correspons to `{Leaf, Node 0 Leaf Leaf, ...}`
- **algebraic** here means the smallest set $S$ where $\text{Leaf}\in S$ and $x\in a\land t_{1}\in S\land t_{2}\in S\implies(\text{Node }x\; t_{1}\; t_{2})\in S$ 
- Intuition: set $S$ is built in steps
	- $\text{Leaf}\in S$ and
	- $(\text{Node}\;x\;t_{1}\;t_{2})\in S$, where $t_{1}$ and $t_{2}$ in $S$ in earlier steps
## Structural induction ![Pasted image 20240329150618.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240329150618.png)