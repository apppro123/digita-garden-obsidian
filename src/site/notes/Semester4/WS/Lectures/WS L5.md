---
{"dg-publish":true,"permalink":"/semester4/ws/lectures/ws-l5/"}
---


>[!info] #Theorem 3.3. **Wahrscheinlichkeit eines Punktes**
>Gegeben: Zufallsvariable $X:\Omega\to \mathbb{R}$ mit Verteilungsfunktion $F$.
>Für jedes $x\in\mathbb{R}$ gilt $\mathbb{P}[X=x]=F(x)-F(x-)$
>- Interpretation: Sei $x\in\mathbb{R}$ fixiert
>	- Wenn $F$ in einem Punkt $x\in\mathbb{R}$ nicht stetig ist, dann ist die "Sprunghöhe" $F(x)-F(x-)$ gleich der Wahrscheinlichkeit, dass $X=x$
>	- Falls $F$  stetig in einem Punkt $x\in\mathbb{R}$ ist, dann gilt $\mathbb{P}[X=x]=0$

>[!info] #Def 3.4. 
>Gegeben: Ereignis $A\in\cal{F}$
>Wir sagen $A$ tritt $\mathbb{P}$-fast sicher ( #short $\mathbb{P}$-f.s.) ein, falls $\mathbb{P}[A]=1$ ( #english $\mathbb{P}$-almost surely ( #short $\mathbb{P}$-a.s.))
>- Abkürzung falls Wahrscheinlichkeitsmass $\mathbb{P}$ klar ist und schreiben nur "fast sicher ( #short f.s.)"
>- #disclaimer 3.5. Erweiterung der Notation auf allgemeine Mengen $A\subset\Omega$ (nicht unbedingt $A\in\cal{F}$). Wir sagen, dass $A$ fast sicher eintritt, falls ein Ereignis $A'\in\cal{F}$ existiert, sodass $A'\subset A$ und $\mathbb{P}[A']=1$
>- e.g. Wir schreiben $X\leq Y$ $\mathbb{P}$-f.s., falls $\mathbb{P}[X\leq Y]=1$
>- Wenn wir mit stetigen ZV arbeiten, ist es oft restriktiv die Ungleichung $X(\omega)\leq Y(\omega)$ für alle $\omega\in\Omega$ zu fordern. Deshalb fordern wir die Ungleichung nur auf einer Menge mit Mass $1$.
### Diskrete Zufallsvariablen
>[!info] #Def 3.7. **Diskrete Zufallsvariablen**
>Eine ZV $X:\Omega\to \mathbb{R}$ heisst **diskret**, falls eine endliche oder abzählbare Menge $W\subset \mathbb{R}$ existiert, sodass $\mathbb{P}[X\in W]=1$, wenn also die Werte von $X$ fast sicher in $W$ liegen.
>- #disclaimer 3.8. 
>  gegeben: endlicher oder abzählbarer Grundraum $\Omega$
>  Dann ist jede ZV $X:\Omega\to \mathbb{R}$ diskret. In der Tat ist das Bild 
>  $$X(\Omega)=\{x\in\mathbb{R}|\exists \omega \in\Omega:X(\omega)=x\}$$
>  endlich oder abählbar und wir haben $\mathbb{P}[X\in W]=1$ mit $W=X(\Omega)$

>[!info] #Def 3.9. **Gewichtsfunktion**
>Für eine diskrete ZV $X$ mit Wertebereich $W(X)=\{x_{1},x_{2},\dots\}$ und den dazugehörigen Wahrscheinlichkeiten $\{p_{1},p_{2},\dots\}$ definieren wir die Gewichtsfunktion ( #short probability mass function ( #short pmf)) oder diskrete Dichte von $X$ als
>$$p_{X}:W(X)\to[0,1]\text{  mit  }p_{X}(x_{k}):=\mathbb{P}[X=x_{k}]=p_{k}$$
>Die Zahlenfolge $\{p_{X}(x_{k})\}_{x_{k}\in W(X)}$ nennen wir auch **Verteilung von $X$**

>[!info] #Proposition 3.10. 
>Die Gewichtsfunktion $p_{X}$ einer diskreten ZV $X$ hat folgende Eigenschaften:
>- Für alle $x_{k}\in W(X)$ gilt $p_{X}(x_{k})\in[0,1]$
>- Die Wahrscheinlichkeiten addieren sich zu $1$,
>  $$\sum\limits_{x_{k}\in W(X)}p_{X}(x_{k})=\mathbb{P}[X\in W(X)]=1$$

>[!info] #disclaimer 3.11. 
>Umgekehrt, wenn wir eine Folge von Zahlen $(p(x)_{x\in W})$ mit Werten in $[0,1]$ haben, sodass $\sum\limits_{x\in W}p(x)=1$, dann gibt es nach *Satz 2.35* einen Wahrscheinlichkeitsraum $(\Omega,\cal{F},\mathbb{P})$ und eine ZV $X$ mit zugehöriger Verteilung $(p(x))_{x\in W}$.
>Diese Bebachtung ist in der Praxis wichtig, den sie erlaubt uns zu schreiben: "Sei $X$ eine diskrete ZV mit Verteilung $(p(x))_{x\in W}$."

### Zusammenhang Verteilungs- und Gewichtsfunktion
>[!info] #Theorem 3.12. 
>Sei $X$ eine diskrete ZV mit Werten in $W$ und Gewichtsfunktionen $p_{X}$. Dann ist die Verteilungsfunktion von $X$ gegeben durch 
>$$\begin{equation}
>F_{X}(x)=\mathbb{P}[X\leq x]=\sum\limits_{y\leq x, y\in W}p_{X}(y)
>\end{equation}$$
>- Insbesondere ist $F_{X}$ also durch $p_{X}$ **vollständig festgelegt**. Mit dem gleichen Argument erhält man auch für jede messbare Teilmenge $B\subseteq W$, $P[X\in B]=\sum\limits_{x\in B}p_{X}(x)$
>- #disclaimer 3.13 
>  Gleichung (3.1) drückt die Verteilungsfunktion $F_{X}$ in Bezug auf $p_{X}$ als eine stückweise konstante Funktion aus.
>  Umgekehrt ist eine ZV mit einer stückweisen konstankten Verteilungsfunktion $F_{X}$ diskret. $W$ und $p_{X}$ sind dann gegeben durch $W=\{\text{ Sprungstelle von }F_{X}\}$ und $p(x)=\text{"Sprunghöhe im Punkt }x\in W$
>

>[!info] #Theorem 3.19. **Summe unabhängiger Bernoulli-ZV**
>Gegeben: $p\in[0,1]$, $n\in\mathbb{N}$, unabhängige $X_{1},\dots,X_{n}\sim Ber(p)$
>Dann gilt $S_{n}:=X_{1}+\dots+X_{n}\sim Bin(n,p)$

>[!info] #Theorem 3.23 
>Gegeben: unendliche Folge von unabhängigen Bernoulli-ZV $X_{1},X_{2},\dots$ mit Parameter $p$
>Dann ist $T:=\inf\{n\geq 1|X_{n}=1\}$ eine geometrisch verteilte ZV mit Parameter $p$.
>- #disclaimer 3.24. Sei z.B. $T\sim \operatorname{Geom}(p)$, dann ist $T>n$, wenn die ersten $n$ Bernoulli-Expiremente fehlschlagen. Daher gilt $\mathbb{P}[T>n]=(1-p)^{n}$

