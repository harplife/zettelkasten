# 1.1 Real Numbers

## Key Points

- Real Numbers
- Properties of Real Numbers
- Addition and Subtraction
- Multiplication and Division
- The Real Line
- Sets and Intervals
- Absolute Value and Distance

## Real Numbers


A <mark class="hltr-trippy">Real Number</mark> is a number that can be used to measure a continuous one-dimensional quantity. The set of real numbers, sometimes called "the reals", is traditionally denoted by a bold $R$ or blackboard bold $\mathbb{R}$.

The adjective *real*, used in the 17th century by **Rene Descartes**, distinguishes real numbers from imaginary numbers (e.g. $\sqrt{ -1 }$).

> ![[Pasted image 20250902212157.png|200]]
> "I think, therefore I am" - [Rene Descartes](https://en.wikipedia.org/wiki/René_Descartes)

The real numbers include both the *rational numbers* and the *irrational numbers*.

A <mark class="hltr-trippy">Rational Number</mark> is a real number that can be expressed as a quotient (or fraction) of two integers, a numerator $p$ and a non-zero denominator $q$. The set of rational numbers, often referred to as "the rationals", is denoted by a bold $Q$ or blackboard bold $\mathbb{Q}$.

The real numbers that are *rational* are those whose decimal expansion either terminates after a finite number of digits (e.g. $\frac{3}{4}=0.75$), or eventually begins to repeat the same finite sequence of digits over and over (e.g. $\frac{9}{44}=0.20454545\dots$).

An <mark class="hltr-trippy">Irrational Number</mark> is a real number that is not rational. The set of irrational numbers, often referred to as "the irrationals", is denoted by either $\mathbb{R}/\mathbb{Q}$ or $\mathbb{R} - \mathbb{Q}$.

The real numbers that are *irrational* are those whose decimal expansion does not terminate and does not repeat. This includes $\sqrt{ 2 }$, $\pi$, and $\gamma$ (Euler's Constant).

#otod The irrational numbers include the [algebraic numbers](https://en.wikipedia.org/wiki/Algebraic_number) and the [transcendental numbers](https://en.wikipedia.org/wiki/Transcendental_number). This, I think, is a topic for another day.

An Integer is 

whole numbers

natural numbers





### Properties of the Real Numbers

Given $a,b \in \mathbb{R}$,

1. <mark class="hltr-trippy">Closed</mark> : $a + b$, $a - b$, $a \times b$, $\frac{a}{b} (b \neq 0)$ are all in $\mathbb{R}$.
2. <mark class="hltr-trippy">Commutative</mark> : $a + b = b + a$, $a \times b = b \times a$
3. <mark class="hltr-trippy">Associative</mark> : $(a + b) + c = a + (b + c)$, $(a \times b) \times c = a \times (b \times c)$
4. <mark class="hltr-trippy">Distributive</mark> : $a(b + c) = ab + ac$
5. <mark class="hltr-trippy">Ordered</mark> : Real numbers can be compared (e.g. less than, or greater than) and ordered on the number line.
6. <mark class="hltr-trippy">Complete</mark> : Every non-empty set of real numbers that is bounded above has a *least upper bound* (supremum). This is what separates $\mathbb{R}$ from the rationals $\mathbb{Q}$ and makes calculus possible.

#### Explanation of Completeness

Consider the set :
$$
S = {x \in \mathbb{Q} : x^2 < 2}
$$

That is, all *rational* numbers whose square is less than 2.
- $1.4^2 = 1.96 < 2$, so $1.4 \in S$.
- $1.41^2 = 1.9881 < 2$, so $1.41 \in S$.
- $1.4142^2 = 1.99996 < 2$, so $1.4142 \in S$.
- But $1.5^2 = 2.25 > 2$, so $1.5 \notin S$.

So the set $S$ is "pushing up" towards $\sqrt{ 2 }$. This means that any number $\geq \sqrt{ 2 }$ is an upper bound. For example, 2, 1.5, and 100. The least (smallest) upper bound would be $\sqrt{ 2 }$, except this is NOT a rational number. In other words, this set has a "hole", making the set *incomplete*.

If this set was a set of real numbers, such that :

$$
S = {x \in \mathbb{R} : x^2 < 2}
$$

This set has a least upper bound and therefore has no holes - making it *complete*.