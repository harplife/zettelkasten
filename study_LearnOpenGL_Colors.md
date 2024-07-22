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