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


### Ellipsoid Transformations

![[Sphere_to_Hyperboloid_One_Sheet_T.mp4| Sphere to Hyperboloid of One Sheet | center]]

Given this equation:
$$
Ax^2 + By^2 + Cz^2 - 1 = 0
$$
If the value of $B$ is set to change from $1$ to $-1$ over time, we get a surface that changes from a sphere ($B=1$) to cylinder ($B=0$) and then to hyperboloid of one sheet ($B=1$).

---

![[Sphere_to_Hyperboloid_Two_Sheets_T.mp4| Sphere to Hyperboloid of Two Sheets | Center]]

Given this equation:
$$
Ax^2 + By^2 + Cz^2 - 1 = 0
$$
If the value of both $A$ and $B$ are set to change from $1$ to $-1$ over time, we get a surface that changes from a sphere ($B=1$) to cylinder ($B=0$) and then to hyperboloid of one sheet ($B=1$).

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

Basically:
$$
x^2 + y^2 + z^2 - 1 = 0
$$

Note that the equation above is not like the standard equation. The coefficients are variables that I can control, and whatever values I put in them are equivalent to whatever the standard equation says that they are.
- It is important that the opposite side remains $0$ because it basically defines the surface as where the function equals zero (iso-surface).

---
If coefficients $A=B=C$, then a <mark class="hltr-trippy">Sphere</mark> is generated. Note:
- Increasing the magnitude of $J$ simply increases the size of the sphere because $J=r^2$.
	- If the values of $A,B,C$ are increased at the same rate while $J$ remains the same, the size of the sphere decreases.
		- If $A,B,C$ gets bigger and $J$ remains constant, the sphere gets smaller.
- As long as $A=B=C$ and the signs $(-/+)$ match across all coefficients, you get a sphere.

![[Pasted image 20261020120340.png | center | 300]]

---
If $A,B,C$ becomes disproportionate (values differ), then we get an <mark class="hltr-trippy">Ellipsoid</mark>.
- **Oblate Spheroid**: As one of $A,B,C$ becomes relatively larger than the others, the side that the coefficient belongs to (e.g. $B$ affects y coordinates) becomes thinner. For example, if $B>A,C$, the sides of the ellipsoid that's on y-axis becomes thinner. It's difficult to tell with image alone, but imagine a thick, puffy pancake.![[Pasted image 20261020120414.png | center | 300]]
- **Prolate Spheroid**: Interestingly, if one of $A,B,C$ becomes relatively smaller than the others (but above zero), the side that the coefficient belongs to becomes elongated; it takes on a football-like shape. This reflects the standard equation, because any value between $0$ and $1$ is pretty much fraction.
  ![[Pasted image 20261020120948.png | center | 300]]
- **Triaxial Ellipsoid**: If all $A,B,C$ are different, then it's just a squished football shape.

---
When one of the coefficients $A,B,C$ becomes smaller than the others and it approaches zero, the side (where the coefficient belongs to) becomes infinitely elongated until the shape becomes a <mark class="hltr-trippy">Cylinder</mark>.
- To be exact, when two coefficients are the same (e.g. $A=C$), the surface is a **Circular Cylinder**.
- #todo It will be a better visualization as a gif![[Pasted image 20261020121818.png | center | 300]]
- It remains the same that either decreasing the other two sides or increasing the magnitude of $J$ affects the radius.
- The signs still have to match.
- When $B=0$, then the equation becomes $Ax^2 + Cz^2 +J = 0$. It is basically an equation of a circle (in 3D, extended infinitely along y-axis).


---
As one of the coefficients $A,B,C$ becomes even smaller past zero (e.g. $B<0$), we then get a <mark class="hltr-trippy">Hyperboloid of One Sheet</mark>:
- ![[Pasted image 20261020122757.png | center | 300]]
- Note that $J=1$ has kept the "circle" on xz-plane to remain constant with the same radius. This means that any change to $B$ reflects how a circle along y-axis behaves.

---
So far, for a sphere (ellipsoid), cylinder, and hyperboloid of one sheet, $J$ has remained a negative constant.

If $J=0$,
- Sphere becomes a dot $x = z = y$
- Cylinder becomes a line along y-axis $x = z$ (omitted the square roots)
- Hyperboloid of One Sheet becomes an <mark class="hltr-trippy">Elliptic Cone</mark>:
  ![[Pasted image 20261023171930.png | center | 300]]

