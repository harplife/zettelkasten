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
#example Is the following function continuous at $a=3$ ?

$$
f(x)= \begin{cases}
\frac{x^2-4x+3}{x-3}, &x \neq 3 \\
2, &x=3
\end{cases}
$$
1) Prove that $f(a)$ is defined.

$f(3)=2$ --> defined.

2) Prove that $\lim\limits_{x \to a} f(x)$ exists.

First, we determine what $\lim\limits_{x \to a} f(x)$ is, and then simplify :
$$
\begin{align}
  \lim\limits_{x \to 3} f(x) &= \frac{x^2-4x+3}{x-3} \\
  &= \frac{(x-3)(x-1)}{x-3} \\
  &= x-1
\end{align}
$$

Second, we find the limit : $\lim\limits_{x \to 3} f(x) = 3-1 = 2$ --> exists

3) Prove that $f(a) = \lim\limits_{x \to a} f(x)$ .

$f(3)=\lim\limits_{x \to 3} f(x)=2$

All three conditions are met. Therefore, the $f$ is continuous at $a=3$.

---
#example Is the following function continuous at $a=2$ ?

$$
f(x)=\sqrt{ x-3 }
$$
1)
$f(2)=\sqrt{ x-3 }=\sqrt{ -1 }$ --> Undefined.

It fails the first condition, so it is not continuous.


## Continuity of Composite Functions at a Point

#theorem Limits of Composite Functions

1. If $g$ is continuous at $a$ and $f$ is continuous at $g(a)$, then $f(g(x))$ is continuous at $a$ and $\lim\limits_{x \to a} f(g(x))=f(\lim\limits_{x \to a} g(x))$ .
2. If $\lim\limits_{x \to a} g(x) = L$ and $f$ is continuous at $L$, then $\lim\limits_{x \to a} f(g(x))=f(L)$ .

> [!important] This is a preview of **Chain Rule**, which we'll learn later on.

---
#example Evaluate the following function, and justify the answer : $$\lim\limits_{x \to \infty} \left( \frac{2x+1}{x} \right)^3$$

Using the Limits of Composite Functions Theorem, we can identify $f(x)$ and $g(x)$ as :

$$
\begin{align}
  f(x) &= x^3 \\
  g(x) &= \frac{2x+1}{x}
\end{align}
$$

We first find the limit of $g(x)$ as $x \to \infty$ :

$$
\lim\limits_{x \to \infty} \left( \frac{2x+1}{x} \right)
= \lim\limits_{x \to \infty} \frac{\left( 2+\frac{1}{x} \right)}{1}
\to \frac{2+0}{1} = 2
$$

Then we find the limit of $f(g(x))$ as $x \to \infty$ :

$$
\lim\limits_{x \to \infty} \left( \frac{2x+1}{x} \right)^3 \to 2^3 = 8
$$

---
#example Evaluate the following function, and justify the answer : $$\lim\limits_{x \to 4} \tan \left( \frac{x-4}{\sqrt{ x }-2} \right)$$

Using the Limits of Composite Functions Theorem, we can identify $f(x)$ and $g(x)$ as :

$$
\begin{align}
  f(x) &= \tan x \\
  g(x) &= \frac{x-4}{\sqrt{ x }-2}
\end{align}
$$

We first find the limit of $g(x)$ as $x \to 4$ :

$$
\begin{align}
  \lim\limits_{x \to 4} \frac{x-4}{\sqrt{ x }-2} &= \lim\limits_{x \to 4} \frac{(x-4)(\sqrt{ x }+2)}{(\sqrt{ x }-2)(\sqrt{ x }+2)} \\
  &= \lim\limits_{x \to 4} \frac{(x-4)(\sqrt{ x }+2)}{x-4} \\
  &= \lim\limits_{x \to 4} \sqrt{ x }+2 \\
  &\to \sqrt{ 4 } + 2 = 4
\end{align}
$$

Then we find the limit of $f(g(x))$ as $x \to 4$ :

$$
\lim\limits_{x \to 4} \tan \left( \frac{x-4}{\sqrt{ x }-2} \right) \to \tan 4 \approx 1.158
$$


## Continuity on an Interval

Informally : A function is **continuous** on an interval $I$ if it is continuous at **every** point in that interval.

We can look at a graph and easily determine if the graph is continuous at a given interval.

#example By looking at a graph, if we see that there are no holes or break in between $[-3,2]$, then we can say that $f$ is continuous on $[-3,2]$.


### Continuity at Endpoints

Def : Continuity at Endpoints

1. A function is **right** continuous at $a$ if $\lim\limits_{x \to a^{+}} f(x)=f(a)$ .
2. A function is left continuous at $a$ if $\lim\limits_{x \to a^{-}} f(x) = f(a)$ .

---
#example If we see a graph of a curve that goes from $-3$ (filled dot) and $2$ (empty dot), then we can say $f$ is **right** continuous at $-3$. Additionally, we can say $f$ is continuous at $[-3,2)$.


## The Intermediate Value Theorem

Theorem : The Intermediate Value Theorem

Suppose $f$ is continuous on the interval $[a,b]$ and $L$ is a number strictly between $f(a)$ and $f(b)$. Then, there exists at least one number $c$ in $(a, b)$ satisfying $f(c)=L$.




## Precise Definition (Epsilon-Delta Def)


$$\lim\limits_{x \to c} f(x)=L \iff \forall \epsilon > 0, \exists \delta > 0 \text{ s.t. } 0 < |x-c| < \delta \implies |f(x)-L|<\epsilon$$

Interpretation :

"**For every** error margin (ϵ > 0), **there exists** a window on the x-axis (δ > 0), **such that** **if** the distance between x and c is within the window (but not exactly c), **then** the distance between the function and the limit is smaller than the error margin".