# Camera
- In the previous chapter, using the View Matrix to move around the scene was discussed. OpenGL itself is not familiar with the concept of a "camera", but as a developer, one can simulate a camera by moving all objects in the scene - giving the illusion that the camera itself is moving.
- In this chapter, setting up a fly style camera that can freely move around in a 3D scene will be discussed. Using keyboard and mouse input to move the camera will be discussed as well. The chapter will conclude by making a custom camera class.

## Camera/View Space
- When a Camera/View Space is discussed, it generally refers to all the Vertex Coordinates as seen from the Camera's perspective as the origin of the scene: the View Matrix transforms all the World Coordinates into View Coordinates that are relative to the Camera's position and direction.
- There are a few things that are needed to define a Camera:
	- Its position in World Space
	- The direction it's looking at
	- A vector pointing to the right and a vector pointing upwards from the camera
- ![[camera_axes.png]]
- All in all, a Camera's own coordinate system will be created with 3 perpendicular unit axes with the Camera's position as the origin.

### 1. Camera Position
- Previously, objects in the scene were pushed back to simulate a camera. This time a vector will be used to represent the Camera's position in World Space, like so:

```C++
glm::vec3 cameraPos = glm::vec3(0.0f, 0.0f, 3.0f);
```

### 2. Camera Direction
- Another vector is required to represent the Camera's direction. For now, the Camera will be set to look at the origin of the scene `(0,0,0)`.
- The Camera's Direction Vector can be produced by subtracting the Camera Position Vector by the Target Vector (the Origin).
	- In this case, `(0,0,3)` subtracted by `(0,0,0)` is `(0,0,3)`.
- Once it is normalized, it becomes a unit vector that holds only the direction.
- The code:

```C++
glm::vec3 cameraTarget = glm::vec3(0.0f, 0.0f, 0.0f);
glm::vec3 cameraDirection = glm::normalize(cameraPos - cameraTarget);
```

- Note that the Direction Vector points toward positive Z-axis. Not sure how it works just yet (and the website does a poor job at explaining it), but it will be reversed by the OpenGL later on.

### 3. Right Axis
- Along with Direction Vector, another vector that is needed to define a camera is a Right Vector, which represents the positive X-axis of the Camera Space.
- In order to get a Right Vector, first specify an "up" vector that points upwards in World Space `(0,1,0)`, and then do a cross product on the "up" vector and the Direction Vector.
	- Note that "up" vector is not referring to the Camera's Up Vector.
- The result of a cross product is a vector perpendicular to both vectors. In this case, it produces a vector that points in the positive X-axis.
- Code as follows:

```C++
glm::vec3 up = glm::vec3(0.0f, 1.0f, 0.0f);
glm::vec3 cameraRight = glm::normalize(glm::cross(up, cameraDirection));
```

### 4. Up Axis
- Camera's Up Vector is the cross product between the Direction Vector and the Right Vector:

```C++
// cross product of unit vectors is a unit vector
glm::vec3 cameraUp = glm::cross(cameraDirection, cameraRight);
```


- Setting up Camera's Z-axis (Camera Direction), X-axis (Right Vector), and Y-axis (Up Vector) is related to the Gram-Schmidt Process.

>[!important] The Gram-Schmidt Process
>The Gram-Schmidt process is a mathematical algorithm that transforms a set of vectors into an orthogonal or orthonormal basis¹. It's a fundamental tool in many areas of mathematics and physics, including computer graphics¹³. Here are some of its key applications in computer graphics:
>
>1. **Generating Orthogonal Bases**: In computer graphics, we often need to work with bases that are orthogonal (i.e., the vectors are at right angles to each other) for more efficient computations in rendering pipelines³. The Gram-Schmidt process can transform any set of linearly independent vectors into an orthonormal set¹, which is very useful for this purpose.
>
>2. **Preservation of Span**: The process preserves the span of the original vectors. In other words, any vector that could be created through linear combinations of the original set can also be created from the orthonormal set produced by the process¹. This is important in computer graphics where transformations and projections are commonly used.
>
>3. **Efficient Computations**: The resulting set of orthonormal vectors can serve as a basis for the subspace they span. This means they are linearly independent and can represent any vector in the subspace through linear combinations¹. This property is useful in many graphics algorithms where we need to perform computations in a certain basis.
>
>4. **Signal Processing**: In signal processing, which is often used in computer graphics for tasks like texture mapping and digital image processing, the Gram-Schmidt process is used to orthogonalize signals to remove redundancy and noise³.
>
>In summary, the Gram-Schmidt process is a powerful tool in computer graphics, helping to simplify computations and provide geometric insights in vector spaces¹. I hope this helps! 😊
>
>원본: Copilot과의 대화, 2024. 7. 13.
>(1) The Gram-Schmidt Process-Definition, Applications and Examples - The Story of Mathematics. https://www.storyofmathematics.com/gram-schmidt-process/.
>(2) Gram-Schmidt Process Definition | DeepAI. https://deepai.org/machine-learning-glossary-and-terms/gram-schmidt-process.
>(3) 그람-슈미트 과정(Gram-Schmidt Orthogonalization Process) : 네이버 블로그. https://m.blog.naver.com/qio910/221778224660.
>(4) Gram Schmidt Process: A Brief Explanation - Programmathically. https://programmathically.com/gram-schmidt-process/.
>(5) CPU vs. GPU - Performance comparison for the Gram-Schmidt algorithm | The ... - Springer. https://link.springer.com/article/10.1140/epjst/e2012-01638-7.

