# Coordinate Systems
- Big part of graphics programming is dealing with coordinate systems. So far, we've only dealt with 3D coordinates as if we were dealing with 2D coordinates - drawing only 2D triangles that fit inside the 2D rectangle area (that is Normalized Device Coordinates). In this chapter, we'll deal with actual 3D coordinate systems, what they all mean, and how to convert from one coordinate system to another.

>[!important]
>In the context of computer graphics and mathematics, a **coordinate system** and a **space** are related concepts, but they are not exactly the same.
>
>A **coordinate system** is a method for identifying each point uniquely in a space with a set of numerical coordinates. It's a way of defining where something is in relation to everything else. For example, in a 2D coordinate system, you might describe a point as (x, y). In a 3D coordinate system, a point could be described as (x, y, z).
>
>On the other hand, a **space** refers to the area or volume within which things exist and move. In computer graphics, we often talk about different types of spaces, each with its own coordinate system:
>
>- **Model Space**: This is where the vertices of a model are defined. The origin (0, 0, 0) is typically at the center of the model, and the coordinates of the vertices are relative to this origin.
>
>- **World Space**: After a model is placed in a scene, its vertices are in world space. The coordinates are now relative to a fixed point in the scene, usually chosen as the world origin.
>
>- **View Space** (or Camera Space): This is the world as seen from the camera's point of view. The origin is now at the camera, and everything in the world is defined relative to the camera.
>
>- **Clip Space**: After the view space coordinates are transformed by the projection matrix, they are in clip space. In this space, everything that is visible on screen is within a cube that goes from -1 to +1 in all three dimensions.
>
>- **Screen Space**: Finally, the coordinates are mapped to screen space, where each coordinate corresponds to a pixel on the screen.
>
>So, in summary, a **space** is a context in which objects exist and move, and a **coordinate system** is a way of describing positions within that space. Each space in a graphics application typically has its own coordinate system associated with it.

- As mentioned in previous chapter, the final product of render is drawn using Normalized Device Coordinates. With NDC, coordinates on each axis ranges from `-1.0` to `1.0`. When a coordinate is within that range, it is said to be within a **screen space**. When coordinates go beyond that range, it is quite literally off the screen, and will not be rendered.
- There are five spaces that are most common and important when it comes to graphics programming; Local Space, World Space, View Space, Clip Space, and Screen Space.

## The Global Picture
![[coordinate_systems.png]]

- Several transformation matrices are used to convert the coordinates from one space to the next. The most important are the Model Matrix, the View Matrix, and the Projection Matrix.
- Vertices of an object are first defined in **Local Space (aka Object Space, or Model Space)**. The Local Coordinate of each vertex is set relative to the center of the object itself, as the center of the object is the origin $(0, 0, 0)$.
	- What matters in this space is the general shape of the object.
- Using the **Model Matrix**, the Local Coordinates are converted to the World Coordinates (coordinates in World Space). The object is now inside an abstract world among other objects, with its coordinates relative to the world origin.
	- What matters in this space is where the object is placed in this world.
- Using the **View Matrix**, the World Coordinates are converted to the View Coordinates (coordinates in View Space). This is where Camera is introduced, and all coordinates are relative to the camera.
	- What matters in this space is where the object is located relative to the camera.
- Using the **Projection Matrix**, the View Coordinates are converted to the Clip Coordinates (coordinates in Clip Space). This is where clipping, culling, and projection is introduced.
	- A **frustum** (aka cube), a shape in the form of a pyramid with a cut-off top, represents the area a camera can see. Any object that is outside this frustum is **clipped**, which means they are partially rendered or not rendered at all.
		- ![[Frustum.png]]
		- ![[Cube_clipping.svg]]
	- Similarly to Clipping, **Culling** is a process that determines whether a polygon inside the frustum is rendered. **Back-Face Culling** excludes polygons that are not directly facing the camera. **Z-Culling (aka Occlusion Culling)** excludes polygons that are hidden by other polygons in front.
	- Once clipping and culling is finalized, everything inside the frustum is drawn onto a 2D plane. This is called **Projection**. There are different ways to project a 3D object onto a 2D plane, which will be discussed further later on.
