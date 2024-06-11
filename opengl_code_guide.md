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
	- Passing `0` as argument unbinds the currently bound VAO. Sometimes it's good practice to unbind before the render loop to prevent further modification, but it comes with a small performance cost.
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
	- `buffer` set to `0` effectively unbinds any buffer object previously bound, and restores client memory usage for that buffer object target. Sometimes it's good practice to unbind VBOs to prevent further modification, but it comes with small performance cost.
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
- <mark class="hltr-trippy">function</mark> `void glGetBufferParameteriv(target, value, data)` : returns in `data` a selected parameter of the buffer object specified by `target`.
	- **param** `GLenum target` : specifies the target buffer object.
	- **param** `GLenum value` : specifies the name of a buffer object parameter, such as `GL_BUFFER_ACCESS`, `GL_BUFFER_MAPPED`, `GL_BUFFER_SIZE`, and `GL_BUFFER_USAGE`.
	- **param** `GLint* data` : returns the requested parameter.
	- This function is useful to check whether a buffer object has been loaded with data successfully. This is done so by specifying `value` as `GL_BUFFER_SIZE` (which returns the size of the data inside the buffer object) and then comparing the returned value with the size of the data.
	- Unlike shader or program, there isn't a function like `glShaderInfoLog` to get detailed information about errors that occur with buffer objects. It's important to utilize other methods to keep the application bug free.
- <mark class="hltr-trippy">function</mark> `GLenum glGetError()` : returns the value of the error flag.
	- Each detectable error is assigned a numeric code and symbolic name. When an error occurs, the error flag is set to the appropriate error code value - no other errors are recorded until `glGetError` is called, the error code is returned, and the flag is reset to `GL_NO_ERROR`.
	- There may be several error flags; `glGetError` should always be called in a loop, until it returns `GL_NO_ERROR`.
- <mark class="hltr-trippy">function</mark> `void glVertexAttribPointer(index, size, type, normalized, stride, pointer)` : specifies the location and data format of an array of generic vertex attributes. It is basically an instruction on how to interpret the data.
	- **param** `GLuint index` : specifies the index of the generic vertex attribute to be modified.
	- **param** `GLint size` : specifies the number of components (between 1~4) per generic vertex attribute. For example, a 3D coordinate consists of 3 components.
	- **param** `GLenum type` : specifies the data type of each component in the array, such as `GL_FLOAT`, `GL_INT`, and etc.
	- **param** `GLboolean normalized` : specifies whether fixed-point data values should be normalized (`GL_TRUE`) or converted directly as fixed-point values (`GL_FALSE`) when they are accessed.
	- **param** `GLsizei stride` : specifies the byte offset between consecutive generic vertex attributes. If set to `0`, the generic vertex attributes are understood to be tightly packed in the array.
	- **param** `const GLvoid *pointer` : specifies a offset of the first component of the first generic vertex attribute in the array in the data store of the buffer currently bound to the `GL_ARRAY_BUFFER` target.
	- When a generic vertex attribute array is specified, all of its arguments are saved as vertex array state, in addition to the current vertex array buffer object binding.
- <mark class="hltr-trippy">function</mark> `void glEnableVertexAttribArray(index)` : enables the generic vertex attribute array.
	- **param** `GLuint index` : specifies the index of the generic vertex attribute to be enabled.
	- Once enabled, the values in the generic vertex attribute array will be accessed and used for rendering when calls are made to vertex array commands.
	- Enabling/disabling the generic vertex attribute is necessary in order to select which attribute is used for rendering, as opposed to using all (max 16) attributes which aren't necessary and will slow down rendering.
	- Do *NOT* disable the vertex attribute arrays if VAO is being used, as VAOs encapsulates them.
- <mark class="hltr-trippy">function</mark> `int glfwWindowShouldClose(window)` : returns the value of the close flag of the specified window.
	- **param** `GLFWwindow* window` : specifies the window to query from.
	- The output of this function is ultimately the condition for the render loop; that is, the render loop should run as long as the close flag's value is not true.
