
# Hello Triangle
- In OpenGL, everything is in 3D space. However, the screen/window is a 2D array of pixels, which means a large part of OpenGL's work is about transforming all 3D coordinates to pixels that fit on the screen.
- The Graphics Pipeline of OpenGL manages the process of transforming 3D coordinates to 2D pixels. It can be divided into two large parts:
	- Transforming 3D coordinates into 2D coordinates
	- Transforming the 2D coordinates into actual colored pixels.
- The Graphics Pipeline takes as input a sec of 3D coordinates and transforms these to colored 2D pixels on the screen.
- The Graphics Pipeline can be divided into several steps where each step requires the output of the previous step as its input.
	- All of these steps are highly specialized, and can easily be executed in parallel.
	- Because of the parallel nature of the Graphics pipeline, GPUs of today have thousands of small processing cores to quickly process data within the Graphics Pipeline.
	- The processing cores run small programs, known as **Shaders**, on the GPU for each step of the pipeline.
- Shaders are configurable by the developer, which allows for custom shaders to replace the existing default shaders.
	- This gives more fine-grained control over specific parts of the pipeline.
- Shaders are written in the OpenGL Shading Language (GLSL).
- Abstract representation of all the stages of the Graphics Pipeline:
  ![[opengl_graphics_pipeline.png]]
- **Vertex** (**Vertices** in plural) : a data structure that describes certain attributes, like the position of a point in 2D/3D space, or multiple point on a surface. Vertices play a crucial role in creating and manipulating shapes and paths in graphics software. They are the fundamental units used to define the structure of 3D models.
- **Vertex Data** : the information associated with each vertex, which can include the position of the vertex in 2D/3D space, color, texture coordinates, normal vectors, tangent vectors, and more. The vertex data is crucial for setting out how everything will look.
- **Vertex Attributes** : an input variable to a shader that is supplied with per-vertex data.
- (note) a vertex is a dot, a vertex data is information on the dot, and a vertex attribute is a variable that corresponds to an element of information.
- In order for OpenGL to know what to make of a collection of coordinates (and color values), OpenGL requires a hint on the type of render to form with the data.
	- The hint indicates whether the data be rendered as a collection of points, a collection of triangles, or a long line. These hints are called **Primitives**.
	- Primitives are given to OpenGL while calling any of the drawing commands.
	- Some of the primitives are `GL_POINTS`, `GL_LINE_STRIP`, and `GL_TRIANGLES`.
- In the first part of the Graphics Pipeline, the vertex shader takes a single vertex as an input.
- The main purpose of the **Vertex Shader** is to transform 3D coordinates into different 3D coordinates (more on this later).
	- The vertex shader allows for some basic processing on the vertex attributes.
