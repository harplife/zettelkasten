# 3.4 Real Zeros of Polynomials

## Key Concepts

- Rational Zeros of Polynomials
- Descarte's Rule of Signs
- Upper and Lower Bounds Theorem
- Using Algebra and Graphing Devices to Solve Polynomial Equations


## Rational Zeros of Polynomials

Suppose there's a polynomial :

$$
f(x)=a_{n}x^n+a_{n-1}x^{n-1}+\cdots+a_{1}x+a_{0}
$$

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

Since all other terms on the right side are multiples of $q$, the left side must be, too. Because $p$ and $q$ have no common factors, we can conclude that $q$ must divide $a_{n}$.

Similarly, if we arrange so that the last (constant) term to the left-side :



