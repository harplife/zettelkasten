# 3.7 Polynomial and Rational Inequalities

## Key Concepts

- Polynomial Inequalities
- Rational Inequalities


## Polynomial Inequalities

> [!important] Refer to [[8_Inequalities#Solving Nonlinear Inequalities|Chapter 1.8]] for solving nonlinear inequalities.

Solving polynomial inequalities like $P(x) \geq 0$ involves the following steps :

1. Move all terms to one side (so that the other side is $0$)
2. Factor completely
3. Find the intervals determined by the real zeros
4. Test each interval for sign
5. Determine the solutions of the inequality

---
For example, solving for $2x^3+x^2+6 \geq 13x$ looks like the following.

1. Move all terms to one side

$$
\begin{align}
  2x^3+x^2+6 &\geq 13x \\
  2x^3+x^2-13x+6 &\geq 0
\end{align}
$$

2. Factor completely

Given $2x^3+x^2-13x+6$, we use the Rational Zero Theorem to find the candidates for $\frac{p}{q}$ . The factors of $p$ are $\pm\{ 1,2,3,6 \}$, where as the factors of $q$ are $\pm\{ 1,2 \}$. Thus, we have the candidates

$$
\pm \left\{  \frac{1}{2}, 1, \frac{3}{2},2,3,6  \right\}
$$

We find that $2$ is a real zero :

```lua
2  |   2   1  -13   6
           4   10  -6
   --------------------
       2   5   -3   0
```

which leaves us with $2x^2+5x-3$ . Using the quadratic formula, we find that the other real zeros are $\frac{1}{2}$ and $-3$ .

Thus, the complete factored form looks like $(x-2)(x+3)(2x-1)$ .

3. Find the intervals

Since the roots are $-3$, $\frac{1}{2}$, and $2$, the intervals are :
- $(-\infty,-3)$
- $\left( -3, \frac{1}{2} \right)$
- $\left( \frac{1}{2}, 2 \right)$
- $(2, \infty)$

4. Test each interval for sign

- $-4$ : $-,-,-$
- $0$ : $-,+,-$
- $1$ : $-,+,+$
- $3$ : $+,+,+$

4. Determine the solution of the inequality

Because $(x-2)(x+3)(2x-1) \geq 0$, the intervals that satisfy the inequality are $\left( -3, \frac{1}{2} \right)$ and $(2, \infty)$ . This means the solution is :

$$
\left[ -3, \frac{1}{2} \right] \cup [2,\infty)
$$

---



## Rational Inequalities

