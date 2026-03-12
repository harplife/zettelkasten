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

> [!important] I previously thought exponential function just meant any constant raised to $x$.
> I think it's an important to note that $e^x$ is the base function; changing the base $n^x$ is just a variation of that base function. In fact, $f(x)=ab^x$ is called the **General Exponential Function** - but it's just commonly referred to as an exponential function.
> 
> This makes sense why derivative of an exponential function whose base is not $e$ still includes a natural log.


## The Limit Definition of $e^x$

Recall the compound interest formula :
$$
A = P\left( 1+\frac{r}{n} \right)^{nt}
$$

Let's say the initial investment is $P=1$ with interest rate $r=1$. The formula then becomes :
$$
\left( 1+\frac{1}{n} \right)^{nt}
$$

By the product rule of the exponents, we can change the expression to :
$$
\left( 1+\frac{1}{n} \right)^{nt} = \left[ \left( 1+\frac{1}{n} \right)^n \right]^t
$$

Recall the limit definition of $e$ :
$$
e = \lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)^n
$$

Suppose we take compound frequency $n$ to infinity, we then get :
$$
\left[\lim_{ n \to \infty }  \left( 1+\frac{1}{n} \right)^n \right]^t = e^t
$$

Here, we see that $e^t$ is represents the theoretical upper limit of the growth rate at any given time $t$.

<center>. . .</center>



---



If we look at what happens to growth as $n$ approaches infinity, we get :
$$
\lim_{ n \to \infty } \left( 1+\frac{r}{n} \right)^n
$$



$$
e^x = \lim_{ n \to \infty } \left( 1+\frac{x}{n} \right)^n
$$

$$
e = \lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)^n
$$


Suppose $m=\frac{n}{r}$ :
$$
\begin{align}
  A &= P\left( 1+\frac{r}{n} \right)^{nt} \\
    &= P\left[ \left( 1+\frac{r}{n} \right)^{n/r} \right]^{rt} \\
    &= P\left[ \left( 1+\frac{1}{m} \right)^m \right]^{rt}
\end{align}
$$


As $m$ becomes infinitely large, the quantity $\left( 1+\frac{1}{m} \right)^m$ approaches the number $e$. Thus, we can define the formula when compounding is done continuously :
$$
\begin{align}
  A &= P\left[ \lim_{ n \to \infty } \left( 1+\frac{1}{m} \right)^m \right]^{rt} \\
    &= Pe^{rt}
\end{align}
$$

This is the formula for **Continuously Compounded Interest**, which serves as the theoretical upper limit of how fast the amount can grow under a given interest rate.

Now, given that initial investment is $P=1$ and one year of time $t=1$, we can describe the total money after interest $A$ as a function of growth rate $r$. Say $x=r$ for convenience.

$$
f(x) = e^x
$$

In other words :
$$
f(x) = P\left[ \lim_{ n \to \infty } \left( 1+\frac{1}{m} \right)^m \right]^{xt}
$$

