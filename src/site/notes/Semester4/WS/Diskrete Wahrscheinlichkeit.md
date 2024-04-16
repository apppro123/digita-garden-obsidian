---
{"dg-publish":true,"permalink":"/semester4/ws/diskrete-wahrscheinlichkeit/"}
---

Oft ist im Zusammenhang mit Andwendungen aus der Informatik $\Omega=\{\omega_{1},\dots, \omega_{N}\}$ endlich oder $\Omega=\{\omega_{1},\omega_{2},\dots\}$abzählbar. Dann...
- wird $\cal{F}=\mathbb{P}(\Omega)$, d.h. jede Teilmenge von $\Omega$ ist ein (beobachtbares Ereignis), gewählt.
- ist $\mathbb{P}$ definiert durch die Wahrscheinlichkeiten $p_{n}:=\mathbb{P}[\omega_{n}]$, $n=1,\dots,N$ bzw. $n\in\mathbb{N}$, aller Elementarereignisse. Denn für jede beliebe Menge $A\subseteq \Omega$ gilt $A\in\cal{F}$ und 
  $$\mathbb{P}[A]=\mathbb{P}\left[ \bigcup\limits_{\omega_{n}\in A}\{\omega_{n}\} \right]=\sum\limits_{\omega_{n}\in A}\mathbb{P}[\{\omega_{n}\}]=\sum\limits_{\{n|\omega_{n}\in A\}}p_{n}$$
>[!info] #Def 1.14 Laplace Modell
  >Sei $\Omega=\{\omega_{1,\dots,\omega_{n}}\}$ mit $|\Omega|=N$ ein endlicher Grundraum. $(\Omega,\cal{F},\mathbb{P})$ heisst Laplace Modell auf $\Omega$, wenn
  >- $\cal{F}=\cal{P}(\Omega)$
  >- $\mathbb{P}$ ist die diskrete Gleichverteilung auf $\Omega$, d.h. alle Elementarereignisse sind **gleich wahrscheinlich**,$p_{1}=\dots=p_{N}=\frac{1}{N}$. Insbesondere gilt für belibiege $A\subseteq \Omega$, $\mathbb{P}[A]=\frac{|A|}{|\Omega|}$
  
  