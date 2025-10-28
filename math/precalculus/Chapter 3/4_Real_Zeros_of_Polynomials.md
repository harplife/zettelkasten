# 3.4 Real Zeros of Polynomials

## Key Concepts

- Rational Zeros of Polynomials
- Descarte's Rule of Signs
- Upper and Lower Bounds Theorem
- Using Algebra and Graphing Devices to Solve Polynomial Equations


## Rational Zeros of Polynomials

Let

$$
f(x)=a_{n}x^n+a_{n-1}x^{n-1}+\cdots+a_{1}x+a_{0}
$$

be a polynomial with real coefficients.

Suppose $r=\frac{p}{q}$ is a root of $f(x)$, where $p$ and $q$ are integers with no common factors and $q \neq 0$. That means :

$$
f\left( \frac{p}{q} \right)=0
$$

Substitute this into the polynomial :

$$
a_{n}\left( \frac{p}{q} \right)^n+a_{n-1}\left( \frac{p}{q} \right)^{n-1}+\cdots+a_{1}\left( \frac{p}{q} \right)+a_{0}=0
$$

Now multiply both sides by $q^n$ to clear the denominators :

$$
a_{n}p^n+a_{n-1}p^{n-1}q+a_{n-2}p^{n-2}q^2+\cdots+a_{1}pq^{n-1}+a_{0}q^n=0
$$

If we arrange so that the leading term $a_{n}p^n$ is on the left-side :

$$
a_{n}p^n=-(a_{n-1}p^{n-1}q+q_{n-2}p^{n-2}q^2+\cdots+a_{1}pq^{n-1}+a_{0}q^n)
$$

We see that :
- Every term on the right-side has a factor of $q$
- The left-side, $a_{n}p^n$, might not

Since all other terms on the right-side are multiples of $q$, the left side must be, too. Because $p$ and $q$ have no common factors, we can conclude that $q$ must divide $a_{n}$.

Similarly, if we arrange so that the last (constant) term $a_{0}q^n$ to the left-side :

$$
a_{0}q^n=-(a_{n}p^n+a_{n-1}p^{n-1}q+\cdots+a_{1}pq^{n-1})
$$

We see that :
- Every term on the right-side has a factor of $p$
- The left-side, $a_{0}q^n$, might not

Since all other terms on the right-side are multiples of $p$, the left side must be, too. Because $p$ and $q$ have no common factors, we can conclude that $p$ must divide $a_{0}$.

To summarize :
- $p$ divides the constant term $a_{0}$
- $q$ divides the leading coefficient $a_{n}$

Which also means :
- $p$ is a **factor of the constant term** $a_{0}$
- $q$ is a **factor of the leading coefficient** $a_{n}$

Above, is what the <mark class="hltr-trippy">Rational Zero Theorem</mark> states.

> [!important] Rational Zero Theorem is also called the **Rational Root Theorem**.

---
We can make use of the Rational Zero Theorem to narrow down which rational numbers might make $f(x)=0$.

Once all possible $\frac{p}{q}$ candidates are listed, each of them are tested (using substitution) until one that gives a remainder of $0$ is found.

Each successful zero gives a corresponding factor.

For example, to find the rational zeros of the following function $f(x)$:

$$
f(x)=x^3-6x^2+11x-6
$$

We first identify the coefficients :

$$
a_{n}=1, \quad a_{0}=6
$$

Then we find the factors of $a_{0}$ and $a_{n}$ :
- The factors of $a_{0}=6$ are $p=\pm 1,\pm 2,\pm 3,\pm 6$
- The factors of $a_{n}=2$ are $q=\pm 1$

Which means all possible candidates of $\frac{p}{q}$ are :

$$
\pm 1, \pm 2, \pm 3, \pm 6
$$

Using substitution, each candidate is tested. Starting with $1$ :

$$
f(1) = 1-6+11-6=0
$$

We find that $x-1$ is a factor.

We then divide $f(x)=x^3-6x^2+11x-6$ by $x-1$ :

$$
\frac{x^3-6x^2+11x-6}{x-1}=x^2-5x+6
$$

which can be further factored to $(x-2)(x-3)$.

