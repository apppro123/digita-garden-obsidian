---
{"dg-publish":true,"permalink":"/semester4/ws/wahrscheinlichkeit/normalverteilung/"}
---


> [!info] #Example 3.46 **Normalverteilung** !
> Eine stetige Zufallsvariable $X$ heisst **normalverteilt mit Parametern $\mu\in\mathbb{R}$ und $\sigma^{2}>0$**, wir schreiben $X\sim\cal{N}(\mu,\sigma^{2})$, falls ihre Dichte gegeben ist durch (3.5)
> $$f_{X}(x)=\frac{1}{\sigma \sqrt{ 2\pi }}e^{-\frac{1}{2}(\frac{x-\mu}{\sigma})^{2}}$$
> ![Pasted image 20240415215918.png](/img/user/Semester4/WS/Wahrscheinlichkeit/attachments/Pasted%20image%2020240415215918.png)
> - #disclaimer 3.47 Die Funktion in Gleichung (3.5) hat u.a. folgende Bezeichnung: Gauss-Funktion, gausssche Normalverteilung, gausssche Verteilungsfunktion, Gauss-Kurve, (gausssche) Glockenkurve, Gauss-Glocke
> - #disclaimer 3.48 Ein wichtiger Spezialfall ist die **Standardnormalverteilung** mit $\mu=0$ und $\sigma^{2}=1$ also $\cal{N}(0,1)$.
>   Die zugehörige Dichte wird meistens mit $\varphi$ und die Verteilungsfunktion mit $\phi$ bezeichnet. Die dazugehörige Variable nennen wir meistens $Z$
>   Weder für $F_{X}$ noch für $\phi$ gibt es einen geschlossenen Ausdruck, aber das Integral 
>   $$\phi(x)=\int\limits_{-\infty}^{x} \varphi(t)\, dt=\frac{1}{\sqrt{ 2\pi }}\int\limits_{-\infty}^{x} e^{-\frac{t^{2}}{2}} \, dt$$
>   ist tabelliert (siehe Appendix => Standardnormalverteilung)
> - Eigenschaften ( #source TA Yanik Yanik Künzi) 
> 	- pdf ist symmetrisch mit Symmetrieachse $x=\mu$
> 	- für cdf gibt es keinen geschlossenen Ausdruck => braucht Tabellen
> 	- beliebige normalverteilte ZV können auf die Standardnormalverteilung zurückgeführt werden
> 	- 68-95-99-Regel ![Pasted image 20240430190309.png](/img/user/Semester4/WS/Wahrscheinlichkeit/attachments/Pasted%20image%2020240430190309.png)

Es genügt die Werte von $\phi$ zu tabellieren
>[!info] #Proposition 3.49 **Standardnormalverteilung**
>Für $X\sim\cal{N}(\mu,\sigma^{2})$ gilt $\frac{X-\mu}{\sigma}\sim\cal{N}(0,1)$, also
>$$F_{X}(x)=\mathbb{P}[X\leq x]=\mathbb{P}[\frac{X-\mu}{\sigma}\leq\frac{x-\mu}{\sigma}]=\phi(\frac{x-\mu}{\sigma})$$
> - #disclaimer 3.50 
>  Gegeben: unabhängige normalverteilte Zufallsvariablen $X_{1},\dots,X_{n}$ mit Parametern $(\mu_{1},\sigma_{1}^{2}),\dots,(\mu_{n},\sigma_{n}^{2})$. Dann gilt
>  $$Z:=\mu_{0}+\sum\limits_{k=1}^{n}a_{k}X_{k}\sim\cal{N}\left( \mu_{0}+\sum\limits_{k=1}^{n} a_{k}\mu_{k},\sum\limits_{k=1}^{n}a_{k}^{2}\sigma_{k}^{2}\right)$$
>  - #disclaimer 3.51 Aus Proposition 3.49 lesen wir direkt ab, dass für $\mu\in\mathbb{R},\sigma^{2}>0$ und $Z\sim\cal{N}(0,1)$ gilt
>    $$\mu+\sigma Z\sim \cal{N}(\mu,\sigma^{2})$$
>    D.h. wenn wir z.B. $X\sim\cal{N}(\mu,\sigma^{2})$ auf dem Computer simulieren wollen, reicht es ein $Z\sim\cal{N}(0,1)$ zu simulieren und die erhaltenen Werte mit $\sigma$ zu multiplizieren und $\mu$ zu addieren.
>  - #disclaimer 3.52 Für $X\sim\cal{N}(\mu,\sigma^{2})$ liegt der "Grossteil" des Wahrscheinlichkeitsmasses im Intervall $[\mu-3\sigma,\mu+3\sigma]$. Genauer gilt $\mathbb{P}[|X-\mu|\geq 3\sigma]\leq 0.0027$
>    ![Pasted image 20240415221940.png](/img/user/Semester4/WS/Wahrscheinlichkeit/attachments/Pasted%20image%2020240415221940.png)

>[!info] Transformation zur Standardnormalverteilung
> Gegeben: $X\sim\cal{N}(\mu,\sigma^{2})$ und $Y=\alpha+\beta X$ dann gilt $Y\sim\cal{N}(\mu+\alpha,\beta^{2}\sigma^{2})$. Dann ist die standardnormalverteilte ZV $Z:=\frac{x-\mu}{\sigma}\sim\cal{N}(0,1)$
> - Intuition ![Pasted image 20240430191242.png](/img/user/Semester4/WS/Wahrscheinlichkeit/attachments/Pasted%20image%2020240430191242.png)