## Look At
- Putting the Right Vector $R$, the Up Vector $U$, the Direction Vector $D$, and the Position Vector $P$ together, something called a **LookAt Matrix** can be made.

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\begin{gathered}
\text{LookAt} =
\mymat{
	R_x & R_y & R_Z & 0\\
	U_x & U_y & U_z & 0\\
	D_x & D_y & D_z & 0\\
	0 & 0 & 0 & 1
} \cdot
\mymat{
	1 & 0 & 0 & -P_x\\
	0 & 1 & 0 & -P_y\\
	0 & 0 & 1 & -P_z\\
	0 & 0 & 0 & 1
}
\end{gathered}
$$

- LookAt Matrix is a View Matrix that *looks* at a given target.
- GLM library provides a function that returns a LookAt Matrix when Position Vector, Target Vector, and Up Vector (world space) is given:

```C++
glm::vec3 cameraPosition(0.0f, 0.0f, 3.0f);
glm::vec3 cameraTarget(0.0f, 0.0f, 0.0f);
glm::vec3 cameraUp(0.0f, 1.0f, 0.0f);
glm::mat4 view = glm::lookAt(cameraPosition, cameraTarget, cameraUp);
```

- The `view`:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\begin{gathered}
\mymat{
	1 & 0 & 0 & 0\\
	0 & 1 & 0 & 0\\
	0 & 0 & 1 & -3\\
	0 & 0 & 0 & 1
}
\end{gathered}
$$

- As it is, the LookAt Matrix is the same as the View Matrix made previously:

```C++
glm::mat4 view(1.0f);
view = glm::translate(view, glm::vec3(0.0f, 0.0f, -3.0f));
```

- However, the LookAt Matrix can be more versatile in terms of usuage:

```C++
// inside render loop
const float radius = 10.0f;
float camX = sin(glfwGetTime()) * radius;
float camZ = cos(glfwGetTime()) * radius;
glm::vec3 cameraPosition(camX, 0.0f, camZ);
glm::vec3 cameraTarget(0.0f, 0.0f, 0.0f);
glm::vec3 cameraUp(0.0f, 1.0f, 0.0f);
glm::mat4 view = glm::lookAt(cameraPosition, cameraTarget, cameraUp);
```

- The result: [[OpenGL Application 2024-07-16 16-45-39.mp4]]
	- The Camera is rotating around the origin while maintaining its focus on the target (origin).
- By using the LookUp Matrix/Function, it is easier to manipulate the camera in such a way that it is no longer necessary to "imagine" a camera.

## Camera Control
- Instead of rotating Camera around while locking onto a target, the Camera can be set up so that it moves around while facing forward:

```C++
glm::vec3 cameraPosition(0.0f, 0.0f, 3.0f);
glm::vec3 cameraFront(0.0f, 0.0f, -1.0f);
glm::vec3 cameraUp(0.0f, 1.0f, 0.0f);
glm::mat4 view = glm::lookAt(cameraPosition, cameraPosition + cameraFront, cameraUp);
```

- Note that instead of `cameraTarget` 
- Cross Product of `CameraFront` and `cameraUp` yields an orthogonal vector between the two - meaning, a vector pointing left or right can be made (be sure to normalize):

```C++
glm::vec3 cameraRight = glm::normalize(glm::cross(cameraFront, cameraUp));
```

- Using the knowledge above, the Camera can move front/back/left/right using the WASD key:

```C++
glm::vec3 cameraPosition(0.0f, 0.0f, 3.0f);
glm::vec3 cameraFront(0.0f, 0.0f, -1.0f);
glm::vec3 cameraUp(0.0f, 1.0f, 0.0f);
glm::vec3 cameraRight = glm::normalize(glm::cross(cameraFront, cameraUp));

void keyCallback(GLFWwindow* window, int key, int scancode, int action, int mods)
{
	float speed = 0.05f;

	if (action == GLFW_PRESS || action == GLFW_REPEAT)
	{
		switch (key)
		{
			case GLFW_KEY_W:
				cameraPosition += cameraFront * speed;
				break;
			case GLFW_KEY_S:
				cameraPosition -= cameraFront * speed;
				break;
			case GLFW_KEY_D:
				cameraPosition += cameraRight * speed;
				break;
			case GLFW_KEY_A:
				cameraPosition -= cameraRight * speed;
				break;
		}
	}
}
```