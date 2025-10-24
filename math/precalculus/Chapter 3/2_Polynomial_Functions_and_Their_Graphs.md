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

There are four main cases of end behaviors :

| Degree | Leading Coefficient | End Behavior<br>(as $x \to -\infty$, $x \to \infty$) | Shape                      |
| ------ | ------------------- | ---------------------------------------------------- | -------------------------- |
| Even   | Positive            | Both ends **up**                                     | ($y = x^2$), ($y = x^4$)   |
| Even   | Negative            | Both ends **down**                                   | ($y = -x^2$), ($y = -x^4$) |
| Odd    | Positive            | Left end **down**, right end **up**                  | ($y = x^3$), ($y = x^5$)   |
| Odd    | Negative            | Left end **up**, right end **down**                  | ($y = -x^3$), ($y = -x^5$) |

