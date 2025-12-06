# 4.2 The Natural Exponential Function

## Key Concepts

- The Euler's Number
- The Natural Exponential Function
- Continuously Compounded Interest


## The Euler's Number

<mark class="hltr-trippy">Euler's Number</mark>, written as $e$, is a mathematical constant which is irrational and naturally appears in situations involving growth and decay. It is approximately equal to :

$$
e \approx 2.718281828\dots
$$

The Euler's Number is important because $e$ naturally appears when a quantity grows at a rate proportional to its current amount.

---
> [!important] **Limit** is a calculus concept that describes what value an expression approaches when it is repeated infinitely. We'll learn more about it later, but this definition is sufficient enough to learn about how the Euler's Number get its value.

Let's talk about compound interest. Suppose we invest $1 at 100% interest for 1 year.

If the bank compounds once per year, then :

$$
(1+1)^1 = 2
$$

Twice per year :

$$
\left( 1+\frac{1}{2} \right)^2 = 2.25
$$

Four times per year :

$$
\left( 1+\frac{1}{4} \right)^4 \approx 2.441
$$

$n$ times per year :

$$
\left( 1+\frac{1}{n} \right)^n
$$

If we compound infinitely often, the expression approaches :

$$
e = \lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)^n
$$

Which approximates to $2.718\dots$


## The Natural Exponential Function

The Euler's Number is the base of the <mark class="hltr-trippy">Natural Exponential Function</mark> :

$$
f(x)=e^x
$$

The Natural Exponential Function is the only exponential function whose proportional growth rate is exactly $1$ - which means the rate of change is proportional to the current value. This makes for the most "stable" growth, which can be used as a basis for solving many exponential growth problems.

> [!important] The natural exponential function is often referred to as *the exponential function*.
> Also, it can be referred to as $\exp x$.

> [!warning] All of this will make more sense once we explore **Logarithms** and **Natural Logs**.


## Continuously Compounded Interest

We had previously covered above how $e$ gets its value :

$$
e = \lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)^n \approx 2.718\dots
$$

If we recall the compound interest formula :

$$
A(t) = P\left( 1+\frac{r}{n} \right)^{nt}
$$

If we were to compound infinitely (or *continuously*), the formula then becomes :

$$
A(t) = Pe^{rt}
$$

This is the <mark class="hltr-trippy">Continuously Compounded Interest</mark> (or **Continuous Compounding**), which serves as the theoretical upper limit of how fast the amount can grow under a given interest rate - *without changing the rate itself*.

For example, if we were to find the amount after 3 years if $1000 is invested at an interest rate of 12% per year, we can use continuous compounding to figure out what the maximum amount would be.

$$
A(3) = 1000e^{(0.12)3} = 1000e^{0.36} = 1433.33
$$

If we were to compound the interest annually (\$1404.93), quarterly (\$1425.76), or monthly (\$1430.77), it would be less than the maximum.

> [!important] Continuous compounding is a good way to get a realistic approximation.

