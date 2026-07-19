# Series


## Standard Series

|**Series**|**Converges?**|**Reason**|
|---|---|---|
|(\displaystyle \sum\frac1n)|No|Harmonic Series|
|(\displaystyle \sum\frac1{n^p},\ p>1)|Yes|p-Series Test|
|(\displaystyle \sum\frac1{n^p},\ p\le1)|No|p-Series Test|
|(\displaystyle \sum ar^n,\ \lvert r\rvert<1)|Yes|Geometric Series Test|
|(\displaystyle \sum ar^n,\ \lvert r\rvert\ge1)|No|Geometric Series Test|




## Convergence/Divergence Tests

| **Test**                                   | **When You Can Use It**                                                                                                                                                           | **What You Compute / Check**                                                                           | **Conclusion**                                                                                                                                                      |
| ------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Divergence (nth-Term) Test**             | Any series. This should always be the first test you try.                                                                                                                         | Compute $\displaystyle \lim_{n\to\infty} a_n$.                                                         | 1) If $\displaystyle \lim_{n\to\infty} a_n \neq 0$ or DNE, the series **diverges**. 2) If  $\displaystyle \lim_{n\to\infty} a_n = 0$, the test is **inconclusive**. |
| **Geometric Series Test**                  | The series has the form $\displaystyle \sum ar^n$ or $\displaystyle \sum ar^{n-1}$, where every term is obtained by multiplying the previous term by the same constant ratio $r$. | Identify or compute the common ratio $r$.                                                              | If $\lvert r\rvert<1$, the series **converges** (with sum $\frac{a}{1-r}$. If $\lvert r\rvert \ge 1$, the series **diverges**.                                      |
| **p-Series Test**                          | The series has exactly the form $\displaystyle \sum \frac{1}{n^p}$.                                                                                                               | Determine the exponent $p$.                                                                            | **Converges** if $p > 1$. **Diverges** if $p \le 1$.                                                                                                                |
| **Telescoping Series Test**                | Terms cancel when the partial sums are written out. Often requires partial fraction decomposition first.                                                                          | Find the partial sum $S_n$ and simplify after cancellation.                                            | If $\displaystyle \lim_{n\to\infty}S_n$ exists, the series **converges**. Otherwise, it **diverges**.                                                               |
| **Integral Test**                          | $a_n=f(n)$, where $f(x)$ is **positive, continuous, and decreasing** for all sufficiently large $x$.                                                                              | Evaluate the improper integral $\displaystyle \int_N^\infty f(x)\,dx$.                                 | The series converges **if and only if** the improper integral converges.                                                                                            |
| **Direct Comparison Test**                 | Terms are **nonnegative** and can be compared using inequalities to a known series.                                                                                               | Compare $a_n$ to a simpler series $b_n$ using inequalities.                                            | If $a_n\le b_n$ and $\sum b_n$ converges, then $\sum a_n$ converges. If $b_n\le a_n$ and $\sum b_n$ diverges, then $\sum a_n$ diverges.                             |
| **Limit Comparison Test**                  | Terms are **positive** and resemble a known series but direct inequalities are difficult.                                                                                         | Compute $\displaystyle L=\lim_{n\to\infty}\frac{a_n}{b_n}$.                                            | If $0<L<\infty$, both series either converge or diverge together. Otherwise, the test is usually inconclusive.                                                      |
| **Alternating Series Test (Leibniz Test)** | The series alternates signs, usually because of $(-1)^n$ or $(-1)^{n+1}$.                                                                                                         | Verify that $a_n$ decreases eventually and that $\displaystyle \lim_{n\to\infty}a_n=0$.                | If both conditions hold, the series converges.                                                                                                                      |
| **Ratio Test**                             | Especially useful for factorials, exponentials, powers, and products.                                                                                                             | Compute $\displaystyle L=\lim_{n\to\infty}\left(\frac{\lvert a_{n+1}\rvert}{\lvert a_n\rvert}\right)$. | If $L<1$, the series converges absolutely. If $L>1$ or $L=\infty$, the series diverges. If $L=1$, the test is inconclusive.                                         |
| **Root Test**                              | Best when each term is raised to the $n$th power or contains an $n$th root.                                                                                                       | Compute $\displaystyle L=\lim_{n\to\infty}\sqrt[n]{\lvert a_n\rvert}$.                                 | If $L<1$, the series converges absolutely. If $L>1$, the series diverges. If $L=1$, the test is inconclusive.                                                       |
| **Absolute Convergence Test**              | The series contains both positive and negative terms.                                                                                                                             | Test the series (\displaystyle \sum\lvert a_n\rvert) using any appropriate convergence test.           | If (\sum\lvert a_n\rvert) converges, then (\sum a_n) converges absolutely.                                                                                          |
| **Conditional Convergence Test**           | The series contains both positive and negative terms.                                                                                                                             | Show that (\sum a_n) converges, but (\sum\lvert a_n\rvert) diverges.                                   | The series is **conditionally convergent**.                                                                                                                         |


### How to Choose a Test

|**If the series contains...**|**Best test(s) to try first**|
|---|---|
|Any series|nth-Term (Divergence) Test|
|Constant ratio (r^n)|Geometric Series Test|
|(\frac1{n^p})|p-Series Test|
|Terms that cancel|Telescoping Series Test|
|Positive terms from a function (f(x))|Integral Test|
|Positive rational expressions|Direct Comparison or Limit Comparison Test|
|Alternating signs|Alternating Series Test, then Absolute Convergence Test|
|Factorials ((n!))|Ratio Test|
|Exponential terms ((2^n,\ 5^n,\ e^n,) etc.)|Ratio Test|
|Entire expression raised to the (n)th power|Root Test|
|Logarithms ((\ln n))|Usually Comparison or Integral Test|
|Rational functions (polynomials in numerator/denominator)|Usually Comparison or Limit Comparison Test|