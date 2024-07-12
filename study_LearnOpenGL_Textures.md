
# Textures
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

## Texture Wrapping
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

## Texture Filtering
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

### Mipmaps
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

## Loading and Creating Textures
### Image Loading Library
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

### Texture Units
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

### Generating a Texture
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

## Applying Textures
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

glUniform1i(glGetUniformLocation(shaderProgram, "texture0"), 0);
```

## Source Code
Refer to [[opengl_texture_code]]

![[Pasted image 20240626173535.png]]
