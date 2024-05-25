# Getting Started
## OpenGL
### What is OpenGL
- OpenGL is a specification that is developed and maintained by the Khronos Group.
	- Even though OpenGL is mainly considered an API, OpenGL itself does not provide any functions.
- The OpenGL specificaton specifies exactly what the result/output of each funtion should be and how it should perform.
- It is up to the developers *implementing* this spec to come up with a solution of how this function should operate (in other words, it's up to GPU to provide functionalities as according to this spec).
- Since the OpenGL spec does not give implementation details, the actual developed versions of OpenGL are allowed to have different implementations, as long as their results comply with the spec.
- The people develping the actual OpenGL libraries are usually the GPU manufacturrs. Each GPU supports specific versions of OpenGL. Because different versions of OpenGL exists for different GPUs, it is the fault of the GPU manufacturers if OpenGL behaves in a way that it shouldn't.

### Core-Profile vs Immediate Mode
- Immediate Mode (aka Fixed Function Pipeline) is an old way to develope with OpenGL.
	- Immediate Mode abstracted a lot of the actual operations of OpenGL. While it is easy to learn, it is harder to grasp how OpenGL actually operates.
	- Most of the functionalitiy of OpenGL was hidden inside the library and developers did not have much control over how OpenGL does its calculations.
	- The Immediate Mode is easy to use and to understand, but it is also extremely inefficient.
	- The Immediate Mode is deprecated from version 3.2 onwards.
- Core-Profile is replaced Immediate Mode and it is much more flexible and efficient.
	- Core-Profile forces developers to use modern practices.
	- Core-Profile requires the developer to truly understand OpenGL and graphics programming.

### Versions
- At the time of writing, OpenGL 4.6 is the newest version.
- It is recommended to learn OpenGL 3.3 instead because all concepts and techniques remain the same with newer versions. The newer versions introduce slightly more efficient/useful wys to accomplish the same tasks without changing the OpenGL's core mechanics.
- The most recent version of OpenGL faces an issue where only the most modern GPUs are able to support it. Most developers generally target lower versions of OpenGL and optionally enable higher version functionality.

### Extensions
- A great feature of OpenGL is its support of extensions.
- Whenever a grphics company comes up with a new technique or a new large optimization for rendering, this is often found in an extension implemented in the drivers.
- If the hardware an application runs on supports such an extension, the developer can use the functionality provided by the extension for more advanced/efficient graphics.
	- This way, a graphics developer can still use these new rendering techniques without having to wait for OpenGL to include the functionality in its future versions, simply by checking if the extension is supported by the GPU.
- The developer has to query whether any of these extensions are available before using them (or use an OpenGL extension library).
- With OpenGL 3.3, an extension is rarely needed for most techiques.

### State Machine
- OpenGL is a large state machine; it is a collection of variables that define how OpenGL should currently operate.
- The state of OpenGL is commonly referred to as the OpenGL __context__.
- When using OpenGL, its state can be changed by setting some options and manipulating some buffers. Then, render can be done using the current context.
- Telling OpenGL to switch from drawing triangles to drawing lines is done by chaging some context variable that sets how OpenGL should draw (effectively changing the OpenGL's state).
	- Once the context is set to "Draw Lines", the next drawing commands will draw lines instead of triangles.
- Working with OpenGL is all about using __state-changing__ functions that change the context, and __state-using__ functions that perform some operations based on the current state of OpenGL.

### Objects
- The OpenGL libraries are written in C, and allows for many derivations in other languages.
- Since many of C's language-constructs do not translate well to other higher-level languages, OpenGL was developed with several abstarctions in mind.
	- One of those abstractions are objects in OpenGL.
- An object in OpenGL is a collection of options that represents a subset of OpenGL's state.
	- For example, an object can represent the settings of the drawing window.

### Additional Resources
- [OpenGL Official Website](https://www.opengl.org/)
- [OpenGL specifications and extensions (Khronos Registry)](https://registry.khronos.org/OpenGL/index_gl.php)

## Setting Up Libraries
- First thing to do before drawing anything with OpenGL is to create an OpenGL context and an application window to draw in.
	- These are operations that are specific per operating system, and OpenGL itself does not provide these operations.
	- It is up to the developers to create a window, define a context, and handle user input.
- There are a few libraries that provide such functionalities, some specifically aimed at OpenGL.
	- Some of the more popular libraries are GLUT, SDL, SFML and GLFW.
- GLFW library is used on the LearnOpenGL course.
- Additionally, GLAD library is used to locate OpenGL functions.

### GLFW
- GLFW is a library specifically targeted at OpenGL.
- GLFW provides the bare necessities required for rendering to the screen, such as creating an OpenGL context, defining window parameters, and handling user input.

### Building GLFW
- Download GLFW (64-bit) source code from http://www.glfw.org/download.html
- Although GLFW does come pre-compiled, it is better to compile in the system for better compatibility.
- The items that are to be used are:
	- The resulting library from compilation
	- The `include` folder
- Not everyone uses the same setups for their project, which means that the project/solution files need to be converted to match the setup it is to be used in. CMake is the tool that is used specifically for that purpose.

#### CMake
- CMake is a tool that can generate project/solution files of the user's choice from a collection of source code files using pre-defined CMake scripts.
- Download CMake from http://www.cmake.org/cmake/resources/software.html
- Convert GLFW project files using CMake:
	1. Extract GLFW source code zip file.
	2. Open CMake
	3. Choose the root folder of GLFW source code as the source code folder.
	4. Create a few folder `build` inside the root folder, and select it as the build target folder.
	5. Click the Configure button, then choose the generator (an IDE of choice, Visual Studio) on the configure window.
	6. Click Finish to configure.
	7. Leave the options as default, then click Generate to compile.
	8. Check to see that the resulting project files are created inside the build folder.

![[Pasted image 20240521103035.png]]

#### Compilation
- Once the project files are converted using CMake, a project file `GLFW.sln` can be found inside the build folder. Open it with Visual Studio and proceed to build (compile).
- Compiled library `glfw3.lib` can be found in `build/src/Debug` folder.
- There are two approaches to using third party libraries:
	- Add the library to the IDE's `/lib` folder.
	- (Recommended) Set a location (i.e. `C://cpp_libraries`) where all the header files/libraries from third party libraries are to be stored at. Create `/include` folder and `/lib` folder.
- Move files from GLFW's `/include` folder to third party libaries `/include` folder.
- Move `glfw3.lib` to third party libraries `/lib` folder.

### First Project
- Create an empty project with Visual Studio.
- Make sure the debug mode is set to `x64`.

### Linking
- In order for the project to use GLFW, the library needs to be linked with the project.
- This can be done by specifying `glfw3.lib` in the linker settings.
	- The project does not yet know where to find `glfw3.lib` because third party libraries are stored in a different directory. This directory needs to be added to the project first.
- Project Libraries Configuration:
	1. Right-click the project name in the solution explorer, and then click on `properties` on the right click menu.
	2. On the Property Pages window, select `VC++ Directories`.
	3. Edit `Library Directories` to add `/lib` folder. Edit `Include Directories` to add `/include` folder.
	   ![[Pasted image 20240521121331.png]]
	4. Under `Linker` > `Input`, edit `Additional Dependencies` by adding `glfw3.lib`.
	   ![[Pasted image 20240521110212.png]]

#### OpenGL library on Windows
- On Windows, `opengl32.lib` comes with the Microsoft SDK (which is installed by default with VS).
- Add `opengl32.lib` to the linker settings.

### GLAD
- Different GPUs come with different versions of OpenGL drivers, which means location of most of its functions is not known at compile-time and needs to be queried at run-time.
- It is the task of the developer to retrieve the location of the functions that they need, and store them in function pointers for later use.
- Retrieving those locations is OS-specific, and it can get rather complex and cumbersome to locate functions and store them in function pointers.
- GLAD library simplifies the process of locating/storing OpenGL functions.

#### Setting up GLAD
- Go to http://glad.dav1d.de/
	- Set Language to C++
	- Set Specification to OpenGL
	- Set API gl to Version 3.3
	- Set Profile to Core
	- Under Options, check Generate a loader
	- Click *Generate* to produce library files
- Download the zip file. It should contain `/include` folder and `/src` folder.
- Inside `/include` folder, there should be `glad` folder and `KHR` folder. Move them to the `C://cpp_libraries/include` folder.
- Inside `/src` folder, there is `glad.c` file. Copy & paste this to the project folder. Then, add it to the `Source Files` on Visual Studio.
- Create a file and name it `Main.cpp`. Type `#include <glad/glad.h>` and build. There should be no errors.

### Additional Resources
- Official GLFW Guide : https://www.glfw.org/docs/latest/window_guide.html
- http://www.opengl-tutorial.org/miscellaneous/building-your-own-c-application/
- http://wiki.codeblocks.org/index.php?title=Using_GLFW_with_Code::Blocks
- http://www.cmake.org/runningcmake/
- Writing a build system under Linux : https://learnopengl.com/demo/autotools_tutorial.txt
- Polytonic/Glitter (a simple boilerplate project) : https://github.com/Polytonic/Glitter

## Hello Window
- This chapter will cover writing a code to open a simple application window.
- In `Main.cpp` file, add the following directives to the top.

```C++
#include<iostream>
#include<glad/glad.h>
#include<GLFW/glfw3.h>
using namespace std;
```

- It is important to include GLAD before other header files that require OpenGL (like GLFW).
- Create the `main` function where GLFW window will be instantiated.

```C++
int main()
{
	glfwInit();
	glfwWindowHint(GLFW_CONTEXT_VERSION_MAJOR, 3);
	glfwWindowHint(GLFW_CONTEXT_VERSION_MINOR, 3);
	glfwWindowHint(GLFW_OPENGL_PROFILE, GLFW_OPENGL_CORE_PROFILE);

	return 0;
}
```

- `glfwInit()` : initializes GLFW library, which must be done before anything else.
- `glfwWindowHint()` : used to configure GLFW.
	- First argument sets the option to be configured.
	- Second argument sets the (integer) value of the option.
	- GLFW's options and values are prefixed with `GLFW_`.
	- A list of all the possible options and its corresponding values can be found at [GLFW's Window Handling Documentation](https://www.glfw.org/docs/latest/window.html#window_hints).
	- `GLFW_CONTEXT_VERSION_MAJOR` & `*_MINOR` : the option to set the version of the OpenGL that is being used. Setting it to 3 and 3 indicates that the version is `3.3`.
	- `GLFW_OPENGL_PROFILE` : the option to set the profile between Immediate Mode and Core Profile. In this case, use `GLFW_OPENGL_CORE_PROFILE` to set its value to core profile.
- Create a window object. This window object holds all the windowing data and is required by most of GLFW's other functions.

```C++
// settings
const unsigned int SCR_WIDTH = 800;
const unsigned int SCR_HEIGHT = 600;

int main()
{
//..
	GLFWwindow* window = glfwCreateWindow(SCR_WIDTH, SCR_HEIGHT, "LearnOpenGL", NULL, NULL);
	if (window == NULL)
	{
		cerr << "Failed to create GLFW window" << endl;
		glfwTerminate();
		return -1;
	}
	glfwMakeContextCurrent(window);
//..
}
```

- `glfwCreateWindow()` : creates a window object and its associated context.
	- First & second argument sets the window's width and height.
	- Third argument sets the window's title.
	- Fourth & fifth argument is ignored for now.
	- The function returns a `GLFWwindow` object, which is needed for other GLFW operations.
- `glfwTerminate()` : once GLFW is initialized, it needs to be terminated once operations are done.
- `glfwMakeContextCurrent()` : sets the context as the main context on the current thread.

### GLAD
- GLAD manages function pointers for OpenGL, so it nees to be initialized before any OpenGL function is called.

```C++
int main()
{
//..
	if (!gladLoadGLLoader((GLADloadproc)glfwGetProcAddress))
	{
		cerr << "Failed to initialize GLAD" << endl;
		return -1;
	}
//..
}
```

- `glfwGetProcAddress` : the function to load the address of the OpenGL function pointers (which is OS-specific).
- `gladLoadGLLoader()` : initializes GLAD with the address function.

### Viewport
- **Window** : a rectangular area that defines which portion of the data is viewed on the screen.
- **Viewport** : a rectangular area that defines where the data is positioned.
- Window and Viewport are almost synonyous to each other. An image is "drawn" on Viewport, and the drawn image on the Viewport is then displayed on the Window.
- Note that there can be multiple viewports on a window. Each of these viewports can draw the same image with different projections.
- Once GLFW and GLAD libraries are initialized, a Viewport can be set by calling the function `glViewport(0, 0, width, height)`.
	- First & second argument sets the location of viewport in respect to the window.
	- Third & fourth argument sets the width and height of the viewport.

#### Resize
- A custom callback function can be defined to resize the viewport when the window is resized.

```C++
void framebuffer_size_callback(GLFWwindow* window, int width, int height)
{
	glViewport(0, 0, width, height);
}
```

- The custom callback function is then registered with `glfwSetFramebufferSizeCallback(window, framebuffer_size_callback)`.
	- Callback functions are registered after the window is created and before the render loop is initiated (which will be covered next).

### Render Loop
- A loop ("Render Loop") is required to repeatly draw an image until the program has been explicitly told to stop.
- A very simple render loop:

```C++
int main()
{
//..
	while (!glfwWindowShouldClose(window))
	{
		glfwSwapBuffers(window);
		glfwPollEvents();
	}
//..
}
```

- `glfwWindowShouldClose()` : checks at the start of each loop iteration if GLFW has been instructed to close. If so, the function returns true and the render loop stops running.
- `glfwSwapBuffers()` : swaps the color buffer (a large 2D buffer that contains color values for each pixel in the window) that is used to render to during this render iteration, and show it as output to the screen.
- `glfwPollEvents()` : checks if any events are triggered (like keyboard/mouse input), updates the window state, and calls the corresponding callback functions.
- **Double Buffer** : when an application draws in a single buffer, the resulting image may display flickering issues. This is because the resulting output image is not drawn in an instant but drawn pixel by pixel (usually from left to right, top to bottom) instead, which causes unintended artifacts. To circumvent these issues, windowing applications apply a double buffer for rendering.
	- The front buffer contains the render complete image that is shown at the screen.
	- The back buffer contains the image that is being drawn by the rendering commands.
	- As soon as all the rendering commands are finished, the buffers are then swapped. In the end, the screen only shows the render complete images, effectively removing all the aforementioned artifacts.
- Once all operations are done and the window is closed, GLFW needs to be terminated by calling `glfwTerminate()`.
- At this point, the program is ready to be compiled. The compiled program outputs a simple window with a black image.
#### Input
- A simple input function can be used to close the application with an `ESC` key:

```C++
void processInput(GLFWwindow* window)
{
	if (glfwGetKey(window, GLFW_KEY_ESCAPE) == GLFW_PRESS)
		glfwSetWindowShouldClose(window, true);
}
```

- `glfwGetKey()` : a function that checks whether a specified key is pressed. First argument is the window, and the second argument is the key. If the user presses the key, the function returns `GLFW_PRESSS`. Otherwise, it returns `GLFW_RELEASE`.
- `glfwSetWindowShouldClose()` : sets the state of the window to close. First argument is the window, and the second argument is the boolean value. If the second argument is set to `true`, then calling the function `glfwWindowShouldClose()` will return true. In this case, the render loop will stop.
- **Frame** : an iteration of the render loop.
- By inserting the `processInput()` function inside the render loop, the program checks at every frame if the `ESC` key is pressed and react accordingly.

#### Rendering
- In a typical rendering program, the screen's color buffer needs to be cleared at the start of every frame, otherwise the results from the previous frame would be visible.
- The screen's color buffer can be cleared by calling `glClear(GL_COLOR_BUFFER_BIT)`.
	- There are other bits, such as `GL_DEPTH_BUFFER_BIT` and `GL_STENCIL_BUFFER_BIT`. For now, only the color buffer will be cleared.
- Normally the screen will clear with the default color of black, but the color to clear the screen can be set by calling `glClearColor(r, g, b, a)` before `glClear()`. Each argument can accept a value between `0.0` and `1.0`.
- Note that `glClearColor()` is a **state-setting function**, and `glClear()` is a **state-using function**.
- Putting it all together, the render loop code looks like this:

```C++
int main()
{
//..
	while (!glfwWindowShouldClose(window))
	{
		processInput(window);
		
		glClearColor(0.2f, 0.3f, 0.3f, 1.0f);
		glClear(GL_COLOR_BUFFER_BIT);

		glfwSwapBuffers(window);
		glfwPollEvents();
	}
//..
}
```

### Source Code
Refer to [[cpp_hello_window_code]]

## Hello Triangle
- In OpenGL, everything is in 3D space. However, the screen/window is a 2D array of pixels, which means a large part of OpenGL's work is about transforming all 3D coordinates to pixels that fit on the screen.
- The Graphics Pipeline of OpenGL manages the process of transforming 3D coordinates to 2D pixels. It can be divided into two large parts:
	- Transforming 3D coordinates into 2D coordinates
	- Transforming the 2D coordinates into actual colored pixels.
- The Graphics Pipeline takes as input a sec of 3D coordinates and transforms these to colred 2D pixels on the screen.
- The Graphics Piepline can be divided into several steps where each step requires the output of the previous step as its input.
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
	- Some of the primitives are `GL_POINTS`, `GL_TRIANGLES`, and `GL_LINE_STRIP`.
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

### Vertex Input
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

### Vertex Shader
- Once a vertex data is ready, it goes through the Vertex Shader. The Vertex Shader is written in GLSL (OpenGL Shading Language).
- (note) a Shader is a type of program that runs on GPU. Just like a vertex data that is stored on GPU, a shader is also stored on GPU.
- Example vertex shader written in GLSL:

```C
#version 330 core
layout (location = 0) in vec3 aPos;

void main()
{
	gl_Position = vec4(aPos.x, aPos.y, aPos.z, 1.0);
}
```

- GLSL is similar to C language.
- Each shader begins with a declaration of its version; `#version 330 core`.
	- It indicates that the OpenGL 3.3 Core Profile is being used.
- GLSL has a vector datatype that contains 1 to 4 floats based on its postfix digit.
	- `vec3` means it is a vector type that contains 3 floats (for x, y, z in this case).
- `layout (location = 0)` : this is a layout qualifier that specifies the location of the input variable. The number `0` is the location index.
- `in vec3 aPos` : this declares an input variable `aPos` for the shader. The `in` keyword means it's an input to the shader. `vec3` is the type of the variable.
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

### Compiling a Shader
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

### Fragment Shader
- The Fragment Shader is all about calculating the color output of the pixels.
- The Fragment Shader source code:

```C
#version 330 core
out vec4 FragColor;

void main()
{
	FragColor = vec4(1.0f, 0.5f, 0.2f, 1.0f);
}
```

- The Fragment Shader only requires one output variable; a vector of size 4 that defines the final color output.
- The output values of the Fragment Shader is declared with the `out` keyword, with variable name `FragColor`.
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

### Shader Program
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
glDeleteShader(vertexShader);
glDeleteShader(fragmentShader);
```

- The last step before rendering is to link the Vertex Attributes.

### Linking Vertex Attributes
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
- Once the instruction to interpret the Vertex Data is given to OpenGL via `glVertexAttribPointer()` function, the Vertex Attribute needs to be enabled with `glEnableVertexAttribArray(location)` function.

## Shaders

## Textures

## Transformations

## Coordinate Systems

## Camera

## Review

