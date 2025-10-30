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

The <mark class="hltr-trippy">Conjugate Zeros Theorem</mark> states that if the coefficients are real, but not all roots are real, then nonreal complex roots will always appear in conjugate pairs :

$$
r=a+bi \quad \text{ and } \quad \overline{r}=a-bi
$$

where $b \neq 0$ .

This is the <mark class="hltr-red">Proof</mark> :

Suppose $P(x)=a_{n}x^n+a_{n-1}x^{n-1}+\cdots+a_{0}$ , and all $a_{k}$ are real.

If $a_{bi}$ is a zero, then

$$
P(a+bi)=0
$$

When we take the complex conjugate of both sides, we get :

$$
\overline{P(a+bi)}=\overline{0}=0
$$

Because all the coefficients are real, we can move the conjugate inside the polynomial :

$$
\overline{P(a+bi)} = P(\overline{a+bi})=P(a-bi)
$$

> [!important] We are skipping over a lot of details here, but the gist of it is that we make use of the fact that **(1)** complex conjugate of a sum of two complex numbers is the sum of the conjugates, and **(2)** the conjugate of a product is the product of the conjugates.
> ![[Pasted image 20251029145940.png | center | 400]]

Thus,

$$
P(a-bi)=0
$$

> [!important] This is easier to understand when we see that applying the Quadratic Formula often gives us the roots as a complex conjugate pair.
> For example, given $P(x)=x^2-4x+13$, applying the Quadratic Formula gives us $x=2 \pm 3i$. Thus, the roots are complex conjugates $2+3i$ and $2-3i$.

> [!important] Going back to Descarte's Theorem, the reason why the possible number of real zeros are in intervals of two (as in, if there are 3 sign changes, then either there's 3 or 1 real zeros), it is because if there isn't a real zero, then there's likely a complex zero - which always comes in conjugate pairs.


## Linear and Quadratic Factors

A quadratic polynomial with no real zero is said to be <mark class="hltr-trippy">irreducible</mark> over the real numbers. For example, $P(x)=x^2-4x+13$ does not have real roots.

The <mark class="hltr-trippy">Linear and Quadratic Factors</mark> Theorem states that every polynomial with real coefficients can be factored into a product of linear factors and irreducible quadratic factors with real coefficients.

> [!important] Previously, we covered that every polynomial with real coefficients can be factored completely with complex roots. Here, the theorem is saying that every polynomial with real coefficients can be factored completely, as long as it's a product of linear factors (e.g. $(x-3)$) and irreducible quadratic factors (e.g. $x^2-4x+13$).
> Basically, it would look like $P(x)=(x-3)(x^2-4x+13)$ .

This is the <mark class="hltr-red">Proof</mark> :

We first observe that if $r=a+bi$ is a complex number, then

$$
\begin{align}
  (x-r)(x-\overline{r}) &= [x-(a+bi)][x-(a-bi)] \\
  &= [(x-a)-bi][(x-a)+bi] \\
  &= (x-a)^2-(bi)^2 \\
  &= x^2-2ax+(a^2+b^2)
\end{align}
$$

The last expression is a quadratic with real coefficients.

Now, if $P$ is a polynomial with real coefficients, then by the Complete Factorization Theorem

$$
P(x) = a(x-r_{1})(x-r_{2})\cdots(x-r_{n})
$$

Since the complex roots occur in conjugate pairs, we can multiply the factors corresponding to each such pair to get a quadratic factor with real coefficients. This results in $P$ being factored into linear and irreducible quadratic factors.


## Extra : Symmetric Factorization

> [!warning] **Symmetric Factorization** is not an official term, but it's what chatGPT calls it and it makes sense.

Assume

$$
x^4+x^2+1=(x^2+ax+1)(x^2+bx+1)
$$

Expand the right side :

$$
(x^2+ax+1)(x^2+bx+1) = x^4+(a+b)x^3+(ab+2)x^2+(a+b)x+1
$$

Matching coefficients with $x^4+0x^3+1x^2+0x+1$ gives the system

$$
a+b=0, \quad ab+2=1
$$

From $a+b=0$, we have $b=-a$ . Plugging into the second equation :

$$
a(-a)+2=1 \implies -a^2=-1 \implies a^2=1
$$

So $a= \pm 1$ . Thus, two choices give the same factorization up to order :

$$
x^4+x^2+1 = (x^2+x+1)(x^2-x+1)
$$

