# 2.6 Transformations of Functions

## Key Concepts

- Vertical Shifting
- Horizontal Shifting
- Reflecting Graphs
- Vertical Stretching and Shrinking
- Horizontal Stretching and Shrinking
- Even and Odd Functions


## Vertical Shifting

Adding a constant to a function shifts its graph vertically.

Suppose $c>0$,
- $y=f(x)+c$ shifts the graph of $y=f(x)$ upward $c$ units
- $y=f(x)-c$ shifts the graph of $y=f(x)$ downward $c$ units

![[Pasted image 20251021221850.png | center | 500]]

In case of a linear function $f(x)=mx+b$, the constant $b$ moves the graph vertically.

In case of a quadratic function $f(x)=a(x-h)^2+k$, the constant $k$ moves the graph vertically.


## Horizontal Shifting

Adding a constant to a function input shifts its graph horizontally.

Suppose $c>0$,
- $y=f(x-c)$ shifts the graph of $y=f(x)$ to the right $c$ units
- $y=f(x+c)$ shifts the graph of $y=f(x)$ to the left $c$ units

![[Pasted image 20251021222635.png | center | 500]]

> [!important] It's kind of confusing to see this effect when dealing with a linear function, because shifting vertically has the same effect as shifting horizontally.

With a quadratic function, such as $f(x)=x^2$, adding a constant to the input $f(x+c)$ is the same as $f(x)=(x+c)^2$.

> [!important] Call it a revelation, but in a way, it's easier to understand any quadratic function as some sort of a modification of $f(x)=x^2$.
> Also, the modification can be done on either input or the output.


## Reflecting Graphs

Suppose $y=f(x)$,
- $y=-f(x)$ reflects the graph about the x-axis
- $y=f(-x)$ reflects the graph about the y-axis

For example, graph of $f(x)=-x^2$ reflects the graph of $f(x)=x^2$ about the x-axis :

![[Pasted image 20251021223707.png | center | 400]]

Graph of $g(x)=\sqrt{ -x }$ reflects the graph of $g(x)=\sqrt{ x }$ about the y-axis :

![[Pasted image 20251021223725.png | center | 500]]


## Vertical Stretching and Shrinking

Suppose $y=f(x)$, multiplying the y-coordinates by constant $c$, such that $y=cf(x)$, has the effect of vertically stretching or shrinking the graph by a factor of $c$.

If $c>1$, the graph of $y=f(x)$ stretches vertically.

If $0<c<1$, the graph of $y=f(x)$ shrinks vertically.

![[Pasted image 20251021224409.png | center | 600]]

For some graphs, such as a graph of $f(x)=x^2$, stretching them vertically may make them look leaner, while shrinking them vertically make them look wider.

![[Pasted image 20251021224627.png | center | 400]]


## Horizontal Stretching and Shrinking

Suppose $y=f(x)$, multiplying the input by constant $c$, such that $y=f(cx)$, has the effect of horizontally stretching or shrinking the graph by a factor of $c$.

If $c>1$, the graph of $y=f(x)$ shrinks horizontally by a factor of $\frac{1}{c}$.

If $0<c<1$, the graph of $y=f(x)$ stretches horizontally by a factor of $\frac{1}{c}$.

![[Pasted image 20251022004538.png | center | 600]]


## Even and Odd Functions

---
If a function $f$ satisfies $f(-x)=f(x)$ for every number $x$ in its domain, then $f$ is called an <mark class="hltr-trippy">Even Function</mark>.

For instance, the function $f(x)=x^2$ is even because :

$$
f(-x) = (-x)^2 = x^2 = f(x)
$$

The graph of an even function is symmetric with respect to the y-axis.

![[Pasted image 20251022005535.png | center | 400]]

---
If a function $f$ satisfies $f(-x)=-f(x)$ for every number $x$ in its domain, then $f$ is called an <mark class="hltr-trippy">Odd Function</mark>.

For example, the function $f(x)=x^3$ is odd because :

$$
f(-x)=(-x)^3=-x^3=-f(x)
$$

The graph of an odd function is symmetric with respect to the origin.

![[Pasted image 20251022005557.png | center | 400]]

---

> [!note] I guess there isn't anything about symmetry with respect to the x-axis because we are dealing with functions (as opposed to equations).


## Extra : Combination and Order

When multiple transformations are applied to a graph, order can matter. For example, starting with the function $y=\sqrt{ x }$,
1. Reflecting about the x-axis, then shifting upward 1 unit results in the equation $y=-\sqrt{ x }+1$
2. Shifting upward 1 unit, then reflecting about the x-axis results in the equation $y=-(\sqrt{ x }+1) =-\sqrt{ x }-1$.


## Extra : Summary of Transformations

