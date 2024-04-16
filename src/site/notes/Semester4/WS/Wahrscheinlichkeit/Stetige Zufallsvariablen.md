---
{"dg-publish":true,"permalink":"/semester4/ws/wahrscheinlichkeit/stetige-zufallsvariablen/"}
---

>[!info] #Def 3.37 **Stetig verteilte Zufallsvariablen**
> Eine Zufallsvariable $X:\Omega\to \mathbb{R}$ heisst **stetig**, wenn eine nicht-negative Funktion $f_{X}:\mathbb{R}\to \mathbb{R}_{+}$ existiert, sodass die Verteilungsfunktion $F_{X}$ dargestellt werden kann als
> $$F_{X}(x)=\int\limits_{-\infty}^{x} f_{X}(t) \, dt $$
> Wir nennen $f_{X}$ die Dichte(-funktion) von $X$ ( #english probability density function ( #short pdf)).
> - **Intuition**: Der "Wert" $f_{X}(t)dt$ ist die Wahrscheinlichkeit, dass $X$ Werte im Intervall $[t,t+dt]$ annimmt.
>   Die Terminologie "stetig" ergibt sich aus der Tatsache, dass die Gleichung oben impliziert, dass $F_{X}$ eine stetige Funktion ist. Insbesondere gilt für alle $x\in\mathbb{R}$ laut Satz 3.3, $\mathbb{P}[X=x]=0$

>[!info] #Def 3.38 **Stückweise stetig differenzierbare Funktion**
>- Im Kontext von $\mathbb{R}$ wird oft gesagt, dass ein Objekt eine Eigenschaft **stückweise** ( #english piecewise) erfüllt, wenn sie die Eigenschaft auf einer Partition des Definitionsbereichs erfüllt.
>- Wir sagen, eine Funktion $f$ ist **stückweise stetig differenzierbar**, wenn es eine Partition $-\infty=x_{0}<x_{1}<\dots<x_{n-1}<x_{n}=\infty$ gibt, sodass $f$ auf jedem Intervall $x_{i},x_{i+1}$ stetig differenzierbar ist.
>- Intuition: D.h. dass die Funktion $f$ nur an den Punkten $x_{1},\dots,x_{n-1}$ "Probleme" machen könnte. Wir lösen diese Probleme, indem wir diese Punkte effektiv entfernen und die Funktion nur auf der daraus entstehenden Partition betrachten.

>[!info] #Theorem 3.39 
>Gegeben: Zufallsvariable $X$, stetige und stückweise differenzierbare Verteilungsfunktion $F_{X}$ auf einer Partition $-\infty=x_{0}<x_{1}<\dots<x_{n-1}<x_{n}=\infty$
>Dann ist $X$ eine stetige Zufallsvariable und die Dichtefunktion $f_{X}$ kann wie folgt konstruiert werden:
>$$f_{X}(x)\begin{cases} 
> F_{X}'(x)&\exists k\in\{0,\dots,n-1\}:x\in(x_{k},x_{k+1}) \\
> a_{k}&x\in\{x_{1},\dots,x_{n-1}\}
> \end{cases}$$
>wobei die Werte $a_{k}$ beliebig gewählt werden dürfen.
>In anderen Worten, es gilt $f_{X}(x)=F'(X)(x)$ in allen Stetigkeitspunkten $x$ von $f_{X}$
>- #disclaimer 3.40 Die Dichtefunktion $f_{X}$ ist (fast exakt) dast **stetige Analogen** zur Gewichtsfunktion $p_{X}$ einer diskreten Zufallsvariablen
>	- Für messbare Mengen $B\subset \mathbb{R}$ gilt
>	  $$\mathbb{P}[X\in B]=\int\limits_{B}f_{X}(x)  \, dx \text{ analog zu }\mathbb{P}[X\in B]=\sum\limits_{x\in B}p_{X}(x)$$ 
> 	- Da allerdings $\mathbb{P}[X=x]=0$ für jedes $x\in\mathbb{R}$, hat in diesem Sinn $X$ keine Gewichtsfunktion wie eine diskrete Zufallsvariable.
> 	- Ist allerdings $f_{X}$ stetig an der Stelle $x$, so haben wir
> 	  $$f_{X})(x)=\lim\limits_{ \epsilon \searrow 0 } \frac{1}{\epsilon}\int\limits_{x}^{x+\epsilon} f_{X}(t) \, dt  =\lim\limits_{ \epsilon \searrow 0 } \frac{\mathbb{P}[x<X\leq x+\epsilon]}{\epsilon} $$
> 	  und somit
> 	  $\mathbb{P}[X\in(x,x+\epsilon)]\approx \epsilon f_{X}(x)$ für kleine $\epsilon$
> 	 - Einfache **Merkregel**: Um vom diskreten zum stetigen Fall zu kommen, kann die Kombination (Summe, Gewichtsfunktion) systematisch durch (Integral, Dichtefunktion) ersetzt werden.

## Beispiele
- #Example 3.41 Gleichverteilung: ![Pasted image 20240402174928.png](/img/user/Semester4/WS/Wahrscheinlichkeit/attachments/Pasted%20image%2020240402174928.png)
	- Intuition: Die Gleichverteilung auf einem Intervall $[a,b]$ ist ein Modell für die zufällige Wahl eines Punktes in $[a,b]$.
	- Eigenschaften: ![Pasted image 20240402175210.png](/img/user/Semester4/WS/Wahrscheinlichkeit/attachments/Pasted%20image%2020240402175210.png)
- #Example 3.43 **Exponentialverteilung** ![Pasted image 20240402175236.png](/img/user/Semester4/WS/Wahrscheinlichkeit/attachments/Pasted%20image%2020240402175236.png)
	- Intuition: ![Pasted image 20240402175453.png](/img/user/Semester4/WS/Wahrscheinlichkeit/attachments/Pasted%20image%2020240402175453.png)
	- Eigenschaften: ![Pasted image 20240402175518.png](/img/user/Semester4/WS/Wahrscheinlichkeit/attachments/Pasted%20image%2020240402175518.png)
- #Example 3.45 **Cauchy-Verteilung**: ![Pasted image 20240402175559.png](/img/user/Semester4/WS/Wahrscheinlichkeit/attachments/Pasted%20image%2020240402175559.png)
	- ![Pasted image 20240402175615.png](/img/user/Semester4/WS/Wahrscheinlichkeit/attachments/Pasted%20image%2020240402175615.png)
## [[Semester4/WS/Wahrscheinlichkeit/Normalverteilung\|Normalverteilung]]