---
{"dg-publish":true,"permalink":"/semester4/ws/lectures/ws-l2/"}
---

> [!info] #Def 1.22 **Bedingte Wahrscheinlichkeit**
> Gegeben: Wahrscheinlichkeitsraum ($\Omega,\cal{F},\mathbb{P}$), $\mathbb{P}[B]>0$
> Dann ist $\mathbb{P}[A|B]:=\frac{\mathbb{P}[A\cap B]}{\mathbb{P}[B]}$
> - $\mathbb{P}[A|A]=1$
> - $\mathbb{P}[A|\Omega]=P[A]$
> - $\mathbb{P}[A\cap B]=\mathbb{P}[A|B]\mathbb{P}[B]$
> - $\mathbb{P}[A|B]$ ist **nicht definiert** für $\mathbb{P}[B]=0$



> [!info] #Theorem 1.25 
> Gegeben: Wahrscheinlichkeitsraum $(\Omega,\cal{F},\mathbb{P}), \mathbb{P}[B]>0$
> Dann ist $\mathbb{P}^{*}:\cal{F}\to[0,1]$ definiert durch $A\mapsto \mathbb{P}^{*}[A]:=P[A|B]$ wieder ein Wahrscheinlichkeitsmass auf $(\Omega,\cal{F})$
> - bedingte Wahrscheinlichkeit ist **nicht symmetrisch** in den beiden Argumenten. Insbesondere ist bei fixiertem Ereignis $A$ die Funktion $B\mapsto \mathbb{P}[A|B]$ kein Wahrscheinlichkeitsmass
> - Ist $\Omega$ endlich oder abzählbar mit $\cal{F}=\cal{P}(\Omega)$, dann ist $\mathbb{P}$ gegeben durch die Wahrscheinlichkeiten $p_{n}=\mathbb{P}[\{\omega_{n}\}]$. Das bedingte Wahrscheinlichkeitsmass $\mathbb{P}^{*}[\cdot]=\mathbb{P}[\cdot|B]$ ist dann durch 
>   $$p_{n}^{*}=\mathbb{P}^{*}[\{\omega_{n}\}]=\mathbb{P}[\{\omega_{n}\}|B]=\begin{cases}\frac{p_{n}}{\mathbb{P}[B]}&\text{für }\omega_{n}\in B,\\0&\text{für }\omega_{n}\ne B,\end{cases}$$
>   gegeben. Wir setzen alle Gewichte ausserhalb von $B$ auf Null und skalieren die Gewichte in $B$ mit einem festen Faktor, sodass ihre Summe wieder $1$ ergibt.

> [!info] #Theorem 1.29 **Satz von der totalen Wahrscheinlichkeit**
> Gegeben: $B_{1},\dots,B_{N}$ mit $\mathbb{P}[B_{n}]>0$ für jedes $1\leq n\leq N$ eine Partitione des Grundraums $\Omega$, d.h. $\bigcup_{n=1}^{N}B_{n}=\Omega$ mit $B_{n}\cap B_{m}=\emptyset$ für $n\ne m$. 
> Dann gilt für alle $A\in\cal{F}$
> $$\mathbb{P}[A]=\sum\limits_{n=1}^{N}\mathbb{P}[A|B_{n}]\mathbb{P}[B_{n}]$$


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



> [!info] #Theorem 1.32 **Satz von Bayes**
> Gegeben: $B_{1},\dots,B_{N}\in\cal{F}$ eine Partition von $\Omega$ mit $\mathbb{P}[B_{n}]>0$ für alle $n$.
> Für jedes Ereignis $A$ mit $\mathbb{P}[A]>0$ und jedes $n\in\{1,\dots,N\}$ gilt
> $\mathbb{P}[B_{n}|A]=\frac{\mathbb{P}[A|B_{n}]\mathbb{P}[B_{n}]}{\sum\limits_{k=1}^{N}\mathbb{P}[A|B_{k}]\mathbb{P}[B_{k}]}$
> - Spezialfall n=2 mit $\Omega=B\cup B^{\complement}$ so ist 
>   $\mathbb{P}[B|A]=\frac{\mathbb{P}[A|B]\mathbb{P}[B]}{\mathbb{P}[A|B]\mathbb{P}[B]+\mathbb{P}[A|B^{\complement}]\mathbb{P}[B^{\complement}]}$

</div></div>



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



>[!info] **Unabhängigkeit zweier Ereignisse**
>(WS #Def 1.35)
>Gegeben: $(\Omega,\cal{F},\mathbb{P})$ ein Wahrscheinlichkeitsraum
>Zwei Ereignisse $A$ und $B$ heissen **(stochastisch)** unabhängig, falls
>$P[A\cap B]=\mathbb{P}[A]\mathbb{P}[B]$
>- Falls $\mathbb{P}[A]\in\{0,1\}$, dann ist $A$ unabhängig von jedem Ereignis
>- Falls Ereignis von sich selbst unabhängig ist, dann muss $\mathbb{P}[A]\in\{0,1\}$ gelten. ( #disclaimerN (falls richtig) $A$ von sich selbst unabhängig $\iff \mathbb{P}[A]\in\{0,1\}$)
>- $A$ ist unabhängig von $B\iff A$ unabhängig von $B^{\complement}$

</div></div>



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



>[!info] (WS #Proposition 1.37)
>Gegeben: $A,B\in\cal{F}$ zwei Ereignisse mit $\mathbb{P}[A],\mathbb{P}[B]>0$
>Dann sind folgende Aussagen äquivalent:
>- (i) $\mathbb{P}[A\cap B]=\mathbb{P}[A]\mathbb{P}[B]$ d.h. $A$ und $B$ sind unabhängig
>- (ii) $\mathbb{P}[A|B]=\mathbb{P}[A]$ d.h. Eintreten von $B$ hat keinen Einfluss auf $A$
>- (iii) $\mathbb{P}[B|A]=\mathbb{P}[B]$ d.h. Eintreten von $A$ hat keinen Einfluss auf $B$

</div></div>



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



>[!info] **Unabhängigkeit** (WS #Def 1.40)
>Gegeben: $I$ eine beliebige Indexmenge
>Eine Familie von Ereignissen $()A_{i})_{i\in I}$ heisst **(stochastisch) unabhängig**, wenn für alle endlichen Teilmengen $J\subset I$ gilt: $\mathbb{P}\left[\bigcap\limits_{j\in J}A_{j}\right]=\prod\limits_{j\in J}\mathbb{P}[A_{j}]$
>- falls Menge unabhängig $\implies$ Ereignisse paarweise unabhängig (Umkehrung gilt nicht!)

</div></div>



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



>[!info] **Zufallsvariable** (WS #Def 2.1) 
>Gegeben: Wahrscheinlichkeitsraum $(\Omega,\cal{F},\mathbb{P})$
>Eine **(reellwertige) Zufallsvariable (Z.V.)** ist eine Abbildung $X:\Omega\to \mathbb{R}$, sodass für alle $x\in\mathbb{R}$ gilt, 
>$\{\omega \in\Omega|X(\omega)\leq x\}\in\cal{F}$

</div></div>
