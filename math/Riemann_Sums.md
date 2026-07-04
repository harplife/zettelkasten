# Riemann Sums Equations

| Method                                   | Summation Form                                                                                                                                                                  |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Left-Hand Riemann Sum**                | $\displaystyle L_n=\sum_{i=0}^{n-1}f(a+i\Delta x)\,\Delta x$                                                                                                                    |
| **Midpoint Riemann Sum**                 | $\displaystyle M_n=\sum_{i=0}^{n-1}f!\left(a+\left(i+\tfrac12\right)\Delta x\right)\Delta x$                                                                                    |
| **Right-Hand Riemann Sum**               | $\displaystyle R_n=\sum_{i=1}^{n}f(a+i\Delta x)\,\Delta x$                                                                                                                      |
| **Trapezoidal Rule**                     | $\displaystyle T_n=\frac{\Delta x}{2}\left[f(a)+2\sum_{i=1}^{n-1}f(a+i\Delta x)+f(b)\right]$                                                                                    |
| **Simpson's Rule** _(requires even (n))_ | $\displaystyle S_n=\frac{\Delta x}{3}\left[f(a)+4\sum_{\substack{i=1\ i\text{ odd}}}^{n-1}f(a+i\Delta x)+2\sum_{\substack{i=2\ i\text{ even}}}^{n-2}f(a+i\Delta x)+f(b)\right]$ |

Trapezoidal Rule
$$
T_{n} = \frac{\Delta x}{2}[f(x_{0})+2f(x_{1})+2f(x_{2})+2f(x_{3})+\dots+2f(x_{n-1})+f(x_{n})]
$$

Simpson's Rule
$$
S_{n} = \frac{\Delta x}{3}[f(x_{0})+4f(x_{1})+2f(x_{2})+\dots+4(x_{n-1})+f(x_{n})]
$$




| Method                     | Choice of (x_k^*)                                       | Summation Form                                        |
| -------------------------- | ------------------------------------------------------- | ----------------------------------------------------- |
| **General Riemann Sum**    | Any point in the (k)-th subinterval                     | $\displaystyle \sum_{k=1}^{n} f(x_k^*),\Delta x$      |
| **Left-Hand Riemann Sum**  | $\displaystyle x_k^*=a+(k-1)\Delta x$                   | $\displaystyle L_n=\sum_{k=1}^{n} f(x_k^*)\,\Delta x$ |
| **Midpoint Riemann Sum**   | $\displaystyle x_k^*=a+\left(k-\tfrac12\right)\Delta x$ | $\displaystyle M_n=\sum_{k=1}^{n} f(x_k^*)\,\Delta x$ |
| **Right-Hand Riemann Sum** | $\displaystyle x_k^*=a+k\Delta x$                       | $\displaystyle R_n=\sum_{k=1}^{n} f(x_k^*)\,\Delta x$ |
