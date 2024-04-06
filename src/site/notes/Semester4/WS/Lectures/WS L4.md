---
{"dg-publish":true,"permalink":"/semester4/ws/lectures/ws-l4/"}
---


Beweis zu Satz 2.13
1. Existenzsatz von Kolmogorov und Folgen von i.i.d. Bernoulli Zufallsvariablen
>[!info] #Def 2.24 **Bernoulli**
>Gegeben: $p\in[0,1]$.
>Eine Zufallsvariable $X$ heisst **Bernoulli Zufallsvariable** mit Parameter $p$, wenn gilt
>$$\mathbb{P}[X=0]=1-p\text{ und }\mathbb{P}[X=1]=p$$
>Wir schreiben $X\sim Ber(p)$.

>[!info] #Theorem 2.26 **Existenz von Kolmogorov**
>Es existiert ein Wahrscheinlichkeitsraum $(\Omega,\cal{F},\mathbb{P})$ und eine unendliche Folge von i.i.d. Bernoulli Zufallsvariablen $X_{1},X_{2},\dots$ auf $(\Omega,\cal{F},\mathbb{P})$ mit Parameter $\frac{1}{2}$

>[!info] #Theorem 2.27. 
>Eine Zufallsvariable $U$ heisst **gleichverteilt auf $[0,1]$**, wir schreiben $U\sim\cal{U}([0,1])$, falls ihre Verteilungsfunktion gegeben ist durch
>$$F_{U}(x)=\begin{cases} 
0&x<0 \\ 
x&0\leq x\leq 1 \\
1&x>1\end{cases}$$
> ![Pasted image 20240318094630.png](/img/user/Semester4/WS/Lectures/attachments/Pasted%20image%2020240318094630.png)
2. Konstruktion von gleichverteilten Zufallsvariablen auf $[0,1]$ ![Pasted image 20240318094745.png](/img/user/Semester4/WS/Lectures/attachments/Pasted%20image%2020240318094745.png)
 >[!info] #Theorem 2.28 
 >Die Abbildung $X:\Omega\to[0,1]$ definiert in Gleichung (2.3) ist eine gleichverteilte Zufallsvariable auf $[0,1]$.
 >>[!Info]- **Beweis**
 >>Es ist schnell sichtbar, dass für alle $\omega\in\Omega$ gilt, $X(\omega)\in[0,1]$. Somit gilt für $x<0$, dass $F_{X}(x)=\mathbb{P}[X\leq x]=0$ und für $x\geq 1$, dass $F_{X}(x)=1$
 >>Sei also $x\in[0,1)$ und sei $\{x_{n}\}_{n\in\mathbb{N}}$ ihre eindeutige Binärdarstellung wie in Lemma 2.29. Dann gilt
 >>$$\begin{align}\{X>x\}=&\{X_{1}>x_{1}\}\cup\\
&\{\{X_{1}=x_{1}\}\cap\{X_{2}>x_{2}\}\}\cup\dots \\
\end{align}$$
>> Also entweder ist die erste Ziffer grösser oder die erste Ziffer ist gleich und die zweite ist grösser usw.
>> ![Pasted image 20240318100249.png](/img/user/Semester4/WS/Lectures/attachments/Pasted%20image%2020240318100249.png)
 
 >[!info] #Lemma 2.29 **Binärdarstellung**
 > Jedes $x\in[0,1)$ kann eindeutig in der Form
 > $$x=\sum\limits_{n=1}^{\infty}2^{-n}x_{n}$$
 > dargestellt werden, wobei für alle $n\in\mathbb{N}$ gilt,$x_{n}\in\{0,1\}$, und für jedes $N\in\mathbb{N}$ gibt es ein $k>N$, sodass $x_{k}=0$ (als odie Folge "endet" nicht in unendlich vielen $1$-en.) Die Folge $\{x_{n}\}_{n\in\mathbb{N}}$ heisst Binärdarstellung von $x$ und wir schreiben $x=(.x_{1}x_{2}\dots)_{2}$
