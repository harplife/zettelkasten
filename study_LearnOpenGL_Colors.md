# Colors
- There are many ways to represent colors in digital; RGB, Grayscale, Monochrome, CMYK, HSV/HSL, YUV/YCbCr, Lab Color Space, and etc.
- The most common way to represent colors is using Red, Green, and Blue - which matches with the receptors in human eyes.
	- RGB mix is able to make most of observable colors.
- RGB image is commonly stored 8-bit per component; meaning, each component is represented as an integer value between 0~255 (256 values).
	- 16,777,216 colors can be made with RGB combinations.
- Although each RGB component is stored as an integer between 0~255, it is converted to a float in range `[0,1]` for computation purposes; it is more efficient and precise, especially when it comes to interpolation.
- In OpenGL code, a color is represented with a 3D vector, like so: `glm::vec3 coral(1.0f, 0.5f, 0.31f);`
- The ray from the sun contains all spectrums of color; when the ray hits an object, the perceived color that are seen from the object is a mix of colors that are not absorbed but rather reflected from the object.
	- For example, when the light from the sun shines upon a blue object, everything but blue color is absorbed in the object. Only the blue color is reflected.
- The rule of absorption/reflection applies directly in Computer Graphics. A light source is defined with a color, and when it is shone upon an object with a color, the colors are multiplied.
	- When the light color is white `(1.0, 1.0, 1.0)` and the object color is red `(1.0, 0.0, 0.0)`, multiplying these colors return red.
	- When the light color is red `(1.0, 0.0, 0.0)` and the object color is green `(0.0, 1.0, 0.0)`, multiplying these colors return yellow.
## A Lighting Scene
- From here on, real-world lighting will be simulated by making extensive use of colors. In order to do so, light sources will be displayed as visual objects in the scene, as there will be objects that will have light shine upon.
- For simplicity, a cube model will be used for both the light source and the object.
	- This means that these objects will share the same model of the cube; specifically the Vertex Data.
	- These objects will also share the same VBO.
	- However, each object will be assigned their own VAOs.
- Configure VBO & VAO:

```C++
GLuint VAO;
glGenVertexArrays(1, )
```

- Reminder of how buffer objects are built with `allocateBuffer` function:
```C++
GLuint allocateBuffer(GLenum bufferTarget, const void* bufferData, unsigned int dataSize, GLenum bufferUsuage)
{
	GLuint bufferObject;

	glGenBuffers(1, &bufferObject);
	glBindBuffer(bufferTarget, bufferObject);
	glBufferData(bufferTarget, dataSize, bufferData, bufferUsuage);

	GLint bufferSize = 0;
	glGetBufferParameteriv(bufferTarget, GL_BUFFER_SIZE, &bufferSize);

	if (bufferSize != dataSize)
	{
		GLenum error = glGetError();

		while (error != GL_NO_ERROR)
		{
			cerr << "OpenGL Error: " << error << endl;
			error = glGetError();
		}

		// returns 0
		glDeleteBuffers(1, &bufferObject);
	}

	return bufferObject;
}
```

- Another shader program will be made specifically for light sources; a new set of vertex shader and fragment shader will also created.
- 