- Finally, the coordinates are mapped to Screen Space, where the Clip Coordinates are transformed to the range defined by `glViewport` (the window size).

## Projection
- **Projection** is a general term that refers to the process of mapping 3D points in a space onto a 2D plane. There are two main types of projections used in Computer Graphics; Parallel Projection and Perspective Projection.

![[3d_projection_diagram.svg]]

![[graphical_projections_all_types.svg]]

### Parallel Projection
- **Parallel Projection** is a type of projection where the lines of projection remain parallel. It preserves the relative proportions of objects, meaning distance from the camera does not affect the shape of object (no depth).
	- ![[parallel_projection_diagram_0.svg]]
- Because Parallel Projection preserves the relative proportions of objects, it is used in technical and engineering fields to produce scale drawings of 3D objects.
- **Orthographic Projection** is a type of Parallel Projection where the projection lines are perpendicular (orthogonal) to the projection plane. The frustum becomes more like a cube.
	- ![[orthographic_projection_view_volume_diagram.png]]
- GLM provides its built-in function `glm::ortho` to create an orthographic projection matrix:

```C++
glm::ortho(left, right, bottom, top, zNear, zFar);
```

- First and second parameters specify the left and right coordinate of the frustum. Third and fourth specify the bottom and top part of the frustum. Basically, first through fourth describe a rectangle.
- Fifth and sixth parameter specify the distance between the near and far plane.

### Perspective Projection
- **Perspective** is an approximate representation, generally on a flat surface, of an image as it is seen by the eye. The most characteristic features of perspective are that objects appear smaller as their distance from their observer increases, and that they are subject to foreshortening.
	- **Foreshortening** describes an effect where an object's dimensions parallel to the line of sight appear shorter than its dimensions perpendicular to the line of sight.
- **Perspective Projection** is a type of projection where the lines of projection converge at a single point called the center of projection (camera). It is used to create a sense of depth and three-dimensionality on a 2D plane (screen).
	- ![[perspective_projection_view_volume_diagram.png]]
- The easiest way to simulate depth is to divide X and Y coordinate by Z - further a vertex is, the higher the Z value, which also means that the result of division is smaller.
	- This division by Z coordinate is carried out by Perspective Division, which will be discussed later.
- There are several things to account for in Perspective Projection - Aspect, Field of Vision, and Normalization.
	- Aspect refers to the ratio between screen's height and width.
	- Field of View is the angular extent of the observable world that is seen at any given moment. Note that the wider the angle, the more of the world that is observed and the smaller the objects within.
	- Normalization refers to conversion of the coordinates to values within `-1` to `1` range. Perspective Division is responsible for this calculation (covered in further discussion).
