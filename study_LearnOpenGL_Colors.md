# Colors
- There are many ways to represent colors in digital; RGB, Grayscale, Monochrome, CMYK, HSV/HSL, YUV/YCbCr, Lab Color Space, and etc.
- The most common way to represent colors is using Red, Green, and Blue - which matches with the receptors in human eyes.
	- RGB mix is able to make most of observable colors.
- RGB image is commonly stored 8-bit per component; meaning, each component is represented as an integer value between 0~255 (256 values).
	- 16,777,216 colors can be made with RGB combinations.
- Although each RGB component is stored as an integer between 0~255, it is converted to a float in range `[0,1]` for computation purposes; it is more efficient and precise, especially when it comes to interpolation.
- 
## A Lighting Scene