If $J>0$,
- Both Sphere and Cylinder becomes a degenerate, indefinite surface (totally empty)
- Hyperboloid of One Sheet becomes a <mark class="hltr-trippy">Hyperboloid of Two Sheets</mark>:
  ![[Pasted image 20261023172407.png | center | 300]]

When the magnitude of the coefficients are all $1$ and one of the coefficients $A,B,C$ faces a negative direction, the positive value of $J$ seems to represent the distance from the origin to one side of the split surface.
- The closest point on each sheet to the origin is called a <mark class="hltr-trippy">Vertex</mark>.
- The distance from the origin to a vertex is called the <mark class="hltr-trippy">Semi-Transverse Axis Length</mark>.


### Hyperbolic Cylinder Transformations

![[Hyperbolic_Cylinder_Transforms.mp4 | center]]

---
Given a surface $Ax^2 + By^2 + Cz^2 + J = 0$ where:
- $A>0$ expressed as $i$
- $B=0$ expressed as $j$
- $C<0$ expressed as $k$
- $J<0$ (e.g. $-1$) expressed as $d$

This is a <mark class="hltr-trippy">Hyperbolic Cylinder</mark>. It basically looks like two bent planes that are symmetric at y-axis.

![[Pasted image 20261023183614.png | center | 300]]

What's interesting about this shape is that it's can become two different surfaces just by changing the value (and the sign) of $B$.

When $B>0$, the surface becomes a *Hyperboloid of One Sheet* that opens along z-axis:
$$
ix^2 + jy^2 - kz^2 - d = 0
$$

![[Pasted image 20261023184252.png | center | 300]]

When $B<0$, the surface becomes a *Hyperboloid of Two Sheets* that opens along x-axis:
$$
ix^2 - jy^2 - kz^2 - d = 0
$$

![[Pasted image 20261023184317.png | center | 300]]


### Parabolic Quadrics

![[Parabolic_Quadrics_Transforms.mp4 | center]]

---
Given a surface $Ax^2 + By^2 + Cz^2 + Gx + Hy + Iz+ J = 0$ where:
- $A>0$ (constant variable)
- $B>0$ (independent variable)
- $C=0$
- $G=H=0$
- $I<0$
- $J=0$

In other words:
$$
x^2 + y^2 - z = 0
$$

This is an <mark class="hltr-trippy">Elliptic Paraboloid</mark> with one end opening up towards positive z-axis.
- In this case, we have two coefficients for *quadric terms* and one coefficient for a *linear term*.
- The sign of $I$ decides the direction at which the surface opens towards; $-I$ points to positive z-axis.
- As long as $J=0$, it sits on the origin.

![[Pasted image 20261025110117.png | Elliptic Paraboloid | center | 300]]
From here, we can change the value of $B$ to change to different surfaces.

---
If $B=0$, the equation becomes this:
$$
x^2 - z = 0
$$

Which is basically an equation of parabola:
$$
y = x^2
$$

Extended in 3D space, what we get is a <mark class="hltr-trippy">Parabolic Cylinder</mark> which opens up towards positive z-axis.
- In this case, two coefficients for quadric terms are *missing*, which can be seen as the surface opening up in two different directions.
![[Pasted image 20261025110310.png | Parabolic Cylinder | center | 300]]

---
If $B<0$, the equation becomes this:
$$
x^2 - y^2 - z = 0
$$

This is a <mark class="hltr-trippy">Hyperbolic Paraboloid</mark> (aka **Saddle**).
- Unlike Elliptic Paraboloid or Hyperboloids, this surface does not have just one opening axis; it has **two opposing principal directions of curvature**. In this example, XZ trace shows a parabola opening upward to positive z-axis, and YZ trace shows a parabola opening downwards to negative z-axis.

![[Pasted image 20261025111800.png | Hyperbolic Paraboloid | center | 300]]





### Anisotropic Scaling

Given a surface $Ax^2 + By^2 + Cz^2 + J = 0$ where:
- $A=C$ and positive real numbers
- $J<0$
- $B>0$

This is an **Ellipsoid**, where #todo the surface is said to be **Closed** and **Bounded**.

