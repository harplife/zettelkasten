# 1.8 Inequalities

## Key Points

- Solving Linear Inequalities
- Solving Nonlinear Inequalities
- Absolute-Value Inequalities
- Modeling with Inequalities

## Solving Linear Inequalities

### Inequality

An **equation** is made up of two algebraic expressions that are equal to each other; the two expressions are separated by the equal $=$ sign, and each expression is referred to as either the left-hand-side, or the right-hand-side depending on where they locate in respect to the equal sign.

An <mark class="hltr-trippy">Inequality</mark> looks just like an equation, except that in the place of the equal sign is one of the symbols of $<$, $>$, $\leq$, or $\geq$. For example, $4x+7 \leq 19$ is an inequality.

To **solve an inequality** that contains a variable means to find all values of the variable that makes the inequality true.
- Unlike an equation, an inequality generally has infinitely many solutions, which form an interval or a union of intervals on the real line.

![[Pasted image 20251001125027.png]]


### Rules for Inequalities

| Rule                                                                  | Description                                                                                                                    |
| --------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| $A \leq B \iff A+C \leq B+C$                                          | **Adding/subtracting** the same quantity to each side of an inequality gives an equivalent inequality.                         |
| If $C>0$, then $A\leq B \iff CA \leq CB$                              | **Multiplying** each side of an inequality by the same positive quantity gives an equivalent inequality                        |
| If $C<0$, then $A \leq B \iff CA \geq CB$                             | **Multiplying** each side of an inequality by the same negative quantity *reverses the direction* of the inequality.           |
| If $A>0$ and $B>0$, then $A \leq B \iff \frac{1}{A} \geq \frac{1}{B}$ | **Taking reciprocals** of each side of an inequality involving positive quantities *reverses the direction* of the inequality. |
| If $A \leq B$ and $C \leq D$, then $A+C \leq B + D$                   | Inequalities can be added.                                                                                                     |
| If $A \leq B$ and $B \leq C$, then $A \leq C$                         | Inequality is transitive.                                                                                                      |


### Linear Inequality

An inequality is <mark class="hltr-trippy">Linear</mark> if each term is constant or a multiple of the variable. In other words, the degree of the expressions on both sides has to be $1$.

Solving a linear inequality is similar to solving an equation. For example,

$$
\begin{align}
  3x &< 9x + 4 \\
  3x - 9x &< 9x + 4 - 9x \\
  -6x &< 4 \\
  \left( -\frac{1}{6} \right)(-6x) &> \left( -\frac{1}{6} \right)(4) \\
  x &> -\frac{2}{3}
\end{align}
$$

The solution of the inequality above is the interval $\left( -\frac{2}{3}, \infty \right)$.


### Simultaneous Inequalities

Solving inequalities can become a little complex when there are multiple inequalities all at the same time - in other words, <mark class="hltr-trippy">Simultaneous Inequalities</mark>. It looks like this :

$$
A < B + C < D
$$

Solving inequalities :

$$
\begin{align}
  4 &\leq 3x - 2 < 13 \\
  4+2 &\leq 3x -2 +2 < 13+2 \\
  6 &\leq 3x < 15 \\
  6\left( \frac{1}{3} \right) &\leq 3x\left( \frac{1}{3} \right) < 15\left( \frac{1}{3} \right) \\
  2 &\leq x < 5
\end{align}
$$

The solution set is $\{ x \in \mathbb{R} \mid 2 \leq x < 5 \} = [2, 5)$.


## Solving Nonlinear Inequalities

A Non-linear Inequality is an inequality involving a polynomial of degree greater than $1$, or sometimes rational, exponential, or other non-linear functions. For example,
- Polynomial : $x^2-5x+6>0$
- Rational : $\frac{x+1}{x-2} \leq 0$

### General Strategy for Polynomial

Given a polynomial non-linear inequality : $x^2-5x>-6$

1. Rewrite in standard form; move everything to one side so the other side becomes $0$.

$$
\begin{align}
  x^2-5x &> -6 \\
  x^2-5x+6 &> 0
