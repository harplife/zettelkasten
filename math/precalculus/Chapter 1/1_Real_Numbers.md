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

The adjective *real*, used in the 17th century by **Rene Descartes**, distinguishes real numbers from *imaginary* numbers (e.g. $\sqrt{ -1 }$).

> ![[Pasted image 20250902212157.png|200]]
> "I think, therefore I am" - [Rene Descartes](https://en.wikipedia.org/wiki/René_Descartes)

#todo Complex numbers and imaginary numbers are topics for later.

### Rational vs. Irrational

The real numbers include both the *rational numbers* and the *irrational numbers*.

A <mark class="hltr-trippy">Rational Number</mark> is a real number that can be expressed as a quotient (or fraction) of two integers, a numerator $p$ and a non-zero denominator $q$. The set of rational numbers, often referred to as "the rationals", is denoted by a bold $Q$ or blackboard bold $\mathbb{Q}$.

> [!fun fact] The rational numbers are denoted with $Q$ because it comes from the word "quotient".

The real numbers that are *rational* are those whose decimal expansion either terminates after a finite number of digits (e.g. $\frac{3}{4}=0.75$), or eventually begins to repeat the same finite sequence of digits over and over (e.g. $\frac{9}{44}=0.20454545\dots$).

An <mark class="hltr-trippy">Irrational Number</mark> is a real number that is not rational. The set of irrational numbers, often referred to as "the irrationals", is denoted by either $\mathbb{R} \setminus \mathbb{Q}$ or $\mathbb{R} - \mathbb{Q}$.

The real numbers that are *irrational* are those whose decimal expansion does not terminate and does not repeat. This includes $\sqrt{ 2 }$, $\pi$, and $\gamma$ (Euler's Constant).

#otod The irrational numbers include the [algebraic numbers](https://en.wikipedia.org/wiki/Algebraic_number) and the [transcendental numbers](https://en.wikipedia.org/wiki/Transcendental_number). This, I think, is a topic for another day.

#### Natural Numbers

The <mark class="hltr-trippy">Natural Numbers</mark> are the most basic numbers which are used to counting, and does not contain any fractional part (1, 2, 3, and so on). Typically, the natural numbers do not include 0.

> [!note] Whether the natural numbers include 0 is a topic of debate.
> Is 0 a number or an absence of number? Does 0 even exist?

The set of natural numbers is denoted by a bold $N$ or blackboard bold $\mathbb{N}$.

The **Whole Numbers** are basically natural numbers with 0 included.

The <mark class="hltr-trippy">Integers</mark> are all natural numbers, their negatives, and zero. The set of integers is denoted by a bold $Z$ or blackboard bold $\mathbb{Z}$.

> [!fun fact] The integers are denoted with $Z$ because of the German word "Zahlen", which means "numbers".

> [!important] The integers are a subset of rational numbers.
> Putting it all together, the hierarchy of number systems goes like this :
> $N \subset Z \subset Q \subset R \subset C$


### Properties of the Real Numbers

Given $a,b \in \mathbb{R}$,

1. <mark class="hltr-trippy">Closed</mark> : $a + b$, $a - b$, $a \times b$, $\frac{a}{b} (b \neq 0)$ are all in $\mathbb{R}$.
2. <mark class="hltr-trippy">Commutative</mark> : $a + b = b + a$, $a \times b = b \times a$
3. <mark class="hltr-trippy">Associative</mark> : $(a + b) + c = a + (b + c)$, $(a \times b) \times c = a \times (b \times c)$
4. <mark class="hltr-trippy">Distributive</mark> : $a(b + c) = ab + ac$
5. <mark class="hltr-trippy">Ordered</mark> : Real numbers can be compared (e.g. less than, or greater than) and ordered on the number line.
6. <mark class="hltr-trippy">Complete</mark> : Every non-empty set of real numbers that is bounded above has a *least upper bound* (supremum). This is what separates $\mathbb{R}$ from the rationals $\mathbb{Q}$ and makes calculus possible.

> [!note] Commutative, Associative, and Distributive properties are all that matters in everyday Algebra.

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

## Sets and Intervals

### Sets

A <mark class="hltr-trippy">Set</mark> is a well-defined collection of *distinct* objects that are considered as a single entity.
- It is denoted with capital letters (e.g. $A$, $B$, $C$).
- Set notation uses curly braces to list its objects (e.g. $A = \{ 1,2,3,4 \}$).
- There are no duplicates in a set (e.g. $\{ 1,2,2,3 \} = \{ 1, 2, 3 \}$).
- Order of objects does not matter.
- A set can be either finite (e.g. $\{ 1,2,3 \}$) or infinite (e.g. $\mathbb{Z}$).
- A set can be empty, which is denoted as $\emptyset$.

An <mark class="hltr-trippy">Element</mark> (aka **Member**) is an individual object contained in a set.
- If $x$ is an element of a set $A$, then it is written as $x \in A$ (x is in A).
- If $x$ is not an element of a set $A$, then it is written as $x \notin A$ (x is not in A).

A <mark class="hltr-trippy">Set-Builder Notation</mark> is a concise way to describe a set by a property that its elements must satisfy, rather than listing all elements. It uses the form :

$$
\{ x \in U | \text{condition on } x \}
$$

> [!example] A set of even integers
> $A = \{x \in \mathbb{Z} \mid x \bmod 2 = 0\}$

> [!example] A set of integers between 1 and 10
> $A = \{ x \in \mathbb{Z} \mid 1 \leq x \leq 10 \}$

> [!example] A set of rational numbers greater than 0
> $A = \{ x \in Q \mid x > 0 \}$

> [!example] Real solutions to $x^2 = 4$
> $A = \{ x \in R \mid x^2 = 4 \}$



#### Common Set Notations & Operations


| Notation                   | Name                                | Meaning                                        | Example                               |
| -------------------------- | ----------------------------------- | ---------------------------------------------- | ------------------------------------- |
| $x \in A$                  | Membership                          | $x$ is an element of set $A$                   | $3 \in \{1,2,3\}$                     |
| $x \notin A$               | Non-Membership                      | $x$ is not an element of set $A$               | $4 \notin \{1,2,3\}$                  |
| $\emptyset$                | Empty Set                           | The set with no elements                       | $\emptyset = \{\}$                    |
| $A^c$ or $A^\prime$        | Complement                          | Not in $A$ (relative to the universal set $U$) | $A^c = U - A$                         |
| $A \subseteq B$            | Subset                              | Every element of $A$ is also in $B$            | $\{1, 2\} \subseteq \{1,2,3\}$        |
| $A \subset B$              | Proper Subset                       | $A$ is a subset of $B$, but $A \neq B$         | $\{1, 2\} \subset \{1,2,3\}$          |
| $A \supseteq B$            | Superset                            | Every element of $B$ is in $A$                 | $\{1,2,3\} \supseteq \{1,2\}$         |
| $A \supset B$              | Proper Superset                     | $A$ is a superset of $B$, but $A \neq B$       | $\{1,2,3\} \supset \{1,2\}$           |
| $A = B$                    | Equality                            | Sets contain exactly the same elements         | $\{1,2,3\} = \{3,2,1\}$               |
| $\lvert A \rvert$          | Cardinality                         | Number of elements of set $A$                  | $\|\{1,2,3\}\| = 3$                   |
| $A \cup B$                 | Union                               | Elements in $A$ or $B$ (or both)               | $\{1,2\} \cup \{2,3\} = \{1,2,3\}$    |
| $A \cap B$                 | Intersection                        | Elements common to both $A$ and $B$            | $\{1,2\} \cap \{2,3\} = \{2\}$        |
| $A - B$ or $A \setminus B$ | Difference<br>(Relative Complement) | Elements in $A$ but not in $B$                 | $\{1,2,3\} - \{2,3\} = \{1\}$         |
| $A \triangle B$            | Symmetric Difference                | Elements in $A$ or $B$ but not both            | $\{1,2\} \triangle \{2,3\} = \{1,3\}$ |

There are more, such as :
- Power Set
- Cartesian Product
- Indexed Union
- Indexed Intersection

#todo This all relates to [Set Theory](https://en.wikipedia.org/wiki/Set_theory), which is a topic for later.

> [!note] Significance of Sets in Calculus
> Sets provide a precise language for describing where a function "lives" and where it's valid. Functions in calculus are written as mappings between sets, like
> 
> $$
> f : A \to B
> $$
> 
> which means "$f$ takes elements from set $A$ (the domain) into set $B$ (the codomain)".
> 
> Other than defining a Function, sets are used in Calculus; Derivatives and integrals are defined on sets. Series and convergence rely on subsets of numbers.

### Intervals

An <mark class="hltr-trippy">Interval</mark> is a set of real numbers that contains all real numbers between two given endpoints.
- If $a$ and $b$ are real numbers with $a < b$, then an interval is all the numbers between $a$ and $b$, possibly including or excluding the endpoints.

An interval can be *open*, *closed*, or *half-open/closed*.

An <mark class="hltr-trippy">Open Interval</mark> contains all numbers strictly between two given endpoints, endpoints not included. The open interval is denoted with parenthesis (i.e. $(a, b)$).

$$
(a, b) = \{x \in R \mid a < x < b\}
$$

A <mark class="hltr-trippy">Closed Interval</mark> contains all numbers between two given endpoints, endpoints included. The closed interval is denoted with brackets (i.e. $[a, b]$).

$$
[a,b] = \{ x \in R \mid a \leq x \leq b \}
$$

A <mark class="hltr-trippy">Half-Open/Closed Interval</mark> contains all numbers between two given endpoints, either including or excluding one of the endpoints.
- $[a, b)$ : includes $a$ but not $b$
- $(a, b]$ : includes $b$ but not $a$

An interval can also be either *bounded* or *unbounded*.

A <mark class="hltr-trippy">Bounded Interval</mark> is an interval with finite endpoints; in other words, both endpoints $a$ and $b$ are finite.

An <mark class="hltr-trippy">Unbounded Interval</mark> is an interval that extends infinitely in one direction :
1. $(-\infty, b)$ : all real numbers less than $b$
2. $(-\infty, b]$ : all real numbers less than or equal to $b$
3. $(a, \infty)$ : all real numbers greater than $a$
4. $[a, \infty)$ : all real numbers greater than or equal to $a$
5. $(-\infty,\infty)$ : the entire real line $R$

> [!important] Infinity is NOT a number, so intervals with infinity are always open on that side.

On a graph, an open interval is marked with open circle and a closed interval is marked with closed circle. Like so :

![[Pasted image 20250903104158.png|500]]

> [!note] No smallest or largest number in an open interval
> Any interval contains infinitely many number. In a closed interval, such as $[0, 1]$, the smallest number is $0$ and the largest is $1$. In an open interval, such as $(0, 1)$, there is no smallest or largest number. There is always a smaller number reaching $0$, such as $0.1$, $0.01$, and so on. Likewise, there is always a larger number reaching $1$, such as $0.9$, $0.99$, and so on.

## Absolute Value and Distance

The <mark class="hltr-trippy">Absolute Value</mark> of a real number $x$, written $\lvert x \rvert$, is its *distance* from $0$ on the real number line.

In piecewise form, Absolute Value is :

$$
\lvert a \rvert =
  \begin{cases}
    a & \text{if $a \geq 0$} \\
    -a & \text{if $a < 0$}
  \end{cases}
$$

The distance between two real numbers $a$ and $b$ is defined as :

$$
d(a, b) = \lvert a - b \rvert
$$

> [!note] The distance formula `d(a,b)` is generalized later to 2D and beyond.
> 2D (plane) distance formula is solved using Pythagoras :
> 
> $$
> d((x_{1},y_{1}),(x_{2},y_{2})) = \sqrt{ (x_{1}-x_{2})^2 + (y_{1}-y_{2})^2 }
> $$


There are several properties of Absolute Value :

