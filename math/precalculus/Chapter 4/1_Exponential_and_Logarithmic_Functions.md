# 4.1 Exponential Functions

## Key Concepts

- Exponential Functions
- Graphs of Exponential Functions
- Compound Interest


## Exponential Functions

An <mark class="hltr-trippy">Exponential Function</mark> is a function where the variable is in the exponent :

$$
f(x) = a \cdot b^x
$$

where :
- $a$ is a nonzero constant (vertical scale/shift factor)
- $b$ is the base, which must be positive and not equal to $1$

Examples :
- $2^x$
- $5 \cdot 3^x$
- $0.5^x$
- $-4 \cdot 1.2^x$

> [!warning] If $b<0$, the function oscillates and becomes undefined for many real $x$.

> [!warning] If $b=1$, then $1^x=1$, which is not exponential growth or decay, it's contant.


### Properties of Exponential Functions

Exponential functions are **always increasing** or **always decreasing**. Exponential functions are divided into two main families : **Growth** and **Decay**.

<mark class="hltr-trippy">Exponential Growth</mark> occurs when $b>1$. This function rapidly increases as $x \to \infty$ and approaches $0$ as $x \to -\infty$.

Graph of $f(x)=2^x$ :

![[Pasted image 20251202103151.png|center]]

<mark class="hltr-trippy">Exponential Decay</mark> occurs when $0 < b < 1$. This function rapidly decreases toward $0$ as $x \to \infty$ and increases as $x \to -\infty$.

Graph of $f(x)=(0.5)^x$ :

![[Pasted image 20251202104741.png|center]]



---
The **domain** of exponential functions are all real numbers $(-\infty, \infty)$.

The **range** of exponential functions depends on $a$ :
- If $a>0$, the range is $(0, \infty)$
- If $a<0$, the range is $(-\infty, 0)$

---
Every exponential function has a horizontal asymptote at (disregarding vertical shift) :

$$
y = 0
$$

This also means there is **no x-intercept**.

---
Every exponential function has a y-intercept at $f(0)=a$.

Which, in most cases, means $f(0)=1$. For $f(x)=2^x$, the y-intercept is $f(0)=2^0=1$.

---
> [!warning] This is something that will be covered more later.

The function

$$
f(x)=e^x
$$

is called the <mark class="hltr-trippy">Natural Exponential Function</mark>.

This is a special function where its rate of change at any point is equal to its value (which is something we'll learn in Calculus).


### Transformations of Exponential Functions

Given the base function :

$$
f(x) = b^x \quad (b>0, b \neq 1)
$$

Every transformed exponential function can be written in the form :

$$
g(x) = a \cdot b^{c(x-h)} + k
$$

Each parameter changes the graph in a specific way :

| Parameter | Effect                                               |
| --------- | ---------------------------------------------------- |
| $a$       | Vertical stretch/shrink & reflection across x-axis   |
| $c$       | Horizontal stretch/shrink & reflection across y-axis |
| $h$       | Horizontal shift                                     |
| $k$       | Vertical shift & moves the horizontal asymptote      |

> [!important] Multiplying the exponent changes the rate of growth (or decay).
> $$b^{cx}=(b^c)^x$$
> 
> Not only does this stretch/shrink the graph horizontally, it also **changes the effective base**. For example : $$2^{2x}=(2^2)^x=4^x$$



