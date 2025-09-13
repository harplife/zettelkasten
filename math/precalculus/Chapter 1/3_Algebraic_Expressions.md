# 1.3 Algebraic Expressions

## Key Points

- Algebraic Expressions and Polynomials
- Adding and Subtracting Polynomials
- Multiplying Algebraic Expressions
- Special Product Formulas
- Factoring Common Factors
- Factoring Trinomials
- Special Factoring Formulas
- Factoring by Grouping Terms

## Algebraic Expressions and Polynomials

A <mark class="hltr-trippy">variable</mark> is a letter than can represent any number from a given set of numbers.

An <mark class="hltr-trippy">Algebraic Expression</mark> is a mathematical phrase that combines numbers, variables, and operations.

> [!note] If there is an equals sign ($=$), that's an **equation**, not an expression.

A <mark class="hltr-trippy">Term</mark> is a single piece of an algebraic expression, made of :
- A number (coefficient)
- Variable(s) with exponent(s)
- Multiplication between them

Terms are separated by $+$ or $-$.

> [!note] A <mark class="hltr-trippy">Coefficient</mark> is any number that is multiplied with a variable.
> In the expression $2x^2 - 3x + 4$, there are two coefficients :
> - $2$
> - $-3$

For example, take this expression :

$$
7x^2y - 3y +5
$$

In the above expression, there are three terms :
- $7x^2y$
- $-3y$
- $5$

A <mark class="hltr-trippy">Polynomial</mark> is an expression with one or more terms, in which the terms have **whole number** exponents.

> [!important] Polynomials are their own special, simple class of functions.
> When an expression has a negative exponent (variable in the denominator) or fractional exponent (radicals), the expression is *NOT* a polynomial. For example, following expressions are not polynomials :
> - $x^{-2} + 3$
> - $\sqrt{ x } + 2$
> - $\frac{1}{x} + 5$
> 
> Furthermore, in polynomials, variables cannot be inside another function (e.g. $\sin(x)$, $\ln(x)$, $2^x$).
> 
> Using a simple expression, like a polynomial, is important because it makes arithmetic simple, predictable, and closed. Polynomials are central to algebra and calculus. General approach in math, throughout history, is to study polynomials and then the others.
> 

A **monomial** is a polynomial with only one term (e.g. $5x$). A **binomial** is a polynomial with two terms (e.g. $x + 1$). A **trinomial** is a polynomial with three terms (e.g. $x^2 + x + 1$).

A <mark class="hltr-trippy">Degree</mark> is the highest exponent in a polynomial. For example, the degree of the polynomial $x^8 + 5x$ is $8$.

A polynomial without any variable (e.g. $6$) has a degree of $0$.

## Adding and Subtracting Polynomials

<mark class="hltr-trippy">Like Terms</mark> are terms with the same variables raised to the same powers.

Like terms can be combined, using the Distributive Property of Real Numbers. For instance,

$$
5x^7 + 3x^7 = (5 + 3)x^7 = 8x^7
$$

When it comes to adding and subtracting polynomials, it's best to group like-terms and then combine them. For example,

$$
\begin{align*}
  &(x^3 - 6x^2 + 2x +4) - (x^3 + 5x^2 - 7x) \\
  &\quad = x^3 - 6x^2 + 2x +4 - x^3 - 5x^2 + 7x \\
  &\quad = (x^3 - x^3) + (-6x^2 - 5x^2) + (2x + 7x) + 4 \\
  &\quad = -11x^2 + 9x + 4
\end{align*}
$$


## Multiplying Algebraic Expressions

Finding the product of polynomials (or other expressions) involve using the Distributive Property repeatedly.

For example, the process of multiplying the two binomials looks like this :

$$
(a + b)(c + d) = a(c + d) + b(c + d) = ac + ad + bc + bd
$$

Multiplying binomials can be simplified using the <mark class="hltr-trippy">FOIL method</mark>, like so :

![[Pasted image 20250912232902.png]]

FOIL stands for First, Outside, Inside, and Last.

> [!note] Multiplying expressions so that there aren't any variables grouped together is referred to as **Expanding**.
> For example, expanding $(x-2)(x+3)$ results with $x^2 + x - 6$.

## Special Product Formulas

Certain types of products occur frequently, and it may be worth memorizing them. The <mark class="hltr-trippy">Special Product Formulas</mark> are shortcuts for expanding certain kinds of binomials.

| Formula                | Equation                                |
| ---------------------- | --------------------------------------- |
| Square of a sum        | $(a + b)^2 = a^2 + 2ab + b^2$           |
| Square of a difference | $(a-b)^2 = a^2 - 2ab + b^2$             |
| Sum and difference     | $(a+b)(a-b) = a^2 - b^2$                |
| Cube of a sum          | $(a + b)^3 = a^3 + 3a^2b + 3ab^2 + b^3$ |
| Cube of a difference   | $(a - b)^3 = a^3 - 3a^2b + 3ab^2 - b^3$ |

### Recognizing a Special Product Formula

The product of trinomials (or bigger) can be "converted" to the product of binomials to make use of the special product formulas, as long as there are terms on both polynomials that can be grouped together.

For example, $(x + y - 1)(x + y + 1)$ is the product of trinomials but it can be treated like binomials like so :

$$
\begin{align*}
  (x+y-1)(x+y+1) &= [(x + y) - 1][(x + y) + 1] \\
  &= (x + y)^2 - 1^2 \\
  &= x^2 + 2xy + y^2 - 1
\end{align*}
$$

## Factoring Common Factors

<mark class="hltr-trippy">Factoring</mark> is the reverse process of expanding - it is rewriting an expression as a product of simpler expressions, called <mark class="hltr-trippy">Factors</mark>.

For example, factoring $x^2 + x -6$ results with two factors :
- $x - 2$
- $x + 3$

Factoring an expression starts by finding the common factors and the greatest common factor.

A <mark class="hltr-trippy">Common Factor</mark> is something that divides two or more numbers/expressions. For example, 
- Between $12$ and $18$, the common factors are $1,2,3,6$
- Between $12x^2y$ and $18xy^2$, the common factors are $2, 3, x, y, 6xy$

The <mark class="hltr-trippy">Greatest Common Factor</mark> is the largest number or expression that divides all terms exactly. For example,
- Between $12$ and $18$, the GCF is $6$
- Between $12x^2y$ and $18xy^2$, the GCF is $6xy$


Factoring expressions usually starts by pulling out the GCF - this is like reversing the distributive property.

Take $12x^2y + 18xy^2$, whose GCF is $6xy$. Factoring the expression using the GCF looks like this :

$$
12x^2y + 18xy^2 = 6xy(2x + 3y)
$$

Another example :

$$
\begin{align*}
  8x^4y^2 + 6x^3y^3 -2xy^4 &= (2xy^2)(4x^3) + (2xy^2)(3x^2y) + (2xy^2)(-y^2) \\
  &= 2xy^2(4x^3 + 3x^2y - y^2)
\end{align*}
$$


## Factoring Trinomials

Factoring a trinomial usually involves recognizing 