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


## Key Properties of $e$

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

Which means, by the **Power Law of the Limits** :
$$
e^x = \left( \lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)^n \right)^x
= \lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)^{nx}
$$

Second, it requires understanding the **Taylor Series Expansion** and how it is used as a **fundamental linear approximation** :
$$
\ln(1+t) \approx t
$$

Which leads to :
$$
\ln\left( 1+\frac{1}{n} \right) \approx \frac{1}{n}
$$

Which basically proves that (by taking natural logarithm on both sides) :
$$
\lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)^{nx} \iff \lim_{ n \to \infty } \left( 1+\frac{x}{n} \right)^n
$$

> [!important] The intuition behind this is that taking *many small steps* (left) is effectively the same as taking *fewer but larger steps* (right).

So that :
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
  \vdots &\to 1
\end{align}
$$

Which leads to the **Power Series** for $e^h$ :
$$
e^h = 1 + h + \frac{h^2}{2!} + \frac{h^3}{3!} + \dots
$$

Lastly, it requires understanding that substituting the power series of $e^h$ is the key to taking the limit :
$$
\begin{align}
  e^h &= 1 + h + \frac{h^2}{2!} + \frac{h^3}{3!} + \dots \\
  e^h-1 &= h + \frac{h^2}{2!} + \frac{h^3}{3!} + \dots \\
  \frac{e^h-1}{h} &= 1 + \frac{h}{2!} + \frac{h^2}{3!} + \dots
\end{align}
$$

Let $h \to 0$. This means every term containing $h$ goes to $0$ :
$$
\begin{align}
  \frac{h}{2!} \to 0 \\
  \frac{h^2}{3!} \to 0 \\
  \vdots \to 0
\end{align}
$$

So the limit becomes :
$$
\lim_{ h \to 0 } (1 + \frac{h}{2!} + \frac{h^2}{3!} + \dots) \to
(1 + 0 + 0 + \dots)
= 1
$$

Therefore :
$$
\lim_{ h \to 0 } \frac{e^h-1}{h}=1
$$

## Derivative of $e^x$

The fact that
$$
\lim_{ h \to 0 } \frac{e^h-1}{h}=1
$$

helps proving why
$$
\frac{d}{dx} e^x = e^x
$$

---
**Step 1 - Apply the limit definition of derivative to** $e^x$

The limit definition of derivative :
$$
\frac{d}{dx} f(x) = \lim_{ h \to 0 } \frac{f(x+h)-f(x)}{h}
$$

Which, when applied to $f(x)=e^x$ :
$$
\frac{d}{dx} e^x = \lim_{ h \to 0 } \frac{e^{x+h}-e^x}{h}
$$

---
**Step 2 - Use the product rule of the exponents**

$$
e^{x+h} = e^xe^h
$$

Which means :
$$
\lim_{ h \to 0 } \frac{e^{x+h}-e^x}{h} = 
\lim_{ h \to 0 } \frac{e^xe^h-e^x}{h}
$$

From here, we can factor out $e^x$ from the numerator :
$$
\lim_{ h \to 0 } e^x \cdot \frac{e^h-1}{h}
$$

---
**Step 3 - Take the limit**

By the constant multiple law of the limits :
$$
\lim_{ h \to 0 } e^x \cdot \frac{e^h-1}{h} = e^x \cdot \lim_{ h \to 0 } \frac{e^h-1}{h}
$$

Using the property of $e$ which states that :
$$
\lim_{ h \to 0 } \frac{e^h-1}{h} = 1
$$

We get :
$$
e^x \cdot \lim_{ h \to 0 } \frac{e^h-1}{h} = e^x \cdot 1 = e^x
$$

Therefore,
$$
\frac{d}{dx} e^x = e^x
$$

> [!important] The number $e$ is **specifically chosen** so that the exponential function satisfies :
> *rate of growth = current value* at every point on the curve.




$$
1+h \leq e^h \leq \frac{1}{1-h}
$$