# 2.1 Functions

## Key Points

- Functions All Around Us
- Definition of Function
- Evaluating a Function
- The Domain of a Function
- Four Ways to Represent a Function


## Functions All Around Us

A <mark class="hltr-trippy">Function</mark> is a special kind of relationship between two sets of numbers (or objects) where each input has exactly one output.

> [!important] Textbook definition of a Function
> A function $f$ is a rule that assigns to each element in $x$ in a set $A$ exactly one element, called $f(x)$, in a set $B$.

A function that takes $x$ as its input is written as $f(x)$, and this is read as "function of $x$" or just "$f$ of $x$" for short.

> [!important] Other ways to read a function
> - $f$ at $x$
> - Value of $f$ at $x$
> - Image of $x$ under $f$

For a simple equation like $y=mx^{n}+b$ (where we expect one output for each input), we can say that $y$ is a function of $x$. Thus, it can be written as $f(x)=mx^n+b$. In this case, $y$ is called the 

> [!important] A Function as a "Mapping" Between Sets
> <mark class="hltr-trippy">Mapping</mark> is an operation that associate each element of a given set with one (or more) elements of a second set. A function is a mapping of one set to another.
> In terms of mapping, a function can be written as $f : A \to B$ and be read as "$f$ is a function from set $A$ to set $B$".

> [!important] Difference between equations and functions
> So far we've been dealing with **Equations**, which is a statement of equality between two expressions, but now we are dealing with **Functions**, which is a rule that assigns each input to exactly one output.
> 
> An equation is about **solving** (finding values tat make both sides equal), whereas a function is about **mapping** (defining a relationship between input and output).

Every function has :
- <mark class="hltr-trippy">Domain</mark> : all the possible input values (x-values) that are allowed.
- <mark class="hltr-trippy">Range</mark> : all the possible output values (y-values) the function can produce.

> [!important] Textbook definitions of Domain and Range
> - The domain of $f$ is the set $A$, the set of all $x$.
> - The range of $f$ is the subset of $B$, the set of all possible values of $f(x)$.

Range of $f$ is also written as $\{ f(x) \mid x \in A \}$.

> [!warning] To clear up a confusion between set B and the Range
> With the textbook definition of a Function, it almost seems to suggest that set $B$ is the Range of a Function, but it sneakily mentions that the range is the subset of $B$. It should've added an explanation that set $B$ is called the <mark class="hltr-trippy">Codomain</mark>, the set of all possible outputs the function can map into.
> In other words, the domain (set $A$) is all valid inputs (such as all real numbers $\mathbb{R}$), the codomain (set $B$) is the set of all possible outputs (such as all real numbers $\mathbb{R}$), and the range is the actual outputs (subset of $B$).
> It's easier to understand with $f(x)=x^2$, where the domain is all real numbers, the codomain is all real numbers, but the range is all non-negative numbers.

> [!example]- Domain and Range of $f(x)=\frac{1}{x}$
> - Domain : all real numbers except $0$
> - Range : all real numbers except $0$

Every function can be represented as a **set of ordered pairs** $(x,y)$, where :
- $x$ is an input (aka **independent** variable)
- $y$ is an output (aka **dependent** variable)
- no two pairs share the same x-value

In other words, a graph of $f(x)$ is set of all $(x, f(x))$.
