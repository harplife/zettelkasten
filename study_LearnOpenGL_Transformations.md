
# Transformations
- Because an object in a Graphics program is basically an array of data, it can be represented as a matrix; which means that all transformation in regards to an object involves some kind of matrix operations.

## Vectors
- A vector has a direction and a magnitude (aka strength or length).
- If a vector has 2 dimensions, it represents a direction on a plane. When it has 3, it can represent any direction in 3D world.
- Generally, a vector is described as a character symbol with a little bar on top, like $\bar{v}$.
- Displaying a vector in a formula:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\bar{v} = \mymat{x\\y\\z}
$$

- When the vector's origin is set to `(0, 0, 0)`, then the point has both a direction and a position which makes it a **Position Vector**.

## Scalar Vector Operations
- A scalar is a single digit. When adding/subtracting/multiplying or dividing a vector with a scalar, the operation is applied to each element of the vector.
- A scalar addition would look like this:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\mymat{1\\2\\3} + x \rightarrow \mymat{1\\2\\3} + \mymat{x\\x\\x} = \mymat{1+x\\2+x\\3+x}
$$

## Vector Negation
- Negating a vector (flipping its positive/negative sign) results in a vector in the reversed direction. It is equivalent to a scalar multiplication with `-1`.

## Component-wise Operations
- Addition/subtraction of two vectors is defined as component-wise addition/subtraction, where each component of one vector is added/subtracted to the same component of the other vector. For example:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\begin{gathered}
\bar{v} = \mymat{1\\2\\3}, \bar{k} = \mymat{4\\5\\6}\\
\bar{v} + \bar{k} \rightarrow \mymat{1+4\\2+5\\3+6}
=
\mymat{5\\7\\9}
\end{gathered}
$$

- For vectors $\bar{v}=(4,2)$ and $\bar{k}=(1,2)$, vector addition $\bar{v}+\bar{k}$ can be visualized like this:
  ![[vectors_addition.png]]

## Magnitude/Length
- In order to calculate the magnitude (aka length) of a vector, 
- A vector forms a triangle when its individual `x` and `y` component as two sides of a triangle:
  ![[vectors_triangle.png]]
- the **Pythagoras Theorem** can be used to calculate the magnitude (which is represented as the hypotenuse of the triangle):

$$
||\bar{v}|| = \sqrt{x^2 + y^2}
$$

- The magnitude of vector $\bar{v} = (4, 2)$ can be calculated like so:

$$
||\bar{v}|| = \sqrt{4^2 + 2^2} = \sqrt{20} = 4.47
$$

## Unit Vector
- **Unit Vector** is a special type of vector that has magnitude of $1$, which is to say that it is a vector used to denote direction.
- Unit Vector can be represented as a letter with a hat : $\hat{n}$
- **Normalizing** a vector is a process of converting a vector into a Unit Vector, which is done by dividing the vector by its own magnitude:

$$
\hat{n} = \frac{\bar{v}}{||v||}
$$

- Normalized vectors are widely used in computer graphics for various purposes:
	- Lighting and Reflections
	- Surface Normals
	- Force Directions
	- Data Preprocessing
	- Bump Mapping and Normal Mapping
	- Transformations

## Vector Multiplications
- There are two types of vector multiplications - Dot Product and Cross Product.

### Dot Product
- Dot Product is denoted as $\bar{v} \cdot \bar{k}$
- The dot product of two vectors is equal to the product of their magnitudes and the cosine of the angle $\theta$ between them:

$$
\bar{v}\cdot\bar{k} = ||\bar{v}||\cdot||\bar{k}||\cdot\cos{\theta}
$$

- Above formula gets reduced down to the cosine of the angle $\theta$ between them when both vectors are unit vectors (length of 1):

$$
\hat{v}\cdot\hat{k} = 1\cdot1\cdot\cos{\theta} = \cos{\theta}
$$

