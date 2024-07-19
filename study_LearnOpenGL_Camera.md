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

- Note that instead of `cameraTarget` which was set to the Origin is now `cameraPosition + cameraFront`; this sets up so that the camera always faces forward even if the camera's position has changed.
- Cross Product of `CameraFront` and `cameraUp` yields an orthogonal vector between the two - meaning, a vector pointing left or right can be made (be sure to normalize):

```C++
glm::vec3 cameraRight = glm::normalize(glm::cross(cameraFront, cameraUp));
```

- Using the knowledge above, the Camera can move front/back/left/right using the WASD key:

```C++
// outside main
glm::vec3 cameraPosition(0.0f, 0.0f, 3.0f);
glm::vec3 cameraFront(0.0f, 0.0f, -1.0f);
glm::vec3 cameraUp(0.0f, 1.0f, 0.0f);
glm::vec3 cameraRight = glm::normalize(glm::cross(cameraFront, cameraUp));


void keyCallback(GLFWwindow* window, int key, int scancode, int action, int mods)
{
	float speed = 3.0f * deltaTime;
	cout << speed << endl;

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

// inside render loop
glm::mat4 view = glm::lookAt(cameraPosition, cameraPosition + cameraFront, cameraUp);
```

### Movement Speed
- As of now, the speed at which the Camera moves is set to `0.05` and it is processed for each frame inside the render loop. The problem with this set up is that different computers have different processing powers, which means that a computer with higher processing power renders more frames per second - thereby also processing speed more often (and faster).
	- For example, if there's a computer that renders at 60 FPS and another at 30 FPS, the 60 FPS computer will process key input twice as fast as the 30 FPS one - not to mention move the camera twice as far (if the key is on repeat).
- Graphics applications and games usually keep track of the time it took to render the last frame - in a variable called `deltaTime`:

```C++
// outside main
float deltaTime = 0.0f;
float lastFrame = 0.0f;

// inside render loop
float currentFrame = static_cast<float>(glfwGetTime());
deltaTime = currentFrame - lastFrame;
lastFrame = currentFrame;
```

- Graphics application can make up for the difference in Render/Processing Rate by multiplying the Camera speed by `deltaTime`; making the Camera speed proportional to the Frame Rate.
	- For example, 30 FPS computer would have a delta time of $\frac{1}{30}$ second, and 60 FPS computer would have a delta time of $\frac{1}{60}$ second. If the Camera's speed is set to 3, then 30 FPS computer would move 0.1 per Frame, whereas 60 FPS computer would move 0.05 per Frame - in the end, the Camera would move 3 per second on either of the computers.
	- In code, `float speed = 3.0f * deltaTime;`
- The concept of using Delta Time is called **Variable Time Step**. While this can make the game feel smooth and responsive, it can lead to inconsistent game behavior if the Frame Rate varies significantly.

>[!important] (personal note) `glfwSetKeyCallback` vs. `glfwGetKey`
>So far I've deviated from the guide a little bit by using the `glfwSetKeyCallback` function instead of the `glfwGetKey` for the Key Input Processing. The main reasons why I did that:
>- The Callback function receives several parameters that are convenient to use.
>- The Callback function seems to work alongside the Render Loop, not inside; meaning it's not blocked by any of the processes that happen inside the Render Loop.
>- The Callback function seems to run only when there's a key input, whereas `glfwGetKey` runs and checks for every keys (that are set).
>
>However, it turns out the `glfwSetKeyCallback` has some disadvantages over `glfwGetKey`:
>- The frequency at which the callback function is checked is not determined by OpenGL itself, but by the underlying operating system's event handling. Meaning, movement by key input could differ by machines' spec, regardless of the Render Rate.
>- Since the callback function is not tied to the Render Loop, it's difficult to apply Variable Time Step. In fact, when I tried with the callback function, the movement did not seem smooth at all.

- WASD key movement implementation with `glfwGetKey` (replacing the callback function):

```C++
void processInput(GLFWwindow* window)
{
	// ..

	float speed = 3.0f * deltaTime;
	if (glfwGetKey(window, GLFW_KEY_W) == GLFW_PRESS)
		cameraPosition += speed * cameraFront;
	if (glfwGetKey(window, GLFW_KEY_S) == GLFW_PRESS)
		cameraPosition -= speed * cameraFront;
	if (glfwGetKey(window, GLFW_KEY_A) == GLFW_PRESS)
		cameraPosition -= glm::normalize(glm::cross(cameraFront, cameraUp)) * speed;
	if (glfwGetKey(window, GLFW_KEY_D) == GLFW_PRESS)
		cameraPosition += glm::normalize(glm::cross(cameraFront, cameraUp)) * speed;
}
```

- Result: [[OpenGL Application 2024-07-18 10-37-58.mp4]]

## Camera Rotations
- The `cameraFront` vector is the key to implement camera rotations.

### Euler Angles
- **Euler Angles** are 3 values that can represent any rotations in 3D; Pitch, Yaw, and Roll.
- ![[camera_pitch_yaw_roll.png]]
- **Pitch** : the angle that depicts looking up or down; a rotation on X-axis.
- **Yaw** : the angle that depicts looking left or right; a rotation on Y-axis.
- **Roll** : the angle that depicts leaning left or right; a rotation on Z-axis.
- A bit of Trigonometry is useful for establishing direction:

$$
\begin{gather}
\sin{\theta} = \frac{y}{\bar{v}}\\
\cos{\theta} = \frac{x}{\bar{v}}\\
\text{let } \bar{v} = 1,\\
\sin{\theta} = y\\
\cos{\theta} = x
\end{gather}
$$

- Since `cameraFront` is a Unit Vector with length of 1, change in vector coordinate can be represented as $(\cos{\theta}, \sin{\theta})$.
- In case of Yaw, the Direction Vector would be represented as $(\cos{\theta}, 1, \sin{\theta})$.
	- ![[camera_yaw.png]]
- Finding Direction Vector in code:

```C++
float yaw = 30;
glm::vec3 direction;
direction.x = cos(glm::radians(yaw));
direction.z = sin(glm::radians(yaw));
```


#todo thought: instead of messing with sin & cos, couldn't I just use GLM's matrix rotation?

`trans = glm::rotate(trans, glm::radians(90.0f), glm::vec3(0.0f, 0.0f, 1.0f));`