\end{align}
$$

2. Factor the polynomial.

$$
\begin{align}
  x^2-5x+6 = (x-2)(x-3)
\end{align}
$$

3. Find the roots (disregard the inequality for now).

$$
\begin{align}
  (x-2)(x-3) = 0 \implies x=2,3
\end{align}
$$

4. Identify the intervals; divide the real line by the values of $x$ (which makes each factor equal to zero).

Given $x=2,3$, the intervals are $(-\infty, 2)$, $(2, 3)$, and $(3, \infty)$.


5. Test the sign in each interval; pick a random value from each interval and test whether the product is positive or negative.

- For $(-\infty, 2)$, say $x=0$ : $(0-2)(0-3) = (-2)(-3) = 6$, the sign is positive (+)
- For $(2, 3)$, say $x=2.5$ : $(2.5-2)(2.5-3) = (0.5)(-0.5) = -0.25$, the sign is negative (-)
- For $(3, \infty)$, say $x=4$ : $(4-2)(4-3) = (2)(1) = 2$, the sign is positive (+)

> [!important] Any random value from each interval is representative of the interval itself.
> If a value from an interval shows its sign, rest of the values will show the same sign.


6. Choose the intervals that satisfy the inequality.

Since $x^2-5x+6>0$, the factors have to be positive; in other words, the value of $x$ has to meet the condition where, if plugged in, the resulting value is positive. We checked that any value from $(-\infty, 2)$ and $(3, \infty)$ satisfy this condition. Therefore, the solution for the inequality is :

$$
(-\infty, 2) \cup (3, \infty)
$$


#### Example for Less Than or Equal To 0

Given $x^2 \leq 5x -6$ :

1. Rewrite to the standard form.

$$
x^2-5x+6 \leq 0
$$


2. Factor

$$
x^2-5x+6 = (x-2)(x-3)
$$


3. Find the roots

$x = 2, 3$


4. Identify the intervals

Intervals are : $(-\infty, 2)$, $(2, 3)$, and $(3, \infty)$


5. Test the sign of each interval

- $(-\infty, 2)$ : positive
- $(2, 3)$ : negative
- $(3, \infty)$ : positive


5. Choose the intervals that satisfy the inequality

$(2,3)$ satisfy the inequality. The values $2$ and $3$ also satisfy the inequality, so they must be included. Therefore, the solution is $[2, 3]$.


### General Strategy for Quotient

Solving an inequality involving a quotient is similar to solving a polynomial inequality, except the solution needs to be checked for Division-by-Zero (undefined).

Given $\frac{1+x}{1-x} \geq 1$ :

1. Move all terms to one side.

$$
\begin{align}
  \frac{1+x}{1-x} &\geq 1 \\
  \frac{1+x}{1-x} -1 &\geq 0 \\
  \frac{1+x}{1-x} - \frac{1-x}{1-x} &\geq 0 \\
  \frac{2x}{1-x} &\geq 0
\end{align}
$$

> [!warning] Do not simplify the inequality by multiplying both sides by the value of the denominator (e.g. $1-x$).
> One of the rules for inequalities states that multiplying both sides of the inequality reverses the inequality. The value of the denominator can be either negative or positive, so it's impossible to tell whether the inequality needs to be reversed.


2. Identify the intervals

The factors on the left-hand side are $2x$ and $1-x$. The factors are zero when $x$ is $0$ and $1$ (disregard the Division-by-Zero for now). Thus, the intervals are $(-\infty, 0)$, $(0, 1)$, and $(1, \infty)$.


3. Test the sign of each interval

- $(-\infty, 0)$ : negative
- $(0, 1)$ : positive
- $(1, \infty)$ : negative


3. Choose the intervals that satisfy the inequality

The interval $(0,1)$ satisfy the inequality (of being greater than $0$). The value $0$ also satisfy the inequality (of being equal to $0$), but plugging $1$ causes the inequality to be undefined (by Division-By-Zero). Thus, the final solution is :

$$
[0, 1)
$$


## Absolute-Value Inequalities

