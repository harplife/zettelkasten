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


## Evaluating a Function

<mark class="hltr-trippy">Evaluating a Function</mark> at a number means to plugging in the number in the place of $x$.

> [!example]- Let $f(x)=3x^2+x-5$. Evaluate $f(-2)$
> $$
> \begin{align}
>   f(-2)&=3(-2)^2+(-2)-5 \\
>   f(-2)&=12-2-5 \\
>   f(-2)&=5
> \end{align}
> $$
> Answer : $f(-2)=5$


### Piecewise Function


A <mark class="hltr-trippy">Piecewise Function</mark> is a function that's defined by different rules (formulas) over different parts of its domain.
- In other words, the rule for $f(x)$ changes depending on which interval or condition $x$ falls into.
- Each formula is called a <mark class="hltr-trippy">Piece</mark>.

A piecewise function is written like this :

$$
f(x)=
\begin{cases}
  rule_{1} & \text{if condition}_{1} \\
  rule_{2} & \text{if condition}_{2} \\
  rule_{3} & \text{if condition}_{3} \\
  \vdots
\end{cases}
$$

Each *rule* applies only when the *condition* on $x$ is true.
Together, they cover the whole domain.

An example of a piecewise function :

$$
f(x) =
\begin{cases}
  x^2 & \text{ if } x < 0 \\
  x+1 & \text{ if } x \geq 0
\end{cases}
$$

This means :
- If $x$ is less than $0$, use the rule $f(x)=x^2$
- If $x$ is $0$ or more, use the rule $f(x)=x+1$

Evaluating the piecewise function above :
- $f(-2) = (-2)^2=4$
- $f(0)=0+1=1$
- $f(3)=3+1=4$

> [!important] Why Use Piecewise Functions?
> Piecewise Functions are used to model real-world situations where a rule changes depending on the condition. For example :
> - Shipping cost
> - Tax brackets
> - Absolute value

A piecewise function is called <mark class="hltr-trippy">Continuous</mark> if all the pieces connect perfectly without any jumps or holes. Otherwise, <mark class="hltr-trippy">Discontinuous</mark>.


### Net Change

The <mark class="hltr-trippy">Net Change</mark> of a function measures the overall difference in the function's output between two input values.

Given a function $f(x)$ and two points $x_{1}$ and $x_{2}$, then the net change is :

$$
f(x_{2}) - f(x_{1})
$$

> [!example]- Suppose $f(x)=2x+3$. What's the net change from $x=1$ to $x=4$?
> Net change = $f(4)-f(-1)$
> Compute : $f(4)=2(4)+3=11$
> Compute : $f(1)=2(1)+3=5$
> Net change = $11-5=6$
> Answer : $6$

The <mark class="hltr-trippy">Average Rate of Change</mark> is based on net change :

$$
\text{Average Rate of Change} = \frac{\text{Net Change in } f(x)}{\text{Change in } x} = \frac{f(x_{2})-f(x_{1})}{x_{2}-x_{1}}
$$

> [!important] Net change focuses only on the vertical difference, while the average rate of change includes the horizontal difference.


## The Domain of a Function

If a function is given by an algebraic expression and the domain is not stated explicitly, then by convention the domain of the function is the domain of the algebraic expression.
- That is, the set of all real numbers for which the expression is defined as a real number.

All the usual domain rules apply :
- No division by zero
- No negative numbers in root square (or even index roots)
- The domain can be expressed in set notation or interval notation

> [!example]- Finding Domains of Functions
> 1) Suppose $f(x)=\frac{1}{x^2-x}$. The function becomes undefined when $x=0$ or $x=1$. Thus, the domain of $f$ is $\{ x \in \mathbb{R} \mid x\neq 0, x\neq 1 \}$.
> 2) Suppose $f(x)=\sqrt{ 9-x^2 }$. The function becomes undefined (in real number system) when a square root of a negative number is taken. Thus, the domain of $f$ is $\{ x \in \mathbb{R} \mid -3 \leq x \leq 3 \}$


## Four Ways to Represent a Function

A specific function can be described in four different ways :
- Verbally (by a description in words)
- Algebraically (by an explicit formula)
- Visually (by a graph)
- Numerically (by a table of values)

