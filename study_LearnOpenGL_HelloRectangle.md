
# Hello Rectangle
- Drawing shapes that are more complex than triangles, such as a rectangle, requires breaking them down into base primitives. For example, a rectangle is drawn with two triangles.
- When complex shapes are broken down into simpler shapes, some of the vertices are reused. For example, a rectangle that is broken down into two triangles have 4 vertices, 2 of which are shared between the triangles.
- In order to keep track of the vertices that are reused, **indexed drawing** comes into play.
- An **Element Buffer Object (EBO)** is a type of buffer that allows vertices to be reused in order to create multiple primitives. It is also known as **Index Buffer Object (IBO)**. Basically, it is a buffer that holds an array of indices that keeps track of the arrangement of the vertices.
- A rectangle (w/ two triangles) without EBO will have 6 vertices, like so:

```C++
float vertices[] = {
    // first triangle
     0.5f,  0.5f, 0.0f,  // top right
     0.5f, -0.5f, 0.0f,  // bottom right
    -0.5f,  0.5f, 0.0f,  // top left 
    // second triangle
     0.5f, -0.5f, 0.0f,  // bottom right
    -0.5f, -0.5f, 0.0f,  // bottom left
    -0.5f,  0.5f, 0.0f   // top left
};
```

- With the use of EBO, the rectangle is drawn with 4 vertices, like so:

```C++
float vertices[] = {
     0.5f,  0.5f, 0.0f,  // top right
     0.5f, -0.5f, 0.0f,  // bottom right
    -0.5f, -0.5f, 0.0f,  // bottom left
    -0.5f,  0.5f, 0.0f   // top left 
};
unsigned int indices[] = {  // note that we start from 0!
    0, 1, 3,   // first triangle
    1, 2, 3    // second triangle
};
```

- Using EBO is similar to VBO, where an index for EBO is generated, which is then bound to a buffer, and then lastly the data (indices) are uploaded.

```C++
unsigned int EBO;
glGenBuffers(1, &EBO);

glBindBUffer(GL_ELEMENT_ARRAY_BUFFER, EBO);
glBufferData(GL_ELEMENT_ARRAY_BUFFER, sizeof(indices), indices, GL_STATIC_DRAW);
```

- <mark class="hltr-trippy">function</mark> `void glDrawElements(mode, count, type, indices)` <mark class="hltr-trippy">:</mark> render primitives from array data. Used instead of `glDrawArrays` when EBO is used.
	- `GLenum mode` : specifies what kind of primitives to render. In this case, `GL_TRIANGLES`.
	- `GLsizei count` : specifies the number of *elements* to be rendered. This includes the duplicate vertices; since a rectangle is drawn with two triangles (of 3 points), the count is 6.
	- `GLenum type` : specifies the type of the values in indices. Most commonly `GL_UNSIGEND_INT`.
	- `const GLvoid *indices` : specifies an offset of the first index in the array in the data store of the buffer currently bound to the `GL_ELEMENT_ARRAY_BUFFER` target.

```C++
// ..
glDrawElements(GL_TRIANGLES, 6, GL_UNSIGNED_INT, 0);
```

- A VAO stores the last EBO that gets bound while the VAO is bound.
- A VAO stores the `glBindBUffer()` calls when the target is `GL_ELEMENT_ARRAY_BUFFER`. This also means it stores its unbind calls; be sure not to unbind the EBO before unbinding VAO, otherwise the VAO won't have an EBO configured.
- ![[vertex_array_objects_ebo.png]]
- The resulting initialization and drawing code now looks something like this:

