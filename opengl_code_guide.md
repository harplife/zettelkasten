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
	- The callback function must have the function signature `GLFWframebuffersizefun`, which expects `GLFWwindow* window`, `GLsizei width`, and `GLsizei height` as its parameters.
- <mark class="hltr-trippy">function</mark> `void glViewport(x, y, width, height)` : specifies the affine transformation of x and y from normalized device coordinates to window coordinates.
	- **param** `GLint x, y` : specify the lower left corner of the viewport rectangle, in pixels. The initial value is (0, 0).
	- **param** `GLsizei width, height` : specify the width and height of the viewport. When a GL context is first attached to a window, width and height are set to the dimensions of that window.
- <mark class="hltr-trippy">function</mark> `int gladLoadGLLoader((GLADloadproc)glfwGetProcAddress)` : initializes the GLAD library and loads the function that reads the address of an OpenGL function.
	- Although `gladLoadGL()` does the job, it is recommended in the GLAD documentation to use the address function provided by the windowing library (GLFW).
- <mark class="hltr-trippy">function</mark> `GLuint glCreateShader(shaderType)` : creates an empty shader object and returns a non-zero value by which it can be referenced.
	- **param** `GLenum shaderType` : Specifies the type of shader to be created. Must be one of `GL_VERTEX_SHADER`, `GL_GEOMETRY_SHADER`, or `GL_FRAGMENT_SHADER`.
- <mark class="hltr-trippy">function</mark> `void glShaderSource(shader, count, string, length)` : sets the source code in `shader` to the source code in the array of strings specified by `string`.
	- **param** `GLuint shader` : specifies the handle of the shader object whose source code is to be replaced. Meaning, it takes the output of the `glCreateShader` as input.
	- **param** `GLsizei count` : specifies the number of elements in the `string` and `length` arrays.
	- **param** `const GLchar **string` : specifies an array of pointers to strings containing the source code to be loaded into the shader. (note) reason for double pointers is because `string` is an array of char arrays.
	- **param** `const GLint *length` : specifies an array of string lengths. If `NULL`, each string is assumed to be null terminated. Otherwise, it points to an array containing a string length for each of the corresponding elements of `string`.
	- OpenGL copies the shader source code strings when `glShaderSource` is called, so an application may free its copy of the source code strings immediately after the function returns.
- <mark class="hltr-trippy">function</mark> `void glCompileShader(shader)` : compiles the source code strings that have been stored in the shader object specified by `shader`.
	- **param** `GLuint shader` : specifies the shader object to be compiled.
	- The compilation status will be stored as part of the shader object's state. This value will be set to `GL_TRUE` if the shader was compiled without errors and is ready for use, and `GL_FALSE` otherwise. It can be queried by calling `glGetShaderiv`.
- <mark class="hltr-trippy">function</mark> `void glGetShaderiv(shader, pname, params)` : returns in `params` the value of a parameter for a specific shader object.
	- **param** `GLuint shader` : specifies the shader object to be queried.
	- **param** `GLenum pname` : specifies the object parameter. Accepted symbolic names are `GL_SHADER_TYPE`, `GL_DELETE_STATUS`, `GL_COMPILE_STATUS`, `GL_INFO_LOG_LENGTH`, and `GL_SHADER_SOURCE_LENGTH`.
	- **param** `GLint *params` : returns the requested object parameter.
	- Status of the shader compilation can be queried by calling this function with `pname` set to `GL_COMPILE_STATUS`. `params` will return with either `GL_TRUE` (1) or `GL_FALSE` (0).
- <mark class="hltr-trippy">function</mark> `void glGetShaderInfoLog(shader, maxLength, length, infoLog)` : returns the information log for the specified shader object.
	- **param** `GLuint shader` : specifies the shader object whose information log is to be queried.
	- **param** `GLsizei maxLength` : specifies the size of the character buffer for storing the returned information log.
	- **param** `GLsizei *length` : returns the length of the string returned in `infoLog` (excluding the null terminator). If the length of the returned string is not required, a value of `NULL` can be passed in.
	- **param** `GLchar *infoLog` : specifies an array of characters that is used to return the information log. The string that is returned will be null terminated.
	- The information log for a shader object is a string that may contain diagnostic messages, warning messages, and other information about the last compile operation. Note that the different OpenGL implementations may produce different information logs.
	- The size of the buffer required to store the returned information log can be obtained by calling `glGetShaderiv` with the value `GL_INFO_LOG_LENGTH`.
