
# Hello Window
- This chapter will cover writing a code to open a simple application window.
- In `Main.cpp` file, add the following directives to the top.

```C++
#include <iostream>
#include <glad/glad.h>
#include <GLFW/glfw3.h>
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
		std::cerr << "Failed to create GLFW window" << std::endl;
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

## GLAD
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

## Viewport
- **Window** : a rectangular area that defines which portion of the data is viewed on the screen.
- **Viewport** : a rectangular area that defines where the data is positioned.
- Window and Viewport are almost synonyous to each other. An image is "drawn" on Viewport, and the drawn image on the Viewport is then displayed on the Window.
- Note that there can be multiple viewports on a window. Each of these viewports can draw the same image with different projections.
- Once GLFW and GLAD libraries are initialized, a Viewport can be set by calling the function `glViewport(0, 0, width, height)`.
	- First & second argument sets the location of viewport in respect to the window.
	- Third & fourth argument sets the width and height of the viewport.

### Resize
- A custom callback function can be defined to resize the viewport when the window is resized.

```C++
void framebufferSizeCallback(GLFWwindow* window, int width, int height)
{
	glViewport(0, 0, width, height);
}
```

- The custom callback function is then registered with `glfwSetFramebufferSizeCallback(window, framebufferSizeCallback)`.
	- Callback functions are registered after the window is created and before the render loop is initiated (which will be covered next).
- A **Framebuffer** is a portion of RAM that contains a bitmap driving a video display. It's essentially a memory buffer containing data representing all the pixels in a complete video frame. Modern GPUs contain framebuffer circuitry in their cores.
	- There can be multiple framebuffers in memory at the same time; a **Front Buffer** that's currently displayed, and a **Back Buffer** that is being prepared.
	- The size of the Framebuffer determines the resolution and maximum colors that can be shown. The information in the buffer typically consists of color values for every pixel to be shown on the display. The total amount of memory required for the Framebuffer depends on the resolution of the output signal, and on the color depth or palette size.

## Render Loop
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
### Input
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

### Rendering
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

## Source Code
Refer to [[cpp_hello_window_code]]