- Above formula is useful to test if the two vectors are Orthogonal or Parallel to each other.
	- Orthogonal : the angle between the two vectors is 90 degrees. Cosine of 90 degrees is 1.
	- Parallel : the angle between the two vectors is 0 degrees. Cosine of 0 degrees is 0.
	- Opposite : the angle between the two vectors is 180 degrees. Cosine of 180 degrees is -1.
- The cosine factor is crucial because it captures the directional relationship between the two vectors.
- The dot product is a component-wise multiplication where each component is multiplied by its corresponding component and the results are all added together. In a way, it is a matrix-vertex multiplication.
- Example of the dot product of two vectors when they are both unit vectors:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\begin{gathered}
\bar{v} = \mymat{0.6\\-0.8\\0}, \bar{k} = \mymat{0\\1\\0}\\
\bar{v} \cdot \bar{k} \rightarrow \mymat{0.6 & -0.8 & 0} \times \mymat{0 \\ 1 \\ 0}\\
= (0.6*0) + (-0.8*1) + (0*0)\\
= -0.8
\end{gathered}
$$

- To calculate the degree between both these  unit vectors, the inverse of the cosine function $\arccos$ ($\cos^{-1}$) is used.
	- For above example, $\arccos{(-0.8)} = 143.1$
- The Dot Product has several important applications in Computer Graphics:
	- **Cosine of the Angle Between Two Vectors**
	- **Projection** : The dot product can be used to project one vector onto another. This is useful in various algorithms, such as calculating the reflection of a light ray off a surface.
	- **Surface Normal and Lighting** : The dot product is used in lighting calculations. For instance, in the Phong lighting model, the dot product between the light direction and the surface normal vector is used to determine the intensity of the light on the surface.
	- **Backface Culling** : The backface culling is an optimization technique that avoids rendering polygons facing away from the viewer. This is determined using the dot product between the view direction and the polygon's normal.
	- **Collision Detection** : The dot product can be used to determine whether two objects are moving towards each other.

### Cross Product
- Cross Product is denoted as $\bar{v}\times\bar{k}$
- The Cross Product is only defined in 3D space. It takes two non-parallel vectors as input and produces a third vector that is orthogonal to both the input vectors.
	- ![[vectors_crossproduct.png]]
	- The direction of the resulting vector will always follow the right-hand rule.
	  ![[Pasted image 20240701162831.png|150]]
- The Cross Product is computed as follows:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\begin{gathered}
\bar{v} = \mymat{v_x \\ v_y \\ v_z}, \bar{w} = \mymat{w_x \\ w_y \\ w_z}\\
\bar{v}\times\bar{w} \rightarrow \mymat{v_x\\v_y\\v_z} \times \mymat{w_x \\ w_y \\ w_z}
= \mymat{v_yw_z-w_yv_z \\ v_zw_x-w_zv_x \\ v_xw_y - w_xv_y}
\end{gathered}
$$

- (example) given that $\bar{v}$ is a vector that sits along Z-axis and $\bar{w}$ is a vector that sits along Y-axis, the cross product of these two vectors is a vector that sits along X-axis in a negative direction:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\begin{gathered}
\bar{v} = \mymat{0\\0\\2}, \bar{w} = \mymat{0\\2\\0}\\
\bar{v}\times\bar{w} \rightarrow \mymat{0\\0\\2} \times \mymat{0\\2\\0}
= \mymat{-4\\0\\0}
\end{gathered}
$$

- The Cross Product has several important applications in Computer Graphics:
	- **Calculating Surface Normals** : The cross product is used to calculate the normal of a surface. Given two vectors that lie on the surface (for example, two sides of a triangle), the cross product of these vectors gives a vector that is perpendicular to the surface. This is particularly useful in lighting calculations, where the normal of a surface determines how it reflects light.
	- **Calculating the Area of a Parallelogram** : The magnitude of the cross product of two vectors gives the area of the parallelogram that the vectors span. This can be useful in collision detection and physics simulations.
	- **Determining the Orientation of Points** : In computational geometry, the cross product can help determine the clockwise or counterclockwise orientation of a set of points.
	- **Computing Torque** : In physics-based animation and game physics, the cross product is used to compute torque, which is a measure of the force that can cause an object to rotate about an axis.

