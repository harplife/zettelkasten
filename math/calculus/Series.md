# Series


## Standard Series

| **Series**                                     | **Converges?** | **Reason**            |
| ---------------------------------------------- | -------------- | --------------------- |
| $\displaystyle \sum\frac1n$                    | No             | Harmonic Series       |
| $\displaystyle \sum\frac1{n^p},\ p>1$          | Yes            | p-Series Test         |
| $\displaystyle \sum\frac1{n^p},\ p\le1$        | No             | p-Series Test         |
| $\displaystyle \sum ar^n,\ \lvert r\rvert<1$   | Yes            | Geometric Series Test |
| $\displaystyle \sum ar^n,\ \lvert r\rvert\ge1$ | No             | Geometric Series Test |


## Convergence/Divergence Tests

### Identify

| **Test**                    | **When You Can Use It**                                                                                                                                                           | **What You Compute / Check**                                | **Conclusion**                                                                                                                 |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| **Geometric Series Test**   | The series has the form $\displaystyle \sum ar^n$ or $\displaystyle \sum ar^{n-1}$, where every term is obtained by multiplying the previous term by the same constant ratio $r$. | Identify or compute the common ratio $r$.                   | If $\lvert r\rvert<1$, the series **converges** (with sum $\frac{a}{1-r}$. If $\lvert r\rvert \ge 1$, the series **diverges**. |
| **p-Series Test**           | The series has exactly the form $\displaystyle \sum \frac{1}{n^p}$.                                                                                                               | Determine the exponent $p$.                                 | **Converges** if $p > 1$. **Diverges** if $p \le 1$.                                                                           |
| **Telescoping Series Test** | Terms cancel when the partial sums are written out. Often requires partial fraction decomposition first.                                                                          | Find the partial sum $S_n$ and simplify after cancellation. | If $\displaystyle \lim_{n\to\infty}S_n$ exists, the series **converges**. Otherwise, it **diverges**.                          |


### Standard Tests

| **Test**                         | **When You Can Use It**                                                                              | **What You Compute / Check**                                                                           | **Conclusion**                                                                                                                                                      |
| -------------------------------- | ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Divergence (nth-Term) Test**   | Any series. This should always be the first test you try.                                            | Compute $\displaystyle \lim_{n\to\infty} a_n$.                                                         | 1) If $\displaystyle \lim_{n\to\infty} a_n \neq 0$ or DNE, the series **diverges**. 2) If  $\displaystyle \lim_{n\to\infty} a_n = 0$, the test is **inconclusive**. |
| **Integral Test**                | $a_n=f(n)$, where $f(x)$ is **positive, continuous, and decreasing** for all sufficiently large $x$. | Evaluate the improper integral $\displaystyle \int_N^\infty f(x)\,dx$.                                 | The series converges **if and only if** the improper integral converges.                                                                                            |
| **Direct Comparison Test**       | Terms are **nonnegative** and can be compared using inequalities to a known series.                  | Compare $a_n$ to a simpler series $b_n$ using inequalities.                                            | If $a_n\le b_n$ and $\sum b_n$ converges, then $\sum a_n$ converges. If $b_n\le a_n$ and $\sum b_n$ diverges, then $\sum a_n$ diverges.                             |
| **Limit Comparison Test**        | Terms are **positive** and resemble a known series but direct inequalities are difficult.            | Compute $\displaystyle L=\lim_{n\to\infty}\frac{a_n}{b_n}$.                                            | If $0<L<\infty$, both series either converge or diverge together. Otherwise, the test is usually inconclusive.                                                      |
| **Ratio Test**                   | Especially useful for factorials, exponentials, powers, and products.                                | Compute $\displaystyle L=\lim_{n\to\infty}\left(\frac{\lvert a_{n+1}\rvert}{\lvert a_n\rvert}\right)$. | If $L<1$, the series converges absolutely. If $L>1$ or $L=\infty$, the series diverges. If $L=1$, the test is inconclusive.                                         |
| **Root Test**                    | Best when each term is raised to the $n$th power or contains an $n$th root.                          | Compute $\displaystyle L=\lim_{n\to\infty}\sqrt[n]{\lvert a_n\rvert}$.                                 | If $L<1$, the series converges absolutely. If $L>1$, the series diverges. If $L=1$, the test is inconclusive.                                                       |


