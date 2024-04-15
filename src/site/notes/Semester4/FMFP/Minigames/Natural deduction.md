---
{"dg-publish":true,"permalink":"/semester4/fmfp/minigames/natural-deduction/"}
---

## Natural Deduction
>[!info]- Abstract example of a formal proof
> ![Pasted image 20240223151558.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240223151558.png)

- **rules** are used to construct derivations under assumptions
- **proof** is a derivation whose root has no assumptions (at the root on the left there is nothing)
- **derivations** are trees (normally done from bottom to top) ![proof_example.png](/img/user/Semester4/FMFP/Lectures/attachments/proof_example.png)
### Propositional logic
#### Syntax![Pasted image 20240223151900.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240223151900.png)
- Is a **bird a formula**? No, bc. it's about the smallest set (inductive definition), so there is not other stuff there!
#### Semantics
- **valuation** $\sigma:\cal{V}\to\{\text{True,False}\}$ is a function mapping variables to truth values (truth assignment).
	- valuations are simple kinds of models (interpretations)
	- Let **Valuations** be the set of valuations.
- **Satisfiability**: ![Pasted image 20240223152359.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240223152359.png)
- Note that $\sigma\not\models\bot$ for every $\sigma\in$ Valuations: meaning falsity is never satisfied (as it should bebn )
- a formula $A\in\cal{L}_{P}$ is **satisfiable** if $\sigma\models A$, for some valuation $\sigma$
	- **valid** (a tautology) if it holds for all valuations $\sigma$
- **semantic entailment**: $A_{1},..A_{n}\models A$ if for all $\sigma$, if $\sigma\models A_{1},\dots,\sigma\models A_{n}$ then $\sigma\models A$
#### requirements for deductive system
- syntactic entailment $\vdash$ (derivation rules) semantic entailment $\models$ (truth tables) should agree
- For $\Gamma \equiv A_{1},\dots,A_{n}$ some collection of formulae for which holds:
	- **soundness**: If $\Gamma\vdash A$ can be derived, then $\Gamma\models A$
	- **completeness**: If $\Gamma\models A$, then $\Gamma\vdash A$ can be derived
- (desirable, but not necessary) **Decidability**: What is complexity of determining:
	- If a proposition $A$ is satisfied by a valuation $\sigma$? => linear
	- If $A$ is satisfiable? => exponential to check all possible evaluation and it's NP-complete
	- If $A$ is a tautology? => it's in Co-NP
#### Natural deduction for propositional formulae ![Pasted image 20240305161646.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240305161646.png)
#### derivation rules![Pasted image 20240223162856.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240223162856.png)
### First-Order Logic
#### Syntax
- **signature** consists of a set of function symbols $\cal{F}$ and a set of predicate symbols $\cal{P}$ (and their arities e.g. $f^{k}$ to indicate function/predicate symbol $f$ has arity $k\in\mathbb{N}$)
	- constants are $0-ary$ function symbols
- Let $\cal{V}$ be a set of variables
- **Term**, the terms of first-order logic, is the smallest set where 
1. $x\in\text{Term}$ if $x\in\cal{V}$ and 
2. $f^{n}(t_{1},\dots,t_{n})\in \text{Term}$ if $f^{n}\in\cal{F}$ and $t_{i}\in\text{Term}$ for all $1\leq i\leq n$
- **Form**, the formulae of first-order logic, is the smallest set where
1. $\bot\in\text{Form}$
2. $p^{n}(t_{1},\dots,t_{n})\in\text{Form}$ if $p^{n}\in\cal{P}$ and $t_{j}\in\text{Term}$, for all $1\leq j\leq n$
3. $A\circ B\in\text{Form}$ if $A\in\text{Form}$, $B\in\text{Form}$, and $\circ\in\{\land,\lor,\to\}$
4. $Qx.A\in\text{Form}$ if $A\in\text{Form},x\in\cal{V}$ and $Q\in\{\forall,\exists\}$
- bound/free ![Pasted image 20240223164022.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240223164022.png)
	- names of bound variables are irrelevant, they just encode the binding structure
	- **$\alpha$-conversion**: renaming **bound** variables is okay
- **Operators: omitting paranthesis**: 
	- Binary operators:
		- $\land$ stronger than $\lor$ stronger than $\to$
		- associates: $\to$ to the right while $\land$ and $\lor$ do to the left
	- negation stronger than binary
	- quantifiers extend to the right as far as possible i.e. end of line or $)$
#### Semantics
- **structure** is a pair $\cal{S} = \langle U_{\cal{S}},I_{\cal{S}}\rangle$ where $U_{\cal{S}}$ is a nonempty set, the **universe**, and $I_{\cal{S}}$ is a mapping where
	1. $I_{\cal{S}}(p^{n})$ is an $n$-ary relation on $U_{\cal{S}}$, for $p^{n}\in\cal{P}$
	2. $I_{\cal{S}}(f^{n})$ is an $n$-ary (total) function on $U_{\cal{S}}$, for $f^{n}\in\cal{F}$
As shorthand, write $p^\cal{S}$ for $I_{\cal{S}}(p)$ and $f^{\cal{S}}$ for $I_{\cal{S}}(f)$
- an **interpretation** is a pair $\cal{I}=\langle\cal{S},v\rangle$, where $\cal{S}=\langle U_{\cal{S}},I_{\cal{S}}\rangle$ is a structure and $v:\cal{V}\to U_{\cal{S}}$ a valuation.
- The **value** of a term $t$ under the interpretation $\cal{I}=\langle\cal{S},v\rangle$ is written as $\cal{I}(t)$ and defined by
	1. $\cal{I}(x)=v(x)$, for $x\in\cal{V}$ and
	2. $\cal{I}(f(t_{1},\dots,t_{n}))=f^\cal{S}(\cal{I}(t_{1}),\dots,\cal{I}(t_{n}))$ 
- **Satisfiability** ![Pasted image 20240223204428.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240223204428.png)![Pasted image 20240223204513.png](/img/user/Semester4/FMFP/Lectures/attachments/Pasted%20image%2020240223204513.png)
- **Substitution**
	- replace in a formula all occurences of a **free** variable $x$ with some term $t$ e.g. ![Pasted image 20240306160000.png](/img/user/Semester4/FMFP/attachments/Pasted%20image%2020240306160000.png)
	- substitution must avoid capture of variables: if they would have the same name, then we have to first rename  bound variables with $\alpha$-conversion
### Symbols
#### Equality
- logical symbol wi