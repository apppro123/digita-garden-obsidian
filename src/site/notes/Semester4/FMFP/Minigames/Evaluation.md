---
{"dg-publish":true,"permalink":"/semester4/fmfp/minigames/evaluation/"}
---

## General
- infix functions e.g. `1+2 = (+) 1 2` where `+` is infix
	- and for `(+a) b = b + a = (+)b a`, `a` is the second argument and the following a
- functions are always applied to exactly one argument at a time
## Lazy evaluation
To evaluate $(t_{1}\;t_{2})$
1. evaluate $t_{1}$
2. if the result of $t_{1}$ is $(\lambda x.u)$, return $u[x/t_{2}]$
3. Then evaluate the result of the substitution
To evaluate $(\lambda x.t)$ return it unchanged
## Eager evaluation
To evaluate $(t_{1}\;t_{2})$
1. evaluate $t_{1}$, then evaluate $t_{2}$ to $t_{2}'$
2. if the result of $t_{1}$ is $(\lambda x.u)$, return $u[x/t_{2}']$
3. Then evaluate the result of the substitution
To evaluate $(\lambda x.t)$, evaluate $t$ to $t'$ and return $(\lambda x.t')$
## Common mistakes/special care
- **incorrect parenthesis** at the beginning: e.g. $\lambda x.\;x\;(\lambda y.\;x\;y)\not\equiv(\lambda x.\;x)\;(\lambda y.\;x\;y)$
- **substitution removes** the lambda $(\lambda x.x)(\lambda y.x\;y)\not\leadsto\lambda(\lambda y.x\;y).\lambda y.x\;y$ but just $\lambda y.x\;y$
- in **lazy evaluation** there is **no evaluation** under **lambdas**
- in **eager evaluation**, need to evaluate **argument before substitution**