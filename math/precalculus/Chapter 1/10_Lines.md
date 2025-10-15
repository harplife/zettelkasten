# Lines

## Key Points

- The Slope of a Line
- Point-Slope Form of the Equation of a Line
- Slope-Intercept Form of the Equation of a Line
- Vertical and Horizontal Lines
- General Equation of a Line
- Parallel and Perpendicular Lines


## The Slope of a Line

The <mark class="hltr-trippy">Slope of a Line</mark> is the ratio of rise to run :

$$
slope = \frac{rise}{run}
$$

If a line lies in a coordinate plane, then the <mark class="hltr-trippy">Run</mark> is the change in the x-coordinate and the <mark class="hltr-trippy">Rise</mark> is the corresponding change in the y-coordinate between any two points on the line.

![[Pasted image 20251015133951.png]]

It is important to understand that the Slope of a line represents a <mark class="hltr-trippy">Rate of Change</mark> :

$$
m = \frac{\text{change in output}}{\text{change in input}} = \frac{\Delta y}{\Delta x}
$$

> [!important] The uppercase Delta $\Delta$ most commonly means "change".

The change in input is the difference of the two points along x-coordinate ($x_{2}-x_{1}$), and the change in output is the difference of the two points along y-coordinate ($y_{2}-y_{1}$). Thus, putting it together :

$$
m = \frac{y_{2}-y_{1}}{x_{2}-x_{1}}
$$

The geometric interpretation of the slope $m$ :
- If $m>0$, the line is rising
- If $m <0$, the line is falling
- If $m=0$, the line is horizontal

> [!warning] If the line is vertical, then there is **no slope** (undefined).


Example of finding the slope of a line, given $P(2,1)$ and $Q(8,5)$ :

$$
m = \frac{5-1}{8-2} = \frac{4}{6} = \frac{2}{3}
$$

> [!important] An equation with one degree (i.e. $y=x$) is called a Linear Equation. When a linear equation is graphed, a line is drawn on the coordinate plane. A line means that there is a slope to find.

While the slope can be calculated by plotting two points, it is also possible to find the slope based on the different forms of linear equations :

| Form                | Equation               | How to Find Slope                  |
| ------------------- | ---------------------- | ---------------------------------- |
| **Slope–Intercept** | $y = mx + b$           | $m$                                |
| **Point–Slope**     | $y - y_1 = m(x - x_1)$ | $m$                                |
| **Standard**        | $Ax + By = C$          | $m = -\frac{A}{B} \quad (B \ne 0)$ |
| **Vertical**        | $x = a$                | Undefined slope                    |
| **Horizontal**      | $y = b$                | $m=0$                              |


## Point-Slope Form of the Equation of a Line

Given two points, the slope of the line is $m = \frac{y_{2}-y_{1}}{x_{2}-x_{1}}$. This equation can be rewritten in the <mark class="hltr-trippy">Point-Slope Form</mark> :

$$
y_{2}-y_{1} = m(x_{2}-x_{1})
$$

This form is useful when only the coordinate of a point and the value of the slope is given. For example, an equation of the line through the point $(1-,3)$ with slope $-\frac{1}{2}$ :

$$
\begin{align}
  y+3 &= -\frac{1}{2}(x-1) \\
  2y + 6 &= -x+1 \\
  x + 2y + 5 &= 0
\end{align}
$$


## Slope-Intercept Form of the Equation of a Line

Suppose a non-vertical line has slope $m$ and y-intercept $b$.

![[Pasted image 20251015151233.png| center | 300]]

This means that the line intersects the y-axis at the point $(0, b)$, so the point-slope form of the equation of the line, with $x=0$ and $y=b$, becomes :

$$
y-b=m(x-0)
$$

This simplifies to $y=mx+b$, which is called the <mark class="hltr-trippy">Slope-Intercept Form</mark> of the equation of a line.

> [!example]- Find an equation of the line with slope $3$ and y-intercept $-2$.
> Answer : $y=3x-2$

> [!example]- Find the slope and y-intercept of the line $3y-2x=1$
> $$
> \begin{align}
>   3y-2x &= 1 \\
>   3y &= 2x+1 \\
>   y &= \frac{2}{3}x+\frac{1}{3}
> \end{align}
> $$
> 
> Answer : Slope $\frac{2}{3}$, y-intercept $\frac{1}{3}$


## Vertical and Horizontal Lines

When a line is horizontal, its slope $m=0$, so its equation is $y=b$ where $b$ is the y-intercept.

A vertical line does not have a slope, but its equation can be written as $x=a$, where $a$ is the x-intercept.


## General Equation of a Line (Standard Form)

A <mark class="hltr-trippy">Linear Equation</mark> in the variables $x$ and $y$ is an equation of the form

$$
Ax + By + C = 0
$$

where $A$, $B$, and $C$ are constants and $A$ and $B$ are not *both* $0$.

When a non-vertical line has the equation $y=mx+b$, it can be rewritten as $-mx+y-b=0$, which is a linear equation with $A=-m$, $B=1$, and $C=-b$.

A vertical line has the equation $x=a$ (or $x-a=0$), which is a linear equation with $A=1$, $B=0$, and $C=-a$.

A linear equation can be rewritten in the Slope-Intercept Form, if $B \neq 0$:

$$
y = -\frac{A}{B}x - \frac{C}{B}
$$

In this form, slope $m=-\frac{A}{B}$ and y-intercept $b=-\frac{C}{B}$.


> [!warning] The general (or standard) form of a linear equation can be written as either $Ax+By+C=0$ or $Ax+By=C$.
> Both are equivalent, and each version of the form is used in different contexts.

> [!important] The graph of every linear equation is a line. Conversely, every line is the graph of a linear equation.

> [!important] Easiest way to graph a linear equation is to plot two points at intercepts; one point at x-intercept and the other at y-intercept.


## Parallel and Perpendicular Lines

Two non-vertical lines are **parallel** if and only if they have the same slope.

Two lines with slopes $m_{1}$ and $m_{2}$ are **perpendicular** if and only if their slopes are **negative reciprocals**. In other words :

$$
m_{1}m_{2}=-1 \quad or \quad m_{2}=-\frac{1}{m_{1}}
$$

> [!important] A **multiplicative inverse** or **reciprocal** for a number $x$, denoted by $\frac{1}{x}$ or $x^{-1}$, is a number which when multiplied by $x$ yields the multiplicative identity $1$.