The complete factorization is :

$$
f(x) = (x-1)(x-2)(x-3)
$$

So the zeros are $1$, $2$, and $3$.


## Descarte's Rule of Signs

---
<mark class="hltr-trippy">Descarte's Rule of Signs</mark> states the following :

Let

$$
f(x)=a_{n}x^n+a_{n-1}x^{n-1}+\cdots+a_{1}x+a_{0}
$$

be a polynomial with real coefficients.

The **number of positive real zeros** of $f(x)$ equals the **number of sign changes** in the coefficients of $f(x)$, or less than that by an even number.

The **number of negative real zeros** of $f(x)$ equals the **number of sign changes** in the coefficients of $f(-x)$, or less than that by an even number.

---
Take this function $f(x)$ as an example :

$$
f(x)=2x^4-x^3-14x^2+19x-6
$$

The coefficients are $\{ +2,-1,-14,+19,-6 \}$

From the first coefficient $+2$ to second coefficient $-3$, we see a **sign change** from positive to negative. So, when we count all of the sign changes :
1. $+2 \to -1$
2. $-14 \to +19$
3. $+19 \to -6$

We find that there are $3$ sign changes, which means there may be $3$ or $1$ **positive real zeros**.

In order to find negative real zeros, we see the sign changes for $f(-x)$ :

$$
\begin{align}
  f(-x) &= 2(-x)^4-(-x)^3-14(-x)^2+19(-x)-6 \\
  f(-x) &= 2x^4+x^3-14x^2-19x-6
\end{align}
$$

In this case, there may be $1$ **negative real zero**.

---
Descarte's Rule of Signs work hand-in-hand with the Rational Zero Theorem, as knowing the number of positive/negative real zeros may possibly reduce the work to find the zeros.

For example, going back to the polynomial above :

$$
f(x)=2x^4-x^3-14x^2+19x-6
$$

We know that this function may have $3$ or $1$ positive real zeros, and $1$ negative real zeros.

The constant term is $6$, which means $p$ is a factor of $4$. That is, $\{ 1,2,3,6 \}$.

The leading term is $2$, which means $q$ is a factor of $2$. That is, $\{ 1,2 \}$

The possible candidates of $\frac{p}{q}$ are :

$$
\left\{  \pm 1,\pm 2, \pm 3, \pm 6, \pm \frac{1}{2}, \pm \frac{3}{2}  \right\}
$$

Then we test it out using substitution. We can prioritize the positives first because there may be several positives.

First, we check $1$ :

$$
f(1)=2-1-14+19-6=0
$$

We find that $1$ is a real zero. So, when we factor out $x-1$ from the function, what we get is $2x^3+x^2-13x+6$.

Then, we check $2$ with the leftover function :

$$
\begin{align}
  f(2) &= 2(2)^3+(2)^2-13(2)+6 \\
  f(2) &= 16+4-26+6 \\
  f(2) &= 0
\end{align}
$$

We find that $2$ is a real zero as well. So, when we factor out $x-2$ from the function, what we get is $2x^2+5x-3$.

We can use quadratic formula to figure out the rest of the real zeros :

$$
\frac{-5 \pm \sqrt{ 25-4(2)(-3) }}{2(2)}=\frac{-5 \pm 7}{4} \implies x=-3 \text{ or } x=\frac{1}{2}
$$

We see that $2x^2+5x-3=(x+3)(2x-1)$, thus the real zeros are $-3$ and $\frac{1}{2}$.

Putting it all together :

$$
2x^4-x^3-14x^2+19x-6 = (x-1)(x-2)(x+3)(2x-1)
$$

Thus, the real zeros are $\left\{  1,2,-3, \frac{1}{2}  \right\}$ .

Just as the Descarte's Theorem suggested, there are $3$ positive and $1$ negative real zeros.

> [!important] The practical takeaway from this section
> - Use Descarte's Theorem first to know how many positives/negatives to expect. This helps prioritize testing.
> - Use the Rational Zero Theorem to produce a list of candidates.
> - Use substitution (or synthetic division) to test each candidates.


## Upper and Lower Bounds Theorem


