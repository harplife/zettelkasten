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
9. Write Shader Files (vertext & fragment)
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
- <mark class="hltr-trippy">function</mark> `void glfwWindowHint(hint, value)` : sets hints for the next call to `glfwCreateWindow`.
	- **param** `int hint` : the window hint to set
	- **param** `int value` : the new value of the window hint
	- Only integer value hints can be set with this function. String value hints are set with `glfwWindowHintString`.
	- This function does not check whether the specified hint values are valid. If you set hints to invalid values this will instead be reported by the next call to `glfwCreateWindow`.
	- Some hints are platform specific. These may be set on any platform, but they will only affect their specific platform (other platforms will ignore them). Setting these hints does not require platform specific headers or functions.
	- [Window Creation Hints](https://www.glfw.org/docs/latest/window_guide.html#window_hints)
	- Notable Hints : `GLFW_CONTEXT_VERSION_MAJOR`, `GLFW_CONTEXT_VERSION_MINOR`, `GLFW_OPENGL_PROFILE`
- <mark class="hltr-trippy">function</mark> `GLFWwindow* glfwCreateWindow(width, height, title, monitor, share)` : creates a window and its associated OpenGL context.