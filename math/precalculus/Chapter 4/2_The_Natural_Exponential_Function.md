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

The Natural Exponential Function is the only exponential function whose proportional growth rate is exactly $1$. This makes for the most "balanced" growth, which can be used as a basis for many exponential growth problems.

