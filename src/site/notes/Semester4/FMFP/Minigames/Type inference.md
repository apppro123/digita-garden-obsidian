---
{"dg-publish":true,"permalink":"/semester4/fmfp/minigames/type-inference/"}
---

## Formal type inference
### Step-by-step
1. Start with judgement $\vdash t::\tau_{0}$ where $\tau_{0}$ is a fresh type variable
2. Build derivation tree bottom-up by applying rules
3. introduce fresh type variables $\tau_{i}$ and collect constraints if needed
4. Solve constraints using unification to get possible types
- Example for resolving constraints ![Pasted image 20240410153219.png](/img/user/Semester4/FMFP/Minigames/attachments/Pasted%20image%2020240410153219.png)
- Example unification ![Pasted image 20240410153247.png](/img/user/Semester4/FMFP/Minigames/attachments/Pasted%20image%2020240410153247.png)
## Informal type inference
- (see step-by-step from formal type inference but) skip tree building and directly start unifying
## Common mistakes/car
- care for **infix functions** e.g. $1+2=(+)\;1\;2$
- functions are always applied to exactly **one argument** at a time
- be careful when **parsing** $x\;(<)$ not same as $(x\;<)$
- Numeric constants are **polymorphic** in Haskell e.g. ![Pasted image 20240410153709.png](/img/user/Semester4/FMFP/Minigames/attachments/Pasted%20image%2020240410153709.png)
## Examples
- [Exercises with explanations by TA Ramon Wick](https://n.ethz.ch/~rawick/slides/FMFP_Woche_7_Informal_Inference.pdf)