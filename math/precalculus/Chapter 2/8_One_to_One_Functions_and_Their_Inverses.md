# 2.8 One-to-One Functions and Their Inverses

## Key Concepts

- One-to-One Functions : The Horizontal Line Test
- The Inverse of a Function
- Finding Inverse of a Function
- Graphing the Inverse of a Function
- Applications of Inverse Functions


## One-to-One Functions : The Horizontal Line Test

A function is called a One-to-One Function if no two elements in its domain have the same image, that is,

$$
f(x_{1}) \neq f(x_{2}) \text{ whenever } x_{1} \neq x_{2}
$$

If a **horizontal line** intersects the graph of $f$ at more than one point, then the function $f$ is not a one-to-one function.

Basically, any function that has symmetry about the y-axis is *not* a one-to-one function. Meanwhile, any linear function is a one-to-one function.

Examples of one-to-one function :
- $f(x)=x$
- $f(x)=x^3$
- $f(x)=\frac{1}{x}$
- $f(x)=\sqrt{ x }$

Examples of NOT one-to-one function :
- $f(x)=x^2$
- $f(x)=x^4$


## The Inverse of a Function

Let $f$ be a **one-to-one function** with domain $A$ and range $B$. Then its inverse function $f^{-1}$ has domain $B$ and range $A$ and is defined by :

$$
f^{-1}(y) = x \iff f(x)=y
$$

for any $y$ in $B$.

In other words, $f$ takes $x$ to $y$ and $f^{-1}$ takes $y$ back to $x$. The inverse function $f^{-1}$ satisfies the following cancellation equations :
- $f^{-1}(f(x))=x$ for every $x$ in $A$
- $f(f^{-1}(x)) = x$ for every $x$ in $B$

> [!important] In order to check if $g(x)$ is an inverse of $f(x)$, check if the composite function $f(g(x))=x$.

> [!warning] Not every function has an inverse. To have an inverse, a function must be one-to-one.

### Extra : Common Inverse Function Pairs

| Function                                          | Inverse Function          |
| ------------------------------------------------- | ------------------------- |
| $f(x) = x + a$                                    | $f^{-1}(x) = x - a$       |
| $f(x) = ax ) (where ( a \neq 0 )$                 | $f^{-1}(x) = \frac{x}{a}$ |
| $f(x) = x^2 ), ( x \ge 0$                         | $f^{-1}(x) = \sqrt{x}$    |
| $f(x) = e^x$                                      | $f^{-1}(x) = \ln(x)$      |
| $f(x) = \sin(x)$, restricted to $[-\pi/2, \pi/2]$ | $f^{-1}(x) = \arcsin(x)$  |


## Finding the Inverse of a Function

The inverse of a function can be found algebraically by : 
1. Set $y=f(x)$
2. Swap $y$ with $x$
3. Solve for $y$
4. Define the new function $f^{-1}(x)$.

For example, given $f(x)=\frac{x-5}{2}$, its inverse can be found by :
1. $y=\frac{x-5}{2}$
2. $x=\frac{y-5}{2}$
3. $y=2x+5$
4. $f^{-1}(x)=2x+5$

$f(f^{-1}(x))=\frac{(2x+5)-5}{2} = x$, therefore, the inverse function is confirmed.


## Graphing the Inverse of a Function

The graph of $f^{-1}(x)$ is a reflection of $f(x)$ across the line $y=x$.

![[Pasted image 20251023111418.png | center | 400]]


## Applications of Inverse Functions

> [!example] Conversion from Celsius-to-Fahrenheit and vice versa
> From Celsius $C$ to Fahrenheit $F$ : $$F=\frac{9}{5}C+32$$
> The inverse function converts Fahrenheit to Celsius : $$C=\frac{5}{9}(F-32)$$


