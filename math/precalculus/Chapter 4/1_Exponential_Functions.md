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


## Graphs of Exponential Functions


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


## Compound Interest

<mark class="hltr-trippy">Compound Interest</mark> is interest that is calculated on both the initial amount (called **Principal**) and on previously earned interest.

If a principal $P$ is invested at an annual interest rate $r$ (written as a decimal), compounded $n$ times per year, then the amount after $t$ years is :

$$
A(t) = P\left( 1+\frac{r}{n} \right)^{nt}
$$

Compound interest is already in the form of an exponential function.

Given the general exponential :

$$
f(x) = a \cdot b^x
$$

If we set :
- $a=P$
- $x=t$
- $b=\left( 1+\frac{r}{n} \right)^{n}$

Then we can get :

$$
A(t) = P \cdot b^t
$$

> [!important] Note that compound interest *grows exponentially* because $b$ will always be higher than $1$.

---
To note, simple interest looks like this :

$$
A(t) = P(1+rt)
$$

which is a linear function.

---
Annual compound interest looks like this :

$$
A = P(1+r)^t
$$

Monthly compound interest looks like this :

$$
A = P\left( 1+\frac{r}{12} \right)^{12t}
$$

---
For example, let's calculate monthly compound interest if :
- $P=1000$
- $r=0.12$
- $t=3$

Plugging in the values according to the formula, we get :

$$
1000\left( 1+\frac{0.12}{12} \right)^{12(3)} = \$1430.77
$$

In other words, with the initial amount of investment (or loan) of $1000, the total amount with compound interest after 3 years is $1430.77.

Compare that with simple interest :

$$
1000(1+0.12(3)) = \$1360.00
$$

