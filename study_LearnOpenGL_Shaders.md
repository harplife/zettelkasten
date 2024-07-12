# Shaders
## GLSL
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

## GLSL Data Types
- GLSL has most of the default basic types, such as `int`, `float`, `double`, `uint`, and `bool`.
- GLSL also features two container types, such as `vectors` and `matrices`.

## Vectors
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

## Ins and Outs
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

## Uniforms
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

## Multiple Attributes
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

## Custom Shaders
- Skipping the custom shader part since this mostly deals with abstracting shader related work into a class. Refer to https://learnopengl.com/Getting-started/Shaders
- Main source code : [[opengl_custom_shader_main]]
- Shader class source code : [[opengl_custom_shader_class]]
