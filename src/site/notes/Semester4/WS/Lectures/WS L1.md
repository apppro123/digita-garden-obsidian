---
{"dg-publish":true,"permalink":"/semester4/ws/lectures/ws-l1/"}
---

## Definitions
>[!info] #Def 1.2 **Grundraum** ( #aka Ereignisraum) ( #english sample space)
>$\Omega \ne\varnothing$ ist die Menge alle möglichen Ergebnisse des betrachteten Zufallsexperiments.
>- Die Elemente $w\in\Omega$ heissen **Elementarereigniss** #aka Ausgänge des Experiments #english outcomes
>- Wir sagen, dass ein Ereignis $A$ eintritt, falls das realisierte Elementarereignis $\omega$ in $A$ liegt d.h. $\omega\in A$


>[!info] #Def 1.4 Die **Potenzmenge** ( #english power set) 
>von $\Omega$, $\cal{P}(\Omega)$ oder $2^{\Omega}$, ist die Menge aller Teilmengen von $\Omega$.
>- Ein **prinzipielles Ereignis** ( #english event) ist eine Teilmenge $\cal{A}\subseteq \Omega$, also eine Kollektion von Elementarereignissen
>- Die Klasse aller **(beobachtbaren) Ereignisse** bezeichnen wir mit $\cal{F}$. Das ist eine Teilmenge der Potenzmenge von $\Omega$
>	- Falls $\Omega$ endlich oder abzählbar, dann ist oft $\cal{F}=\cal{P}(\Omega)$, und das ist ein diskreter Wahrscheinlichkeitsraum.
>	- Falls $\Omega$ überabzählbar, muss $\cal{F}$ eine echte Teilklasse von $\cal{P}(\Omega)$ sein
>	- In jedem Fall muss $\cal{F}$ gewisse Axiome erfüllen 

>[!Info] #Def 1.5 $\sigma$-Algebra (manchmal $\sigma$-field)
>Ein Mengensystem $\cal{F}\subseteq\cal{P}(\Omega)$ nennt man eine **$\sigma$-Algebra**, wenn
>1. $\Omega\in\cal{F}$
>2. für jedes $A\in\cal{F}$ auch das Komplement $A^{\complement}\in\cal{F}$ ist
>3. für jede Folge $(A_{n})_{n\in\mathbb{N}}$ mit $A_{n}\in\cal{F},n\in\mathbb{N}$, auch die Vereinigung $\cup_{n\in\mathbb{N}}A_{n}\in\cal{F}$ ist

>[!info] #Def 1.9 Wahrscheinlichkeitsmass ( #english probability measure)
>Sei $\Omega$ ein Grundraum und sei $\cal{F}$ eine $\sigma$-Algebra. Eine Abbildung 
>$$\mathbb{P}:\cal{F}\to[0,1],\text{mit }A\mapsto\mathbb{P}[A]$$
>heisst Wahrscheinlichkeitsmass auf $(\Omega,\cal{F})$, wenn die folgenden Axiome erfüllt sind
>1. Normiertheit: $\mathbb{P}[\Omega]=1$
>2. $\sigma$-Additivität: $\mathbb{P}[\cup_{n\in\mathbb{N}}A_{n}]=\sum\limits_{n=1}^{\infty}\mathbb{P}[A_{n}]$ für paarweis disjunkte Mengen $A_{n}$, d.h. $A_{n}\cap A_{m}=\varnothing$ für alle $n\ne m$

>[!info] #Proposition 1.10 
>Für ein Wahrscheinlichkeitsmass $\mathbb{P}$ auf $(\Omega,\cal{F})$ und Mengen $A,B\in\cal{F}$ gelten folgende Aussagen:
>- $\mathbb{P}[A^{\complement}]=1-\mathbb{P}[A]$, und insbesondere $\mathbb{P}[\varnothing]=0$
>- Monotonie: wenn $A\subseteq B$, dann $\mathbb{P}[A]\leq \mathbb{P}[B]$
>- Additionsregel: $\mathbb{P}[A]+\mathbb{P}[B]=\mathbb{P}[A\cup B]+\mathbb{P}[A\cap B]$

>[!info] #Def 1.12 Wahrscheinlichkeitsraum
>Sei $\Omega$ ein Grundraum, $\cal{F}$ eine $\sigma$-Algebra und $\mathbb{P}$ ein Wahrscheinlichkeitsmass auf $(\Omega,\cal{F})$. Das Tripel $(\Omega,\cal{F},\mathbb{P})$ heisst  Wahrscheinlichkeitsmass ( #english probability space)

>[!info] #disclaimer 1.13 Messbarer Raum ( #english measurable space)
>Allgemein verwenden wir in der Masstheorie folgende Terminologie:
>- Für eine $\sigma$-Algebra $\cal{A}$ auf einer Grundmenge $\Omega$ wird das Paar $(\Omega,\cal{A})$ ein messbarer Raum genannt.
>- Elemente $A\in\cal{A}$, also Teilmengen $A\subset \Omega$, die wir messen wollen, heissen messbare Mengen ( #english measurable sets).
>- Auf messbaren Räumen (bzw. den $\sigma$-Algebren) lassen sich Masse ( #english measures) $\mu$ definieren. Diese sind im Allgemeinen nicht auf $1$ nomiert. Man verlangt staddessen $\mu(\varnothing)=0$.
>- Das Tripel $(\Omega,\cal{A},\mu) $ heisst Massraum ( #english measure space).
>- Ist das Mass normiert, $\mu(\Omega)=1$, dann ist das Mass ein Wahrscheinlichkeitsmass und der Messraum wird zum Wahrscheinlichkeitsraum.

[[Semester4/WS/Diskrete Wahrscheinlichkeit\|Diskrete Wahrscheinlichkeit]]