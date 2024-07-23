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
	- Each object will be placed at different positions.
- In order to avoid the light source cube object to be affected by its own light, a separate shader program will be used to draw the light source cube object.
	- Meanwhile, the original shader program will apply lighting to the objects that it draws.

### Shader Class
- Creating a Shader Class was originally in Getting Started section of the guide. I skipped it because there wasn't any need for multiple shaders at the time. But now that two shaders are required to simulate lighting, I'll now work on a Shader Class.