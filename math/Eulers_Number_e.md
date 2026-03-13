# Euler's Number $e$

The number $e$ is a mathematical constant, approximately equal to $2.71828$.
- It is an *irrational* number, meaning that it cannot be represented as a ratio of integers.
- It is a *transcendental* number, meaning that it is not a root of any non-zero polynomial with rational coefficients.
- It is referred to as **Euler's Number**.
- It is the base of the natural logarithm $\ln x$.
- It is the base of the exponential function $f(x)=e^x$


## The Limit Definition of $e$

As we learn math, $e$ first appears when studying **continuous growth** in precalculus. Specifically, we see that $e$ appears in **compound interest**.

Compound interest is defined by the formula :
$$
A = P\left( 1+\frac{r}{n} \right)^{nt}
$$
where :
- $A$ is the total money after interest
- $P$ is the initial investment called the principal
- $r$ is the annual interest rate expressed as a decimal
- $n$ is the compounding frequency (e.g. annually=1, monthly=12, daily=365)
- $t$ is the total number of years

Compound interest becomes the number $e$ when interest is calculated and added to the principal continuously - at every possible instant rather than annually or monthly.

In other words, the number $e$ represents the maximum possible growth rate for a 100% interest rate over one period, often referred to as **continuous compounding**.

<center>. . .</center>

Say initial investment is $P=1$, and the interest rate is $r=1$. Given one year $t=1$, let's see what happens when the compounding frequency $n$ is increased.

If the bank compounds once per year $n=1$, then :
$$
(1+1)^1 = 2
$$

Four times per year $n=4$ :
$$
\left( 1+\frac{1}{4} \right)^4 \approx 2.441\dots
$$

365 times per year $n=365$ :
$$
\left( 1+\frac{1}{365} \right)^{365} \approx 2.714\dots
$$

If we compound infinitely often, the expression approaches :
$$
\lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)^n \approx 2.718\dots
$$
Which is, $e$.

Thus, $e$ is defined as :
$$
e = \lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)^n
$$


## Exponential Function

The [Exponential Function](https://en.wikipedia.org/wiki/Exponential_function) is the unique real function which maps zero to one and has a derivative everywhere equal to its value. It is denoted as $e^x$ or $\exp x$.

![[exponential_function.svg|center|500]]

It is called *exponential* because its argument can be seen as an exponent to which a constant number $e$ (the base) is raised.

Note that in most math textbooks, $f(x)=e^x$ is referred to as the **Special Exponential Function**, while $f(x)=ab^x$ is referred to as the **General Exponential Function** or just **exponential function**.

> [!important] I previously thought exponential function just meant any constant raised to $x$.
> I think it's an important to note that $e^x$ is the base function; changing the base $n^x$ is just a variation of that base function.
> 
> This makes sense why derivative of an exponential function whose base is not $e$ still includes a natural log.



$e$ is defined such that :
$$
\lim_{ h \to 0 } \frac{e^h-1}{h}=1
$$

Meaning, the slope of the tangent line at $x=0$ for $f(x)=e^x$ is equal to $1$.

It is defined in this way so that $e^x$ is the only exponential whose derivative equals itself.

> [!important] $e$ is not some number that mathematicians arbitrarily chose.
> Mathematicians chose this number because of the specific properties :
> - Slope of the tangent line at $x=0$ for $e^x$ is $1$
> - Derivative of $e^x$ is $e^x$

<center>. . .</center>

Proving
$$
\lim_{ h \to 0 } \frac{e^h-1}{h}=1
$$
is a bit difficult.

First of all, it requires understanding that :
$$
e = \lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)^n
$$

Second, it requires understanding that :
$$
e^x = \lim_{ n \to \infty } \left( 1+\frac{x}{n} \right)^n
$$

Third, it requires understanding the **Binomial Theorem** :
$$
\left( 1+\frac{h}{n} \right)^n = 1 + h + \frac{n(n-1)}{2!n^2}h^2 + \frac{n(n-1)(n-2)}{3!n^3}h^3 + \dots
$$

Which, as $n \to \infty$ :
$$
\begin{align}
  \frac{n(n-1)}{n^2} &\to 1 \\
  \frac{n(n-1)(n-2)}{n^3} &\to 1 \\
  \dots &\to 1
\end{align}
$$

This is how we get the **Power Series** for $e^h$ :
$$
e^h = 1 + h + \frac{h^2}{2!} + \frac{h^3}{3!} + \dots
$$




<center>. . .</center>

The fact that
$$
\lim_{ h \to 0 } \frac{e^h-1}{h}=1
$$

helps proving why
$$
\frac{d}{dx} e^x = e^x
$$

Because ..