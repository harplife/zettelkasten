# Geometric Calculus with Houdini

## Vector Operations


## Line


## Plane



## Conic Surfaces



## Quadric Surfaces


![[Quadric Surfaces Reference Chart.png]]

Implicit equation of quadric surfaces are given in Calculus 3 class like the above image. I find it rather difficult to see the relationship between these surfaces with those implicit equations. In fact, it is only after I've played around with the equations in Houdini that I've found out how a shape can turn into other shapes.

---
The full general implicit equation for a quadric surface in 3D (second-degree polynomial equation):

$$
Ax^2 + By^2 + Cz^2 + Dxy + Exz + Fyz + Gx + Hy + Iz + J = 0
$$

---

I like to think all quadric surfaces begin with an Ellipsoid:
$$
Ax^2 + By^2 + Cz^2 + J = 0
$$

Where:
- $A>0$ (e.g. 1)
- $B>0$ (e.g. 1)
- $C>0$ (e.g. 1)
- $J<0$ (e.g. -1)

Note that the equation above is not like the standard equation. The coefficients are variables that I can control, and whatever values I put in them are equivalent to whatever the standard equation says that they are. It'll make more sense later on.
- It is important that the opposite side remains $0$ because it basically defines the surface as where the function equals zero (iso-surface).

---
If coefficients $A=B=C$, then a <mark class="hltr-trippy">Sphere</mark> is generated. Note:
- Increasing the magnitude of $J$ it simply increases the size of the sphere because $d=r^2$.
	- If the values of $a,b,c$ are increased at the same rate while $d$ remains the same, the size of the sphere decreases. It is as if the radius is divided by the multiplicative factor.
- As long as $a=b=c$ and the signs $(-/+)$ match across all coefficients, you get a sphere.

![[Pasted image 20261020120340.png | center | 300]]

---
If $a,b,c$ becomes disproportionate (values differ), then we get an <mark class="hltr-trippy">Ellipsoid</mark>.
- **Oblate Spheroid**: As one of $a,b,c$ becomes relatively larger than the others, the side that the coefficient belongs to (e.g. $b$ affects $y$) becomes thinner. For example, if $b>a=c$, the sides of the ellipsoid that's on y-axis becomes thinner. It's difficult to tell with image alone, but imagine a thick, puffy pancake.![[Pasted image 20261020120414.png | center | 300]]
- **Prolate Spheroid**: Interestingly, if one of $a,b,c$ becomes relatively smaller than the others (but above zero), the side that the coefficient belongs to becomes elongated; it takes on a football-like shape. This reflects the standard equation, because any value between $0$ and $1$ is pretty much fraction.
  ![[Pasted image 20261020120948.png | center | 300]]
- **Triaxial Ellipsoid**: If all $a,b,c$ are different, then it's just a squished football shape.

---
When one of the coefficients $a,b,c$ becomes smaller than the others and it approaches zero, the side (where the coefficient belongs to) becomes infinitely elongated until the shape becomes a <mark class="hltr-trippy">Cylinder</mark>.
- #todo It will be a better visualization as a gif![[Pasted image 20261020121818.png | center | 300]]
- It remains the same that either decreasing the other two sides or increasing $d$ affects the radius.
- The signs still have to match.
- When $b=0$, then the equation becomes $ax^2 + cz^2 -d = 0$. It is basically an equation of a circle (in 3D, extended infinitely along y-axis).

---
As one of the coefficients $a,b,c$ becomes even smaller past zero (negative), we then get a <mark class="hltr-trippy">Hyperboloid of One Sheet</mark>:
- ![[Pasted image 20261020122757.png | center | 300]]
- Note that $d=1$ has kept the "circle" on xz-plane to remain constant with the same radius. This means that any change to $b$ reflects how a circle along $z$ axis behaves.
	- #todo not really sure how it works though. If $c$ positive, it gets flatter. As $c$ approaches zero, the surface gets elongated until it becomes a cylinder. Then, when $c$ is negative, it becomes a hyperboloid. It's like one way, the "circle" along z is smaller, whereas the other way, it's bigger.