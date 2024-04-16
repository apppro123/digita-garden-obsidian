---
{"dg-publish":true,"permalink":"/semester4/ws/appendix/"}
---

## Kombinatorik
- Permutationen: $n! =  n*(n-1)*\dots*2*1$
	- Frage: Auf wie viele Arten kann man n Objekte anordnen?
	- Herleitung: erste Objekt aus $n$ Objekten wählen, zweite aus $n-1$ usw.
- Kombinationen $\pmatrix{n\\k}=\frac{n!}{k!(n-k)!}$
	- Frage: Auf wie viele Arten kann man $k\leq n$ aus den $n$ Objekten ohne Zurücklegen auswählen.
	- Herleitung: 
		- erste Objekt aus $n$, zweite aus $n-1$ wählen usw. d.h. $n*(n-1)*\dots*(n-k+1)=\frac{n!}{(n-k)!}$ Sequenzen der Länge $k$
		- aber wir interessieren uns nicht für die Reihenfolge und teilen dadurch durch die möglichen Permuationen d.h. durch $k!$ (siehe Permutationen)
- Variationen: $n^{m}$
	- Frage: Wie viele Sequenzen der Länge $m$ kann man mit den $n$ Elementen bilden?
	- Herleitung: Für jeden der $m$ Plätze sind jeweils $n$ Elemente zur Auswahl.
### Example
- ![Pasted image 20240311072045.png](/img/user/Semester4/WS/attachments/Pasted%20image%2020240311072045.png)