# Getting Started
- Following the guide https://learnopengl.com
- Next : [[study_LearnOpenGL_Lighting]]

## PERSONAL NOTES
### Real Tangible Goals
- Make a Sound Wave Simulator - perhaps implementing raytracing onto sound?

### Learning Goals
- Learn Graphics Pipeline.
- Learn how to make a graphics program with OpenGL.
- Learn how to make a game engine with OpenGL.
- Make a simple 3D editor.
- Make a 3D Asset Library.
- Implement one of Pixar's researches.

### Future Plans
- Learn GUI Programming - preferably Qt + OpenGL
- Learn GPU Programming - preferably OpenCL + OpenGL
- Learn Raytracing
- Learn Computer Vision - preferably OpenCV
- Learn Machine Learning - library undecided

### Troubleshooting
#### Casting Void Pointer
In C++, you can safely convert an `unsigned int` to a `void*` using a `reinterpret_cast`. Here's how you can do it:

```cpp
unsigned int ui = 12345;
void* ptr = reinterpret_cast<void*>(static_cast<uintptr_t>(ui));
```

In this code, `ui` is first cast to `uintptr_t`, which is an integer type that is guaranteed to be large enough to hold a pointer. Then, `reinterpret_cast` is used to convert the `uintptr_t` to a `void*`.

Please note that this kind of conversion can be platform-dependent and should be used with caution. The size of an `unsigned int` may not be the same as the size of a pointer on all platforms, which is why we use `uintptr_t` in the intermediate step. This ensures that the conversion is safe on platforms where the size of a pointer is larger than the size of an `unsigned int`.

Also, keep in mind that converting an integer to a pointer and then dereferencing it is generally unsafe unless you know exactly what you're doing. The integer would have to be a valid memory address that your program has access to, otherwise, you'll run into undefined behavior.

#### Suppressing warnings
```c++
#pragma warning(push, 0)
#define STB_IMAGE_IMPLEMENTATION
#include "stb_image.h"
#pragma warning(pop)
```

## OpenGL
![[study_LearnOpenGL_OpenGL]]


## Setting Up Libraries
![[study_LearnOpenGL_Libraries]]

## Hello Window
![[study_LearnOpenGL_HelloWindow]]


## Hello Triangle
![[study_LearnOpenGL_HelloTriangle]]

## Hello Rectangle
![[study_LearnOpenGL_HelloRectangle]]


## Shaders
![[study_LearnOpenGL_Shaders]]

## Textures
![[study_LearnOpenGL_Textures]]

## Transformations
![[study_LearnOpenGL_Transformations]]

## Coordinate Systems
![[study_LearnOpenGL_CoordinateSystems]]

## Camera
![[study_LearnOpenGL_Camera]]
