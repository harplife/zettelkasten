# 2.6 Continuity

## Continuity at a Point (In General)

Informally : A function $f$ is **continuous** at $a$ if the graph of $f$ does not have a *hole* or *break* at $a$. In other words, the graph near $a$ can be drawn without lifting the pencil from the paper.

---
Def : Continuity at a Point

A function $f$ is **continuous** at $a$ if $f(a)=\lim\limits_{ x \to a } f(x)$.

If $f$ is *not* continuous at $a$, then $a$ is a **point of discontinuity**.


### Continuity Checklist

In order for $f$ to be continuous at $a$, the following **three conditions** must hold :

1. $f(a)$ is defined ($a$ is in the domain of $f$).
2. $\lim\limits_{ x \to a } f(x)$ exists (it is a number).
3. $f(a)=\lim\limits_{ x \to a } f(x)$ (the value of $f$ equals the limit of $f$ at $a$).

If any of the above fail, then $f$ is not continuous at $a$.

---
From the checklist, we have the following consequence :

If $f$ is continuous at $a$, then $\lim\limits_{ x \to a } f(x)=f(a)$ and **direct substitution** may be used to evaluate $\lim\limits_{ x \to a } f(x)$. In other words, solve for $f(a)$ to get the limit.

---
#example Is the function $f(x)=$

---
#example Is the function $f(x)=\sqrt{ x-3 }$ continuous at $a=2$ ?

$f(2)=\sqrt{ x-3 }=\sqrt{ -1 }$ --> Undefined.

It fails the first condition, so it is not continuous.







## Precise Definition (Epsilon-Delta Def)


$$\lim\limits_{x \to c} f(x)=L \iff \forall \epsilon > 0, \exists \delta > 0 \text{ s.t. } 0 < |x-c| < \delta \implies |f(x)-L|<\epsilon$$

Interpretation :

"**For every** error margin (ϵ > 0), **there exists** a window on the x-axis (δ > 0), **such that** **if** the distance between x and c is within the window (but not exactly c), **then** the distance between the function and the limit is smaller than the error margin".