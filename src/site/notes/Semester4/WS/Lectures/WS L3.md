---
{"dg-publish":true,"permalink":"/semester4/ws/lectures/ws-l3/"}
---

> [!info] #Def 2.1 **Zufallsvariable**
> Gegeben: Wahrscheinlichkeitsraum $(\Omega,\cal{F},\mathbb{P})$
> Eine **(reelwertige) Zufallsvariable** ( #short Z.V.) ist eine Abbildung $X:\Omega\to \mathbb{R}$ sodass für alle $x\in\mathbb{R}$ gilt
> $$\{\omega\in\Omega|X(\omega)\leq x\}\in\cal{F}$$

>[!info] #Remark 2.5 **Messbarkeit**
>Wenn eine (reelwertige) Funktion die Eigenschaft (2.1) erfüllt, heisst diese Funktion messbar ( #english measurable).
>Da wir an Ausgängen von Zufallsexperimenten interessiert sind, wollen wir Wahrscheinlichkeiten der Form
>$$\mathbb{P}[\{\omega\in\Omega|X(\omega)\in B\}]\text{ für bestimme Mengen }B\subset \mathbb{R}$$
>berechnen können. Z.B.
>- Falls $B=\{2,4,6\}$ wenn wir die Wahrscheinlichkeit für einen gerade Zahl beim Würfeln möchten.
>- Weil das Wahrscheinlichkeitsmass $\mathbb{P}$ auf $\cal{F}$ definiert ist, müssen die Urbilder aller dieser Mengen $B$,
>  $$X^{-1}(B):=\{\omega\in\Omega|X(\omega)\in B\}$$
>  in $\cal{F}$ enthalten sein.
> - In dieser Vorlesung verlangen wir für Messbarkeit, dass $X^{-1}(B)\in\cal{F}$ für alle $B\in\cal{B}(\mathbb{R})$
> 	- Hierbei ist $\cal{B}(\mathbb{R})$ die **borelsche $\sigma$-Algebra** auf $\mathbb{R}$
> 	- z.B. alle offenen, abgeschlossenen und kompakten Mengen in $\mathbb{R}$ oder alle Intervalle der Form $(a,b),[a,b],(a,b],[a,b),(-\infty,b),(-\infty,b],(a,\infty),[a,\infty)$ für $a,b\in\mathbb{R}$

>[!info] #Def 2.10 **Verteilungsfunktion**
>Gegeben: reelwertige Zufallsvariable $X$, Wahrscheinlichkeitsraum $(\Omega,\cal{F},\mathbb{P})$
>Die **(kumulative) Verteilungsfunktion von $X$** ( #english cumulative distribution function) ( #short cdf) ist die Funktion $F_{X}:\mathbb{R}\to[0,1]$, definiert durch
>$$F_{X}(x):=\mathbb{P}[X\leq x]$$

>[!info] #Theorem 2.13 **Eigenschaften von Verteilungsfunktionen**
>Gegeben: Zufallsvariable $X$, Wahrscheinlichkeitsraum $(\Omega,\cal{F},\mathbb{P})$
>Die Verteilungsfunktion $F_{X}:\mathbb{R}\to[0,1]$ von $X$ erfüllt folgende Eigenschaften:
>- (i) $F_{X}$ ist **monoton wachsend**
>- (ii) $F_{X}$ ist **rechtsstetig** d.h. für alle $x\in\mathbb{R}$ gilt $F_{X}(x)=\lim_{ h \to 0 }F_{X}(x+h)$
>- (iii) Es gelten die Grenzwerte $\lim_{ x \to -\infty }F_{X}(x)=0$ und $\lim_{ x \to \infty }F_{X}(x)=1$
>I also found
>- [wikipedia](https://en.wikipedia.org/wiki/Cumulative_distribution_function) 
>	- $\mathbb{P}(X\leq x)=F_{X}(x)$
>	- $\mathbb{P}(a<X\leq b)=F_{X}(b)-F_{X}(a)$
>	- $\mathbb{P}(X=b)=F_{X}(b)-\lim\limits_{ x \to b^{-} }F_{X}(x)$
>- [Math Stackexchange](https://math.stackexchange.com/questions/4555678/what-is-mathbbp-lefta-x-mathbin-colorred-b-right-for-a-discrete)
>	- $\mathbb{P}(a<X<b)=\mathbb{P}(X<b)-\mathbb{P}(X\leq a)=\lim\limits_{ x \to b^{-} }F_{X}(x)-F_{X}(a)$

>[!info] #Def 2.16 **Gemeinsame Verteilungsfunktion**
>Gegeben: Zufallsvariablen $X_{1},\dots,X_{n}$
>Die **gemeinsame Verteilungsfunktion von** $X_{1},\dots,X_{n}$ ist die Abbildung $F:\mathbb{R}^{n}\to[0,1]$ definiert durch
>$$(x_{1},\dots,x_{n})\mapsto F(x_{1},\dots,x_{n})=\mathbb{P}[X_{1}\leq x_{1},\dots,X_{n}\leq x_{n}]$$

>[!info] #Def 2.18 **[[general/Wahrscheinlichkeit/Unabhängigkeit\|Unabhängigkeit]] von Zufallsvariablen**
>Gegeben: Zufallsvariablen $X_{1},\dots,X_{n}$ auf Wahrscheinlicheitsraum $(\Omega,\cal{F},\mathbb{P})$. Dann heissen $X_{1},\dots X_{n}$ **unabhängig**, wenn für alle $x_{1},\dots,x_{n}\in\mathbb{R}$ gilt
>$$\mathbb{P}[X_{1}\leq x_{1},\dots,X_{n}\leq x_{n}]=\mathbb{P}[X_{1}\leq x_{1}]*\dots*\mathbb{P}[X_{n}\leq x_{n}]$$
>- #Remark 2.19 $X_{1},\dots,X_{n}$ sind genau dann unabhängig, wenn für alle Intervalle $I\subset \mathbb{R},\dots,I_{n}\subset \mathbb{R}$ die Ereignisse $\{ X_{1}\in I_{1} \},\dots \{ X_{n}\in I_{n} \}$ unabhängig sind.
>- Wenn wir eine Menge unabhängiger Zufallsvariablen haben und disjunkte Gruppen solcher Zufallsvariablen bilden, dann sind diese Gruppen auch wiederum unabhängig voneinander.

> [!info] #Theorem 2.21 **Gruppierung von Zufallsvariablen**
> Gegeben: unabhängige Zufallsvariablen $X_{1},\dots X_{n}$, Indexe $1\leq i_{1}<i_{2}<\dots<i_{k}\leq n$, Abbildungen $\varphi_{1},\dots,\varphi_{k}$
> Dann sind 
> $$Y_{1}:=\varphi_{1}(X_{1},\dots,X_{i_{1}}),Y_{2}:=\varphi_{2}(X_{1},\dots,X_{i_{2}}),\dots,Y_{k}:=\varphi_{k}(X_{1},\dots,X_{i_{k}})$$
> unabhängig.

>[!info] #Def 2.22. **Unabhängig und identisch verteilt**
>Eine Folge von Zufallsvariablen $X_{1},X_{2}$ heisst
>- **unabhängig** falls $X_{1},\dots,X_{n}$ für alle $n\in\mathbb{N}$ unabhängig sind.
>- **unabhängig und identisch verteilt** ( #short u.i.v.) ( #english independent and identically distributed ( #short i.i.d.)) falls sie unabhängig ist und die Zufallsvariablen dieselbe Verteilungsfunktion haben d.h. für alle $k,l\in\mathbb{N}$ gilt $F_{X_{k}}=F_{X_{l}}$