The behavior where the surface becomes compressed or stretched is called <mark class="hltr-trippy">Anisotropic Scaling</mark>; specifically, it is a geometric transformation that enlarges or shrinks an object by different scale factors along different axes, which changes its original shape.
- (Compare to) Isotropic Scaling which applies the exact same scale factor to all axes to preserve shape.

We can see that, by increasing $B$, the surface along y-axis becomes flatter (compressed). However, when $B$ is decreased (approaches zero), the surface along y-axis becomes elongated (stretched).

This can be mathematically explained:
$$
\begin{align}
& x^2 + By^2 + z^2 -1 = 0 \\
&\Rightarrow x^2 + z^2 = 1 - By^2 \geq 0 \\
&\Rightarrow \left| y \right| \leq \frac{1}{\sqrt{ B }}
\end{align}
$$

When $B$ increases, the maximum possible displacement along y-axis decreases.


### Degeneracy

<mark class="hltr-trippy">Degeneracy</mark> is the critical case where a coefficient reaches zero, causing the quadratic form to lose rank.
- Losing a rank pretty much means losing a dimension.

Given a surface $Ax^2 + By^2 + Cz^2 + J = 0$ where:
- $A=C$ and positive real numbers
- $B=0$
- $J<0$

This is a *Circular Cylinder*, which is said to be a **Degenerate Quadric**.
- It is also **Closed** and  **Unbounded**.


### Transverse/Opening Axis

Given a surface $Ax^2 + By^2 + Cz^2 + J = 0$ where:
- $A=C$ and positive real numbers
- $B<0$ expressed as $-k$ where $k>0$
- $J<0$

This is a *Hyperboloid of One Sheet*, where the surface is said to be **Closed** and **Unbounded**.

The equation of the surface can be rewritten so that it describes the radius:
$$
\begin{align}
&x^2 -ky^2 + z^2 = 1 \\
&\Rightarrow x^2 + z^2 = 1 + ky^2 \\
&\Rightarrow r^2 = 1 + ky^2 \\
&\Rightarrow r = \sqrt{ 1 + ky^2 }
\end{align}
$$

This means that, at any fixed y-coordinate, the horizontal cross-section is a circle with the radius:
$$
r(y) = \sqrt{ 1 + ky^2 }
$$

So the further along the Y direction, the larger the cross-section of the surface.

The axis along which the two sheets extend (in this case, y-axis) is called the <mark class="hltr-trippy">Opening Axis</mark>. It is the same as the axis passing through both vertices, which is called the <mark class="hltr-trippy">Transverse Axis</mark>.


### Topological Hole

For any quadric surface that has an opening (e.g. Cylinder, Hyperboloid of One Sheet), the hole itself is referred to as a <mark class="hltr-trippy">Topological Hole</mark> (or just "hole" simply) or a <mark class="hltr-trippy">Tunnel</mark>.
- For a Hyperboloid of One Sheet, the narrowest opening through the surface is called the <mark class="hltr-trippy">Throat</mark>. The cross-section of the throat is called the <mark class="hltr-trippy">Waist</mark>.


### Surface at Limits

#### Elliptic Cone to Plane

Given a surface $Ax^2 + By^2 + Cz^2 + J = 0$ where:
- $A=C$ and positive real numbers
- $B<0$ expressed as $-k$ where $k>0$
- $J=0$

This is an *Elliptic Cone*.

 As $B$ goes to $-\infty$, the open ends on either side of the y-axis becomes bigger and the surface overall becomes flatter; eventually, the surface becomes a plane. This can be verified by taking the limit as $k \to \infty$.
![[Pasted image 20261023180917.png | center | 300]]
The above image is the result of the following equation:
$$
x^2 -15000y^2 + z^2 = 0
$$

What started out as an elliptic cone looks like a single plane.


#### Cylinder to Two Planes

Given a surface $Ax^2 + By^2 + Cz^2 + J = 0$ where:
- $A=C$ and positive real numbers
- $B=0$
- $J<0$ (e.g. $-1$)

This is a *Circular Cylinder*.

When $C$ is no longer the same as $A$, it becomes an **Elliptic Cylinder** that becomes elongated along z-axis as $C$ goes to $0$. In fact, when $C=0$, the surface becomes **Two Planes** where the equation is:
$$
x^2 = 1
$$

In this case, $|J|$ describes the distance from the origin to the closest point on a plane.

![[Pasted image 20261023182711.png | center | 300]]