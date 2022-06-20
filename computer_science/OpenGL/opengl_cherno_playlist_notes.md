---
aliases: [Cherno의 OpenGL 가이드, Cherno OpenGL Guide]
tags: [computer_science, computer_vision, computer_graphics, study, display, programming, cherno, youtube, playlist]
status: ongoing
created: 2022-06-17
edited: 2022-06-19
---

# Cherno의 OpenGL 가이드
유투브 채널 [The Cherno](https://www.youtube.com/c/TheChernoProject)의 [OpenGL 플레이리스트](https://www.youtube.com/playlist?list=PLlrATfBNZ98foTJPJ_Ev03o2oq3-GGOS2) 내용을 정리한다.

영상은 총 31개로, 각 영상의 길이는 10분~30분 정도 된다.

## Welcome to OpenGL
OpenGL이 무엇인지 소개한다.

https://youtu.be/W3gAzLwfIP0
분량 : 16분
난이도 : 2/10

- OpenGL is a graphics API.
- OpenGL is a bunch of functions that we can call to do certain things with graphics.
- OpenGL allows us to actually access our GPU.
- OpenGL is just one of many api's that allows us to access the graphics card. There are others, such as Direct3D, Vulcan, and Metal.
- OpenGL is not a library, an engine, or a framework.
- OpenGL is a specification. It doesn't define any code, but instead defines what functions are needed, what they should do, what their parameters should be, and what the function should return.
- You don't download OpenGL. Instead, you download a library that helps with using OpenGL functions.
- OpenGL is implemented by GPU manufacturer, which means implementation of OpenGL may be different between GPUs.
- OpenGL is cross-platform. But cross-platform doesn't mean it's best.
- It's often best to choose the Graphics API specific to the OS. Also, using multiples of Graphics APIs is common.
- Legacy OpenGL refers to OpenGL where every operations are fixed, and any modifications to the rendering were done by using presets.
- Modern OpenGL refers to OpenGL where some operations are programmable. A program that controls how GPU renders an image is called a Shader.
- Shaders work directly on GPU.

## Setting up OpenGL and Creating a Window in C++
OpenGL 라이브러리를 하나 가져와서 창(윈도) 한 개를 여는 방법을 보여준다.

https://youtu.be/OR4fNpBjmq8
분량 : 22분
난이도 : 3/10
코드 : [github](https://github.com/harplife/thecherno_opengl/blob/linux/ep02-window/main.cpp)

- Managing a Window is generally done by using OS Window API. For example, Windows has [Win32](https://en.wikipedia.org/wiki/Windows_API) and Mac has [Cocoa](https://en.wikipedia.org/wiki/Cocoa_(API)).

- To keep things simple, we'll use OpenGL to create and open a window.

- GLFW is a lightweight library that manages window system. Also, it creates a "Context" for rendering.

- Sidenote: [SDL(Simple DirectMedia Layer)](https://en.wikipedia.org/wiki/Simple_DirectMedia_Layer) is a cross-platform software development library designed to provide a hardware abstraction layer for computer multimedia hardware components. Basically, it's GLFW but WAY BIGGER.

- Sidenote : I'm going to skip Project Setup part of the video. Refer instead to ![[visual_studio_graphics_setup_w_glfw_n_glad|OpenGL 프로젝트 셋업 2]] for using VCPKG to install GLFW and other libraries.

- Go to [GLFW Documentation](https://www.glfw.org/documentation.html) and copy&paste the example code.

밑에서 부터는 실제로 코드를 구현하는 부분이다.

### GLFW 헤더 추가
`#include <GLFW/glfw3.h>`

### GLFW 초기화
- `glfwInit()` to initialize GLFW.

### 윈도 생성
`GLFWwindow* window = glfwCreateWindow(640, 480, "Hello World", NULL, NULL);` to generate a window with a given width, height, title text.

Refer to [GLFW Window Guide](https://www.glfw.org/docs/3.3/window_guide.html)

[glfwCreateWindow()](https://www.glfw.org/docs/3.3/group__window.html#ga3555a418df92ad53f917597fe2f64aeb)

```cpp
GLFWwindow * glfwCreateWindow(
    int width,
    int height,
    const char * title,
    GLFWmonitor * monitor,
    GLFWwindow * share 
)	
```

### OpenGL Context 생성
[OpenGl Context](https://www.khronos.org/opengl/wiki/OpenGL_Context)는 OpenGL의 모든 데이터가 모이고 처리되는 공간이라 보면 된다. Context가 정의되어야 버퍼링이 가능하다.

Refer to [GLFW Context Guide](https://www.glfw.org/docs/3.3/context_guide.html)

`glfwMakeContextCurrent(window);` creates an OpenGL Context.

[glfwMakeContextCurrent()](https://www.glfw.org/docs/3.3/group__context.html#ga1c04dc242268f827290fe40aa1c91157)

```cpp
void glfwMakeContextCurrent(GLFWwindow * window)
```

### 렌더링 루프 구현
While문으로 창이 닫히지 않는 동안 렌더링을 구현하도록 한다.

```cpp
while (!glfwWindowShouldClose(window))
{
    ..
}
```

렌더링 루프 안에는 초기화, 백지화, 도형 정의, 버퍼링 정의 등이 구현되어야 한다.

#### 백지화
윈도우를 업데이트할 때마다 `glClear(GL_COLOR_BUFFER_BIT);`로 백지화 해준다 (안 그러면 매번 렌더링이 구현될때마다 그림 위에 그림이 그려진다).

`GL_COLOR_BUFFER_BIT`는 OpenGL만의 상수(Constant)로서 기본적으로 하얀색으로 생각하면 될 듯 하다. 나중에 이 색을 정의하는 함수를 알게된다.

#### 도형 정의
여기서는 Legacy OpenGL로 도형을 정의하는 방식을 보여준다.

```cpp
glBegin(GL_TRIANGLES);    // 도형 정의 시작
glVertex2f(-0.5f, -0.5f); // 정점 1
glVertex2f(0.5f, -0.5f);  // 정점 2
glVertex2f(0.0f, 0.5f);   // 정점 3
glEnd();                  // 도형 정의 끝
```

이것을 구현하면 실제로 도형이 그려질수도 있고 안 그려질수도 있다. GPU 자체에서 제공하는 셰이더가 있는가에 따라 결정된다.

#### 더블 버퍼링
더블 버퍼링은 OpenGL이 구현하는 것이 아니라 윈도우 라이브러리(GLFW)가 구현하는 것으로, 앞에 보여지는 버퍼(Front Buffer)와 뒤에 준비된 버퍼(Back Buffer)를 정의하여 버퍼가 서로 스위칭 될 수 있게 한다. 더블 버퍼링은 `glfwSwapBuffers()`를 호출하는 것으로 구현된다.

Front Buffer가 윈도우에 그려지는 동안, Back Buffer에는 그릴 그림이 준비된다. Front Buffer에 그림이 그려지면, Back Buffer에 있는 데이터가 Front Buffer로 이동되고, Back Buffer에는 새로운 데이터가 들어온다.

#### 이벤트 처리
[이벤트 처리(Event Processing)](https://www.glfw.org/docs/3.3/input_guide.html#events)는 윈도 업데이트 하는 주기를 정의한다.

[glfwPollEvents()](https://www.glfw.org/docs/3.3/group__window.html#ga37bd57223967b4211d60ca1a0bf3c832)는 윈도 업데이트를 연속적(Continuously)으로 업데이트한다. 주로 게임을 구현할 때 사용된다.

[glfwWaitEvents()](https://www.glfw.org/docs/3.3/group__window.html#ga554e37d781f0a997656c26b2c56c835e)는 이벤트 큐에 적어도 1개의 이벤트가 있을때 윈도를 업데이트 한다. 주로 이미지 편집기를 구현할 때 사용된다.

[glfwWaitEventsTimeout()](https://www.glfw.org/docs/3.3/group__window.html#ga605a178db92f1a7f1a925563ef3ea2cf)는 이벤트 큐에 적어도 1개의 이벤트가 있을때, 또는 주기적으로 윈도를 업데이트 한다.

### 종료 처리 정의
`glfwTerminate()`는 GLFW를 종료하는 함수로, 윈도가 닫히며 렌더링 루프가 끝난 후 실행되어야 한다.

## Using Modern OpenGL in C++
OpenGL 로딩 라이브러리에 대하여 알아보고, GLEW 라이브러리 활용하는 방법을 알아본다.

https://youtu.be/H2E3yO0J7TM
분량 : 18분
난이도 : 3/10
코드 : [github](https://github.com/harplife/thecherno_opengl/blob/linux/ep03-modern-opengl/src/main.cpp)

- 플랫폼(Windows, Mac, Linux)마다 OpenGL 함수들이 정의된 공간이 다르다 (GPU 드라이버 DLL 파일 안에 있다). 따라서, [OpenGL 로딩 라이브러리](https://www.khronos.org/opengl/wiki/OpenGL_Loading_Library)는 OpenGL 함수들에 대한 포인터들을 읽어옴으로서 개발자가 직접 OpenGL 함수들을 찾는 수고를 덜어준다.
- OpenGL 로딩 라이브러리는 Modern OpenGL을 사용할 수 있게 해준다.
- OpenGL 로딩 라이브러리 중 [GLEW](http://glew.sourceforge.net/)가 있다.
- Sidenote : I'm going to skip Project Setup part of the video. Refer instead to ![[visual_studio_graphics_setup_w_glfw_n_glad|OpenGL 프로젝트 셋업 2]] for using VCPKG to install GLFW and other libraries.
- Sidenote : vcpkg 사용하지 않고 직접 라이브러리를 연결하려면, 이 [가이드 영상](https://youtu.be/or1dAmUO8k0)을 참고.
- GLEW 헤더를 include는 다른 OpenGL 라이브러리(예: GLFW)보다 우선적으로 선언되어야 한다.
- `glewInit()`으로 GLEW 라이브러리를 초기화 하려면, 우선 OpenGL Context가 생성되어야 한다.

## Vertex Buffers and Drawing a Triangle in OpenGL
OpenGL로 비디오 버퍼에 데이터를 넣는 방법과 삼각형을 그리는 방법을 본다.

https://youtu.be/0p9VxImr7Y0
분량 : 20분
난이도 : 3/10
코드 : [github](https://github.com/harplife/thecherno_opengl/blob/linux/ep04-vertex-buffers/src/main.cpp)

- A buffer refers to an array of memory in VRAM(Video RAM)
- OpenGL operates as a State Machine. State Machine refers to an abstract device which  can be in one of defined states, depending on its previous condition and the present values of its inputs. In layman's terms, it has stages where it needs to advance in order to do a certain task.
- Vertex Buffer is often dealt alongside to an Index Buffer, which will be covered later.

### Generate a buffer
```cpp
unsigned int buffer;
glGenBuffers(1, &buffer);
```

- First argument specifies how many buffers to generate.
- Everything that is assigned with OpenGL gets an ID(Identifier), including a buffer. An ID is always an unsigned integer.
- `glGenBuffers()` does not return an ID for the buffer. Instead, it takes the second argument, which is an unsigned int, and writes into its memory the ID of the buffer (that's why it takes a pointer).

### Binding the buffer
```cpp
glBindBuffer(GL_ARRAY_BUFFER, buffer);
```

- `glBindBuffer()` puts a buffer in a ready state.
- First argument specifies the purpose of the buffer.
- `GL_ARRAY_BUFFER` is an OpenGL constant that says the buffer is just an array of memory.
- The second argument takes the ID of the buffer that gets bind.

### Put data in the buffer
```cpp
// a traingle with 3 vertices, in xy plane
float positions[6] = {
    -0.5f, -0.5f,
     0.5f, -0.5f,
     0.0f,  0.5f
};

glBufferData(GL_ARRAY_BUFFER, sizeof(float)*6, positions, GL_STATIC_DRAW);
```

- First argument specifies the purpose of the buffer (again?).
- Second argument specifies the size of the data array. The size is in bytes (read the [docs](https://docs.gl/gl4/glBufferData).
- Third argument takes in the data.
- Fourth argument specifies the "usage" of the buffer. The frequency of access may be specified with **STREAM/STATIC/DYNAMIC**, and the nature of access may be specified with **DRAW/READ/COPY**.
- The "usage" is a HINT that is passed to GPU for any possible optimization. It may or may not affect the performance.

## Vertex Attributes and Layouts in OpenGL
정점 속성들에 대하여 알아보고, Layout을 통해 어떻게 데이터가 전송되는지 알아본다.

## How Shaders Work in OpenGL
셰이더에 대하여 알아본다.

## Writing a Shader in OpenGL
셰이더를 직접 구현해 본다.

## How I Deal with Shaders in OpenGL
Cherno가 셰이더를 다루는 방식을 알아본다.

## Index Buffers in OpenGL
인덱스 버퍼를 사용하여 여러 도형에 대한 데이터를 다루는 방법을 알아본다.

## Dealing with Errors in OpenGL
OpenGL은 에러를 알려주지 않는다. 그나마 버전 4.1 이후에는 에러를 알려주는 콜백 함수를 사용할 수 있지만, 그 이전 버전은 아예 그런것이 없다. 따라서, ASSERT를 구현하여 OpenGL 함수를 Wrap해주는 방안을 알아본다.

## Uniforms in OpenGL
셰이더의 입출력 값이 아닌, 단순히 전달되는 값인 Uniform에 대하여 알아본다.

## Vertex Arrays in OpenGL

## Abstracting OpenGL into Classes

## Buffer Layout Abstraction in OpenGL

## Shader Abstraction in OpenGL

## Writing a Basic Renderer in OpenGL

## Textures in OpenGL

## Blending in OpenGL

## Maths in OpenGL

## Projection Matrices in OpenGL

## Model View Projection Matrices in OpenGL

## ImGui in OpenGL

## Rendering Multiple Objects in OpenGL

## Setting up a Test Framework for OpenGL

## Creating Tests in OpenGL

## Creating a Texture Test in OpenGL

## How to make your UNIFORMS FASTER in OpenGL

## Batch Rendering Introduction

## Batch Rendering Color

## Batch Rendering Textures