---
{"dg-publish":true,"permalink":"/semester4/ws/wahrscheinlichkeit/erwartungswert/"}
---

>[!info] #Def 4.1 **Erwartungswert (nicht negativ)**
>Gebenen: Zufallsvariable $X:\Omega \to\mathbb{R}_{+}$ mit nicht-negativen Werten, Verteilungsfunktion $F_{X}$
>Dann heisst (4.1) 
>$$\mathbb{E}[X]=\int\limits_{0}^{\infty} (1-F_{X}(x)) \, dx$$
>der **Erwartungswert von X** ( #english expected value)
>- #disclaimer 4.2 Erwartungswert in Gleichung (4.1) ist immer definiert und kann sowohl endlich als auch unendlich werden.

>[!info] #Theorem 4.3 
> Gegeben: nicht-negative Zufallsvariable $X$
> Dann gilt $\mathbb{E}[X]\geq 0$. Gleichheit gilt genau dann, wenn $X=0$ fast sicher gilt.
> Für allgemeine Zufallsvarialben (nicht unbedingt mitkonstantem Vorzeichen) ist Erwartungswert durch **Zerlegung in positiven und negativen Teil** definiert.
> $$X_{+}(\omega)=\begin{cases} 
> X(\omega)&X(\omega)\geq 0 \\ 
> 0&X(\omega)< 0
> \end{cases}\qquad\text{und}\qquad X_{-}(\omega)=\begin{cases}
>-X(\omega)&X(\omega)\leq 0 \\
> 0 & X(\omega)> 0
\end{cases}$$
> - Kürzer: $X_{+}=\max(X,0)$ und $X_{-}=-\min(X,0)=\max(-X,0)$
> - **Achtung** $X_{+}$ und $X_{-}$ sind nicht-negative Zufallsvariablen und es gilt
> 	- $X=X_{+}-X_{-}$
> 	- $|X|=X_{+}+X_{-}$

>[!info] #Def 4.4 **Allgemeiner Erwartungswert**
>Gegeben: reellwertige Zufallsvariable $X$
>Falls $\mathbb{E}[|X|]<\infty$, dann heisst (4.2) $\mathbb{E}[X]=\mathbb{E}[X_{+}]-\mathbb{E}[X_{-}]$ der **Erwartungswert von $X$**
>- #disclaimer 4.5 
> 	 - $\mathbb{E}[|X|]<\infty \implies \mathbb{E}[X_{-}],\mathbb{E}[X_{+}]<\infty$ da $|X|=X_{+}+X_{-}$. Somit ist Gleichung (4.2) wohldefiniert.
> 	 - Für $X\geq 0$ ist der Erwartungswert von $X$ immer definiert. Er kann endlich oder unendlich sein.
> 	 - Wenn $X$ kein konstantes Vorzeichen hat und $\mathbb{E}[|X|]<\infty$ nicht erfüllt ist, dann sagen wir, der Erwartungswert von $X$ ist **undefiniert**
> -  Erwartungswert aus Gleichung (4.2) kann auch wie folgt ausgedrückt werden $\mathbb{E}[X]=\int\limits_{0}^{\infty}(1-F_{X}(x)) \, dx-\int\limits_{-\infty}^{0} F_{X}(x) \, dx$

## Erwartungswert diskreter Zufallsvariablen
>[!info] #Theorem 4.8 **Erwartungswert (diskret)**
>Gegeben: diskrete Zufallsvariable $X:\Omega\to \mathbb{R}$ deren Werte fast sicher in $W$ (endlich oder abzählbar) liegen.
>Dann gilt 
>$$\mathbb{E}[X]=\sum\limits_{x\in W}x\cdot \mathbb{P}[X=x]=\sum\limits_{x\in W}x p_{X}(x)$$
>solange der Erwartungswert wohldefiniert ist.
>- #disclaimer 4.9 Der Erwartungswert ist wohldefiniert, sofern die Reihe $\sum\limits_{x\in W}x\cdot \mathbb{P}[X=x]$ absolut konvergiert d.h. $\sum\limits_{x\in W}|x|\cdot \mathbb{P}[X=x]<\infty$
>  Andernfalls existiert der Erwartungswert nicht.

### Beispiele
- #Example 4.10 **Bernoulli**: $X\sim Ber(p)\implies \mathbb{E}[X]=p$
	- #Example 4.13 **Indikatorfunktion** (beschreibt, ob ein Element in einer Menge ist oder nicht) $1_{A}\sim Ber(\mathbb{P}[A])\implies \mathbb{E}[+_{A}]=\mathbb{P}[A]$
- #Example 4.12**Poisson**: $X\sim Poisson(\lambda)\implies \mathbb{E}[X]=\lambda$
	- #proof ![Pasted image 20240415224836.png](/img/user/Semester4/WS/Wahrscheinlichkeit/attachments/Pasted%20image%2020240415224836.png)
- #Example 4.14 **Binomialverteilung**: $X\sim Bin(n,p)\implies \mathbb{E}[X]=np$
	- #proof ![Pasted image 20240415225222.png](/img/user/Semester4/WS/Wahrscheinlichkeit/attachments/Pasted%20image%2020240415225222.png)![Pasted image 20240415225255.png](/img/user/Semester4/WS/Wahrscheinlichkeit/attachments/Pasted%20image%2020240415225255.png)
## Erwartungswert transformierte Zufallsvariablen
>[!info] #Theorem 4.15 
>Gegeben: diskrete Zufallsvariable $X:\Omega\to \mathbb{R}$, Abbildung $\phi:\mathbb{R}\to \mathbb{R}$
>Dann gilt $$\mathbb{E}[\phi(x)]=\sum\limits_{x\in W}\phi(x)\cdot \mathbb{P}[X=x]$$
>solange der Erwartungswert wohldefiniert ist.