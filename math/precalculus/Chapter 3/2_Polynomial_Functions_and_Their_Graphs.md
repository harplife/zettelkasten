# 3.2 Polynomial Functions and Their Graphs

## Key Concepts

- Polynomial Functions
- Graphing Basic Polynomial Functions
- Graphs of Polynomial Functions: End Behavior
- Using Zeroes to Graph Polynomials
- Shape of the Graph Near a Zero
- Local Maxima and Minima of Polynomials


## Polynomial Functions

A <mark class="hltr-trippy">Polynomial Function</mark> of degree $n$ is a function of the form

$$
P(x) = a_{n}x^{n} + a_{n-1}x^{n-1} + \dotsi + a_{1}x + a_{0}
$$

where $n$ is a non-negative integer and $a_{n} \neq 0$.

The number $a_{n}x^n$ is the <mark class="hltr-trippy">Leading Term</mark>.

The numbers $a_{0}, a_{1}, a_{2}, \dots, a_{n}$ are called the <mark class="hltr-trippy">Coefficients</mark> of the polynomial.

The number $a_{n}$ (the coefficient of the highest power) is the <mark class="hltr-trippy">Leading Coefficient</mark>.

The number $a_{0}$ is the <mark class="hltr-trippy">Constant Coefficient</mark> or **Constant Term**.

If a polynomial consists of just a single term, then it is called a **monomial**.


## Graphing Basic Polynomial Functions

The simplest polynomial functions are the monomials $P(x)=x^n$, whose graph has the same general shape as the graph of $y=x^2$ when $n$ is even, and the graph of $y=x^3$ when $n$ is odd.
- The graphs become flatter around the origin and steeper elsewhere as the degree $n$ becomes larger.

> [!important] Splines
> The shapes of splines can be obtained by piercing together parts of polynomials. For example, the graph of a cubic polynomial can be made to fit specified points by adjusting the coefficients of the polynomial. Curves obtained in this way are called **Cubic Splines**.
> In Computer design programs, a curve can be drawn between fixed points, called **Anchor Points**. Moving the anchor points amounts to adjusting the coefficients of a cubic polynomial.


## Graphs of Polynomial Functions: End Behavior

The graph of a polynomial function is always **continuous** - the graph has no break or hole.

Moreover, the graph of a polynomial function is a **smooth curve** - it has no corner or sharp point (cusp).

The <mark class="hltr-trippy">End Behavior</mark> of a polynomial describes what happens to the value of $f(x)$ as $x$ becomes very large (towards $+\infty$) or very small (towards $-\infty$).

For example,
- The graph of $y=x^2$ has left and right ends that go up infinitely
- The graph of $y=x^3$ has left end go down, right end go up infinitely

For a polynomial, the leading term $a_{n}x^n$ always **dominates** the graph for very large or very small $x$. Meaning, the end behavior is determined by the leading term.

The end behavior is described using an **arrow notation**, like so :
- $y \to \infty$ as $x \to \infty$ and $y \to \infty$ as $x \to -\infty$
- $y \to \infty$ as $x \to \infty$ and $y \to -\infty$ as $x \to -\infty$

There are four main cases of end behaviors :

| Degree | Leading Coefficient | End Behavior<br>(as $x \to -\infty$, $x \to \infty$) | Shape                      |
| ------ | ------------------- | ---------------------------------------------------- | -------------------------- |
| Even   | Positive            | Both ends **up**                                     | ($y = x^2$), ($y = x^4$)   |
| Even   | Negative            | Both ends **down**                                   | ($y = -x^2$), ($y = -x^4$) |
| Odd    | Positive            | Left end **down**, right end **up**                  | ($y = x^3$), ($y = x^5$)   |
| Odd    | Negative            | Left end **up**, right end **down**                  | ($y = -x^3$), ($y = -x^5$) |


## Using Zeroes to Graph Polynomials

A <mark class="hltr-trippy">Real Zero</mark> of a polynomial $f(x)$ is any real number $x=r$ that makes the polynomial equal to zero :

$f(r)=0$

