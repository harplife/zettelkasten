# 1.4 Rational Expressions

## Key Points

- The Domain of an Algebraic Expression
- Simplifying Rational Expressions
- Multiplying and Dividing Rational Expressions
- Adding and Subtracting Rational Expressions
- Compound Fractions
- Rationalizing the Denominator or the Numerator
- Avoiding Common Errors


## The Domain of an Algebraic Expression

A <mark class="hltr-trippy">Fractional Expression</mark> refers to a quotient of two algebraic expressions.

Example of fractional expressions :
- $\frac{2x}{x-1}$
- $\frac{y-2}{y^2+3}$
- $\frac{x^3-x}{x^2-5x+6}$
- $\frac{x}{\sqrt{ x^2+1 }}$

A <mark class="hltr-trippy">Rational Expression</mark> is a fractional expression in which both the numerator and the denominator are polynomials.

> [!note] Like rational numbers, a rational expression can have its denominator omitted if it's $1$.

A fractional expression fails to be rational when the numerator or denominator is not a polynomial, which happens when there are :
- Roots of the variable (e.g. $\frac{1}{\sqrt{ x }}$)
- Exponents that are negative or fractional (e.g. $\frac{1}{x^{-2}}$, $\frac{1}{x^{3/2}}$)
- Exponentials (e.g. $\frac{2^{x}}{x+1}$)
- Functions (e.g. $\frac{\sin(x)}{x-3}$)


The <mark class="hltr-trippy">Domain</mark> of an algebraic expression is the set of all real numbers for which the expression is *defined*.

In general, all algebraic expression may not be defined for all values of the variable. This is especially the case for **Division-By-Zero** : fractional expressions where the expression itself can become undefined if the denominator evaluates to zero.

For example, for $\frac{1}{x}$, the value of $x$ cannot be $0$. In other words, for given expression $\frac{1}{x}$, the domain of this expression is ${x \mid x \neq 0}$.

Factoring may be required in order to find the domain of an expression. For example, while the domain of $\frac{x}{x^2-5x+6}$ may not be clear, the factored form $\frac{x}{(x-2)(x-3)}$ shows that the domain is $\{x \mid x \neq 2 \text{ and } x \neq 3\}$.

**Even roots of a negative number** (either on numerator or denominator, or both) can cause an expression to be undefined (in real numbers).

For example, for $\sqrt{ x }$, the value of $x$ must be a positive number or zero. In other words, the domain is $\{ x \mid x \geq 0 \}$. Likewise, for expression $\sqrt{ x -5 }$, the domain is $\{ x \mid x \geq 5 \}$.


## Simplifying Rational Expressions

Rational expressions can be simplified if the expressions on the numerator and the denominator share common factors that can be cancelled out.

$$
\frac{AC}{AB} = \frac{A}{B}
$$

For example,

$$
\begin{align*}
  \frac{x^2-1}{x^2+x-2} &= \frac{(x-1)(x+1)}{(x-1)(x+2)} \\
  &= \frac{x+1}{x+2}
\end{align*}
$$

> [!important] Down the rabbit hole : Removable Discontinuity
> So this is outside the content of the current section of the book. The domain for the original expression above is $\{ x \mid x \neq 1 \text{ and } x \neq -2\}$. However, once simplified, there's no longer a "hole" at $x = 1$. Apparently, this hole is considered a *removable discontinuity* - the hole itself is an artifact of the formula, and it does not describe the actual physical world (should the formula be a model of one). I think we are supposed to get to this concept as we learn about **Limits**.
> 
> Related :
> - [Classification of Discontinuities](https://en.wikipedia.org/wiki/Classification_of_discontinuities)
> - [Analytic Continuation](https://en.wikipedia.org/wiki/Analytic_continuation)


## Multiplying and Dividing Rational Expressions

