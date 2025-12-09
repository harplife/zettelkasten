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

### Properties of Logarithms

| Property            | Reasoning |
| ------------------- | --------- |
| $\log_{a}(1)=0$     | $a^0=1$   |
| $\log_{a}(a)=1$     | $a^1=a$   |
| $\log_{a}(a^x)=x$   | $a^x=a^x$ |
| $a^{\log_{a}(x)}=x$ | see below |

In order to understand the property $a^{\log_{a}(x)=x}$, we must first look back on the definition of a logarithm :

$$
y = \log_{a}(x) \iff a^y=x
$$

This means, for $a^y$, we can replace $y$ with $\log_{a}(x)$ in order to get :

$$
a^{\log_{a}(x)} = a^y
$$

Because $a^y=x$, this also means that :

$$
a^{\log_{a}(x)}=x
$$

Intuitively, we can think of it like :

> "Take the exponent that produces $x$, then raise $a$ to that exponent - to get $x$ back."


For example :

$$
10^{\log_{10}(100)} = 100
$$

We can easily deduce that $\log_{10}(100)=10$, and so $10^{10}=100$. It's like applying exponential and its inverse at the same time, just to get back to its identity.


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

Compare to the graph where $a>1$, this graph is a reflection over x-axis.


### Intercepts and asymptotes of logarithms

For base function :

$$
f(x) = \log_{a}(x) \quad \text{with } a > 1
$$



### Transformations of Logarithms

Given this basic logarithmic function :

$$
f(x)=\log_{a}(x) \quad \text{with } a>1
$$

Every transformed logarithmic function can be written in the form :

$$
f(x) = A \cdot \log_{a}(B(x-h))+k
$$

| Parameter | Effect                                               |
| --------- | ---------------------------------------------------- |
| $A$       | Vertical stretch/shrink & reflection across x-axis   |
| $B$       | Horizontal stretch/shrink & reflection across y-axis |
| $h$       | Horizontal shift & moves the vertical asymptote      |
| $k$       | Vertical shift                                       |
