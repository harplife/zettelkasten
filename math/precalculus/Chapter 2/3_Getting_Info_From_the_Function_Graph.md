# 2.3 Getting Information from the Graph of a Function

## Key Concepts

- Values of a Function; Domain and Range
- Comparing Function Values: Solving Equations and Inequalities Graphically
- Increasing and Decreasing Functions
- Local Maximum and Minimum Values of a Function


## Values of a Function; Domain and Range

The domain and range of a function $y=f(x)$ can be obtained from a graph of $f$, as shown in the figure. The domain is the set of all $x$-values for which $f$ is defined, and the range is all the corresponding $y$-values.

![[Pasted image 20251018232625.png| center | 400]]


> [!warning] #todo this section heavily depends on graphing calculator to graph a function, and then finding out the domain and the range visually.


## Comparing Function Values: Solving Equations and Inequalities Graphically

---
The solution(s) of the equation $f(x)=g(x)$ are the values of $x$ where the graphs of $f$ and $g$ intersect.

![[Pasted image 20251018232816.png| center | 400]]

---
The solution(s) of the inequality $f(x)<g(x)$ are the values of $x$ where the graph of $g$ is higher than the graph of $f$.

![[Pasted image 20251018232934.png | center | 400]]

---
The solution(s) of the inequality $f(x)>g(x)$ are the values of $x$ where the graph of $f$ is higher than the graph of $g$.

![[Pasted image 20251018233026.png | center | 400]]

---
It's possible to find the intersection point(s) of two functions algebraically, by just solving for $x$ and plugging in the variable into either of the functions.

> [!example]- What is the intersection point(s) of $f(x) = 2x+1$ and $g(x)=-x+4$ ?
> $$
> \begin{align}
>   \text{(1)} \quad & 2x + 1 = -x+4 \\
>   & 3x = 3 \\
>   & x = 1 \\
>   \text{(2)} \quad & f(1)=3
> \end{align}
> $$
> Answer : $(1,3)$

> [!example]- What is the intersection point(s) of $f(x)=x^2$ and $g(x)=2x+3$ ?
> $$
> \begin{align}
>   \text{(1)}\quad & x^2 = 2x + 3 \\
>   & x^2-2x-3=0 \\
>   & (x-3)(x+1)=0 \\
>   & x=3 \quad \text{ or } \quad x=-1 \\
>   \text{(2)}\quad & f(3)=9 \\
>   & f(-1)=1
> \end{align}
> $$
> Answer : $(3,9)$, $(-1,1)$

> [!example]- What is the intersection point(s) of $f(x)=|x-2|$ and $g(x)=x$ ?
> $$
> \begin{align}
>   \text{Case 1:}\quad & x-2 \geq 0 \to f(x)=x-2 \\
>   & x-2 = x \implies -2 = 0 \quad \text{(no solution)} \\
>   \text{Case 2:}\quad & x-2 < 0 \to f(x)=-(x-2) = -x+2 \\
>   & -x+2=x \implies 2x=2 \implies x = 1
> \end{align}
> $$
> Answer : $(1,1)$

---
Finding the solutions of the inequality such as $f(x)>g(x)$ or $f(x)<g(x)$ is the same as solving the inequality that was taught in [[8_Inequalities]].

Basically, move everything to one side to make them equal to $0$, factor them as necessary, define the critical points (the intersections), define the intervals using these critical points, and then testing the intervals for positive/negative.

For example, given $f(x)=x^2$ and $g(x)=2x+3$, the solutions of the inequality $f(x)<g(x)$ can be found by following the steps :

1. Move everything to one side and factor

$$
\begin{align}
  x^2 &< 2x + 3 \\
  x^2-2x-3 &< 0 \\
  (x-3)(x+1) &< 0
\end{align}
$$

2. Define the critical points and the intervals

Critical points are $x=-1$ and $x=3$. These split the real line into three intervals $(-\infty, -1)$, $(-1,3)$, and $(3, \infty)$.


3. Test each intervals

- Given $x=-2$ : $(-2-3)(-2+1)=5$. Therefore, positive
- Given $x=0$ : $(0-3)(0+1)=-3$. Therefore, negative
- Given $x=4$ : $(4-3)(4+1)=5$. Therefore, positive

The interval that satisfies the inequality is $(-1,3)$.

---

## Increasing and Decreasing Functions

$f$ is **increasing** on an interval $I$ if $f(x_{1})<f(x_{2})$ whenever $x_{1}<x_{1}$ in $I$.

![[Pasted image 20251019105413.png | center | 400]]

$f$ is **decreasing** on an interval $I$ if $f(x_{1})>f(x_{2})$ whenever $x_{1}<x_{1}$ in $I$.

![[Pasted image 20251019105428.png | center | 400]]


> [!important] By convention, open interval (e.g. $(1,5)$) is used to describe the intervals on which a function is increasing/decreasing. However, it is also correct to use closed intervals (e.g. $[1,5]$).

---
> [!important] This section specifically uses visual inspection of a graph (of a function) to find the intervals that are increasing/decreasing.
> The algebraic method of finding the increasing/decreasing intervals is a concept taught in **Calculus**.

It is possible to reason algebraically increasing/decreasing intervals for many common types of functions without relying on graphs.

1. **Linear Functions**

For $f(x)=mx+b$ :
- If $m>0$, it's increasing everywhere
- If $m<0$, it's decreasing everywhere
- If $m=0$, it's constant

2. **Quadratic Functions**

For $f(x)=ax^2+bx+c$ :
- Opens upward if $a>0$ (decreases, then increases)
- Opens downward if $a<0$ (increases, then decreases)
- The vertex (the turning point) is at $x=-\frac{b}{2a}$

3. **Cubic Functions**

- $f(x)=x^3$ increases everywhere because larger $x$ always give larger $f(x)$
- $f(x)=-x^3$ decreases everywhere

3. **Higher-Degree Polynomials**

- Odd powers -> behavior like $x^3$ (increases everywhere).
- Even powers -> behavior like $x^2$ (decreases, then increases)

3. **Rational Functions**

For $f(x)=\frac{1}{x}$ :
- For $(-\infty,0)$, it's decreasing
- For $(0,\infty)$, it's decreasing

---