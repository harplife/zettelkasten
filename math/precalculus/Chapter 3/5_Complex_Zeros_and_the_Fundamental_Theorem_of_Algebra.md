# 3.5 Complex Zeros and the Fundamental Theorem of Algebra

## Key Concepts

- The Fundamental Theorem of Algebra and Complete Factorization
- Zeros and Their Multiplicities
- Complex Zeros Occur in Conjugate Pairs
- Linear and Quadratic Factors


## Fundamental Theorem of Algebra and Complete Factorization

---
The <mark class="hltr-trippy">Fundamental Theorem of Algebra</mark> states that for every polynomial

$$
P(x) = a_{n}x^n+a_{n-1}x^{n-1}+\cdots+a_{1}x+a_{0} \quad (n \geq 1,a_{n} \neq 0)
$$

with complex coefficients has at least **one complex zero**.

In other words, there is at least one root $r \in \mathbb{C}$ such that $P(r)=0$ .

> [!important] Because any real number is also a complex number, the theorem applies to polynomials with *real* coefficients as well.

---
The <mark class="hltr-trippy">Complete Factorization Theorem</mark> is *corollary* (direct consequence) of the FTA, which states that every polynomial $P(x)$ of degree $n \geq 1$ with complex coefficients can be *completely factored* into $n$ linear factors over the complex numbers. That is,

$$
P(x) = a(x-r_{1})(x-r_{2})\cdots(x-r_{n})
$$

where $r_{1}, r_{2}, \dots, r_{n}$ are the **complex zeros** (some possibly repeated).

This is the <mark class="hltr-red">Proof</mark> :

By the Fundamental Theorem, $P$ has at least one zero. Lets call it $r_{1}$ . By the Factor Theorem, $P(x)$ can be factored as :

$P(x)=(x-r_{1})Q_{1}(x)$

where $Q_{1}(x)$ is of degree $n-1$ . Applying the Fundamental Theorem to the quotient $Q_{1}(x)$ gives us the factorization

$$
P(x)=(x-r_{1})(x-r_{2})Q_{2}(x)
$$

where $Q_{x}(x)$ is of degree $n-2$ and $r_{2}$ is a zero of $Q_{1}(x)$ .

Continuing this process for $n$ steps, we get a final quotient $Q_{n}(x)$ of degree $0$, a nonzero constant that we will call $a$ . This means that $P$ has been factored as

$$
P(x) = a(x-r_{1})(x-r_{2}) \cdots (x-r_{n})
$$

---
Example of factoring a polynomial completely :

Let $P(x)=x^3-2x+4$ .

The possible rational zeros are the factors of $4$, which are $\pm \{ 1,2,4 \}$. Using the synthetic division, we find that $-2$ is a zero, and the polynomial factors as

$$
P(x)=(x+2)(x^2-2x+2)
$$

To find the rest of the zeros, we use the Quadratic Formula.

$$
\begin{align}
  & x^2-2x+2=0 \\
  & x=\frac{2 \pm \sqrt{ 4-8 }}{2} \\
  & x = \frac{2 \pm 2i}{2} \\
  & x = 1 \pm i
\end{align}
$$

So the zeros of $P$ are $-2$, $1+i$, and $1-i$. Which also means the complete factorization of $P$ is

$$
P(x)=(x+2)(x-1-i)(x-1+i)
$$

---

## Zeros and Their Multiplicities

Together with the Fundamental Theorem of Algebra and the Complex Factorization Theorem, we ultimately get to the <mark class="hltr-trippy">Zeros Theorem</mark>, which states that a polynomial of degree $n$ has exactly $n$ complex roots (counting multiplicities).

This is the <mark class="hltr-red">Proof</mark> :

Let $P$ be a polynomial of degree $n$ . By the Complex Factorization Theorem

$$
P(x)=a(x-r_{1})(x-r_{2})\cdots(x-r_{n})
$$

Now suppose that $r$ is any given zero of $P$. Then

$$
P(r) = a(r-r_{1})(r-r_{2})\cdots(r-r_{n})=0
$$

Thus by the Zero-Product Property, one of the factors $r-r_{i}$ must be $0$, so $r=r_{i}$ for some $i$. It follows that $P$ has exactly the $n$ zeros $r_{1}, r_{2}, \dots, r_{n}$ .


> [!important] This theorem is more so referred to as the Fundamental Theorem of Algebra than it is called the Zeros Theorem.
> I don't know why the textbook makes this weird distinction.


## Complex Zeros Occur in Conjugate Pairs

The <mark class="hltr-trippy">Conjugate Zeros Theorem</mark> states that if the polynomial $P$ has real coefficients and if the complex number $z$ is a zero of $P$, then its complex conjugate $\overline{z}$ is also a zero of $P$.