### Determinant (Personal Note)
- In Linear Algebra, the Determinant is a special number that can be calculated from a square matrix (i.e. 2x2 matrix, 3x3, etc). It is denoted as $det(A)$ or $|A|$.
- The Determinant of a 2x2 matrix is computed as follows:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\begin{gathered}
A = \mymat{a & b\\c & d}\\
det(A) = ad - bc
\end{gathered}
$$

- ![[Pasted image 20240701161459.png | 3blue1brown Essence of Linear Algebra]]
- The Cross Product is related to Determinant in a way:
	- ![[Pasted image 20240701173920.png]]
	- Refer to [Cross products in the light of linear transformation | Essence of Linear Algebra | 3Blue1Brown](https://youtu.be/BaM7OCEm3G0?si=ruhkTtVkDCGa9aPI) for more info.

## Matrices
- A **Matrix** is a rectangular array of numbers/symbols/expressions.
- Each individual item in a matrix is called an **element** of the matrix.
- Matrices are indexed by $(i, j)$ where $i$ is the row and $j$ is the column.
- When a matrix is referred to as a 2x3 (2 by 3) matrix, it means it has 2 rows and 3 columns.

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\begin{gathered}
A = \mymat{1&2&3\\4&5&6}\\
\end{gathered}
$$

### Addition and Subtraction
- Matrix addition and subtraction between two matrices is done on a per-element basis.

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\begin{gathered}
\mymat{1&2\\3&4} + \mymat{5&6\\7&8} = \mymat{6&8\\10&12}
\end{gathered}
$$

### Scalar Products
- A matrix-scalar product multiplies each element of the matrix by a scalar.

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\begin{gathered}
2\cdot\mymat{1&2\\3&4} = \mymat{2&4\\6&8}
\end{gathered}
$$

### Matrix-Matrix Multiplication
- Matrix multiplication basically means to follow a set of pre-defined rules under few restrictions:
	- Each row of the left-hand matrix is matched with each column of the right-hand matrix, where multiplication of each element is added up and placed at the corresponding row-column of the resulting matrix.
	  ![[Matrix_multiplication_diagram_2.svg]]
	- The number of columns on the left-hand side matrix must equal to the number of rows on the right-hand matrix.
	- Matrix multiplication is not commutative. $A\cdot B \neq B \cdot A$
- Example of a matrix multiplication of 3x3 matrices:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\begin{gathered}
\mymat{A_1&A_2&A_3\\A_4&A_5&A_6\\A_7&A_8&A_9} \cdot \mymat{B_1&B_2&B_3\\B_4&B_5&B_6\\B_7&B_8&B_9}\\
= \mymat{
A_1B_1 + A_2B_4 + A_3B_7 & A_1B_2 + A_2B_5 + A_3B_8 & A_1B_3 + A_2B_6 + A_3B_9 \\
A_4B_1 + A_5B_4 + A_6B_7 & A_4B_2 + A_5B_5 + A_6B_8 & A_4B_3 + A_5B_6 + A_6B_9 \\
A_7B_1 + A_8B_4 + A_9B_7 & A_7B_2 + A_8B_5 + A_9B_8 & A_7B_3 + A_8B_6 + A_9B_9 
}
\end{gathered}
$$

## Matrix-Vector Multiplication
- A vector is essentially a Nx1 matrix where N is the number of components in the vector (aka N-dimensional vector).
- The multiplication between a vector and a matrix is a simple matrix multiplication, as long as the number of rows in the vector matches with the number of columns in the matrix.
- Matrix-Vector Multiplication is important because multiplying a vector with a matrix means *transforming* that vector. Due to the nature of computer graphics, a vector is often used to represent various attributes of a vertex (position, color, etc) and a matrix is often used to apply some kind of change to those attributes.
- Most of the transformations discussed further on will describe 3D transformations. The transformation matrix is described in 4D space. The fourth element $w$ is used as *padding*, which is necessary for certain transforms (such as translation). Search for "Homogeneous Coordinates" for more info.

>[!important]
>In computer graphics, implementing translation with matrix multiplication instead of vector addition has several advantages:
>1. **Uniformity**: Using matrices allows us to represent different types of transformations (like translation, scaling, rotation, and even perspective projection) in a uniform way. This means we can combine multiple transformations into a single matrix and apply them all at once to a set of points or a whole scene.
>2. **Efficiency**: When multiple transformations need to be applied, it's more efficient to combine them into one matrix and perform a single matrix multiplication, rather than applying each transformation individually.
>3. **Homogeneous Coordinates**: Matrix transformations work well with homogeneous coordinates, which are commonly used in 3D graphics. Homogeneous coordinates allow us to represent 3D transformations and even projective transformations as 4x4 matrices. This wouldn't be possible with simple vector addition.
>4. **Hardware Optimization**: Graphics hardware is often optimized for matrix operations, making them faster than equivalent operations implemented separately.
>5. **Interpolation**: Matrices are also useful for interpolating between transformations, which is a common operation in animation.
>
>So, while vector addition is a simpler operation and works fine for simple translations, using matrix multiplication for transformations provides greater flexibility, efficiency, and compatibility with graphics hardware and software.

### Identity Matrix
- Simplest form of transformation matrix is the **Identity Matrix**, where multiplying a vector by the matrix applies no changes to the vector and therefore the result is the same vector.

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\begin{gathered}
\mymat{1&0&0&0\\0&1&0&0\\0&0&1&0\\0&0&0&1} \cdot \mymat{1\\2\\3\\4} = \mymat{1\\2\\3\\4}
\end{gathered}
$$

- The Identity Matrix is usually a starting point for generating other transformation matrices. It is also a useful matrix for proving theorems and solving linear equations.

### Scaling
- Scaling is a type of transformation where a vector is expanded/reduced along one or more axis.
- A scaling matrix on any vector $(x, y, z)$ is defined as:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\mymat{S_x & 0 & 0 & 0 \\ 0 & S_y & 0 & 0 \\ 0 & 0 & S_z & 0 \\ 0&0&0&1}
\cdot
\mymat{x\\y\\z\\1}
=
\mymat{S_x \cdot x \\ S_y \cdot y \\ S_z \cdot z \\ 1}
$$

- For example, scaling a vector $\bar{v}=(2,3,0)$ so that it is expanded by 2 along x-axis and reduced by 2 along y-axis looks like this (ignoring $w$ for now):

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\begin{gather}
\mymat{2&0&0\\0&0.5&0\\0&0&1} \cdot \mymat{2\\3\\0}
=
\mymat{4\\1.5\\0}
\end{gather}
$$

- When the scaling factor is the same for each axis, it is referred to as **Uniform Scale**. If not, it is referred to as **Non-Uniform Scale**.

### Translation
- Translation is a type of transformation where a vector is moved along one or more axis. This can be achieved with a simple vector addition, but it is more common to implement this with a matrix multiplication.
- A translation matrix on any vector $(x, y, z)$ is defined as:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\mymat{
1&0&0&T_x\\
0&1&0&T_y\\
0&0&1&T_z\\
0&0&0&1
}
\cdot
\mymat{x\\y\\z\\1}
=
\mymat{x+T_x\\y+T_y\\z+T_z\\1}
$$

- Translation can be thought of as "Applying shear into higher dimension, and then projecting the result back to the original dimension". Refer to [The True Power of the Matrix | Computerphile](https://youtu.be/vQ60rFwh2ig?si=MCvDV96yO8LP6OOV).

### Rotation
- Rotation is a type of transformation where a vector is moved along a circular path as defined by an angle, a rotation axis, and the center of rotation.
- Rotation around the X-axis given any vector $(x, y, z)$:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\mymat{
1 & 0 & 0 & 0\\
0 & \cos\theta & -\sin\theta & 0\\
0 & \sin\theta & \cos\theta & 0\\
0&0&0&1
}
\cdot
\mymat{x\\y\\z\\1}
=
\mymat{
x \\
\cos\theta \cdot y - \sin\theta \cdot z\\
\sin\theta \cdot y + \cos\theta \cdot z\\
1
}
$$

- Rotation around the Y-axis given any vector $(x, y, z)$:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\mymat{
\cos\theta & 0 & \sin\theta & 0\\
0 & 1 & 0 & 0\\
-\sin\theta & 0 & \cos\theta & 0\\
0&0&0&1
}
\cdot
\mymat{x\\y\\z\\1}
=
\mymat{
\cos\theta \cdot x + \sin\theta \cdot z\\
y\\
-\sin\theta \cdot x + \cos\theta \cdot z\\
1
}
$$

- Rotation around the Z-axis given any vector $(x, y, z)$:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\mymat{
\cos\theta & -\sin\theta & 0 & 0\\
\sin\theta & \cos\theta & 0 & 0\\
0 & 0 & 1 & 0\\
0&0&0&1
}
\cdot
\mymat{x\\y\\z\\1}
=
\mymat{
\cos\theta \cdot x - \sin\theta \cdot y\\
\sin\theta \cdot x + \cos\theta \cdot y\\
z\\
1
}
$$

- Although Matrix Multiplication allows for applying several transformations at the same time by combining matrices, it is not recommended to do so with rotations as it introduces a problem called Gimbal Lock.

### Combining Matrices
- One of the major advantages of using matrix for transformation comes from the fact that matrix transformations can be combined into one matrix, making it so that it only takes one transformation to apply multiple.
- Example of Translation + Scale:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\begin{gathered}
T_1 \cdot T_2 = T_3 \\
\mymat{1&0&0&1\\0&1&0&2\\0&0&1&3\\0&0&0&1} \cdot \mymat{2&0&0&0\\0&2&0&0\\0&0&2&0\\0&0&0&1}
=
\mymat{2&0&0&1\\0&2&0&2\\0&0&2&3\\0&0&0&1}\\
T_3(\bar{v}) = \mymat{2&0&0&1\\0&2&0&2\\0&0&2&3\\0&0&0&1}
\cdot \mymat{x\\y\\z\\1} = \mymat{2x+1\\2y+2\\2z+3\\1}
\end{gathered}
$$

- Note that matrix multiplication is not commutative, which means their order is important.
- It is advised to first do scaling operations, then rotations, and lastly translations when combining matrices. Otherwise, they may (negatively) affect each other.
	- For example, if translation is applied before scale, the translation matrix would also scale (which may not be an intended).

## Transformation In Practice
- OpenGL does not have any form of matrix or vector knowledge built in, so mathematics classes and functions have to be defined separately. It is best to use pre-made mathematics libraries such as GLM.

### GLM
- GLM (Open**GL M**athematics) is a header-only library that's specifically made for math operations for OpenGL.
- GLM can be downloaded from https://github.com/g-truc/glm (look for releases)
- GLM [Getting Started](https://github.com/g-truc/glm/blob/master/manual.md#section1)
- Once downloaded, copy & paste the root folder `glm` over to `includes` directory.
- Most of GLM's functionalities can be found in 3 header files:

```C++
#include <glm/glm.hpp>
#include <glm/gtc/matrix_transform.hpp>
#include <glm/gtc/type_ptr.hpp>
```

- Example of translation with GLM (should print out `2101`):

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\begin{gather}
\bar{v} = \mymat{1\\0\\0\\1},
T = \mymat{
1&0&0&1\\
0&1&0&1\\
0&0&1&0\\
0&0&0&1
}\\
T \cdot \bar{v} =
\mymat{
1&0&0&1\\
0&1&0&1\\
0&0&1&0\\
0&0&0&1
} \cdot \mymat{1\\0\\0\\1} =
\mymat{2\\1\\0\\1}
\end{gather}
$$

```C++
// vector pointing along x-axis
glm::vec4 vec(1.0f, 0.0f, 0.0f, 1.0f);
glm::mat4 trans = glm::mat4(1.0f);
// moving the vector by 1 on x-axis and by 1 on y-axis
trans = glm::translate(trans, glm::vec3(1.0f, 1.0f, 0.0f));
vec = trans * vec;
// should return 2101
cout << vec.x << vec.y << vec.z << vec.w << endl;
```

- GLM provides its built-in data types such as `vec4` and `mat4`.
- `glm::mat4(1.0f)` returns an identity matrix (all 1's diagonally). It's always good to start out with an identity matrix and combine transform matrices on top of it.
- `glm::translate` translates the given matrix by the given translation vector, then returns a new transformation matrix with the matrix transformation applied.
- As covered previously, transformation is applied to a vector via matrix multiplication.

### Passing Transformation Matrix to Shader
- Matrix transformations are best done on shaders (GPU) where it is designed to handle these types of computations efficiently.
- Transformation Matrix can be passed to shaders via Uniform.
- Example of applying matrix transformation:

OpenGL code
```C++
// Matrix Transformation
// TIP: order matters. Rotate -> Scale -> Translate
//-------------------------------------------------------------------------
glm::mat4 trans(1.0f);
trans = glm::rotate(trans, glm::radians(90.0f), glm::vec3(0.0f, 0.0f, 1.0f));
trans = glm::scale(trans, glm::vec3(0.5f, 0.5f, 0.5f));
trans = glm::translate(trans, glm::vec3(0.1f, 0.1f, 0.0f));
cout << trans << endl;
GLuint transformLoc = glGetUniformLocation(shaderProgram, "transform");
glUniformMatrix4fv(transformLoc, 1, GL_FALSE, glm::value_ptr(trans));
```

Vertex Shader
```C
#version 330 core
layout (location = 0) in vec3 a_pos;
layout (location = 1) in vec3 a_color;
layout (location = 2) in vec2 a_txCoord;

out vec3 v_color;
out vec2 v_txCoord;

uniform mat4 transform;

void main()
{
	gl_Position = transform * vec4(a_pos, 1.0);
	v_color = a_color;
	v_txCoord = a_txCoord;
}
```

Before:
![[Pasted image 20240705115947.png|300]]

After:
![[Pasted image 20240705120039.png|300]]

### Transformation With Key Input
- Previously, `glfwGetKey` was used to check for keyboard input and apply changes to the application (such as changing Polygon Mode with 1~3 keys). This time, `glfwSetKeyCallback` will be used instead.
- `glfwSetKeyCallback` registers a custom callback function, and passes several parameters such as `window`, `key`, `scancode`, `action`, and `mods`.
- The parameter `action` is used to check if key press is `GLFW_PRESS`, `GLFW_RELEASE`, or `GLFW_REPEAT`.
- The parameter `key` is used to check which key is being pressed, like `GLFW_KEY_W`.
- Using `glfwSetKeyCallback` to move vertices with `WASD` keys:

```C++
// assuming transform matrix is all set up
void keyCallback(GLFWwindow* window, int key, int scancode, int action, int mods)
{
	float speed = 0.05f;

	if (action == GLFW_PRESS || action == GLFW_REPEAT)
	{
		if (key == GLFW_KEY_W)
			transform = glm::translate(transform, glm::vec3(0.0f, speed, 0.0f));
		else if (key == GLFW_KEY_S)
			transform = glm::translate(transform, glm::vec3(0.0f, -speed, 0.0f));
		else if (key == GLFW_KEY_A)
			transform = glm::translate(transform, glm::vec3(-speed, 0.0f, 0.0f));
		else if (key == GLFW_KEY_D)
			transform = glm::translate(transform, glm::vec3(speed, 0.0f, 0.0f));
	}
}

// inside main function
glfwSetKeyCallback(window, keyCallback);
```

## Source Code
Refer to [[opengl_transform_code]]

## Personal Notes
#todo make 3D Matrix Transformations Cheatsheet

2D Affine Transformations
![[2d_affine_transformation.svg]]

