# Getting Started
Following the guide https://learnopengl.com

## PERSONAL NOTES
### Learning Goal
- Learn Graphics Pipeline.
- Learn how to make a graphics program with OpenGL.
- Learn how to make a game engine with OpenGL.
- Make a simple 3D editor.
- Implement one of Pixar's researches.

### Future Plans
- Learn GUI Programming - preferably Qt + OpenGL
- Learn GPU Programming - preferably OpenCL + OpenGL
- Learn Raytracing
- Learn Computer Vision - preferably OpenCV
- Learn Machine Learning - library undecided

## OpenGL
### What is OpenGL
- OpenGL is a specification that is developed and maintained by the Khronos Group.
	- Even though OpenGL is mainly considered an API, OpenGL itself does not provide any functions.
- The OpenGL specification specifies exactly what the result/output of each function should be and how it should perform.
- It is up to the developers *implementing* this spec to come up with a solution of how this function should operate (in other words, it's up to GPU to provide functionalities as according to this spec).
- Since the OpenGL spec does not give implementation details, the actual developed versions of OpenGL are allowed to have different implementations, as long as their results comply with the spec.
- The people developing the actual OpenGL libraries are usually the GPU manufacturers. Each GPU supports specific versions of OpenGL. Because different versions of OpenGL exists for different GPUs, it is the fault of the GPU manufacturers if OpenGL behaves in a way that it shouldn't.

### Core-Profile vs Immediate Mode
- Immediate Mode (aka Fixed Function Pipeline) is an old way to develop with OpenGL.
	- Immediate Mode abstracted a lot of the actual operations of OpenGL. While it is easy to learn, it is harder to grasp how OpenGL actually operates.
	- Most of the functionality of OpenGL was hidden inside the library and developers did not have much control over how OpenGL does its calculations.
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
- Whenever a graphics company comes up with a new technique or a new large optimization for rendering, this is often found in an extension implemented in the drivers.
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
- (note) according to this [SO answer](https://stackoverflow.com/a/63121201), linking `opengl32.lib` may not be necessary because GLAD loads it during runtime. However, there are conflicting information that says not linking may result in errors during compilation - so, let's just link it to be safe.

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
- GLAD does have a built-in loader which can be called with `gladLoadGL()`, but the documentation recommends that the windowing library (such as GLFW) be used instead.

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
- A **Framebuffer** is a portion of RAM that contains a bitmap driving a video display. It's essentially a memory buffer containing data representing all the pixels in a complete video frame. Modern GPUs contain framebuffer circuitry in their cores.
	- There can be multiple framebuffers in memory at the same time; a **Front Buffer** that's currently displayed, and a **Back Buffer** that is being prepared.
	- The size of the Framebuffer determines the resolution and maximum colors that can be shown. The information in the buffer typically consists of color values for every pixel to be shown on the display. The total amount of memory required for the Framebuffer depends on the resolution of the output signal, and on the color depth or palette size.

### Render Loop
- A loop ("Render Loop") is required to repeatedly draw an image until the program has been explicitly told to stop.
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
// common practice, frees up space
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
- Once the instruction to interpret the Vertex Data is given to OpenGL via `glVertexAttribPointer()` function, the Vertex Attribute needs to be enabled with `glEnableVertexAttribArray(index)` function. `index` is the index of the Vertex Attribute, which in this case is `0`.
- So far, the Vertex Data is in the buffer, and OpenGL is instructed to parse the Vertex Attributes from the data. This process is to be repeated every time an object is drawn, which is rather repetitive if there are multiple Vertex Attributes and multiple shapes to draw. The way to save the state configuration is to use VAO.

### Vertex Array Object
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

### Render
- `glDrawArrays` function is called to draw primitives using the current active shader, the previously defined VA configs, and with the VBO's Vertex Data.
- <mark class="hltr-trippy">function</mark> `void glDrawArrays(mode, first, count)` <mark class="hltr-trippy">:</mark> render primitives from array data.
	- `GLenum mode` : specifies what kind of primitives to render.
	- `GLint first` : specifies the starting index in the enabled arrays.
	- `GLsizei count` : specifies the number of indices to be rendered.
- Example : `glDrawArrays(GL_TRIANGLES, 0, 3)`

### Source Code
Refer to [[cpp_hello_triangle_code]]

## Hello Rectangle
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

### Polygon Modes
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

### Side note : De-allocation
- Although calling `glfwTerminate()` frees up all the resources, it's generally a good practice to de-allocate the resources explicitly, especially in a case where some of the resources are *not* managed by GLFW.

```C++
// optional: de-allocate all resources
glDeleteVertexArrays(1, &VAO);
glDeleteBuffers(1, &VBO);
glDeleteBuffers(1, &EBO);
glDeleteProgram(shaderProgram);
```

### Additional Resources
- http://antongerdelan.net/opengl/hellotriangle.html : Anton Gerdelan's take on rendering the first triangle.
- https://open.gl/drawing : Alexander Overvoorde's take on rendering the first triangle.
- http://antongerdelan.net/opengl/vertexbuffers.html : some extra insights into vertex buffer objects.
- https://learnopengl.com/In-Practice/Debugging : there are a lot of steps involved in this chapter; if you're stuck it may be worthwhile to read a bit on debugging in OpenGL (up until the debug output section).

### Source Code
Refer to [[cpp_hello_rectangle_code]]

### Exercises
- Draw 2 triangles using a single call to `glDrawArrays`
- Draw 2 triangles using 2 separate calls to `glDrawArrays`
- Draw 2 triangles of different color by using 2 separate fragment shaders.

## Shaders
### GLSL
- Shaders are written in the C-like language GLSL.
- GLSL is tailored for use with graphics and contains useful features specifically targeted at vector and matrix manipulation.
- Shaders always begin with a version declaration, followed by a list of input and output variables, uniforms and its `main` function.
- Each shader's entry point is at its `main` function where input variables are processed and the results are stored in its output variables.
- A shader typically has the following structure:

```C++
#version version_number
in type in_variable_name;
in type in_variable_name;

out type out_variable_name;
  
uniform type uniform_name;
  
void main()
{
  // process input(s) and do some weird graphics stuff
  ...
  // output processed stuff to output variable
  out_variable_name = weird_stuff_we_processed;
}
```

- Each input variable inside the Vertex Shader is known as Vertex Attribute.
- The maximum number of Vertex Attributes are limited by the GPU.
- OpenGL guarantees there are always at least 16 Vertex Attributes with 4 components available.
- Some hardware may allow for more which you can retrieve by querying `GL_MAX_VERTEX_ATTRIBS`:

```C++
int nrAttributes;
glGetIntegerv(GL_MAX_VERTEX_ATTRIBS, &nrAttributes);
cout << nrAttributes << endl;
```

### GLSL Data Types
- GLSL has most of the default basic types, such as `int`, `float`, `double`, `uint`, and `bool`.
- GLSL also features two container types, such as `vectors` and `matrices`.

#### Vectors
- A **vector** in GLSL is a 2 to 4 component container for any of the basic types. It can take the following form (`n` represents the number of components):
	- `vecn` : the default vector of `n` floats.
	- `bvecn` : a vector of `n` booleans.
	- `ivecn` : a vector of `n` integers.
	- `uvecn` : a vector of `n` unsigned integers.
	- `dvecn` : a vector of `n` double components.
- Throughout the guide, a vector is `vecn` unless explicitly stated otherwise.
- Components of a vector can be accessed via `vec.x` where `x` is the first component of the vector. The first, second, third, and fourth component is accessed with `.x`, `.y`, `.z` and `.w` respectively.
- Components of a vector can also be accessed with `rgba` for colors, and `stpq` for texture coordinates.
- The vector datatype allows for flexible component selection called `swizzling`, which is best explained by this example:

```C
vec2 someVec;
vec4 differentVec = someVec.xyxx;
vec3 anotehrVec = differentVec.zyw;
vec4 otherVec = someVec.xxxx + anotherVec.yxzy;
```

- Any combination of up to 4 letters can be used to create a new vector (of the same type) as long as the original vector has those components.
- Vectors can be passed as arguments to different vector constructor calls, reducing the number of arguments required:

```C
vec2 vect = vec2(0.5, 0.7);
vec4 result = vec4(vect, 0.0, 0.0);
vec4 otherResult = vec4(result.xyz, 1.0);
```

### Ins and Outs
- GLSL defined the `in` and `out` keywords specifically for inputs and outputs of a shader.
- The Vertex Shader differs from other shaders in the sense that it receives its input straight from the Vertex Data. The Vertex Shader thus requires an extra layout specification for its inputs so it can be linked to the Vertex Data.
- It is possible to omit the layout (`location = 0`) specifier and query for the attribute location via `glGetAttribLocation`. However, it's easier and saves some work for the dev and OpenGL to just set them in the Vertex Shader.
- The Vertex Shader expects a `vec4` variable `gl_Position` to be defined inside the shader in order to set the position of the vertices.
- The Fragment Shader expects a `vec4` output variable because its main function is to generate a final output color. For OpenGL 3.0 and beyond, the variable name does not matter.
- In order to send data from one shader to another, an output needs to be declared in the sending shader and similar input needs to be declared in the receiving shader. When the types and the names are equal on both shaders, OpenGL will link those variables together (which is done when linking a program object).
- An example code of sending data from the Vertex Shader to the Fragment Shader:

Vertex Shader
```C
#version 330 core
layout (locatino = 0) in vec3 a_pos;

out vec4 v_color;

void main()
{
	gl_Position = vec4(a_pos, 1.0);
	v_color = vec4(0.5, 0.0, 0.0, 1.0);
}
```

Fragment Shader
```C
#version 330 core
in vec4 v_color;

out vec4 f_color;

void main()
{
	f_color = v_color;
}
```

### Uniforms
- **Uniforms** are another way to pass data from the application (CPU) to the shaders (GPU).
- Uniforms are global, meaning that a uniform variable is unique per shader program object, and can be accessed from any shader at any stage in the shader program.
- Uniforms are implicitly constant within the shader. Attempting to change them with shader code will result in a compiler error. Similarly, a uniform variable cannot be passed as an `out` or `inout` parameter to a function.
- If a uniform variable is declared in both the Vertex Shader and the Fragment Shader, the types must be consistent. For example, you cannot have `uniform int x;` in the Vertex Shader and `uniform float x;` in the Fragment Shader.
- To declare a uniform variable, the `uniform` keyword is added before the type and the name (i.e. `uniform vec4 v_color`).
- <mark class="hltr-red">WARNING</mark> : a declared uniform variable that is not used anywhere in the GLSL code will be silently removed during compilation, which may cause several frustrating errors.
- The `layout` qualifier for uniforms is *NOT* available for OpenGL version 3.3. It is only available 4.3 and upwards. In other words, location of a uniform variable cannot be explicitly set, and therefore the location must be queried using `glGetUniformLocation(program, variable)`.
- Defining a uniform variable isn't usually done inside a shader - it is common to set a uniform variable's value inside OpenGL code using `glUniform(location, *)`.
	- OpenGL does not have native support for function overloading, so the same function name with different postfix are used to match the type and the number of components of the uniform variable. For example, the value of a uniform variable with an array of four floats is set by `glUniform4f`.
		- postfix `f` : the function expects a float as its value
		- postfix `i` : the function expect an integer as its value
		- postfix `ui` : unsigned integer
		- postfix `3f` : 3 floats
		- postfix `fv` : a float vector/array (this pretty much works for any `#f` postfixes).
- Updating a uniform variable requires that the program is used first (by calling `glUseProgram`).
- Example of setting up a uniform variable `vetexColor`:

Fragment Shader
```C
#version 330 core
out vec4 f_color;

uniform vec4 v_color;

void main()
{
	f_color = v_color;
}
```

OpenGL Code
```C++
// inside render loop
glUseProgram(shaderProgram);

float timeValue = glfwGetTime();
float greenValue = (sin(timeValue)/2.0f) + 0.5f; // sine returns value -1~1
int v_colorLocation = glGetUniformLocation(shaderProgram, "v_color");

glUniform4f(v_colorLocation, 0.0f, greenValue, 0.0f, 1.0f);
```

- Above code results with the shape(s) flashing green.

### Multiple Attributes
- This section covers a way to set up multiple Vertex Attributes so that each vertex has position data and color data.
- ![[vertex_attribute_pointer_interleaved.png]]
- A triangle Vertex Data that includes both the position and color of each vertices:

```C++
float vertices[] = {
    // positions         // colors
     0.5f, -0.5f, 0.0f,  1.0f, 0.0f, 0.0f,   // bottom right
    -0.5f, -0.5f, 0.0f,  0.0f, 1.0f, 0.0f,   // bottom left
     0.0f,  0.5f, 0.0f,  0.0f, 0.0f, 1.0f    // top 
};
```

- Set up Vertex Shader to accept color data:

```C
#version 330 core
layout (location = 0) in vec3 a_pos;
layout (location = 1) in vec3 a_color;

out vec3 v_color;

void main()
{
	gl_Position = vec4(a_pos, 1.0);
	v_color = a_color;
}
```

- Set up Fragment Shader to accept color data:

```C
#version 330 core
in vec3 v_color;
out vec4 f_color;

void main()
{
	f_color = vec4(v_color, 1.0);
}
```

- Re-configure the Vertex Attribute Pointers:

```C++
GLsizei stride = 6 * sizeof(float); // X,Y,Z,R,G,B -> 6 floats
unsigned int colorOffset = 3 * sizeof(float);

// Position
glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, stride, (void*)0);
glEnableVertexAttribArray(0);

// Color
glVertexAttribPointer(1, 3, GL_FLOAT, GL_FALSE, stride, (void*)colorOffset);
glEnableVertexAttribArray(1);

```

- Above code results with a triangle with each corner red, green, and blue (with gradient colors filled in).
- Fragment Shader interpolates the color of the vertices in order to color the pixels in between. This process is referred to as **Fragment Interpolation**.

### Custom Shaders
- Skipping the custom shader part since this mostly deals with abstracting shader related work into a class. Refer to https://learnopengl.com/Getting-started/Shaders
- Main source code : [[opengl_custom_shader_main]]
- Shader class source code : [[opengl_custom_shader_class]]

## Textures
- A texture is a 2D image used to add detail to an object.
- Textures can also be used to store a large collection of arbitrary data to send to the shaders. This will be discussed later on.
- Following image will be used as a texture for the guide:
	- ![[opengl_texture_wall.jpg|150]]
  - **Texture Coordinate** is used to match each vertex to the part of the texture it corresponds to. In other words, each vertex should have a texture coordinate associated with them that specifies what part of the texture image to sample from.
  - When a texture is supplied and each vertex has its own texture coordinate, fragment interpolation fills the rest of the shape with the texture.
  - 2D Texture Coordinate ranges from 0 to 1 in the x and y axis.
  - Retrieving the texture color using texture coordinates is called **Sampling**.
  - Texture Coordinate starts at (0, 0) for the lower left corner of a texture image, and ends at (1, 1) for the upper right corner of a texture image. 
  - ![[tex_coords.png]]

### Texture Wrapping
- If coordinates outside the (0, 0) ~ (1, 1) are specified, texture image is drawn in one of four ways:
	- `GL_REPEAT` : repeats the texture image. It is the default behavior.
	- `GL_MIRRORED_REPEAT` : repeats the image but image is mirrored with each repeat.
	- `GL_CLAMP_TO_EDGE` : edge of the image is stretched to the edge of the coordinates.
	- `GL_CLAMP_TO_BORDER` : coordinates outside of the range are given a user-specified border color.
- ![[texture_wrapping.png]]
- Each of the aforementioned options can be set per coordinate axis `(s, t, r)` with the `glTexParameter*` function:


```C++
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_MIRRORED_REPEAT);
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_MIRRORED_REPEAT);
```

- `GL_TEXTURE_2D` specifies that the texture is a 2D image.
- If `GL_CLMAP_TO_BORDER` is chosen, the border color can be set with `glTexParameter*`, like so:

```C++
float borderColor[] = {1.0f, 1.0f, 0.0f, 1.0f};
glTexParameterfv(GL_TEXTURE_2D, GL_TEXTURE_BORDER_COLOR, borderColor);
```

### Texture Filtering
- Texture Coordinates do not depend on resolution but can be any floating point value, thus OpenGL has to figure out which texture pixel (aka **Texel**) to map the texture coordinate to. This becomes especially important if a low resolution texture is given to a very large object.
- **Texture Filtering** is a method of sampling that decides the color at the given Texture Coordinate based on the Texels that surround it. There are several types of Texture Filtering, such as Nearest-Neighbor Filtering, Bilinear Filtering, Mipmapping, Anisotropic Filtering, and more.
	- **Filtering** refers to the process of determining the color of a pixel based on its surrounding Texels.
	- **Interpolation** is a technique used in the filtering process which involves calculating intermediate values between two points based on the values at those points. In the context of Texture Filtering, interpolation is used to determine the color of a pixel based on the colors of its surrounding Texels.
- **Nearest-Neighbor Filtering** (`GL_NEAREST`) : the simplest method of texture filtering that uses the Texel nearest to the Texture Coordinate as the sampled color. It is the default method.
	- ![[filter_nearest.png]]
- **Bilinear Filtering** (`GL_LINEAR`) : the method that takes an interpolated value from the Texture Coordinate's neighboring Texels, approximating a color between them. The smaller the distance from the Texture Coordinate to a Texel's center, the more that Texel's color contributes to the sampled color. This results in a smoother appearance than Nearest-Neighbor Filtering.
	- ![[filter_linear.png]]
- ![[texture_filtering.png]]
- `GL_NEAREST` results in a blocked patterns where the pixels that from the texture is clear, while `GL_LINEAR` produces a smoother pattern where the individual pixels are less visible. Although `GL_LINEAR` produces a more realistic output, `GL_NEAREST` can be chosen for the 8-bit aesthetics.
- Texture Filtering can be set for magnifying and minifying operations (scaling up or down) via `glTexParameter*`. For example, `GL_NEAREST` can be set for when textures are minified and `GL_LINEAR` can be set for when textures are magnified:

```C++
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_NEAREST);
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
```

#### Mipmaps
- **Mipmaps** is a collection of images of the same texture in sequential order where each subsequent texture is smaller than the previous one.
- A fragment would have too many Texels to sample from when a high resolution image is used for an object that is far away. This results with visible artifacts and waste of memory bandwidth. Mipmaps is used to prevent this problem by supplying a smaller image when the object is further away.
- `glGenerateMipmap` is used to generate Mipmaps in OpenGL (detail about the function call later).
- Switching between Mipmap levels during rendering may show some artifacts like Aliasing, Texture Shimmering, and Texture Popping. Texture Mapping is necessary for Mipmapping in order to prevent these artifacts and provide smooth transition between Mipmap levels.
- There are four Mipmap Texture Mapping options:
	- `GL_NEAREST_MIPMAP_NEAREST` : takes the nearest Mipmap level to match the pixel size, and uses nearest neighbor interpolation for texture sampling.
	- `GL_LINEAR_MIPMAP_NEAREST` : takes the nearest Mipmap level to match the pixel size, and samples that level using linear interpolation.
	- `GL_NEAREST_MIPMAP_LINEAR` : linearly interpolates between the two mipmaps that most closely match the size of a pixel, and samples the interpolated level via nearest neighbor interpolation.
	- `GL_LINEAR_MIPMAP_LINEAR` : linearly interpolates between the two closest mipmaps, and samples the interpolated level via linear interpolation.
- The Texture Filtering for the Mipmap is applied onto the minifying operation with `glTexParameter*`, like so:

```C++
glTexPrameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR_MIPMAP_LINEAR);
glTexParamteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
```

- A common mistake is setting the Mipmap Filtering on the magnifying operation. Doing so will generate `GL_INVALID_ENUM` error.

### Loading and Creating Textures
#### Image Loading Library
- OpenGL (GLAD & GLFW) does not provide functionalities to read & convert image files. For the purpose of the guide, [a single header image loading library](https://github.com/nothings/stb/blob/master/stb_image.h) by Sean Barret will be used.
	- #todo try out OpenImageIO. I feel like I've seen it being used in Houdini.
- Once the header file is downloaded, following preprocessors need to be added:

```C++
#define STB_IMAGE_IMPLEMENTATION
#include "stb_image.h"
```

- By defining `STB_IAMGE_IMPLEMENTATION`, the preprocessor modifies the header file such that it only contains the relevant definition source code, effectively turning the header file into a `.cpp` file.
- With the image loading library ready, following image `container.jpg` will be loaded: 
  ![[container.jpg|100]]
- To load an image, `stbi_load` function is used, like so:

```C++
// nrChannels -> number of color channels
int txWidth, txHeight, txChannels;
// image file is loaded as bytes
unsigned char *data = stbi_load("container.jpg", &txWidth, &txHeight, &txChannels, 0);
```

#### Texture Units
- A Texture Unit is a component of GPU that handles everything related to textures. It's responsible for loading texture data, processing it, and sending it to the shader.
- Each Texture Unit can have one texture of each type bound to it at a time. When a texture is bound to a Texture Unit, all subsequent texture operations on that type of texture are performed on the texture that's bound to the current unit.
- The main purpose of Texture Units is to allow multiple textures to be used in shaders. In other words, each Texture Unit corresponds to a single texture.
- A Texture Unit can be set current with a call to `glActiveTexture`. The proper way to set the active Texture Unit is with the value `GL_TEXTURE0 + i`, where `i` is the texture unit index (starting at `0`).
	- Although there is `GL_TEXTURE1` and so on, the symbolic constant is only supplied up to 31. Number of textures that can be loaded is up to the GPU (`GL_MAX_TEXTURE_IMAGE_UNITS`).
- A Texture Unit is, in a way, a location of an active texture. `GL_TEXTURE0` indicates a texture at location `0`.
	- This location will be assigned as a value to a Uniform via `glUniform1i`, then be fed to `texture` function inside Fragment Shader. Specifics will be discussed later.
- Once a Texture Unit is active, operations such as `glBindTexture` can follow.
- There are various ways to get around the maximum number of texture units, such as Texture Atlas.
	- **Texture Atlas** is an image containing multiple sub-images that can be used as a way to supply multiple textures with only a single texture unit. It is efficient in an application where many small textures are used frequently, as it reduces both the disk I/O overhead and the context switch overhead.

#### Generating a Texture
- Like any objects in OpenGL, an ID must be generated, the ID must be bound to an object, and then the object must be filled with the image data:

```C++
unsigned int texture;
glGenTextures(1, &texture);

glActiveTexture(GL_TEXTURE0);
glBindTexture(GL_TEXTURE_2D, texture);
// image data loaded with stbi_load
if (data)
{
	glTexImage2D(GL_TEXTURE_2D, 0, GL_RGB, width, height, 0, GL_RGB, GL_UNSIGNED_BYTE, data);
	glGenerateMipmap(GL_TEXTURE_2D);
}
```

- <mark class="hltr-trippy">function</mark> `void glTexImage2D(target, level, internalFormat, width, height, border, format, type, data)` : specifies a 2D texture image.
	- param `GLenum target` : specifies the target texture. Ranges from `GL_TEXTURE_2D` to `GL_PROXY_TEXTURE_CUBE_MAP`. More info [here](https://docs.gl/gl3/glTexImage2D).
	- param `GLint level` : specifies the level-of-detail number. Level `0` is the base image level. Level `n` is the *n* th mipmap reduction image.
	- param `GLint internalFormat` : specifies the number of color components in the texture. This parameter tells OpenGL how to store the texture data internally. Commonly used ones are `GL_RGB`, `GL_RGBA`, `GL_LUMINANCE`, and `GL_LUMINANCE_ALPHA`. The choice of internal format can depend on specific needs, such as the supported image format, the level of control over the image loading process, and the hardware capabilities of the target platform.
	- param `GLsizei width` : specifies the width of the texture image.
	- param `GLsizei height` : specifies the height of the texture image.
	- param `GLint border` : must be set to `0`. This part of the function became deprecated since version 3.0, and will generate an error if set other than 0.
	- param `GLenum format` : specifies the format of the pixel data. In other words, it describes the number and the order of color components of the data that is being passed to the function.
	- param `GLenum type` : specifies the data type of the pixel data. Commonly used one is `GL_UNSIGNED_BYTE`.
	- param `const GLvoid * data` : specifies a pointer to the image data in memory.
	- Calling this function converts the original texture image to the image format that OpenGL can use (which is indicated by `internalFormat`).
- After the texture and its corresponding mipmaps are generated, it is good practice to free the image memory with `stbi_image_free(data);`.
- Putting it all together, the process of loading image should look like this:

```C++
unsigned int texture0;
glGenTextures(1, &texture0);

glActiveTexture(GL_TEXTURE0);
glBindTexture(GL_TEXTURE_2D, texture0);
// set the texture wrapping/filtering options (on the currently bound texture object)
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);	
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR_MIPMAP_LINEAR);
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
// load and generate the texture
int txWidth, txHeight, txChannels;
unsigned char *imgData = stbi_load("container.jpg", &txWidth, &txHeight, &txChannels, 0);
if (imgData)
{
    glTexImage2D(GL_TEXTURE_2D, 0, GL_RGB, txWidth, txHeight, 0, GL_RGB, GL_UNSIGNED_BYTE, imgData);
    glGenerateMipmap(GL_TEXTURE_2D);
}
else
{
    std::cout << "Failed to load texture" << std::endl;
}
stbi_image_free(imgData);
```

### Applying Textures
- The Vertex Data should now include position, color, and texture coordinate for each vertex, like so:

```C++
float vertices[] = {
    // positions          // colors           // texture coords
     0.5f,  0.5f, 0.0f,   1.0f, 0.0f, 0.0f,   1.0f, 1.0f,   // top right
     0.5f, -0.5f, 0.0f,   0.0f, 1.0f, 0.0f,   1.0f, 0.0f,   // bottom right
    -0.5f, -0.5f, 0.0f,   0.0f, 0.0f, 1.0f,   0.0f, 0.0f,   // bottom left
    -0.5f,  0.5f, 0.0f,   1.0f, 1.0f, 0.0f,   0.0f, 1.0f    // top left 
};
```

- ![[vertex_attribute_pointer_interleaved_textures.png]]
- The new vertex attribute must be added with the `glVertexAttribPointer` as well:

```C++
glVertexAttribPointer(2, 2, GL_FLOAT, GL_FALSE, 8 * sizeof(float), (void*)(6 * sizeof(float)));
glEnableVertexAttribArray(2); 
```

- Make sure the stride is set correctly with the other vertex attributes (such as position and color).
- The Vertex Shader should be modified to accept the Texture Coordinates as a Vertex Attribute, and then forward the coordinates to the Fragment Shader:

```C++
#version 330 core
layout (location = 0) in vec3 a_pos;
layout (location = 1) in vec3 a_color;
layout (location = 2) in vec2 a_txCoord;

out vec3 v_color;
out vec2 v_txCoord;

void main()
{
	gl_Position = vec4(a_pos, 1.0);
	v_color = a_color;
	v_txCoord = a_txCoord;
}
```

- The Fragment Shader should then accept the `v_txCoord` variable as its input.
- The Texture Object is passed to the Fragment Shader via a Uniform that has a data type `sampler*`. A postfix for that data type is set according to the dimension (e.g. `sampler2D`).
- All in all, the fragment shader should look like this:

```C
#version 330 core
in vec3 v_color;
in vec2 v_txCoord;

uniform sampler2D texture0;

out vec4 f_color;

void main()
{
	f_color = texture(texture0, v_txCoord);
}
```

- The texture location is passed to the Uniform `texture0`:

```C++
// make sure shader program is ready
glUseProgram(shaderProgram);

glUniform1i(glGetUniformLocation(fragmentShader, "texture0"), 0);
```

### Source Code
Refer to [[opengl_texture_code]]

![[Pasted image 20240626173535.png]]

## Transformations
- Because an object in a Graphics program is basically an array of data, it can be represented as a matrix; which means that all transformation in regards to an object involves some kind of matrix operations.

### Vectors
- A vector has a direction and a magnitude (aka strength or length).
- If a vector has 2 dimensions, it represents a direction on a plane. When it has 3, it can represent any direction in 3D world.
- Generally, a vector is described as a character symbol with a little bar on top, like $\bar{v}$.
- Displaying a vector in a formula:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\bar{v} = \mymat{x\\y\\z}
$$

- When the vector's origin is set to `(0, 0, 0)`, then the point has both a direction and a position which makes it a **Position Vector**.

### Scalar Vector Operations
- A scalar is a single digit. When adding/subtracting/multiplying or dividing a vector with a scalar, the operation is applied to each element of the vector.
- A scalar addition would look like this:

$$
\newcommand\mymat[1]{\begin{bmatrix*}[r]#1\end{bmatrix*}}

\mymat{1\\2\\3} + x \rightarrow \mymat{1\\2\\3} + \mymat{x\\x\\x} = \mymat{1+x\\2+x\\3+x}
$$

### Vector Negation
- Negating a vector (flipping its positive/negative sign) results in a vector in the reversed direction. It is equivalent to a scalar multiplication with `-1`.

### Component-wise Operations
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

### Magnitude/Length
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

### Unit Vector
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

### Personal Notes
![[2d_affine_transformation.svg]]

## Coordinate Systems

## Camera

## Review