### Alternating Series

| **Test**                                   | **When You Can Use It**                                                   | **What You Compute / Check**                                                                 | **Conclusion**                                                             |
| ------------------------------------------ | ------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| **Alternating Series Test (Leibniz Test)** | The series alternates signs, usually because of $(-1)^n$ or $(-1)^{n+1}$. | Verify that $a_n$ decreases eventually and that $\displaystyle \lim_{n\to\infty}a_n=0$.      | If both conditions hold, the series converges.                             |
| **Absolute Convergence Test**              | The series contains both positive and negative terms.                     | Test the series $\displaystyle \sum\lvert a_n\rvert$ using any appropriate convergence test. | If $\sum\lvert a_n\rvert$ converges, then $\sum a_n$ converges absolutely. |
| **Conditional Convergence Test**           | The series contains both positive and negative terms.                     | Show that $\sum a_n$ converges, but $\sum\lvert a_n\rvert$ diverges.                         | The series is **conditionally convergent**.                                |


### How to Choose a Test

| **If the series contains...**                             | **Best test(s) to try first**                           |
| --------------------------------------------------------- | ------------------------------------------------------- |
| Any series                                                | nth-Term (Divergence) Test                              |
| Constant ratio $r^n$                                      | Geometric Series Test                                   |
| $\frac1{n^p}$                                             | p-Series Test                                           |
| Terms that cancel                                         | Telescoping Series Test                                 |
| Positive terms from a function $f(x)$                     | Integral Test                                           |
| Positive rational expressions                             | Direct Comparison or Limit Comparison Test              |
| Alternating signs                                         | Alternating Series Test, then Absolute Convergence Test |
| Factorials ($n!$)                                         | Ratio Test                                              |
| Exponential terms ($2^n,\ 5^n,\ e^n$)                     | Ratio Test                                              |
| Entire expression raised to the $n$th power               | Root Test                                               |
| Logarithms ($\ln n$)                                      | Usually Comparison or Integral Test                     |
| Rational functions (polynomials in numerator/denominator) | Usually Comparison or Limit Comparison Test             |


## Integral Test Remainder Estimate

### Bounds of the Remainder

Suppose there exists a convergent series
$$
\sum_{k=1}^{\infty} a_{k}
$$
where
$$
a_{k} = f(x)
$$

and $f(x)>0$, $f \in C$, and $f' < 0$ for all sufficiently large $x$.

> [!important] "For all sufficiently large $x$"
> It means that a mathematical statement becomes true once $x$ crosses a certain threshold and stays true for all values of $x$ greater than that. It is used in limits and asymptotic analysis to describe the behavior of a function as $x$ approaches $\infty$.
> 
> Easy way to think about it is that a statement such as $x^2 > x$ is true only if $x$ is larger than $1$ (for positive real numbers).

After summing the first $n$ terms :
$$
S_{n} = \sum_{k=1}^n a_{k}
$$

The remainder is :
$$
R_{n} = S - S_{n}
$$

Where $S$ is the exact infinite sum.

The remainder always satisfies :
$$
\boxed{
  \int_{n+1}^{\infty} f(x)\,dx \leq R_{n} \leq \int_{n}^{\infty} f(x)\,dx
}
$$

Lower Bound :
$$
L(n) = \int_{n+1}^{\infty} f(x)\,dx
$$

Upper Bound :
$$
U(n) = \int_{n}^{\infty} f(x)\,dx
$$

The Remainder $R_{n}$ can then be estimated by evaluating the integrals of the Lower and Upper bounds.

---
Note that $R_{n}$ can be viewed in terms of Riemann Sums. Assume $a_{k}=f(k)$:
$$
\begin{align}
  R_{n} =&(a_{1} + a_{2} + \dots a_{n} + a_{n+1}+ a_{n+2} + \dots) \\