- <mark class="hltr-trippy">function</mark> `GLuint glCreateProgram()` : creates an empty program object and returns a non-zero value by which it can be referenced.
	- A program object is an object to which shader objects can be attached.
	- The function provides a mechanism to specify the shader objects that will be linked to create a program. For example, a vertex shader and a fragment shader will be linked once they are both attached to the same program.
	- The function provides a means for checking the compatibility of the shaders that will be used to create a program (for instance, checking the compatibility between a vertex shader and a fragment shader).
	- One or more executables are created in a program object by attaching shader objects to it with `glAttachShader`, compiling the shader objects with `glCompileShader`, and linking the program object with `glLinkProgram`. These executables are made part of current state when `glUseProgram` is called.
	- This function returns `0` if an error occurs creating the program object.
- <mark class="hltr-trippy">function</mark> `void glAttachShader(program, shader)` : attaches a shader object to a program object.
	- **param** `GLuint program` : specifies the program object to which a shader object will be attached.
	- **param** `GLuint shader` : specifies the shader object that is to be attached.
	- Any operations can be performed on a shader object regardless of the attachment to a program object. It is permissible to attach a shader object without source code to a program object (also extends to non-compiled shader object).
	- A shader object can be attached to more than one program object.
	- If a shader object is deleted while it is attached to a program object, it will be flagged for deletion; the deletion will not occur until `glDetachShader` is called to detach it from all program objects to which it is attached.
- <mark class="hltr-trippy">function</mark> `void glLinkProgram(program)` : links the program object specified by `program`.
	- **param** `GLuint program` : specifies the handle of the program object to be linked.
	- During the linking stage, any shader object that is attached to `program` will be used to create an executable that will run on the programmable processor (of their own type).
	- If the specified program object is already currently in use (as a result of a previous call to `glUseProgram`), a successful link operation will install the generated executable(s) as part of the current rendering state.
	- As a result of a successful link operation, all active user-defined uniform variables belonging to `program` will be initialized to `0`. Each of the program object's active uniform variables will be assigned to a location that can be queried by calling `glGetUniformLocation`. Also, any active user-defined attribute variables that have not been bound to a generic vertex attribute index will be bound to one at this time.
	- The status of the link operation will be stored as a part of the program object's state. This value will be set to `GL_TRUE` if the program object was linked without errors and is ready for use, and `GL_FALSE` otherwise. It can be queried by calling `glGetProgramiv` with arguments `program` and `GL_LINK_STATUS`.
	- If the link operation is unsuccessful, any information about a previous link operation on `program` is lost (i.e. a failed link does not restore the old state of `program`).
	- Linking of a program object can fail for a number of reasons; refer to https://docs.gl/gl3/glLinkProgram
- <mark class="hltr-trippy">function</mark> `void glGetProgramiv(program, pname, params)` : returns in `params` the value of a parameter for a specific program object.
	- **param** `GLuint program` : specifies the program object to be queried.
	- **param** `GLenum pname` : specifies the object parameter.
	- **param** `GLint *params` : returns the requested object parameter.
	- There are many parameters that can be checked with this function; refer to https://docs.gl/gl3/glGetProgram
- <mark class="hltr-trippy">function</mark> `void glGetProgramInfoLog(program, maxLength, length, infoLog)` : returns the information log for the specified program object.
	- **param** `GLuint program` : specifies the program object whose information log is to be queried.
	- **param** `GLsizei maxLength` : specifies the size of the character buffer for storing the returned information log.
	- **param** `GLsizei *length` : returns the length of the string returned in `infoLog` (excluding the null terminator). `NULL` can be passed in if the length of the returned string is not required.
	- **param** `GLchar *infoLog` : specifies an array of characters that is used to return the information log. The string will be null terminated.
	- The information log for a program object is a string that may contain diagnostic messages, warning messages, and other information about the last compile operation. Note that the different OpenGL implementations may produce different information logs.
	- The size of the buffer required to store the returned information log can be obtained by calling `glGetProgramiv` with the value `GL_INFO_LOG_LENGTH`.
- <mark class="hltr-trippy">function</mark> `void glDeleteShader(shader)` : frees the memory and invalidates the name associated with the shader object specified by `shader`. In other words, it deletes a shader object.
	- **param** `GLuint shader` : specifies the shader object to be deleted.
	- If a shader object to be deleted is attached to a program object, it will be flagged for deletion, but it will not be deleted until it is no longer attached to any program object.
	- To determine whether an object has been flagged for deletion, call `glGetShaderiv` with arguments `shader` and `GL_DELETE_STATUS`.
