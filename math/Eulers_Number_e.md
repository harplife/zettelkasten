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


## The Infinite Series Formula of $e$

> [!warning] We have not yet learned the **Infinite Series**.

The value of $e$ is the sum of the infinite series of the reciprocals of factorials :
$$
e = \sum^{\infty}_{n=0} \frac{1}{0!} + \frac{1}{1!} + \frac{1}{2!} + \frac{1}{3!} + \frac{1}{4!} + \dots
$$

The more terms you add, the more accurate the approximation of $e$ becomes :
$$
e = 1 + 1 + \frac{1}{2} + \frac{1}{6} + \frac{1}{24} + \frac{1}{120} + \dots \approx 2.71828
$$

> [!important] For high-precision calculations, the factorial series is used because it converges faster than the limit formula.


## Exponential Function $e^x$

The [Exponential Function](https://en.wikipedia.org/wiki/Exponential_function) is the unique real function which maps zero to one and has a derivative everywhere equal to its value. It is denoted as $e^x$ or $\exp x$.

![[exponential_function.svg|center|500]]

It is called *exponential* because its argument can be seen as an exponent to which a constant number $e$ (the base) is raised.

Note that in most math textbooks, $f(x)=e^x$ is referred to as the **Special Exponential Function**, while $f(x)=ab^x$ is referred to as the **General Exponential Function** or just **exponential function**.

> [!important] I previously thought exponential function just meant any constant raised to $x$.
> I think it's an important to note that $e^x$ is the base function; changing the base $n^x$ is just a variation of that base function.
> 
> This makes sense why derivative of an exponential function whose base is not $e$ still includes a natural log.


## Key Property of $e$

$e$ is defined such that :
$$
\lim_{ h \to 0 } \frac{e^h-1}{h}=1
$$

Meaning, the slope of the tangent line at $x=0$ for $f(x)=e^x$ is equal to $1$.

It is defined in this way so that $e^x$ is the only exponential whose derivative equals itself.

> [!important] $e$ is not some number that mathematicians arbitrarily chose.
> Mathematicians chose this number because of this specific property.


### Proof of the Key Property

Proving
$$
\lim_{ h \to 0 } \frac{e^h-1}{h}=1
$$
is a bit difficult.

First of all, it requires understanding $e$ is defined as :
$$
e = \lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)^n
$$

Which means, by the **Power Law of the Limits**, we get the definition of $e^x$ :
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

So that we get the *alternate* definition of $e^x$ :
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

Which leads to the **Power Series** of $e^h$ :
$$
e^h = 1 + h + \frac{h^2}{2!} + \frac{h^3}{3!} + \dots
$$

Lastly, it requires understanding that substituting the power series of $e^h$ is the key to taking the limit as $h \to 0$ :

$$
\lim_{ h \to 0 } \frac{e^h-1}{h} = \lim_{ h \to 0 } \frac{(1 + h + \frac{h^2}{2!} + \frac{h^3}{3!} + \dots)-1}{h}
$$

Simplify this step-by-step :
$$
\begin{align}
  e^h &= 1 + h + \frac{h^2}{2!} + \frac{h^3}{3!} + \dots \\
  e^h-1 &= h + \frac{h^2}{2!} + \frac{h^3}{3!} + \dots \\
  \frac{e^h-1}{h} &= 1 + \frac{h}{2!} + \frac{h^2}{3!} + \dots
\end{align}
$$

To get :
$$
\lim_{ h \to 0 } \frac{e^h-1}{h} = \lim_{ h \to 0 } (1 + \frac{h}{2!} + \frac{h^2}{3!} + \dots)
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
\boxed{\lim_{ h \to 0 } \frac{e^h-1}{h}=1}
$$


#### The Classic Inequality Proof

For small $h$ (specifically $-1<h<1$), the exponential function $e^h$ satisfies the inequality :
$$
1+h \leq e^h \leq \frac{1}{1-h}
$$

This inequality can be derived from the limit definition of $e$ :
$$
e^h = \lim_{ n \to 0 } \left( 1+\frac{h}{n} \right)^n
$$

> [!important] Finding the lower-bound and the upper-bound still requires using the binomial theorem and the power-series expansion.
> We'll skip the detail for now.

We can use this inequality to prove that
$$
\lim_{ h \to 0 } \frac{e^h-1}{h}=1
$$

---
**Step 1 - Subtract all side by** $1$

$$
\begin{align}
  &1+h \leq e^h \leq \frac{1}{1-h} \\
  &h \leq e^h-1 \leq \frac{1}{1-h}-1 \\
  &h \leq e^h-1 \leq \frac{h}{1-h}
\end{align}
$$

---
**Step 2 - Divide all side by** $h$

$$
\begin{align}
  &h \leq e^h-1 \leq \frac{h}{1-h} \\
  &1 \leq \frac{e^h-1}{h} \leq \frac{1}{1-h}
