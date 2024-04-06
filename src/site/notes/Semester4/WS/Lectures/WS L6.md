---
{"dg-publish":true,"permalink":"/semester4/ws/lectures/ws-l6/"}
---

> [!info] #Theorem 3.25 **Gedächtnislosigkeit** der geometrischen Verteilung
> Gegeben: $T\sim \operatorname{Geom}(p)$, $p\in(0,1)$
> Dann gilt für alle $n\geq 0$ und alle $k\geq 1$
> $$\mathbb{P}[T\geq n+k|T>n]=\mathbb{P}[T\geq k]$$
> - Wenn wir also nach $n$ Schritten immer noch auf den ersten Erfolg warten, dann ist die verbleibende Wartezeit wiederum $\operatorname{Geom}(p)$ verteilt.
> 
> >[!info]- Beweis
> > $\mathbb{P}[T\geq n+k|T>n]=\frac{\mathbb{P}[\{T\geq n+k\}\cap\{T>n\}]}{\mathbb{P}[T>n]}=\frac{\mathbb{P}[T\geq n+k]}{\mathbb{P}[T>n]}=\frac{(1-p)^{n+k-1}}{(1-p)^{n}}=(1-p)^{k-1}=\mathbb{P}[T\geq k]$

>[!info] #Example 3.26 **negativbinomiale Verteilung**
>Gegeben: Zufallsvariable $X$
>$X$ hat eine negativbinomaile Verteilung mit Parameter $r\in\mathbb{N}$ und $p\in[0,1]$, wir schreiben $X\in \operatorname{NBin}(r,p)$, wenn für alle $k\in\{r,r+1,r+2,\dots\}$ gilt:
>$$\mathbb{P}[X=k]=\pmatrix{k-1\\r-1}p^{r}(1-p)^{k-r}$$
>Das ist eine Verallgemeinerung der geometrischen Verteilung und beschreibt die Wartezeit bis zum r -ten Erfolg in einer unendlichen Folge von Bernoulli-Experimenten. Die geometrische Verteilung erhält man als Spezialfall für $r=1$

>[!info] #Theorem 3.27 
>Gegeben: unendliche Folge von unabhängigen Bernoulli-Zufallsvariablen $X_{1},X_{2}$ mit Parameter $p$
>Dann hat 
>$$T_{r}=\inf\{n\geq 1|\sum\limits_{l=1}^{n}X_{l}=r\}$$
>eine negativbinomiale Verteilung mit Parametern $r$ und $p$
>- #disclaimer 3.28 Sind die Zufallsvariaben $X_{1},\dots,X_{r}\sim\operatorname{Geom}(p)$ und unabhängig, so ist ihre Summe $X=X_{1}+\dots+X_{r}\sim NBin(r,p)$

>[!info] #Example 3.29 **Hypergeometrische Verteilung**
> Eine Zufallsvariable $X$ heisst hypgergeometrische verteilt mit Parametern $n\in\mathbb{N}$ und $m,r\in\{1,\dots,n\}$, wir schreiben $X\sim H(n,r,m)$, wenn für alle $k\in\{0,1,\dots,min(m,r)\}$ gilt
> $$\mathbb{P}[X=k]=\frac{\pmatrix{r\\k}\pmatrix{n-r\\m-k}}{\pmatrix{n\\m}}$$
> Diese Gewichtsfunktion kommt wie folgt zustande
> #Theorem 3.30 Seien in einer Urne $n$ Gegenstände, davon $r$ vom Typ $1$ und $n-r$ vom Typ $2$. Es werden $m$ Gegenstände ohne Zurücklegen gezogen. Sei $X$ nun die Anzahl der gezogenen Gegenstände vom Typ $1$. Dann ist $X$ hypergeometrisch mit den Parametern von oben verteilt.
> >[!info]- Beweis
> >![Pasted image 20240402164835.png](/img/user/Semester4/WS/Lectures/attachments/Pasted%20image%2020240402164835.png)
> 
> #Example 3.31 Lotto 
> Im Schweizer Lotto, wo 6 aus 42 zahlen richtig getippt werden sollen, ist die Anzahl der richtigen getippten Zahlen bei einem einzelnen Tipp hypergeometrisch verteilt mit Parametern $n=42,r=6,m=6$. ![Pasted image 20240402165017.png](/img/user/Semester4/WS/Lectures/attachments/Pasted%20image%2020240402165017.png)

>[!info] Poisson-Verteilung
>Gegeben: positive reelle Zahl $\lambda>0$
>Eine Zufallsvariable $X$ heisst Poisson-verteilt mit Parameter $\lambda$, wir schreiben $X\sim\operatorname{Poisson}(\lambda)$, wenn sie Werte $\mathbb{N}$ annimt und für alle $k\in\mathbb{N}_{0}$ gilt
>$$\mathbb{P}[X=k]=\frac{\lambda^{k}}{k!}e^{-\lambda}$$ 

 >[!info] #Theorem 3.34 **Poisson-Approximation der Binomialverteilung**
 >Gegeben: $\lambda>0$ 
 >Für jedes $n\geq 1$ betrachten wir $n$ Zufallsvariablen $X_{n}\sim\operatorname{Bin}(n,\lambda)$. Sei $N\sim \operatorname{Poisson}(\lambda)$. Dann gilt für alle $k\in\mathbb{N}$
 >$$\lim\limits_{ n \to \infty } \mathbb{P}[X_{n}=k]=\mathbb{P}[N=k]$$
 >- #disclaimer 3.35 Diese Art von Konvergenz wird **Konvergenz in Verteilung** ( #english lish convergence in distribution, convergence in law)oder **schwache Konvergenz** ( #english weak convergence) genannt. Intuitiv besagt sie, dass $X_{n}$ und $N$ sehr ähnliche wahrscheinlichkeitstheoretische Eigenschaften für grosse $n$ haben.
 >- #Example 3.36 ![Pasted image 20240402171959.png](/img/user/Semester4/WS/Lectures/attachments/Pasted%20image%2020240402171959.png)

[[Semester4/WS/Wahrscheinlichkeit/Stetige Zufallsvariablen\|Stetige Zufallsvariablen]]