- The output of the Vertex Shader is *optionally* passed to the **Geometry Shader**.
	- The Geometry Shader has the ability to generate other shapes by emitting new vertices to form new (or other) primitive(s). For example, it can generate two triangles out of one triangle.
	- The Geometry Shader takes a collection of vertices (that form a primitive) as input.
	- (note) The Geometry Shader is useful to implement [Shadow Volume](https://developer.nvidia.com/gpugems/gpugems/part-ii-lighting-and-shadows/chapter-9-efficient-shadow-volume-rendering).
- The **Primitive Assembly** stage takes all the vertices from the vertex (or geometry) shader as input, and then assembles all the point(s) in the primitive shape given.
	- (note) The purpose of Primitive Assembly step is to convert a vertex stream into a sequence of base primitives (base primitives being lines, triangles, rectangles, and etc.). For example, a sequence of 12 vertices generate 11 line (base) primitives. A sequence of 3 vertices can produce a triangle primitive as well.
- The output of the Primitives Assembly stage is then passed on to the **Rasterization Stage**, where it maps the resulting primitive(s) to the corresponding pixels on the screen.
- The result of the Rasterization Stage is the data required for OpenGL to render a single pixel, and it is referred to as a **Fragment**.
- The resulting Fragments from the Rasterization Stage goes through **Clipping**, where it discards all fragments that are outside of the "view".
- The Fragments are then sent to **Fragment Shader**, where the final color of a pixel is calculated.
	- This is usually the stage where all the advanced OpenGL effects occur. The Fragment Shader contains data about the 3D scene that it can use to calculate the final pixel color (like lights, shadows, color of the lights and so on).
- The final object will then pass through **Alpha Test and Blending stage**, where the following occurs:
	1. the corresponding depth/stencil value of the Fragment is evaluated to determine whether the fragment is front or behind other objects. If a fragment is behind a non-transparent object, the fragment is discarded.
	2. the corresponding alpha value (opacity) of the Fragment is evaluated, and then blends the Fragment with other objects as needed.
- There are other stages other than the 6 stages mentioned above, such as the Tessellation Stage and the Transform Feedback Loop. This will be covered later.
- In modern OpenGL, the developer is required to define at least a vertex shader and a fragment shader, as there are no default vertex/fragment shaders on the GPU.

## Vertex Input
- OpenGL is a 3D graphics library, so all coordinates that are specified in OpenGL are in 3D.
- (note) **Screen Space Coordinates**, aka **Device Coordinates**, is a coordinate system where a point is described as coordinates in range between (0, 0) and (width, height) of the window.
	- Coordinate (0, 0) is at the top-left corner of the window.
- OpenGL only processes 3D coordinates that are in **Normalized Device Coordinates (NDC)**, which means the coordinates must be within a specific range between `-1.0` and `1.0` on all 3 axes.
	- All coordinates outside this region will not be displayed on screen.
	- (note) NDC == range (0,0) ~ (width, height) converted to range (-1, 1) ~ (1, -1).
- For the purpose of rendering a single triangle, a total of three vertices with each vertex having a 3D coordinate must be defined in NDCs as a `float array`.

```C++
// Three vertices for a single triangle,
// with coordinates x, y, z (depth)
float vertices[] = {
	-0.5f, -0.5f, 0.0f,
	0.5f, -0.5f, 0.0f,
	0.0f, 0.5f, 0.0f
}
```

![[ndc.png]]

- Sending the Vertex Data (of a single triangle) to the Vertex Shader is done by:
	1. Allocating memory on the GPU where the Vertex Data will be stored,
	2. Configuring how OpenGL should interpret the memory, and
	3. Specifying how to send the data to the GPU
- The **Vertex Buffer** is the allocated memory on the GPU that can store a large number of vertices.
	- (note) rendering from a large chunk of data stored on the GPU is much faster than receiving a stream of data one vertex at a time from the CPU.
- The allocated memory on the GPU is managed by **Vertex Buffer Object (VBO)** which provides methods for uploading Vertex Data to GPU.
	- `void glGenBuffers(GLsizei n, GLuint *buffers)` : returns `n` buffer object names in `buffers`. In other words, `n` number of buffer object names will be generated, and then the array `buffers` will be populated by those names.
	- `void glBindBuffer(GLenum target, GLuint buffer)` : bind a named buffer object. In other words, buffer object names `buffer` (which are generated with `glGenBuffers()`) will be bound to a buffer object `target`. At this point, the state of the buffer object is set to "current" and it is ready to allocate GPU memory for vertex input.
	- `void glBufferData(GLenum target, GLsizeiptr size, const GLvoid *data, GLenum usage)` : creates and initializes a buffer object's data store. In other words, the buffer object `target` will allocate GPU's memory of specific `size` (in bytes), store `data` in the buffer, and "expect" the buffer to be used for some `usuage` (for optimization).
- Example of setting up Vertex Input:

```C++
// one buffer name
unsigned int VBO;
glGenBuffers(1, &VBO);

// one buffer name bound to an array buffer
glBindBuffer(GL_ARRAY_BUFFER, VBO);

// vertex data is stored on the named array buffer, expected to be drawn
glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC DRAW)
```

## Vertex Shader
- Once a vertex data is ready, it goes through the Vertex Shader. The Vertex Shader is written in GLSL (OpenGL Shading Language).
- (note) a Shader is a type of program that runs on GPU. Just like a vertex data that is stored on GPU, a shader is also stored on GPU.
- Example vertex shader written in GLSL:

```C
#version 330 core
layout (location = 0) in vec3 a_pos;

void main()
{
	gl_Position = vec4(a_pos.x, a_pos.y, a_pos.z, 1.0);
}
```

- GLSL is similar to C language.
- Each shader begins with a declaration of its version; `#version 330 core`.
	- It indicates that the OpenGL 3.3 Core Profile is being used.
- GLSL has a vector datatype that contains 1 to 4 floats based on its postfix digit.
	- `vec3` means it is a vector type that contains 3 floats (for x, y, z in this case).
- `layout (location = 0)` : this is a layout qualifier that specifies the location of the input variable. The number `0` is the location index.
- `in vec3 a_pos` : this declares an input variable `a_pos` for the shader. The `in` keyword means it's an input to the shader. `vec3` is the type of the variable.
- `gl_Position` is a pre-defined variable of type `vec4` with the components being x, y, z, and w. The x, y, and z components represent the position of the vertex in 3D space, while the w component is used for perspective division.
- The source code for the Vertex Shader must be passed onto the GPU as a C-style string `const char*`. This is basically a pointer to the character array.
- (note) Loading shaders from external files is a common practice in larger OpenGL projects. Below is an example code for loading shaders:

```C++
#include <fstream>
#include <sstream>
#include <string>

std::string LoadShader(const std::string& filepath)
{
    std::ifstream shaderFile(filepath);
    std::stringstream shaderStream;

    // Read file's buffer contents into streams
    shaderStream << shaderFile.rdbuf();

    // close file handlers
    shaderFile.close();

    // Convert stream into string
    return shaderStream.str();
}

// Usage:
std::string vertexShaderSource = LoadShader("path/to/your/vertex_shader.glsl");
std::string fragmentShaderSource = LoadShader("path/to/your/fragment_shader.glsl");

```

## Compiling a Shader
- Shaders are typically loaded during the initialization of the graphics program (during runtime). The shader files are read, compiled, and linked into a shader program that can be used to render graphics.
- <mark class="hltr-trippy">function</mark> `GLuint glCreateShader(GLenum shaderType)` <mark class="hltr-trippy">:</mark> creates an empty shader object and returns a non-zero value by which it can be referenced.
	- `shaderType` can be `GL_VERTEX_SHADER`, `GL_GEOMETRY_SHADER`, or `GL_FRAGMENT_SHADER`.
	- example : `GLuint vertexShader = glCreateShader(GL_VERTEX_SHADER);`
- <mark class="hltr-trippy">function</mark> `void glShaderSource(GLuint shader, GLsizei count, const GLchar **string, const GLint *length)` <mark class="hltr-trippy">:</mark> sets the source code in shader with the source code provided by the `string`.
	- example : `glShaderSource(vertexShader, 1, &vertexShaderSource, NULL);`
	- OpenGL copies the shader source code strings when `glShaderSource` is called, which means an application may free its copy of the source code strings immediately after the function returns.
- <mark class="hltr-trippy">function</mark> `void glCompileShader(GLuint shader)` <mark class="hltr-trippy">:</mark>  compiles the source code strings that have been stored in the shader object specified by `shader`.
	- example : `glCompileShader(vertexShader);`
- Check for compilation error:

```C++
int success;
char infoLog[512];
glGetShaderiv(vertexShader, GL_COMPILE_STATUS, &success);

if(!success)
{
	glGetShaderInfoLog(vertexShader, 512, NULL, infoLog);
	std::cout << "ERROR::SHADER::VERTEX::COMPILATION_FAILED\n" << infoLog << std::endl;
}
```

## Fragment Shader
- The Fragment Shader is all about calculating the color output of the pixels.
- The Fragment Shader source code:

```C
#version 330 core
out vec4 f_color;

void main()
{
	f_color = vec4(1.0f, 0.5f, 0.2f, 1.0f);
}
```

- The Fragment Shader only requires one output variable; a vector of size 4 that defines the final color output.
- The output values of the Fragment Shader is declared with the `out` keyword, with variable name `f_color`.
- The color output is in `RGBA` format, with values between `0` and `1`.
- The process for compiling a fragment shader is similar to the Vertex Shader, and the only difference is the `GL_FRAGMENT_SHADER` constant as the shader type.
- Compile code:

```C++
unsigned int fragmentShader;
fragmentShader = glCreateShader(GL_FRAGMENT_SHADER);
glShaderSource(fragmentShader, 1, &fragmentShaderSource, NULL);
glCompileShader(fragmentShader);
```

- Once all the shaders are compiled, both the shader objects are ready to be linked to a shader program.

## Shader Program
- A **Shader Program** object is the final linked version of multiple shaders combined.
- To use the compiled shaders, they must be linked to a shader program object.
- The Shader Program then must be activated when rendering objects.
- When linking the shaders into a program, it links the output of each shader to the inputs of the next shader. This is where linking errors will occur if outputs and their corresponding inputs do not match.
- Creating a Shader Program & linking the shaders:

```C++
unsigned int shaderProgram;
shaderProgram = glCreateShader();

glAttachShader(shaderProgram, vertexShader);
glAttachShader(shaderProgram, fragmentShader);
glLinkProgram(shaderProgram);
```

- Checking for errors:

```C++
glGetProgramiv(shaderProgram, GL_LINK_STATUS, &success);
if(!success) {
	glGetProgramInfoLog(shaderProgram, 512, NULL, infoLog);
	//...
}
```


- The Shader Program can then be activated by `glUseProgram(ShaderProgram);`.
- Once the Shader Program object is activated, every shader and rendering call afterwards will use this program object (and thus the shaders).
- Once the shader objects are linked to the program object, they are no longer needed. They can be deleted by:

```C++
// common practice, frees up space
glDeleteShader(vertexShader);
glDeleteShader(fragmentShader);
```

- The last step before rendering is to link the Vertex Attributes.

## Linking Vertex Attributes
- While the Vertex Shader provides great flexibility by allowing devs to specify any input (in the form of Vertex Attribs), it comes with a bit of complexity as the connection between input data and the vertex attributes need to be manually specified.
- As of now (following the guide for code), the vertex buffer data is formatted as follows:
	- ![[vertex_attribute_pointer.png]]
	- There are three vertices, each of the vertex with a position in 3D coordinates.
	- Each position is composed of 3 values (x, y, z).
	- Each positional value is stored as 32-bit (4 byte) floating point value.
	- The values are tightly packed in the array, meaning that there is no space (or other values) between each set of 3 values.
	- The first value in the data is at the beginning of the buffer (no offset).
- With the format in mind, OpenGL is to be instructed to interpret the Vertex Data (per Vertex Attribute). Like so:

```C++
glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(float), (void*)0);
glEnableVertexAttribArray(0);
```

- <mark class="hltr-trippy">function</mark> `void glVertexAttribPointer(index, size, type, normalized, stride, *pointer)` <mark class="hltr-trippy">:</mark> specifies the location and data format of the array (of generic vertex attributes) at `index` to use when rendering.
	- `GLuint index` : specifies which Vertex Attribute is to be configured. This value should match the location of the `position` Vertex Attribute in the Vertex Shader - `layout (location = 0)`. 
	- `GLint size` : specifies the number of components in the Vertex Attribute. For example, if the Vertex Attribute is a `vec3`, then the `size` should be set to 3.
	- `GLenum type` : specifies the type of the data; float values is indicated with `GL_FLOAT`.
	- `GLboolean normalized` : specifies whether the data should be normalized, but only if the data is an integer. If this is set to `GL_TRUE`, the integer data is normalized (0~1, or -1~1). In the case of the float data, `GL_FALSE` will suffice.
	- `GLsizei stride` : specifies the interval between the sets of data. For example, a 3D positional data is a set of 3 float values, therefore the interval between each data is the size of 3 float values (in this case, 4 bytes times 3 == 12 bytes).
	- `const GLvoid *pointer` : specifies the offset where the Vertex Attribute begins in the buffer. Normally the data is at the start of the data array, therefore the value is `0`. Because there is some complex system involved with the offset (will be discussed later), the value needs to be casted as a void pointer.
- Once the instruction to interpret the Vertex Data is given to OpenGL via `glVertexAttribPointer()` function, the Vertex Attribute needs to be enabled with `glEnableVertexAttribArray(index)` function. `index` is the index of the Vertex Attribute, which in this case is `0`.
- So far, the Vertex Data is in the buffer, and OpenGL is instructed to parse the Vertex Attributes from the data. This process is to be repeated every time an object is drawn, which is rather repetitive if there are multiple Vertex Attributes and multiple shapes to draw. The way to save the state configuration is to use VAO.

## Vertex Array Object
- A **Vertex Array Object (VAO)** is an object that contains one or more VBOs, and is designed to store the information for a complete rendered object. The main purpose of VAOs is to simplify the rendering process by saving buffer and attribute configurations.
- Core OpenGL requires that VAO is used - if a VAO is not bound, OpenGL will most likely refuse to draw.
- A Vertex Array Object stores the following:
	- Calls to `glEnableVertexAttribArray` or `glDisableVertexAttribArray`
	- VA configurations via `glVertexAttribPointer`
	- VBOs associated with VAs by calls to `glVertexAttribPointer`
- In order to use a VAO, an ID must be generated and then be bound to a VAO. Then the VA configurations are set to the VAO, which is then enabled for use.
- Example VAO code:

```C++
// 1. create VAO
unsigned int VAO;
glGenVertexArray(1, &VAO);

// 2. bind Vertex Array Object
glBindVertexArray(VAO);
// 3. copy our vertices array in a buffer for OpenGL to use
glBindBuffer(GL_ARRAY_BUFFER, VBO);
glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);
// 4. then set our vertex attributes pointers
glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(float), (void*)0);
glEnableVertexAttribArray(0);

// 5. draw the object (in render loop)
glUseProgram(shaderProgram);

// 6. unbind VAO
glBindVertexArray(0);
```

## Render
- `glDrawArrays` function is called to draw primitives using the current active shader, the previously defined VA configs, and with the VBO's Vertex Data.
- <mark class="hltr-trippy">function</mark> `void glDrawArrays(mode, first, count)` <mark class="hltr-trippy">:</mark> render primitives from array data.
	- `GLenum mode` : specifies what kind of primitives to render.
	- `GLint first` : specifies the starting index in the enabled arrays.
	- `GLsizei count` : specifies the number of indices to be rendered.
- Example : `glDrawArrays(GL_TRIANGLES, 0, 3)`

## Source Code
Refer to [[cpp_hello_triangle_code]]
