# OpenGL Code Guide
## Instruction
1. Put in necessary Include Directives (& namespaces)
2. Forward Declarations for good practice
3. Set up constant values for later use
4. Set up main function
5. Initialize GLFW
6. Create Window & Context
7. Set up Window Resize callback
8. Initialize GLAD
9. Write Shader Files (vertex & fragment)
10. Load and build shaders
11. Link shaders
12. Build a shader program & delete shaders
13. Prepare Vertex Data (& indices as necessary)
14. Set up VBO, VAO, and EBO (if necessary)
15. Set up render loop
16. Set up key input
17. Set up buffer clear
18. Render
19. Swap buffer & poll events
20. Clean up
21. Define the previously declared functions

## Functions & Variables
- <mark class="hltr-trippy">function</mark> `int glfwInit()` : initializes the GLFW library. Returns `GLFW_TRUE` (1) if successful, else `GLFW_FALSE` (0).
	- The initialization checks what features are available on the machine, enumerates monitors, initializes the timer, and performs any required platform-specific initialization.
	- Most of the functions from the library will fail (`GLFW_NOT_INITIALIZED` error) if they are called before the initialization; only a handful, such as `glfwGetVersion`, may be called before the init.
	- If this function fails, it calls `glfwTerminate` before returning. If it succeeds, `glfwTerminate` should be called before the application exits.
	- Additional calls to this function after successful initialization but before termination will return `GLFW_TRUE` immediately.
	- For more information on initialization, refer to https://www.glfw.org/docs/latest/intro_guide.html#intro_init
- <mark class="hltr-trippy">function</mark> `void glfwWindowHint(hint, value)` : sets hints for the next call to `glfwCreateWindow`.
	- **param** `int hint` : the window hint to set
	- **param** `int value` : the new value of the window hint
	- [Window Creation Hints](https://www.glfw.org/docs/latest/window_guide.html#window_hints) affect the window, framebuffer, or context. These are set to their default each time the library is initialized with `glfwinit`.
	- Only integer value hints can be set with this function. String value hints are set with `glfwWindowHintString`.
	- This function does not check whether the specified hint values are valid. If you set hints to invalid values this will instead be reported by the next call to `glfwCreateWindow`.
	- Some hints are platform specific. These may be set on any platform, but they will only affect their specific platform (other platforms will ignore them). Setting these hints does not require platform specific headers or functions.
	- Window hints need to be set before the creation of the window & context. They function as additional arguments to `glfwCreateWindow`.
	- Notable Hints :
		- `GLFW_CONTEXT_VERSION_MAJOR` : version of the OpenGL to use. Major just means the first digit of the version (i.e. 1 if 1.0).
		- `GLFW_CONTEXT_VERSION_MINOR` : version of the OpenGL to use. Minor means the first decimal digit of the version (i.e. 0 if 1.0).
		- `GLFW_OPENGL_PROFILE` : profile of the OpenGL to use. The corresponding value for the modern OpenGL (3.3 and up) must be `GLFW_OPENGL_CORE_PROFILE`.
- <mark class="hltr-trippy">function</mark> `GLFWwindow* glfwCreateWindow(width, height, title, monitor, share)` : creates a window and its associated OpenGL context.
	- **param** `int width` : the desired width (in screen coordinates) of the window.
	- **param** `int height` : the desired height (in screen coordinates) of the window.
	- **param** `const char* title` : the initial window title (in UTF-8 encode).
	- **param** `GLFWmonitor* monitor` : the monitor to use for full screen mode, or `NULL` for windowed mode.
	- **param** `GLFWwindow* share` : the window whose context to share resources with, or `NULL` to not share resources.
	- The function returns the handle of the created window if successful, otherwise `NULL` (errors must be queried).
	- Successful creation of window does *not* change which context is current.
- <mark class="hltr-trippy">function</mark> `void glfwMakeContextCurrent(window)` : makes the OpenGL context of the specified window current on the calling thread.
	- **param** `GLFWwindow* window` : the window whose context to make current. Pass `NULL` to detach the current context.
	- A context must only be made current on a single thread at a time, and each thread can have only a single current context at a time. Making a context current detaches any previously current context on the calling thread.
	- When moving a context between threads, it must be detached on the old thread before making it current on the new one.
	- By default, making a context non-current implicitly forces a pipeline flush.
	- Specifying a window without a context will generate a `GLFW_NO_WINDOW_CONTEXT` error.
	- For more info on context, refer to https://www.glfw.org/docs/latest/context_guide.html
- <mark class="hltr-trippy">function</mark> `GLFWframebuffersizefun glfwSetFramebufferSizeCallback(window, callback)` : sets the framebuffer resize callback of the specified window, which is called when the framebuffer of the specified window is resized.
	- **param** `GLFWwindow* window` : the window whose callback to set.
	- **param** `GLFWframebuffersizefun callback` : the new callback, or `NULL` to remove the currently set callback.
	- This function is primarily used to handle window resizing events. It sets the callback function for framebuffer size changes, which occur when a window is resized.
	- While it's most commonly used to resize the viewport, it can also be used for other tasks that need to be performed when the window size changes. For example, repositioning the UI elements when the window is resized can be handled in the framebuffer size callback.
- <mark class="hltr-trippy">function</mark> `void glViewport(x, y, width, height)` : specifies the affine transformation of x and y from normalized device coordinates to window coordinates.
	- **param** `GLint x, y` : specify the lower left corner of the viewport rectangle, in pixels. The initial value is (0, 0).
	- **param** `GLsizei width, height` : specify the width and height of the viewport. When a GL context is first attached to a window, width and height are set to the dimensions of that window.