- <mark class="hltr-trippy">function</mark> `void glGenVertexArrays(n, arrays)` : generate vertex array object names.
	- **param** `GLsizei n` : specifies the number of vertex array object names to generate.
	- **param** `GLuint *arrays` : specifies an array in which the generated vertex array object names are stored.
	- There is no guarantee that the names form a contiguous set of integers.
	- It is guaranteed that none of the returned names was in use immediately before the call. They are also not returned by subsequent calls, unless they are first deleted with `glDeleteVertexArrays`.
- <mark class="hltr-trippy">function</mark> `void glBindVertexArray(array)` : binds the vertex array object with name `array`.
	- **param** `GLuint array` : specifies the name of the vertex array to bind.
	- VAO must be bound first before VBO and EBO can be bound.
	- VAO acquires state and type when they are first bound.
- <mark class="hltr-trippy">function</mark> `void glGenBuffers(n, buffers)` : returns `n` buffer object names in `buffers`. In other words, it generate buffer object names.
	- **param** `GLsizei n` : specifies the number of buffer object names to be generated.
	- **param** `GLuint *buffers` : specifies an array in which the generated buffer object names are stored.
	- There is no guarantee that the names form a contiguous set of integers.
	- It is guaranteed that none of the returned names was in use immediately before the call. They are also not returned by subsequent calls, unless they are first deleted with `glDeleteBuffers`.
	- No buffer objects are associated with the returned buffer object names until they are first bound by calling `glbindBuffer`.
	- This function should be used to generate VBO & EBO names.
- <mark class="hltr-trippy">function</mark> `void glBindBuffer(target, buffer)` : binds a buffer object to the specified buffer binding point.
	- **param** `GLenum target` : specifies the target to which the buffer object is bound. Basically, it sets the type of buffer to use, such as `GL_ARRAY_BUFFER`, `GL_ELEMENT_ARRAY_BUFFER`, and etc.
	- **param** `GLuint buffer` : specifies the name of a buffer object (i.e. the buffer object names from `glGenBuffers`).
	- `buffer` set to `0` effectively unbinds any buffer object previously bound, and restores client memory usage for that buffer object target.
	- Buffer object names and the corresponding buffer object contents are local to the shared object space of the current GL rendering context; two rendering contexts share buffer object names only if they explicitly enable sharing between context through the appropriate GL windows interfaces functions.
	- The state of a buffer object immediately after it is first bound is an unmapped zero-sized memory buffer with `GL_READ_WRITE` access and `GL_STATIC_DRAW` usage.
	- GL operations on the target to which it is bound affect the bound buffer object, and queries of the target to which it is bound return state from the bound buffer object.
	- A buffer object binding created with this function remains active until a different buffer object name is bound to the same target, or until the bound buffer object is deleted with `glDeleteBuffers`.
	- This function should be used to bind VBO & EBO names.
- <mark class="hltr-trippy">function</mark> `void glBufferData(target, size, data, usage)` : creates a new data store for the buffer object currently bound to `target`.
	- **param** `GLenum target` : specifies the target buffer object.
	- **param** `GLsizeiptr size` : specifies the size in bytes of the buffer object's new data store.
	- **param** `const GLvoid *data` : specifies a pointer to data that will be copied into the data store for initialization, or `NULL` if no data is to be copied.
	- **param** `GLenum usage` : specifies the expected usage pattern of the data store; such as `GL_STATIC_DRAW`, `GL_DYNAMIC_DRAW`, and etc.
	- `usuage` enables the GL implementation to make more intelligent decisions that may significantly impact buffer object performance. However, it does not constrain the actual usage of the data store.
	- `usuage` can be broken down into two parts: first, the frequency of access (static/dynamic/stream), and second, the nature of that access (read/copy/draw).
		- `STREAM` : the data store contents will be modified once and used at most a few times.
		- `STATIC` : the data store contents will be modified once and used many times.
		- `DYNAMIC` : the data store contents will be modified repeatedly and used many times.
		- `DRAW` : the data store contents are modified by the application, and used as the source for GL drawing and image specification commands.
		- `READ` : the data store contents are modified by reading data from the GL, and used to return that data when queried by the application.
		- `COPY` : the data store contents are modified by reading data from the GL, and used as the source for GL drawing and image specification commands.
	- Sometimes it can be better to use `glBufferSubData` instead to update data to a data store. `glBufferSubData` allows updating a subset of a data store, which can be more efficient than updating the whole data. Also, it doesn't have to allocate memory each time it updates data.
- function `void glGetBufferParameteriv(target, value, data)`
	- param `GLenum target`
	- param `GLenum value`
	- param `GLint* data`
- 