\end{align}
$$

---
**Step 3 - Take the limit as** $h \to 0^+$ **and use the squeeze theorem**

Left side :
$$
1 \to 1
$$

Right side :
$$
\frac{1}{1-h} \to 1
$$

Thus, we get :
$$
1 \leq \lim_{ h \to 0^+ } \frac{e^h-1}{h} \leq 1
$$

By the squeeze theorem :
$$
\lim_{ h \to 0^+ } \frac{e^h-1}{h} = 1
$$

---
**Step 4 - Take the limit as** $h \to 0^-$ **and use the squeeze theorem**

For $h<0$, dividing flips inequalities.

$$
1 \geq \lim_{ h \to 0^- } \frac{e^h-1}{h} \geq 1
$$

By the squeeze theorem :
$$
\lim_{ h \to 0^- } \frac{e^h-1}{h} = 1
$$

---
**Step 5 - Finalize the proof**

Since both sides of the limit matches, we can say that :
$$
\boxed{\lim_{ h \to 0 } \frac{e^h-1}{h} = 1}
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
\boxed{\frac{d}{dx} e^x = e^x}
$$

> [!important] The number $e$ is **specifically chosen** so that the exponential function satisfies :
> *rate of growth = current value* at every point on the curve.


## Derivative of $a^x$

Recall the key property of $e$ :
$$
\lim_{ h \to 0 } \frac{e^h-1}{h} = 1
$$

We know that natural logarithm is the inverse of the natural exponential function :
$$
\ln(e^x) = x
$$

Which means :
$$
\ln(e) = 1
$$

Thus, we get that :
$$
\lim_{ h \to 0 } \frac{e^h-1}{h} = \ln(e)
$$

This means that we can replace the base to any number $a$ to get :
$$
\lim_{ h \to 0 } \frac{a^h-1}{h} = \ln(a)
$$

We can use this fact to find the derivative of $a^x$.

---
**Step 1 - Use the limit definition of the derivative**

Recall :
$$
f'(x) = \lim_{ h \to 0 } \frac{f(x+h)-f(x)}{h}
$$

That means the derivative of $a^x$ is :
$$
\frac{d}{dx} a^x = \lim_{ h \to 0 } \frac{a^{x+h}-a^x}{h}
$$

---
**Step 2 - Use the product law of exponents and factor**

$$
\lim_{ h \to 0 } \frac{a^{x+h}-a^x}{h}
= \lim_{ h \to 0 } \frac{a^xa^h-a^x}{h}
= \lim_{ h \to 0 } a^x \cdot \frac{a^h-1}{h}
$$

---
**Step 3 - Use the constant multiple law of limits**

$$
\lim_{ h \to 0 } a^x \cdot \frac{a^h-1}{h}
= a^x \cdot \lim_{ h \to 0 } \frac{a^h-1}{h}
$$

---
**Step 4 - Substitute** $\ln(a)$ **and finalize the proof**

Recall that :
$$
\lim_{ h \to 0 } \frac{a^h-1}{h} = \ln(a)
$$

This means we can substitute in $\ln(a)$ :
$$
a^x \cdot \lim_{ h \to 0 } \frac{a^h-1}{h}
= a^x \cdot \ln(a)
$$

Therefore :
$$
\boxed{\frac{d}{dx} a^x = a^x \cdot \ln(a)}
$$


### Alternative way

Recall the identity law of exponents :
$$e^{\ln x}=x$$

Replace $x$ with $a$ :
$$
e^{\ln a} = a
$$

Raise both sides to the power of $x$ :
$$
e^{x \ln a} = a^x
$$

This means that :
$$
\frac{d}{dx} e^{x \ln a} = \frac{d}{dx} a^x
$$

We can use this fact to find the derivative of $a^x$.

> [!warning] This requires knowing how **derivative of natural logarithm** works.

---
**Step 1 - Use the chain rule**

By the chain rule, $f(u)=e^u$ becomes the outside function, whereas $u = x \ln a$ becomes the inside function :
$$
\frac{d}{dx} e^{x \ln a} = \frac{d}{du} e^u \cdot \frac{d}{dx} u
$$

We know that derivative of $e^x$ is equal to itself :
$$
\frac{d}{du} e^u = e^u = e^{x \ln a}
$$

Since $\ln a$ is just a constant multiple, we get :
$$
\frac{d}{dx} u = \frac{d}{dx} x \ln a = \ln a \frac{d}{dx} x = \ln a
$$

Putting it together, we then get :
$$
\frac{d}{dx} e^{x \ln a} = e^{x \ln a} \cdot \ln a
$$

---
**Step 2 - Substitute back** $a^x$

Since :
$$
e^{x \ln a} = a^x
$$

We get :
$$
\frac{d}{dx} a^x = a^x \ln a
$$

TOdo
- Finding the derivative of $5^{3x}$ (how does the chain rule work?)

