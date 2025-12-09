# 4.3 Logarithmic Functions

## Key Concepts

- Logarithmic Functions
- Graphs of Logarithmic Functions
- Common Logarithms
- Natural Logarithms


## Logarithmic Functions

A <mark class="hltr-trippy">Logarithmic Function</mark> is the inverse of an exponential function.

Given an exponential with base $a$ :

$$
y = a^x
$$

where $a>0$ and $a \neq 1$, its inverse function is :

$$
x = \log_{a}(y)
$$

Intuitively, a logarithm tells us what exponent we need to get a certain number.

For example, a log of $8$ with base $2$ tells us that we need exponent $3$ :

$$
\begin{align}
  \log_{2}(8) &= 3 \\
  2^3 &= 8
\end{align}
$$

> [!important] We can simply refer to logarithmic functions as **logarithms**.

As exponentials describe proportional growth and decay, logarithms describe the **rate**, **scale**, or **time** required in exponential processes.

A logarithm is used to tell how many times a value must multiply by a base to reach a certain target. For example, For $2$ to reach $32$, it must multiply by itself by $\log_{2}(32)=5$ times.

A logarithm is used to tell how much time is required for an exponential process to reach a certain value. For example, for continuous compound interest, we can use a logarithm to calculate the time it takes for an investment to reach a certain amount (save the details for later).

A logarithm is used to compress huge ranges of numbers (scales that follow the power law) to a manageable scale. For example, logarithms scale sound loudness by compressing the vast range of sound intensities into a manageable decibel (dB) scale that mirrors human hearing, which perceives loudness logarithmically (not linearly).

### Properties of Logarithms

| Property            | Reasoning |
| ------------------- | --------- |
| $\log_{a}(1)=0$     | $a^0=1$   |
| $\log_{a}(a)=1$     | $a^1=a$   |
| $\log_{a}(a^x)=x$   | $a^x=a^x$ |
| $a^{\log_{a}(x)}=x$ | see below |

In order to understand the property $a^{\log_{a}(x)}=x$, we must first look back on the definition of a logarithm :

$$
y = \log_{a}(x) \iff a^y=x
$$

This means, for $a^y$, we can replace $y$ with $\log_{a}(x)$ in order to get :

$$
a^{\log_{a}(x)} = x
$$

Intuitively, we can think of it like :

> "Take the exponent that produces $x$, then raise $a$ to that exponent - to get $x$ back."


For example :

$$
2^{\log_{2}(8)} = 8
$$

We can easily deduce that $\log_{2}(8)=3$, and so $2^{3}=8$. It's like applying exponential and its inverse at the same time, just to get back to its identity.


## Graphs of Logarithmic Functions

Given base function $f(x)=\log_{a}(x)$ with $a>0$, graphs of logarithmic functions look like this :

![[Pasted image 20251208215456.png|center]]

Note :
- The x-intercept is at $(1,0)$, and there is no y-intercept.
- The vertical asymptote is at $x=0$, and there is no horizontal asymptote.

Logarithms are inverse of exponentials, it follows that a logarithmic function is a reflection about the line $y=x$ of the corresponding exponential function.

![[Pasted image 20251208215648.png | center | 300]]

Also, since $f(x)=a^x$ has domain $\mathbb{R}$ and range $(0,\infty)$, it follows that its inverse function $y=\log_{a}(x)$ has domain $(0,\infty)$ and range $\mathbb{R}$.

---
Given base function $f(x)=\log_{a}(x)$ with $0<a<1$, graphs of logarithmic functions look like this :

![[Pasted image 20251208221620.png | center]]

Compare to the graph where $a>1$, this graph is a *reflection across x-axis*.

This points out the interesting fact that $-\log_{a}(x) = \log_{1/a}(x)$.

> [!warning] We haven't covered natural logs and the change-of-base formula yet, but the jist is that $\ln(x) = \log_{e}(x)$ and a logarithm $\log_{a}(x)$ is equivalent to $\frac{\ln(x)}{\ln(a)}$.

In order to understand how this happens, we first start with the change-of-base formula :

$$
\log_{a}(x)=\frac{\ln(x)}{\ln(a)}
$$

Apply a negative sign :

$$
-\log_{a}(x)=-\frac{\ln(x)}{\ln(a)}=\frac{\ln(x)}{-\ln(a)}
$$

$-\ln(a)$ is the same as $\ln(a^{-1})$, which is also same as $\ln(1/a)$, so :

$$
-\log_{a}(x)=\frac{\ln(x)}{\ln(1/a)}=\log_{1/a}(x)
$$


### Transformations of Logarithms

Given this basic logarithmic function :

$$
f(x)=\log_{a}(x) \quad \text{with } a>0, a \neq 1
$$

Every transformed logarithmic function can be written in the form :

$$
f(x) = A \cdot \log_{a}(B(x-h))+k
$$

| Parameter | Effect                                               | Note                                                                |
| --------- | ---------------------------------------------------- | ------------------------------------------------------------------- |
| $A$       | Vertical stretch/shrink & reflection across x-axis   |                                                                     |
| $B$       | Horizontal stretch/shrink & reflection across y-axis | Domain changes to $(-\infty, 0)$, and x-intercept moves to $(-1,0)$ |
| $h$       | Horizontal shift                                     | Moves vertical asymptote to $x=h$, and x-intercept to $(1+h, 0)$    |
| $k$       | Vertical shift                                       | Moves x-intercept to $(a^{-k},0)$                                   |

---
Given vertical shift to the base function :

$$
g(x)=\log_{a}(x)+k
$$

We can find the new x-intercept by having the function equal to zero and solving for $x$ :

$$
\begin{align}
  \log_{a}(x)+k &= 0 \\
  \log_{a}(x) &= -k \\
  x &= a^{-k}
\end{align}
$$

For example, for $g(x)=\log_{2}(x)-2$ :

$$
\begin{align}
  \log_{2}(x)-2 &= 0 \\
  \log_{2}(x) &= 2 \\
  x &= 2^2 = 4
\end{align}
$$

The x-intercept is at $(4, 0)$.


## Common Logarithms

The <mark class="hltr-trippy">Common Logarithm</mark> is the logarithm with base 10 :

$$
\log_{10}(x)
$$

We denote common logarithms by omitting the base :

$$
\log(x)
$$

Many real-world phenomena vary across **orders of magnitude** (powers of 10). This makes base 10 logs the natural measurement tools for anything that grows or shrinks by powers of 10. For example :
- pH scale (acidity)
- Sound intensity (decibels)
- Earthquake magnitude (Richter scale)
- Scientific data


## Natural Logarithms

The <mark class="hltr-trippy">Natural Logarithm</mark> is the logarithm with base $e$ :

$$
\log_{e}(x)
$$

Natural logs are denoted as :

$$
\ln(x)
$$

As per the definition of logarithms :

$$
y = \ln(x) \iff e^y = x
$$

Natural log is the inverse of the natural exponential function :

$$
\text{if } f(x)=e^x \text{, then } f^{-1}(x)=\ln(x)
$$

It follows that :

$$
\ln(e^x)=x \iff e^{\ln(x)}=x
$$

Natural log is just as important as the Euler's Number $e$ and the exponential function $e^x$, because they appear everywhere in nature and serve as the basis for solving any growth/decay problems in the real world.

> [!important] We will learn later in Calculus that the natural log is the only logarithm whose derivative is "clean".
> The natural log has a simple, elegant derivate : $$\frac{d}{dx}\ln(x)=\frac{1}{x}$$