```C++
// set up vertex data (and buffer(s)) and configure vertex attributes
// ------------------------------------------------------------------
float vertices[] = {
	 0.5f,  0.5f, 0.0f,  // top right
	 0.5f, -0.5f, 0.0f,  // bottom right
	-0.5f, -0.5f, 0.0f,  // bottom left
	-0.5f,  0.5f, 0.0f   // top left 
};
unsigned int indices[] = {  // note that we start from 0!
	0, 1, 3,  // first Triangle
	1, 2, 3   // second Triangle
};

unsigned int VBO, VAO, EBO;
glGenVertexArrays(1, &VAO);
glGenBuffers(1, &VBO);
glGenBuffers(1, &EBO);
// bind the Vertex Array Object first, then bind and set vertex buffer(s),
// and then configure vertex attributes(s).
glBindVertexArray(VAO);

glBindBuffer(GL_ARRAY_BUFFER, VBO);
glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);

glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, EBO);
glBufferData(GL_ELEMENT_ARRAY_BUFFER, sizeof(indices), indices, GL_STATIC_DRAW);

glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(float), (void*)0);
glEnableVertexAttribArray(0);

// unbind VBO
glBindBuffer(GL_ARRAY_BUFFER, 0); 

// common practice to unbind the VAO once initialization is complete
glBindVertexArray(0);


// ..:: Drawing code (in render loop) ::..
glUseProgram(shaderProgram);
glBindVertexArray(VAO);
glDrawElements(GL_TRIANGLES, 6, GL_UNSIGNED_INT, 0);
glBindVertexArray(0);
```

## Polygon Modes
- By default, OpenGL renders primitives by filling the shapes with color. This can be changed to **Wireframe Mode**, where shapes are not filled and only the lines are shown.
- <mark class="hltr-trippy">function</mark> `void glPolygonMode(GLenum face, GLenum mode)` <mark class="hltr-trippy">:</mark> select a polygon rasterization mode.
	- `GLenum face` : specifies the polygons that mode applies to. Must be `GL_FRONT_AND_BACK` for front and back facing polygons.
	- `GLenum mode` : specifies how polygons will be rasterized. Accepted values are `GL_POINT`, `GL_LINE`, and `GL_FILL`.
- Using key input to switch polygon mode:

```C++
void processInput(GLFWwindow* window)
{
	if (glfwGetKey(window, GLFW_KEY_ESCAPE) == GLFW_PRESS)
		glfwSetWindowShouldClose(window, true);

	if (glfwGetKey(window, GLFW_KEY_1) == GLFW_PRESS)
		glPolygonMode(GL_FRONT_AND_BACK, GL_FILL);

	if (glfwGetKey(window, GLFW_KEY_2) == GLFW_PRESS)
		glPolygonMode(GL_FRONT_AND_BACK, GL_LINE);

	if (glfwGetKey(window, GLFW_KEY_3) == GLFW_PRESS)
		glPolygonMode(GL_FRONT_AND_BACK, GL_POINT);
}
```

## Side note : De-allocation
- Although calling `glfwTerminate()` frees up all the resources, it's generally a good practice to de-allocate the resources explicitly, especially in a case where some of the resources are *not* managed by GLFW.

```C++
// optional: de-allocate all resources
glDeleteVertexArrays(1, &VAO);
glDeleteBuffers(1, &VBO);
glDeleteBuffers(1, &EBO);
glDeleteProgram(shaderProgram);
```

## Additional Resources
- http://antongerdelan.net/opengl/hellotriangle.html : Anton Gerdelan's take on rendering the first triangle.
- https://open.gl/drawing : Alexander Overvoorde's take on rendering the first triangle.
- http://antongerdelan.net/opengl/vertexbuffers.html : some extra insights into vertex buffer objects.
- https://learnopengl.com/In-Practice/Debugging : there are a lot of steps involved in this chapter; if you're stuck it may be worthwhile to read a bit on debugging in OpenGL (up until the debug output section).

## Source Code
Refer to [[cpp_hello_rectangle_code]]

## Exercises
- Draw 2 triangles using a single call to `glDrawArrays`
- Draw 2 triangles using 2 separate calls to `glDrawArrays`
- Draw 2 triangles of different color by using 2 separate fragment shaders.