&-(a_{1} + a_{2} + \dots + a_{n}) \\
=&a_{n+1} + a_{n+2} + a_{n+3} + \dots \\
=&f(n+1) + f(n+2) + f(n+3) + \dots \\
=& \int_{n}^{n+1} f(x)\,dx
\end{align}
$$
Think of each term as the area of a rectangle with $\text{width} = 1$ and $\text{height} = f(k)$.

> [!important] The Lower and Upper bound inequalities are derived from Riemann Sums.
> Because the graph is positive and decreasing, Left-Hand Riemann Sum is always larger than the actual area under the graph. Thus, Left-Hand Riemann Sum becomes the upper bound. Like so, Right-Hand Riemann Sum is always smaller and thus it becomes the lower bound.

$$
\int_{n+1}^{\infty} f(x)\,dx \leq \int_{n}^{n+1} f(x)\,dx \leq \int_{n}^{\infty} f(x)\,dx
$$

#### Example

Given :
$$
\sum \frac{7}{4k^5}
$$

We see that the function is positive, continuous, and decreasing for all positive integers.

The upper bound is :
$$
\int_{n}^{\infty} \frac{7}{4x^5}\,dx = \frac{7}{16n^4}
$$

The lower bound is :
$$
\int_{n+1}^{\infty} \frac{7}{4x^5}\,dx = \frac{7}{16(n+1)^4}
$$

Therefore :
$$
\frac{7}{16(n+1)^4} \leq R_{n} \leq \frac{7}{16n^4}
$$


### Estimate of the Infinite Sum

> [!important] Once the lower and upper bounds for the remainder is found, the bounds can be used to estimate the infinite sum.

Given that :
$$
\begin{align}
  &S = S_{n} + R_{n} \\
  &L(n) \leq R_{n} \leq U(n)
\end{align}
$$
We can deduce that :
$$
S_{n} + L(n) \leq S \leq S_{n} + U(n)
$$

Thus, the infinite sum must lie inside :
$$
S_{n} + \int_{n+1}^{\infty} f(x)\,dx \leq S \leq S_{n} + \int_{n}^{\infty} f(x)\,dx
$$

#### Example

Given :
$$
\sum \frac{7}{4k^5}
$$

Suppose that we want to approximate the value of the infinite sum at 10th term. First, compute the partial sum :
$$
S_{10} = 1.814587847
$$

In the previous example, we found the lower and upper bounds for the remainder :
$$
\frac{7}{16(n+1)^4} \leq R_{n} \leq \frac{7}{16n^4}
$$

Evaluate the bounds at 10th term :
$$
\frac{7}{16(11)^4} \leq R_{10} \leq \frac{7}{16(10)^4}
$$

Therefore :
$$
\begin{align}
  1.814587847 + 0.000029882 \leq &S \leq 1.814587847+ 0.000043750 \\
  \to 1.814617729 \leq &S \leq 1.814631597
\end{align}
$$


## Alternating Series  Remainder Theorem

Suppose
$$
\sum_{k=1}^{\infty}(-1)^{k+1}a_{k}
$$
or
$$
\sum_{k=1}^{\infty}(-1)^k a_{k}
$$
is an alternating series, where
- $a_{k}>0$




Given $b_{n}$ is the non-alternating part of the series; if an alternating series passes the AST and converges to a total sum $S$, the absolute error of using the $n$-th partial sum $S_{n}$ is always less than or equal to the very next term $b_{n+1}$ :
$$
\text{Error} = \lvert S-S_{n} \rvert \leq b_{n+1}
$$

> [!important] This works because the terms alternate signs and decrease in size, each new term overcorrects the previous one.
> The exact total sum $S$ is always trapped between any two consecutive partial sums $S_{n}$ and $S_{n+1}$. The distance from the current guess $S_{n}$ to the actual target $S$ cannot be larger than the jump from $S_{n}$ to $S_{n+1}$. That jump is exactly $b_{n+1}$.


### Finding the terms

Finding the terms needed for precision up to $10^{-n}$