- The calculation of Perspective Projection is not covered in this guide; Refer to [The Math behind (most) 3D games - Perspective Projection | Brendan Galea | Youtube](https://youtu.be/U0_ONQQ5ZNM?si=iITjfz8plq-BM7p5) for a good explanation.
	- ![[Pasted image 20240710144749.png]]
- GLM provides its built-in function `glm::perspective` to create an orthographic projection matrix:

```C++
float fovy = 45.0f;
float aspect = static_cast<float>(SCR_WIDTH) / static_cast<float>(SCR_HEIGHT);
float zNear = 0.1f;
float zFar = 100.0f;
glm::mat4 proj = glm::perspective(glm::radians(fovy), aspect, zNear, zFar);
```

- Note that `fovy` variable sets only the vertical FOV for the perspective projection. The horizontal FOV is derived based on the aspect ratio.

### Perspective Division
- `w` component of 4D vector coordinate serves more purpose than assisting with translation (moving vertex) - it is also used to apply Perspective Division.
- Perspective Division is the final step in Graphics Pipeline where XYZ coordinates are divided by `w`. It is done automatically by the OpenGL.
- In essence, the simplest form of perspective projection will be applied when Perspective Division occurs and `w = z`:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\begin{gather}
\mymat{1&0&0&0\\0&1&0&0\\0&0&1&0\\0&0&1&0} \cdot \mymat{x\\y\\z\\1} = \mymat{x\\y\\z\\z}\\
\mymat{x\\y\\z\\z} \div z = \mymat{x/z\\y/z\\1\\1}
\end{gather}
$$

- Orthographic Projection directly maps all coordinates inside the frustum to Normalized Device Coordinates without any special side effects since it won't touch the `w` component of the transformed vector (`w` component remains equal to `1.0`).

## Putting it all together
- All in all, a Vertex Coordinate is transformed to Clip Coordinate through various transformation matrix multiplication:

$$
V_{clip} = M_{projection} \cdot M_{view} \cdot M_{model} \cdot V_{local}
$$

- Note that the order of matrix multiplication matters - it is not commutative, and it is in reverse.
- The Clip Coordinate is then assigned to `gl_Position` in the Vertex Shader, and then OpenGL will automatically perform Perspective Division and clipping.
- For the rest of the guide, transformation matrix for each space will be implemented in code.

### Local Space
- Start off with, we have a flat plane (made up of two triangles) as a 3D model.
- ![[Pasted image 20240710204719.png|300]]

### World Space
- The 3D model is placed in the World Space by multiplying the Local Coordinate with a Model Matrix.
- The Model Matrix consists of translations, scaling, and/or rotations.
- For now, we'll rotate the 3D model on the x-axis so that it looks like it's laying on the floor.
- Code as follows:

OpenGL Code
```C++
// Model Matrix
glm::mat4 model(1.0f);
model = glm::rotate(model, glm::radians(-55.0f), glm::vec3(1.0f, 0.0f, 0.0f));

// Pass Model Matrix via uniform
GLuint modelLoc = glGetUniformLocation(shaderProgram, "model");
glUniformMatrix4fv(modelLoc, 1, GL_FALSE, glm::value_ptr(model));
```

Vertex Shader
```C
#version 330 core
layout (location = 0) in vec3 a_pos;
layout (location = 1) in vec3 a_color;
layout (location = 2) in vec2 a_txCoord;

uniform mat4 transform;
uniform mat4 model;

out vec3 v_color;
out vec2 v_txCoord;

void main()
{
	gl_Position = transform * model * vec4(a_pos, 1.0f);
	v_color = a_color;
	v_txCoord = a_txCoord;
}
```

- ![[Pasted image 20240710211141.png|300]]

### View Space
- The 3D model is placed in the View Space by multiplying the World Coordinate with a View Matrix.

>[!important] Right-Handed System
>By convention, OpenGL is a right-handed system; meaning `+x` points to right, `+y` points to up, and `+z` is towards the camera.
>![[coordinate_systems_right_handed.png]]
>The handed-ness is better explained with this image:
>![[geo-lefthand-vs-righthand.png]]
>Note that other computer graphics libraries and applications may use Left-Handed System. For example, DirectX uses Left-Handed System.
>Another thing to note is that OpenGL switches from Right to Left-Handed System when coordinates are converted to Normalized Device Coordinates.

- We'll move the "camera" slightly backwards so that the camera isn't sitting right on top of the 3D model; the camera's default position is at the origin `(0,0,0)`, facing `-z` direction.
- Note that moving the camera `+z` direction is the equivalent to moving the entire scene `-z` direction.
- Code as follows:

```C++
glm::mat4 view(1.0f);
view = glm::translate(view, glm::vec3(0.0f, 0.0f, -3.0f));

GLuint viewLoc = glGetUniformLocation(shaderProgram, "view");
glUniformMatrix4fv(viewLoc, 1, GL_FALSE, glm::value_ptr(view));
```

- Make sure to declare uniform variable `view` in the Vertex Shader, and multiply `view` to the coordinate (left to `model`).
- Because OpenGL only renders coordinates within `-1` and `1` range, the render will result in a blank scene. Projection will help with this issue.

### Clip Space
- The last thing to do is to define the Projection Matrix:

OpenGL Code
```C++
float fovy = 45.0f;
float aspect = static_cast<float>(SCR_WIDTH) / static_cast<float>(SCR_HEIGHT);
float zNear = 0.1f;
float zFar = 100.0f;
glm::mat4 projection = glm::perspective(glm::radians(fovy), aspect, zNear, zFar);
GLuint projectionLoc = glGetUniformLocation(shaderProgram, "projection");
glUniformMatrix4fv(projectionLoc, 1, GL_FALSE, glm::value_ptr(projection));
```

Vertex Shader
```C
#version 330 core
layout (location = 0) in vec3 a_pos;
layout (location = 1) in vec3 a_color;
layout (location = 2) in vec2 a_txCoord;

uniform mat4 transform;
uniform mat4 model;
uniform mat4 view;
uniform mat4 projection;

out vec3 v_color;
out vec2 v_txCoord;

void main()
{
	gl_Position = projection * transform * view * model * vec4(a_pos, 1.0f);
	v_color = a_color;
	v_txCoord = a_txCoord;
}
```

- ![[Pasted image 20240710221653.png|300]]
- As a note, `projection` outputs a matrix (aspect 1:1) like below:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\begin{gather}
\mymat{
	2.414 & 0.000 & 0.000 & 0.000 \\
	0.000 & 2.414 & 0.000 & 0.000 \\
	0.000 & 0.000 & -1.002 & -0.200 \\
	0.000 & 0.000 & -1.000 & 0.000
}
\end{gather}
$$

- (exercise) make necessary changes to the `keyCallback` function so the 3D model can be moved forward and backward on Z-axis.

### Maintaining Aspect Ratio
- As it is now, the Perspective Matrix is using the aspect ratio of the initial window width and height. This creates an issue where  the rendered scene (and the objects within) gets distorted when the window is resized (causing the aspect ratio to change).
- One way to fix the aspect ratio issue is to define two variables that represent width and height, have them so that the `framebufferSizeCallback` function assigns new values to them when the window is resized, and then using the aspect ratio between the two for the Perspective Projection.

### Source Code
Refer to [[opengl_perspective_code]]

## More 3D
- This time we'll deal with a cube instead of a plane. To render a cube, a total of 36 vertices (6 faces * 2 triangles * 3 vertices) are needed:

```C++
float vertices[] = {
	// positions          // texture coords
	-0.5f, -0.5f, -0.5f,  0.0f, 0.0f,
	 0.5f, -0.5f, -0.5f,  1.0f, 0.0f,
	 0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
	 0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
	-0.5f,  0.5f, -0.5f,  0.0f, 1.0f,
	-0.5f, -0.5f, -0.5f,  0.0f, 0.0f,

	-0.5f, -0.5f,  0.5f,  0.0f, 0.0f,
	 0.5f, -0.5f,  0.5f,  1.0f, 0.0f,
	 0.5f,  0.5f,  0.5f,  1.0f, 1.0f,
	 0.5f,  0.5f,  0.5f,  1.0f, 1.0f,
	-0.5f,  0.5f,  0.5f,  0.0f, 1.0f,
	-0.5f, -0.5f,  0.5f,  0.0f, 0.0f,

	-0.5f,  0.5f,  0.5f,  1.0f, 0.0f,
	-0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
	-0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
	-0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
	-0.5f, -0.5f,  0.5f,  0.0f, 0.0f,
	-0.5f,  0.5f,  0.5f,  1.0f, 0.0f,

	 0.5f,  0.5f,  0.5f,  1.0f, 0.0f,
	 0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
	 0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
	 0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
	 0.5f, -0.5f,  0.5f,  0.0f, 0.0f,
	 0.5f,  0.5f,  0.5f,  1.0f, 0.0f,

	-0.5f, -0.5f, -0.5f,  0.0f, 1.0f,
	 0.5f, -0.5f, -0.5f,  1.0f, 1.0f,
	 0.5f, -0.5f,  0.5f,  1.0f, 0.0f,
	 0.5f, -0.5f,  0.5f,  1.0f, 0.0f,
	-0.5f, -0.5f,  0.5f,  0.0f, 0.0f,
	-0.5f, -0.5f, -0.5f,  0.0f, 1.0f,

	-0.5f,  0.5f, -0.5f,  0.0f, 1.0f,
	 0.5f,  0.5f, -0.5f,  1.0f, 1.0f,
	 0.5f,  0.5f,  0.5f,  1.0f, 0.0f,
	 0.5f,  0.5f,  0.5f,  1.0f, 0.0f,
	-0.5f,  0.5f,  0.5f,  0.0f, 0.0f,
	-0.5f,  0.5f, -0.5f,  0.0f, 1.0f
};
```

- Note that the Vertex Attributes consists only of position and texture coordinates. Also, there aren't any indices this time.
	- EBO is NOT used in this case.
	- Attribute Vertex Pointer should be set accordingly - meaning, the stride and the offsets should be adjusted.
	- `glDrawArrays` is used instead of `glDrawElements` <-- failure to change this caused the program to freeze.
- The result:
	- ![[Pasted image 20240711163447.png|300]]
- Note that the result image above shows an issue: some sides of the cubes are being drawn over other sides of the cube. This happens because when OpenGL draws the model triangle-by-triangle (fragment-by-fragment) in sequence, and so whatever gets drawn later overwrites any pixel color that is already there.
	- The solution to the above problem is z-buffer.

### Z-Buffer
- OpenGL stores all its depth information in a **Z-Buffer (aka Depth Buffer)**, which is automatically created by the windowing system (GLFW).
	- It stores depth values as 16, 24, or 32 bit floats, with most systems using a depth buffer with a precision of 24 bits.
- Every fragment has a depth value. This value is either computed by the Fragment Shader (if it writes to `gl_FragDepth`), or is the window-space Z coordinate computed as the output of the Vertex Post-Processing steps.
- Depth Buffer stores the depth value of each fragment based on its position in the viewport.
- **Depth Test** is the process where OpenGL tests the depth value of a fragment against the content of the depth buffer. When a fragment is processed, its depth value is compared with the existing value at the same position in the depth buffer; if the new fragment's depth value is less (indicating it is closer to the camera), it passes the Depth Test and its depth value is stored in the depth buffer (replacing the old value).
	- If the Depth Test fails, the fragment is discarded.
- Depth Test is disabled by default, so `glEnable(GL_DEPTH_TEST)` must be called in order to enable it.
	- If Depth Test is enabled, the Depth Buffer should be cleared before each frame using `glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT)`.
- Most GPUs support a feature called Early Depth Testing; this allows the Depth Test to run before the Fragment Shader runs. If a fragment isn't going to be visible, it can be prematurely discarded.
- The result:
	- ![[Pasted image 20240711172419.png|300]]

### Adjusting Control
- So far `transform` is being used to manipulate the model. It wasn't until I tried implementing the rotation that I realized the order where `transform` comes in matters, and that there can be transform for the model itself, and then transform for the camera. So, instead of using `transform`, I may need to directly manipulate `model` and `view`.
- To clean up the code a little, replaced all the `if else` statements with `switch case` statements in `keyCallback` function.
- The code now:

```C++
void keyCallback(GLFWwindow* window, int key, int scancode, int action, int mods)
{
	float speed = 0.05f;

	if (action == GLFW_PRESS || action == GLFW_REPEAT)
	{
		if (modelMode)
		{
			switch (key)
			{
				case GLFW_KEY_Q:
					model = glm::translate(model, glm::vec3(0.0f, 0.0f, -speed));
					break;
				case GLFW_KEY_E:
					model = glm::translate(model, glm::vec3(0.0f, 0.0f, speed));
					break;
				case GLFW_KEY_A:
					model = glm::translate(model, glm::vec3(-speed, 0.0f, 0.0f));
					break;
				case GLFW_KEY_D:
					model = glm::translate(model, glm::vec3(speed, 0.0f, 0.0f));
					break;
				case GLFW_KEY_W:
					model = glm::translate(model, glm::vec3(0.0f, speed, 0.0f));
					break;
				case GLFW_KEY_S:
					model = glm::translate(model, glm::vec3(0.0f, -speed, 0.0f));
					break;
				case GLFW_KEY_UP:
					model = glm::rotate(model, glm::radians(-3.0f), glm::vec3(1.0f, 0.0f, 0.0f));
					break;
				case GLFW_KEY_DOWN:
					model = glm::rotate(model, glm::radians(3.0f), glm::vec3(1.0f, 0.0f, 0.0f));
					break;
				case GLFW_KEY_LEFT:
					model = glm::rotate(model, glm::radians(3.0f), glm::vec3(0.0f, 1.0f, 0.0f));
					break;
				case GLFW_KEY_RIGHT:
					model = glm::rotate(model, glm::radians(-3.0f), glm::vec3(0.0f, 1.0f, 0.0f));
					break;
			}
		}
		else
		{
			// TODO: moving the camera seems a little off right now
			switch (key)
			{
			case GLFW_KEY_Q:
				view = glm::translate(view, glm::vec3(0.0f, 0.0f, -speed));
				break;
			case GLFW_KEY_E:
				view = glm::translate(view, glm::vec3(0.0f, 0.0f, speed));
				break;
			case GLFW_KEY_A:
				view = glm::translate(view, glm::vec3(-speed, 0.0f, 0.0f));
				break;
			case GLFW_KEY_D:
				view = glm::translate(view, glm::vec3(speed, 0.0f, 0.0f));
				break;
			case GLFW_KEY_W:
				view = glm::translate(view, glm::vec3(0.0f, speed, 0.0f));
				break;
			case GLFW_KEY_S:
				view = glm::translate(view, glm::vec3(0.0f, -speed, 0.0f));
				break;
			case GLFW_KEY_UP:
				view = glm::rotate(view, glm::radians(-3.0f), glm::vec3(1.0f, 0.0f, 0.0f));
				break;
			case GLFW_KEY_DOWN:
				view = glm::rotate(view, glm::radians(3.0f), glm::vec3(1.0f, 0.0f, 0.0f));
				break;
			case GLFW_KEY_LEFT:
				view = glm::rotate(view, glm::radians(3.0f), glm::vec3(0.0f, 1.0f, 0.0f));
				break;
			case GLFW_KEY_RIGHT:
				view = glm::rotate(view, glm::radians(-3.0f), glm::vec3(0.0f, 1.0f, 0.0f));
				break;
			}
		}
	}
}
```

- Make sure to initialize `model` and `view` outside `main` function. Also, assign the values to the uniform variables accordingly inside the render loop.

### More Cubes
- A way to draw multiple cubes is to draw the same model multiple times all in a single frame - by calling `glDrawArrays` in a loop (inside a render loop). Follow the procedure:
	- Define a list of different positions for cubes to be in - `cubePositions`.
	- Inside render loop, make a `for` loop that iterates the content of the `cubePositions` and translate each model (with model matrix initialized) accordingly.
- Code as follows:

```C++
// outside render loop
glm::vec3 cubePositions[] = {
    glm::vec3( 0.0f,  0.0f,  0.0f), 
    glm::vec3( 2.0f,  5.0f, -15.0f), 
    glm::vec3(-1.5f, -2.2f, -2.5f),  
    glm::vec3(-3.8f, -2.0f, -12.3f),  
    glm::vec3( 2.4f, -0.4f, -3.5f),  
    glm::vec3(-1.7f,  3.0f, -7.5f),  
    glm::vec3( 1.3f, -2.0f, -2.5f),  
    glm::vec3( 1.5f,  2.0f, -2.5f), 
    glm::vec3( 1.5f,  0.2f, -1.5f), 
    glm::vec3(-1.3f,  1.0f, -1.5f)  
};

//inside render loop
for (unsigned int i = 0; i < 10; i++)
{
	model = glm::mat4(1.0f);
	model = glm::translate(model, cubePositions[i]);
	float angle = 20.0f * i;
	model = glm::rotate(model, glm::radians(angle), glm::vec3(1.0f, 0.3f, 0.5f));
	glUniformMatrix4fv(modelLoc, 1, GL_FALSE, glm::value_ptr(model));

	glDrawArrays(GL_TRIANGLES, 0, 36);
}
```

- Code result:
	- ![[Pasted image 20240716070850.png|300]]
- The issue with the way multiple objects are drawn following the code above is that it is difficult to move each model separately.
	- With the current setup (`model` being initialized outside `main`), `model` has to be reset to an identity matrix, otherwise the value accumulates and it gets thrown off the screen.
	- There is a way to draw multiple copies of the same object in one draw call - `instancing`. This will be covered later on.

## Source Code
Refer to [[opengl_cube_code]]
