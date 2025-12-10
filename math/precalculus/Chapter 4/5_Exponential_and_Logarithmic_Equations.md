# 4.5 Exponential and Logarithmic Equations

## Key Concepts

- Exponential Equations
- Logarithmic Equations
- Compound Interest


## Exponential Equations

An Exponential Equation is an equation in which the variable occurs in the exponent.

Some exponential equations can be solved by using the fact that exponential functions are one-to-one. This means that :

$$
a^x=a^y \implies x=y
$$

For example :

$$
\begin{align}
  5^x &= 125 \\
  5^x &= 5^3 \\
  x &= 3
\end{align}
$$

Above method is not suitable for solving *all* equations; there are cases when one side is not easily expressed as a power of the same base (e.g. $5^x=160$). In order to solve such equations, we take the logarithm of each side and use the power rule to "bring down" the exponent.

For example :

$$
\begin{align}
  3^{x+2} &= 7 \\
  \log(3^{x+2}) &= \log(7) \\
  (x+2)\log(3) &= \log(7) \\
  x+2 &= \frac{\log(7)}{\log(3)} \\
  x &= \frac{\log(7)}{\log(3)}-2
\end{align}
$$

Using a calculator, we find the approximate value $x \approx -0.228756$.

---
Example : An Exponential Equation of Quadratic Type

In order to solve $e^{2x}-e^x-6 = 0$, we first factor the equation :

$$
\begin{align}
  e^{2x}-e^x-6 &= 0 \\
  (e^x)^2-e^x-6 &= 0 \\
  (e^x-3)(e^x+2) &= 0 \\
\end{align}
$$

We find that $e^x=3$ and $e^x=-2$, which we use natural logs to solve for $x$.
- $x=\ln(3)$
- $e^x=-2$ has no solution because $e^x>0$ for all $x$ (horizontal asymptote)

Thus, $x=\ln(3)$ is the only solution.

---
Example : An Equation Involving Exponential Functions

$$
\begin{align}
  3xe^x+x^2e^x &= 0 \\
  x(3+x)e^x &= 0 \\
  x(3+x) &= 0 \\
  x=0 \quad or \quad 3+x&=0
\end{align}
$$

> [!important] Note that both sides were divided by $e^x$. This is possible because $e^x \neq 0$.

Thus, the solutions are $x=0$ and $x=-3$.


## Logarithmic Equations

