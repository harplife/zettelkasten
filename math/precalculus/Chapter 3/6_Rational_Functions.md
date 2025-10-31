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
| (n < m) (degree of numerator smaller)    | (y = 0)                                                                                                     |
| (n = m) (degrees are equal)              | (y = \dfrac{a_n}{b_m}) (ratio of leading coefficients)                                                      |
| (n > m) (degree of numerator larger)     | **No horizontal asymptote** (function grows without bound); sometimes a **slant/oblique asymptote** instead |
