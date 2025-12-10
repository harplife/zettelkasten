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
---
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

A Logarithmic Equation is an equation in which a logarithm of the variable occurs.

Some logarithmic equations can be solved by using the fact that logarithms are one-to-one. This means that :

$$
\log_{a}(x) = \log_{a}(y) \implies x = y
$$

For example :

$$
\begin{align}
  \text{Given : } \log_{5}(x^2+1) &= \log_{5}(x-2)+\log_{5}(x+3) \\
  \log_{5}(x^2+1) &= \log_{5}[(x-2)(x+3)] \\
  \log_{5}(x^2+1) &= \log_{5}(x^2+x-6) \\
  x^2+1 &= x^2+x-6 \\
  x &= 7
\end{align}
$$

---
Above method is not suitable for *all* equations; there are cases when one side is not expressed as a logarithm. To solve such equations, convert the equation to its exponential form (combine logs on one side as necessary).

For example :

$$
\begin{align}
  \text{Given : } \log_{2}(25-x) &= 3 \\
  25-x &= 2^3 \\
  25-x &= 8 \\
  x = 25 - 8 &= 17
\end{align}
$$

> [!note] If the equation is already in its exponential form (and neither side has logs), then we can solve it by taking log on both sides.


## Compound Interest

Recall the formulas :
- Simple interest (for one year) --> $A=P(1+r)$
- Compound interest $n$ times per year --> $A(t)=P\left( 1+\frac{r}{n} \right)^{nt}$
- Continuous compound interest --> $A(t)=Pe^{rt}$

We can use logarithms to determine the time it takes for the principal to increase to a given amount.

---
<mark class="hltr-green">Example</mark>

A sum of \$5000 is invested at an interest rate of 5% per year. Find the time required for the money to double if the interest is compounded (a) semiannually or (b) continuously.

(a) We use the formula for compound interest with $P=5000$, $A(t)=10000$, $r=0.05$, and $n=2$. We solve the resulting exponential equation for $t$.

$$
\begin{align}
  5000\left( 1+\frac{0.05}{2} \right)^{2t} &= 10000 \\
  (1.025)^{2t} &= 2 \\
  \log(1.025)^{2t} &= \log(2) \\
  2t\log(1.025) &= \log(2) \\
  t &= \frac{\log(2)}{2\log(1.025)} \\
  t &\approx 14.04
\end{align}
$$

The money will double in about 14 years.

(b) We use the formula for continuously compounded interest with $P=5000$, $A(t)=10000$, and $r=0.05$. We solve the resulting exponential equation for $t$.

$$
\begin{align}
  5000e^{0.05t} &= 10000 \\
  e^{0.05t} &= 2 \\
  \ln(e^{0.05t}) &= \ln(2) \\
  0.05t &= \ln(2) \\
  t &= \frac{\ln(2)}{0.05} \\
  t &\approx 13.86
\end{align}
$$

The money will double in about 13 years 10 months.