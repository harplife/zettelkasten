---
aliases: [Cherno의 OpenGL 가이드, Cherno OpenGL Guide]
tags: [computer_science, computer_vision, computer_graphics, study, display, programming, cherno]
status: ongoing
created: 2022-06-17
edited: 2022-06-17
---

# Cherno의 OpenGL 가이드
유투브 채널 [The Cherno](https://www.youtube.com/c/TheChernoProject)의 [OpenGL 플레이리스트](https://www.youtube.com/playlist?list=PLlrATfBNZ98foTJPJ_Ev03o2oq3-GGOS2) 내용을 정리한다.

영상은 총 31개로, 각 영상의 길이는 10분~30분 정도 된다.

## Welcome to OpenGL
OpenGL이 무엇인지 소개한다.

https://youtu.be/W3gAzLwfIP0
분량 : 16분
난이도 : 2/10
코드 포함 : False

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



## Using Modern OpenGL in C++

??

## Vertex Buffers and Drawing a Triangle in OpenGL
OpenGL로 비디오 버퍼에 데이터를 넣는 방법과 삼각형을 그리는 방법을 본다.

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