# 1.9 The Coordinate Plane; Graphs of Equations; Circles

## Key Points

- The Coordinate Plane
- The Distance and Midpoint Formulas
- Graphs of Equations in Two Variables
- Intercepts
- Circles
- Symmetry

## The Coordinate Plane

The <mark class="hltr-trippy">Coordinate Plane</mark> (aka **Cartesian Plane**) is a flat, two-dimensional surface used to graphically represent relationships between two variables (usually $x$ and $y$).

> [!note] The Cartesian Plane was named after the French mathematician Rene Descartes (Latinized as Cartesius), who (in 17th century) developed the idea of representing algebraic equations as geometric curves.
> Another Frenchman, Pierre Fermat, also invented the principles of coordinate geometry at the same time.

The Cartesian plane consists of two number lines that intersect at right angles :
- The horizontal line is the x-axis, which represents the independent variable (the input).
- The vertical line is the y-axis, which represents the dependent variable (the output).

The point where these two axes intersect is called the origin, denoted by $O(0,0)$.

Each point in the Cartesian plane is represented by an ordered pair $(x, y)$, where :
- $x$ tells how far to move horizontally, left if negative and right if positive.
- $x$ tells how far to move vertically, up if positive and down if negative.

The axes divide the plane into four regions called <mark class="hltr-trippy">Quadrants</mark>, labeled counter-clockwise :

|Quadrant|Sign of (x)|Sign of (y)|
|:--|:--|:--|
|**I**|+|+|
|**II**|−|+|
|**III**|−|−|
|**IV**|+|−|

![[Pasted image 20251009081423.png|300]]

The Cartesian plane allows the visualization of algebraic equations as geometric figures :

| Equation type     | Shape on the Cartesian plane |
| :---------------- | :--------------------------- |
| $y = 2x + 1$      | Straight line                |
| $x^2 + y^2 = 9$   | Circle                       |
| $y = x^2$         | Parabola                     |
| $y = \frac{1}{x}$ | Hyperbola                    |


## The Distance and Midpoint Formulas

The distance between two points $A(x_{1}, y_{1})$ and $B(x_{2}, y_{2})$ in the plane can be described as $d(A, B)$, which can be solved by using the Pythagorean Theorem :

$$
d(A, B) = \sqrt{ (x_{2}-x_{1})^2 + (y_{2}-y_{1})^2 }
$$

![[Pasted image 20251009084347.png| center | 500]]


The point that bisects the line segment that connects the point $A(x_{1}, y_{1})$ and $B(x_{2}, y_{2})$ is the midpoint $M(x, y)$, whose coordinate can by found by averaging the x- and y-coordinates of $A$ and $B$ :

$$
M(x,y) = \left( \frac{x_{1}+x_{2}}{2}, \frac{y_{1}+y_{2}}{2} \right)
$$

![[Pasted image 20251009085334.png | center | 500]]


## Graphs of Equations in Two Variables

An **equation in two variables** (e.g. $y = x^2 + 1$) expresses a relationship between two quantities. Also, it represents a **curve** in the plane.

A point $(x, y)$ is said to **satisfy** the equation if it makes the equation true when the values for $x$ and $y$ are substituted into the equation.
- For example, the point $(3,10)$ satisfies the equation $y=x^2+1$ because $10 = 3^2+1$. However, the point $(1,3)$ does not, because $3 \neq 1^2 +1$.

The <mark class="hltr-trippy">Graph</mark> of an equation in $x$ and $y$ is the set of all points $(x, y)$ in the Cartesian plane that satisfy the equation.
- The graph of an equation is a curve, so to graph an equation, many points are plotted then connected by a smooth curve.


## Intercepts

An <mark class="hltr-trippy">Intercept</mark> is a point where a graph intersects an axis.
- **x-intercepts** are the points where a graph intersects the x-axis.
- **y-intercepts** are the points where a graph intersects the y-axis.

x-intercepts can be found by setting $y=0$ and then solving for $x$.

y-intercepts can be found by setting $x=0$ and then solving for $y$.


## Circles

The <mark class="hltr-trippy">Circle</mark> is defined as the set of all points $P(x,y)$ whose distance from the center $C(h, k)$ is $r$. In other words, $P$ is on the circle if and only if $d(P,C)=r$.

An equation of the circle with center $(h,k)$ and radius $r>0$ is :

$$
(x-h)^2 + (y-k)^2 = r^2
$$

> [!important] The equation above is the **Standard Form** for the equation of the circle.
> It is derived from the Pythagorean theorem $\sqrt{ (x-h)^2+(y-k)^2 } = r$.

If the center of the circle is the origin $(0,0)$, then the equation is 

$$
x^2 + y^2 = r^2
$$

> [!important] At first glance, the circle is confusing because it seems like there's more than two variables. However, $r$ is a constant which stays the same no matter the changes in $x$ or $y$.
> Also, $h$ describes the horizontal shift (from the center) and $k$ is the vertical shift.


## Symmetry

