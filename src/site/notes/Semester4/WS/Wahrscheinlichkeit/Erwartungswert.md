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

## Erwartungswert stetiger Zufallsvariablen
>[!info] #Theorem 4.17 
>Gegeben: stetige Zufallsvariable $X$ mit Dichte $f_{X}$
>Dann gilt
>$$\mathbb{E}[X]=\int\limits_{-\infty}^{\infty} xf_{X}(x) \, dx $$
>solange das Integral absolute konvergiert. 
>- Falls das Integral nicht absolut konvergiert, existert der Erwartungswert (zumindest in $\mathbb{R}$) nicht. 

>[!info] #Theorem 4.18
>Gegeben: Zufallsvariable $X$ mit Dichte $f_{X}$, Abbildung $\varphi:\mathbb{R}\to \mathbb{R}$.
>Dann gilt
>$$\mathbb{E}[\varphi(X)]=\int_{-\infty}^{\infty} \varphi(x)f_{X}(x) \, dx $$

### Verteilungen
- **Gleichverteilung**: für $X\sim \cal{U}([a,b]),a<b$ ist $\mathbb{E}[X]=\frac{a+b}{2}$
- **Exponentialverteilung**: für $X\sim Exp(\lambda),\lambda>0$ ist $\mathbb{E}[X]=\frac{1}{\lambda}$
- **Normalverteilung**: für $X\sim\cal{N}(\mu,\sigma^{2}) ist $ $\mathbb{E}[X]=\mu$
- **Cauchy-Verteilung**: es existiert **kein Erwartungswert**, da absolute Integral $\infty$ gibt.
## Eigenschaften Erwartungswert
>[!info] #Theorem 4.25. **Linearität des Erwartungswerts**
>Gegeben: Zufallsvariablen $X,Y:\Omega\to \mathbb{R}$, $\lambda\in\mathbb{R}$ 
>Falls die Erwartungswerte wohldefiniert sind, gilt
>- (i) $\mathbb{E}[\lambda X]=\lambda \mathbb{E}[X]$
>- (ii) $\mathbb{E}[X+Y]=\mathbb{E}[X]+\mathbb{E}[Y]$
>- #disclaimer 4.26 
>  Gegeben: Zufallsvariablen $X_{k}:\Omega\to \mathbb{R}$, Konstanten $\lambda_{k}\in\mathbb{R},k\in\{1,\dots,n\}$
>  Falls alle Erwartungswerte wohldefiniert sind, gilt $\mathbb{E}\left[ \sum\limits_{k=1}^{n} \lambda_{k}X_{k} \right]=\sum\limits_{k=1}^{n}\lambda_{k}\mathbb{E}[X_{k}]$

>[!info] Theorem 4.29. **Monotonie des Erwartungswerts**
>Gegeben: Zufallsvariablen $X,Y$ sodass $X\leq Y$ f.s. gilt
>Falls beide Erwartungswerte wohldefiniert sind , gilt $\mathbb{E}[X]\leq \mathbb{E}[Y]$

>[!info] #Theorem 4.30. **Erwartungswerte bei Unabhängigkeit**
>Gegeben: unabhängige Zufallsvariablen $X,Y$ mit endlichen Erwartungswerten
>Dann gilt $\mathbb{E}[XY]=\mathbb{E}[X]\mathbb{E}[Y]$

>[!info] #Theorem 4.31. 
>Gegeben: unabhängige Zufallsvariablen $X_{1},\dots,X_{n}$ mit endlichen Erwartungswerten 
>Dann gilt $\mathbb{E}\left[ \prod\limits_{k=1}^{n} X_{k} \right]=\prod\limits_{k=1}^{n}\mathbb{E}[X_{k}]$

>[!info] #Theorem 4.32 
>Gegeben: Zufallsvariable $X$, Abbildung $f:\mathbb{R}\to \mathbb{R}_{+}$ sodass $\int\limits_{-\infty}^{\infty} f(x) \, dx=1$
>Dann sind folgende Aussagen äquivalent
>- (i) $X$ ist stetig mit Dichte $f$
>- (ii) für jede stückweise stetige, beschränkte Abbildung $\varphi:\mathbb{R}\to \mathbb{R}$ gilt
>  $$\mathbb{E}[\varphi(X)]=\int\limits_{-\infty}^{\infty} \varphi(x)f(x) \, dx $$

>[!Info] #Theorem 4.33 
>Gegeben: Zufallsvariablen $X,Y$
>Die folgenden Aussagen sind äquivalent
>- (i) $X,Y$ sind unabhängig
>- (ii) Für alle stückweise stetigen, beschränkten Abbildungen $\varphi,\psi:\mathbb{R}\to \mathbb{R}$ gilt
>  $\mathbb{E}[\varphi(X)\psi(Y)]=\mathbb{E}[\varphi(X)]\mathbb{E}[\psi(Y)]$

>[!Info] #Theorem 4.34 
>Gegeben: Zufallsvariablen $X_{1},\dots,X_{n}$
>Die folgenden Aussagen sind äquivalent
>- (i) $X_{1},\dots,X_{n}$ sind unabhängig
>- (ii) Für alle stückweise stetigen, beschränkten Abbildungen $\varphi_{1},\dots,\varphi_{n}:\mathbb{R}\to \mathbb{R}$ gilt
>  $\mathbb{E}[\varphi_{1}(X_{1})\cdot\dots \cdot \varphi_{n}(X_{n})]=\mathbb{E}[\varphi_{1}(X_{1})]\mathbb{E}[\varphi_{n}(X_{n})]$

>[!info] #Theorem 4.35 **Markow-Ungleichung**
>Gegeben: nicht-negative Zufallsvariable $X$, wachsende Funktion $g:X(\Omega)\to[0,\infty)$
>Für jedes $c\in\mathbb{R}$ mit $g(c)>0$ gilt $\mathbb{P}[X\geq c]\leq \frac{\mathbb{E}[g(X)]}{g(c)}$

>[!info] #Theorem 4.36 **Jensensche Ungleichung**
>Gegeben: Zufallsvariable $X$, konvexe Funktion $\varphi:\mathbb{R}\to \mathbb{R}$
>Falls $\mathbb{E}[\varphi(X)]$ und $\mathbb{E}[X]$ wohldefiniert sind, gilt (4.5) $$\varphi(\mathbb{E}[X])\leq \mathbb{E}[\varphi(X)]$$
>- #Corollary 4.37 **Dreiecksungleichung**
>  Die Anwedung der Jensenschen Ungleichung auf $\varphi(x)=x$ liefert die Dreiecksungleichung $$|\mathbb{E}[X]|\leq \mathbb{E}[|X|]$$ 
>  Eine weitere Folge ist der Zusammenhang zwischen dem Erwartungswert von $|X|$ und dem Erwartungswert von $X^{2}$. Die Jensensche Ungleichung liefert für die konvexe Funktion $\varphi(x)=x^{2}$ $$\mathbb{E}[|X|]\leq \sqrt{ \mathbb{E}[X^{2}] }$$