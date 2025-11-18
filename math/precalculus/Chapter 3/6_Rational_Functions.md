# 3.6 Rational Functions

## Key Concepts

- The Rational Function $f(x)=\frac{1}{x}$
- Vertical and Horizontal Asymptotes
- Finding Vertical and Horizontal Asymptotes of Rational Functions
- Graphing Rational Functions
- Common Factors in Numerator and Denominator
- Slant Asymptotes and End Behavior
- Applications


## The Rational Function $f(x)=\frac{1}{x}$

A <mark class="hltr-trippy">Rational Function</mark> is any function that can be written as the ratio of two polynomials :

$f(x)=\frac{P(x)}{Q(x)}$

where $P(x)$ and $Q(x)$ are polynomials, and $Q(x) \neq 0$ .

> [!example] $f(x)=\frac{x^2-1}{x-2}$ is a rational function.

Just like how $f(x)=x^2$ is the base for quadratics, $f(x)=\frac{1}{x}$ acts as the base for reciprocal functions of the form :

$$
g(x)=\frac{a}{x-h}+k
$$

where :
- $h$ causes the horizontal shift
- $k$ causes the vertical shift
- $a$ causes the stretch or flip

> [!warning] This applies only to any function of degree $1$ over degree $1$.

The graph of a function $f(x)=\frac{1}{x}$ looks like this :

![[Pasted image 20251030212623.png | center | 400]]

As it can be seen from the graph, $f(x)=\frac{1}{x}$ has these properties :
- $f(x)$ approaches positive infinity as $x$ approaches $0$, if $x > 0$
- $f(x)$ approaches $0$ as $x$ approaches positive infinity
- $f(x)$ approaches negative infinity as $x$ approaches $0$, if $x < 0$
- $f(x)$ approaches $0$ as $x$ approaches negative infinity

> [!example] $g(x)=\frac{2}{x-3}+1$
> This function can be described with transformations from the base $f(x)=\frac{1}{x}$ :
> - Shift right $3$
> - Shift up $1$
> - Stretch by a factor of $2$


## Vertical and Horizontal Asymptotes

An <mark class="hltr-trippy">Asymptote</mark> is a line that a graph approaches but never actually touches (or only touches once, in special cases).

It describes the behavior of a function when :
- $x$ gets very large (positive or negative), or
- $x$ gets close to a value that makes the function "blow up" (like dividing by zero)

There are three types of asymptotes :
- Vertical Asymptotes
- Horizontal Asymptotes
- Oblique (Slant) Asymptotes

A <mark class="hltr-trippy">Vertical Asymptote</mark> is a vertical line $x=a$ where the function value $y$ approaches $\pm \infty$ as $x$ approaches $a$ from the left or right.

![[Pasted image 20251031125051.png]]

A <mark class="hltr-trippy">Horizontal Asymptote</mark> is a horizontal line $y=b$ where the function input $x$ approaches $\pm \infty$ as the function value $y$ approaches $b$.

![[Pasted image 20251031125102.png]]


## Finding Vertical and Horizontal Asymptotes of Rational Functions

### Finding Vertical Asymptotes

Let a rational function be

$$
R(x)=\frac{P(x)}{Q(x)}
$$

where $P(x)$ and $Q(x)$ are polynomials and $Q(x) \ne 0$.

Finding vertical asymptotes requires three steps :
1. Identify the zeros of the denominator
2. Cancel any common factors between $P(x)$ and $Q(x)$
3. Find remaining the zeros of $Q(x)$

> [!example] Vertical asymptote(s) of $R(x)=\frac{x+1}{x-2}$
> For the denominator $Q(x)=x-2$, the zero of $Q(x)$ is $2$. There are no common factors, so the vertical asymptote is at $x=2$.


### Finding Horizontal Asymptotes

Let a rational function be

$$
R(x)=\frac{P(x)}{Q(x)}=\frac{a_{n}x^n+\cdots}{b_{m}x^m+\cdots}
$$

where :
- $P(x)$ is a numerator polynomial of degree $n$
- $Q(x)$ is a denominator polynomial of degree $m$
- $a_{n}$ and $b_{m}$ are the leading coefficients

Finding the horizontal asymptote requires comparing the degrees of the numerator and the denominator. There are three possible results :