3. Konstruktion von Zufallsvariablen mit beliebiger Verteilungsfunktion $F$
Da wir die Gleichverteilung auf $[0, 1]$ haben, würden wir nun gerne Zufallsvariablen mit beliebiger Verteilungsfunktion konstruieren können.
Gegeben: $F:\mathbb{R}\to[0,1]$ eine Funktion, die die Eigenschaften (i)-(iii) aus Satz 2.13 erfüllt.
Falls $F$ streng monoton steigend und stetig ist, dann ist $F$ bijektiv und es existiert eine Umkehrfunktion $F^{-1}$. Für jedes $\alpha\in[0,1]$ ist $x:=F^{-1}(\alpha)$ die eindeutige reelle Zahl, für die $F(x)=\alpha$ gilt.
Allgemein kann die sogenannte **verallgmeinerte inverse Verteilungsfunktion** oder **Quantil-Funktion** für $F$ definiert werden.
>[!info] #Def 2.30 **Verallgemeinerte inverse Verteilungsfunktion**
>Die **Verallgemeinerte inverse Verteilungsfunktion** von $F$ ist eine Abbildung $F^{-1}:(0,1)\to \mathbb{R}$ definiert durch
>$$F^{-1}(\alpha)=\inf\{x\in\mathbb{R}|F(x)\geq\alpha\}$$ 

Nach Definition des Infimums und unter Verwendung der Rechtsstetigkeit von $F$ gilt für jedes $x\in\mathbb{R}$ und $\alpha\in(0,1)$, dass
$$F^{-1}(\alpha)\leq x\iff \alpha\leq F(x)$$
 ![Pasted image 20240318100954.png](/img/user/Semester4/WS/Lectures/attachments/Pasted%20image%2020240318100954.png)
 Mithile der verallgemeinerten inversen Verteilungsfunktion können wir nun Zufallsvariablen mit beliebigen Verteilungsfunktionen konstruieren.
 >[!info] #Theorem 2.31. **Inversionsmethode**
 >Gegeben: $F:\mathbb{R}\to[0,1]$ eine Abbildung mit den Eigenschaften (i)-(iii) aus Satz 2.13, $U\sim\cal{U}([0,1])$
 >Dann hat die Zufallsvariable $X:=F^{-1}(U)$ die Verteiungsfunktion $F$.
 >> [!info]- Beweis
 >> $$\mathbb{P}[X\leq x]=\mathbb{P}[F^{-1}(U)\leq x]=\mathbb{P}[U\leq F(x)]=F(x)\qquad\square$$
 > #disclaimer 2.33
 > Wir bemerken, dass $X=F^{-1}(U)$ strenggenommen nur auf einer Menge mit Wahrscheinlichkeit $1$ (da $\mathbb{P}[U\in(0,1)]=1$) aber nicht unbedingt auf ganz $\Omega$ definiert ist. Wir beheben das Problem mittels folgender Definition
 > $$X(\omega)\begin{cases}
F^{-1}(U(\omega))&U(\omega)\in(0,1) \\
0&\text{sonst}
\end{cases}$$
> Dabei spielt $0$ selbst keine Rolle und es kann jede beliebe reelle Zahl genommen werden.
4. allgemeine Folgen von unabhängigen Zufallsvariablen
>[!info] #Theorem 2.35.
>Gegeben: Folge von Funktionen $F_{1},F_{2}$ auf $\mathbb{R}\to[0,1]$, die die Eigenschaften (i)-(iii) aus Satz 2.13 erfüllen.
>Dann existiert ein Wahrscheinlichkeitsraum $(\Omega,\cal{F},\mathbb{P})$ und eine Folge von Zufallsvariablen $X_{1},X_{2},\dots$ auf diesem Wahrscheinlichkeitsraum, sodass
>- für jedes $k$ gilt, $X_{k}$ hat Verteilungsfunktion $F_{k}$ und
>- $X_{1},X_{2},\dots$ sind unabhängig.
>Dieser Satz erlaubt es uns, direkt mit Zufallsvariablen zu arbeiten, ohne den Wahrscheinlichkeitsraum $(\Omega,\cal{F},\mathbb{P})$ genauer zu definieren. 
>- Z.B. können wir für zwei Verteilungsfunktionen $F$ und $G$ stets annehmen, dass $X$ und $Y$ existieren, die unabhängig sind und Verteilungsfunktionen $F$ und $G$ besitzen