- <mark class="hltr-trippy">function</mark> `void glfwSetWindowShouldClose(window, value)` : sets the value of the close flag of the specified window.
	- **param** `GLFWwindow* window` : specifies the window whose close flag to change.
	- **param** `int value` : specifies the new value to set to the close flag.
	- The close flag value can be set to `GLFW_TRUE` or `GLFW_FALSE`. `1` or `0` works as well.
- <mark class="hltr-trippy">function</mark> `int glfwGetKey(window, key)` : returns the last state reported for the specified key to the specified window. The returned state is either `GLFW_PRESS` or `GLFW_RELEASE`.
	- **param** `GLFWwindow* window` : specifies the window to get key input from.
	- **param** `int key` : specifies the key to query.
	- The US keyboard layout is used for key input. The keys include `GLFW_KEY_ESCAPE` for ESC, `GLFW_KEY_A` for A, `GLFW_KEY_0` for 0, and etc. For the complete list of keys, refer to https://www.glfw.org/docs/latest/group__keys.html
	- Once a key is pressed, the function will return `GLFW_PRESS`.
	- Do not use this function to implement text input.
- <mark class="hltr-trippy">function</mark> `void glClearColor(red, green, blue, alpha)` : specifies the RGBA values used by `glClear` to clear the color buffers.
	- **param** `GLclampf red/green/blue/alpha` : RGBA values that are clamped to the range $[0,1]$.
- <mark class="hltr-trippy">function</mark> `void glClear(mask)` : sets the bitplane area (buffer) of the window to values previously selected by `glClearColor`, `glClearDepth`, and `glClearStencil`.
	- **param** `GLbitfield mask` : specifies the mask to be cleared. There are three masks that can be selected - `GL_COLOR_BUFFER`, `GL_DEPTH_BUFFER`, and `GL_STENCIL_BUFFER_BIT`.
- <mark class="hltr-trippy">function</mark> `void glUseProgram(program)` : installs the program object as part of current rendering state.
	- **param** `GLuint program` : specifies the handle of the program object whose executables are to be used as part of current rendering state.
	- One or more executables are created in a program object by successfully attaching shader objects to it with `glAttachShader`, successfully compiling the shader objects with `glCompileShader`, and successfully linking the program object with `glLinkProgram`.
- <mark class="hltr-trippy">function</mark> `void glDrawElements(mode, count, type, indices)` : renders primitives from array data.
	- **param** `GLenum mode` : specifies the kind of primitives to render, such as `GL_POINTS`, `GL_LINES`, `GL_TRIANGLES`, and etc.
	- **param** `GLsizei count` : specifies the number of elements to be rendered.
	- **param** `GLenum type` : specifies the type of the values in `indices`. Must be one of `GL_UNSIGNED_BYTE`, `GL_UNSIGNED_SHORT`, or `GL_UNSIGNED_INT`.
	- **param** `const GLvoid *indices` : specifies an offset of the first index in the array in the data store of the buffer currently bound to the `GL_ELEMENT_ARRAY_BUFFER` target.
	- VAOs must be bound before this function is called.
- <mark class="hltr-trippy">function</mark> `void glfwSwapBuffers(window)` : swaps the front and back buffers of the specified window.
	- **param** `GLFWwindow* window` : specifies the window whose buffers to swap.
	- Double buffers & swapping is necessary in order to prevent artifacts that occur with single buffer.
- <mark class="hltr-trippy">function</mark> `void glfwPollEvents()` : processes only those events that have already been received and then returns immediately. Processing events will cause the window and input callbacks associated with those events to be called.
	- When the function is called, it processes all window event messages that the OS has accumulated so far for all windows in the process. These events include things like key presses, mouse movement, window resizing, and so on.
	- Most often the function is placed inside the rendering loop. This means that events such as keyboard presses and mouse clicks will only get handled as often as the frame is updated. If the frame rate is lower, events will be processed slower.
- 
