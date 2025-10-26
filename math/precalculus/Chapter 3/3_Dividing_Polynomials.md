# 3.3 Dividing Polynomials

## Key Concepts

- Long Division of Polynomials
- Synthetic Division
- The Remainder and Factor Theorems


## Long Division of Polynomials

<mark class="hltr-trippy">Polynomial Long Division</mark> is a method used to divide one polynomial (the *dividend*) by another polynomial (the *divisor*), finding both the *quotient* and the *remainder*.

Given $f(x)$ and $g(x)$, a division $\frac{f(x)}{g(x)}$ looks like this :

$$
\frac{f(x)}{g(x)}=q(x)+\frac{r(x)}{g(x)}
$$

or

$$
f(x)=q(x) \cdot g(x) + r(x)
$$

where :
- $f(x)$ is the **dividend**
- $g(x)$ is the **divisor** (given $g(x) \neq 0$)
- $q(x)$ is the **quotient**
- $r(x)$ is the **remainder**
- The degree of $r(x)$ is always less than the degree of $g(x)$

The polynomial long division follows these steps :
1. Divide the first terms
2. Multiply and subtract
3. Repeat with new dividend

> [!important] BTW, this is what long division looks like
> ![[Pasted image 20251026085128.png | center]]

For example, given $f(x)=x^3-2x^2+4$ and $g(x)=x-1$, the polynomial long division of

$$
\frac{f(x)}{g(x)}=\frac{x^3-2x^2+4}{x-1}
$$

follows these steps :

1. Divide the first terms

Divide the leading term of the dividend $x^3$ by the leading term of the divisor $x$ :

$\frac{x^3}{x}=x^2$

Add $x^2$ to the top line (it becomes a part of the quotient)

2. Multiply and subtract

Multiply the divisor by $x^2$ (what we got from the first step) :

$(x-1)(x^2)=x^3-x^2$

Then, subtract the result from the dividend :

$(x^3-2x^2+4)-(x^3-x^2)=-x^2+4$

Now, $-x^2+4$ is the new dividend

3. Repeat with new dividend

Repeat step 1 and 2 with the new dividend until the new dividend is of lower degree than the divisor :

New dividend $-x^2+4$, current quotient $x^2$

$$
\begin{align}
&\text{1.} \quad -\frac{x^2}{x}=-x \\
&\text{2a.} \quad (x-1)(-x) = -x^2+x \\
&\text{2b.} \quad (-x^2+4)-(-x^2+x)=-x+4
\end{align}
$$

New dividend $-x+4$, current quotient $x^2-x$

$$
\begin{align}
&\text{1.} \quad -\frac{x}{x}=-1 \\
&\text{2a.} \quad (x-1)(-1) = -x+1 \\
&\text{2b.} \quad (-x+4)-(-x+1)=3
\end{align}
$$

Final quotient is $x^2-x-1$, and the remainder is $3$.

Thus, the result of the division $\frac{f(x)}{g(x)}$ looks like :

$$
\frac{x^3-2x^2+4}{x-1}=x^2-x-1+\frac{3}{x-1}
$$

or

$$
x^3-2x^2+4=(x-1)(x^2-x-1)+3
$$


## Synthetic Division

<mark class="hltr-trippy">Synthetic division</mark> is a quick method of dividing polynomials, which can be used when the divisor is of the form $x-c$.
- In synthetic division, only the essential parts of the long division are written.

![[Pasted image 20251026092610.png | center | 600]]