In other words, if $x=r$ is plugged into the polynomial as input and the output is $0$, then $r$ is a **real zero**.

> [!important] Polynomials can have *real* zeroes or *complex* (nonreal) zeroes.
> Every polynomial of degree $n$ has exactly $n$ total zeroes, but *not* all are real.

> [!tip] Connection to Calculus
> In calculus, the concept of a "zero" extends to studying where a function crosses the x-axis, where it has critical points, and where the rate of change (derivative) is zero. But in precalculus, zeros mainly help you graph functions and solve equations.


---
To find the real zeroes, all it takes is to set $f(x)=0$.

For example, let
$$
f(x)=x^2-5x+6
$$

To find the real zeros, set
$$
x^2-5x+6=0
$$

Factor to get
$$
(x-2)(x-3)=0
$$

And then solving for $x$ gives $x=2$ and $x=3$, which are the real zeroes.

> [!important] Each real zero corresponds to an x-intercept on the graph of $f(x)$.
> That means : $$f(x)=0 \quad \implies \quad \text{the point }(r,0)$$

> [!important] Intermediate Value Theorem for Polynomials
> If $P$ is a polynomial function and $P(a)$ and $P(b)$ have opposite signs, then there exists at least one value $c$ between $a$ and $b$ for which $P(c)=0$.
> ![[Pasted image 20251024152100.png | center | 400]]

## Shape of the Graph Near a Zero

If a factor (e.g. $(x-1)$) appears more than once, that zero has <mark class="hltr-trippy">Multiplicity</mark> greater than $1$. This affects the shape of the graph at that point.

> [!important] In general, if $r$ is a zero of polynomial $P$ and the corresponding factor $x-r$ occurs exactly $m$ times in the factorization of $P$, then we say that $r$ is a **zero of multiplicity** $m$.

| Factor      | Zero | Multiplicity | Graph Behavior                |
| ----------- | ---- | ------------ | ----------------------------- |
| $(x - r)$   | $r$  | 1            | Crosses the x-axis            |
| $(x - r)^2$ | $r$  | 2            | Touches and turns around      |
| $(x - r)^3$ | $r$  | 3            | Flattens slightly and crosses |

It's a good rule of thumb to remember that :
- Even multiplicity means the graph touches the x-axis (and turns around)
- Odd multiplicity means the graph crosses the x-axis

> [!warning] The multiplicity refers to the power the factor is raised to.
> Do not confuse with the number of factors.

> [!example] The graph of $P(x)=x^3-2x^2-4x+8$
> ![[Pasted image 20251024153058.png | center | 400]]
> When the function is factored, the result is $=(x+2)(x-2)^2$. Thus, the real zeros are $x=-2$ and $x=2$.
> In the graph we can see that the graph simply crosses at $x=-2$ because it has multiplicity of $1$, whereas the graph touches and turns around at $x=2$ because its multiplicity is $2$.


## Local Maxima and Minima of Polynomials

> [!note] $\exists$ means "there exists".
> For example, $\exists h>0$ means "there exists a positive number $h$".

$f(a)$ is a <mark class="hltr-trippy">Local Maxima</mark> if $\exists h>0$ such that $f(a)\geq f(x)$ for all $x \in (a-h,a+h)$.
- In other words, a function $f(x)$ has a **local maximum** at $x=a$ if there exists some $h>0$ such that $f(a)\geq f(x)$ for all $x$ in interval $(a-h,a+h)$.

> [!important] The importance of the phrase "there exists $h>0$" in the definition
> The definition does *not* require that the inequality be true *for* all possible $h$. It needs at least one such $h$ for which it works. This is the essence of "local".

$f(a)$ is a <mark class="hltr-trippy">Local Minima</mark> if $\exists h>0$ such that $f(a)\leq f(x)$ for all $x \in (a-h,a+h)$.
- In other words, a function $f(x)$ has a **local minimum** at $x=a$ if there exists some $h>0$ such that $f(a)\leq f(x)$ for all $x$ in interval $(a-h,a+h)$.


$f(x)=x^3-3x^2+2$