| Relationship between degrees (n) and (m) | Horizontal Asymptote                                                                                        |
| ---------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| $n < m$ (degree of numerator smaller)    | $y = 0$                                                                                                     |
| $n = m$ (degrees are equal)              | $y = \dfrac{a_n}{b_m}$ (ratio of leading coefficients)                                                      |
| $n > m$ (degree of numerator larger)     | **No horizontal asymptote** (function grows without bound); sometimes a **slant/oblique asymptote** instead |

> [!example] Horizontal asymptote of $R(x)=\dfrac{2x^2+3x+1}{x^2+5x+4}$
> The horizontal asymptote is $y=\dfrac{2x^2}{x^2}=2$.


### Extra : Behavior near Vertical Asymptotes

Given a rational function :

$f(x)=\frac{P(x)}{Q(x)}$

Its written so that $f(x)$ is in fully factored form (if possible) :

$$
f(x)=\frac{k(x-r_{1})^{p_{1}}(x-r_{2})^{p_{2}}\dots}{(x-a_{1})^{q_{1}}(x-a_{2})^{q_{2}}\dots}
$$

Each factor $(x-a_{i})$ in the denominator can produce a vertical asymptote at $x=a_{i}$ .

The behavior of $f(x)$ as $x \to a^{+}$ and $x \to a^{-}$ is determined by :
- The sign of $f(x)$ when a number greater or less than $a_{i}$ (say $x=a+\epsilon$)
- The multiplicity of the factor (even or odd)

---
When checking for the sign of $f(a+\epsilon)$, there is no need to compute the actual value. Instead, plug in the value into the factored form only to check the resulting sign of each factor.

For example, given $f(x)=\frac{1}{(x-1)(x-2)(x-3)}$, the vertical asymptotes are $x=1,2,3$. We first check the sign around the vertical asymptote $x=1$ by letting $x=1.1$ and $x=0.9$. We can see that the sign of each factor when $x=1.1$ is $+,-,-$, which overall is $+$ (positive). When we check $x=0.9$, the signs are $-,-,-$, which overall is $-$ (negative). This means that the $f(x)$ approaches $-\infty$ on the left side of $x=1$, and $\infty$ on the right side.

---
The multiplicity of the factor determines whether the signs of the $\infty$ on the left and right side of a vertical asymptote are the same or the opposite of each other. Given a factor $(x-a)^q$ :
- If $q$ is **odd**, the signs are opposite of each other
- if $q$ is **even**, the signs are the same

For example, given $f(x)=\frac{1}{(x-1)^2(x-2)}$, the vertical asymptotes are $x=1$ and $x=2$ . When we first check the behavior near $x=1$, we see that when $x=0.9$, the sign is negative, which means $f(x)$ reaches $-\infty$ on the left side of $x=1$ . Because the multiplicity is even, we can assume that $f(x)$ reaches $-\infty$ as well on the right side (which can be confirmed by plugging in $x=1.1$).

---
Behavior near vertical asymptotes can be notated like below.

Given $f(x)=\frac{1}{x-2}$, the behavior of $f(x)$ near the the vertical asymptote is $x=2$ is :

$$
\begin{cases}
  x \to 2^{-} \implies f(x) \to -\infty \\
  x \to 2^{+} \implies f(x) \to +\infty
\end{cases}
$$


## Graphing Rational Functions

Skip


## Slant Asymptotes and End Behavior

A <mark class="hltr-trippy">Slant Asymptote</mark> (aka **Oblique Asymptote**) is a diagonal line that a rational function's graph approaches as $x \to \infty$ or $x \to -\infty$, which occurs when the numerator's degree is exactly one higher than the denominator's degree.

The reason why slant asymptotes occur when the numerator's degree is higher by one, is because the function behaves almost like a linear function once the polynomial division is applied.

$$
\frac{P(x)}{Q(x)} = \text{quotient} + \frac{\text{remainder}}{Q(x)}
$$

The quotient will be a line (of the form $y=mx+b$), and the remainder term will approach $0$ as $x$ approaches positive or negative infinity. That line $y=mx+b$ is the slant asymptote.

For example :

$$
f(x) = \frac{x^2+1}{x+1} = (x-1)+\frac{2}{x+1}
$$

As $x \to \infty$ , the remainder $\frac{2}{x+1} \to 0$ . So, $f(x)$ behaves like $y=x-1$ when $x$ is large. Thus, the slant asymptote is $y=x-1$ .

![[poly_rational_function_graph_01.png | center]]

> [!important] Check out how to graph polynomial rational functions using Python.
> [[graph_rational_function.html]]


## Applications

skip

