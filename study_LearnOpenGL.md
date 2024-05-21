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

## Creating a Window
- First thing to do before drawing anything with OpenGL is to create an OpenGL context and an application window to draw in.
	- These are operations that are specific per operating system, and OpenGL itself does not provide these operations.
	- It is up to the developers to create a window, define a context, and handle user input.
- There are a few libraries that provide such functionalities, some specifically aimed at OpenGL.
	- Some of the more popular libraries are GLUT, SDL, SFML and GLFW.
- GLFW library is used on the LearnOpenGL course.

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

#### Compilation
- Once the project files are converted using CMake, a project file `GLFW.sln` can be found inside the build folder. Open it with Visual Studio and proceed to build (compile).
- 

## Hello Window

## Hello Triangle

## Shaders

## Textures

## Transformations

## Cooridnate Systems

## Camera

## Review

