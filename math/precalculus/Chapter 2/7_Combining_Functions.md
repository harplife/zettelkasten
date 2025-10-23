# 2.7 Combining Functions

## Key Concepts

- Sums, Differences, Products, and Quotients
- Composition of Functions
- Applications of Composition

## Sums, Differences, Products, and Quotients

Functions can be combined to create a *new function*. There are four basic ways it can be done so, which are :
- Addition
- Subtraction
- Multiplication
- Division

To summarize,

| Operation          | Notation                      | Rule                                   |
| :----------------- | :---------------------------- | :------------------------------------- |
| **Addition**       | $(f + g)(x)$                  | $f(x) + g(x)$                          |
| **Subtraction**    | $(f - g)(x)$                  | $f(x) - g(x)$                          |
| **Multiplication** | $(fg)(x)$                     | $f(x) \times g(x)$                     |
| **Division**       | $\left(\frac{f}{g}\right)(x)$ | $\frac{f(x)}{g(x)}$, given$g(x) \ne 0$ |

> [!important] When combining functions, the domain of the new function is limited to all $x$ that are in the domain of both $f$ and $g$, except when division-by-zero occurs.
> Let $f$ and $g$ be functions with domains $A$ and $B$. The domain of the new function is $A \cap B$.


## Composition of Functions

Beyond simple arithmetic, functions can be combined by feeding one function into another - which is called <mark class="hltr-trippy">Composition of Functions</mark>.

Given two functions $f$ and $g$, the **composite function** is defined by :

$$
(f \circ g)(x) = f(g(x))
$$

which means :
> "Apply $g$ first, then apply $f$ to the result"

It can be read as "$f$ composed with $g$".

> [!example]- The composite function of $f(x)=2x+1$ and $g(x)=x^2$
> $$(f \circ g)(x) = f(g(x)) = f(x^2) = 2(x^2)+1=2x^2+1$$

> [!warning] The order of composition matters - $f(g(x)) \neq g(f(x))$.

The domain of $f \circ g$ is the set of all $x$ in the domain of $g$ such that $g(x)$ is in the domain of $f$.
- In other words, $x$ must be in the domain of $g$, and then the result $g(x)$ must be in the domain of $f$.

![[Pasted image 20251023085217.png | center | 600]]


## Applications of Composition

> [!example] The radius of a balloon and the volume of air being pumped
> If air is being pumped into a balloon, then the radius of the balloon is a function of the volume $V$ of air pumped into the balloon, $R=f(V)$. Also the volume $V$ is a function of the time $t$ that the pump has been working, $V=g(t)$. It follows that the radius $R$ is a function of the time $t$ given by $R=f(g(t))$.

> [!example] The temperature scale conversion Celsius-to-Kelvin
> The formula to convert Celsius to Fahrenheit is $$F(C)=\frac{9}{5}C+32$$
> The formula to convert Fahrenheit to Kelvin is $$K(F)=\frac{5}{9}(F-32)+273.15$$
> Then the composite function $K(F(C))$ is $$K(C)=\frac{5}{9}\left( \frac{9}{5}C+32-32 \right)=C+273.15$$

