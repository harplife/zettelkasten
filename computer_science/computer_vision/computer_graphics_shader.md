---
aliases: [셰이더, Shader]
tags: [computer_science, computer_vision, computer_graphics, study, display, programming]
status: ongoing
created: 2022-06-04
edited: 2022-06-04
---

# 셰이더
[셰이딩(Shading)](https://en.wikipedia.org/wiki/Shading)은 3차원 모델을 렌더링하기 위해서 빛(Light), 어두움(Darkness), 그리고 색(Color) 등의 조합 비율을 계산하는 작업/알고리즘을 뜻한다. 주로 현실 세계에 빛(Light)의 특성을 최대한 근접하게 묘사하기 위한 목표로 셰이딩이 사용되지만, 반대로 왜곡시켜 특이한 이펙트(Effect)를 만드는 경우도 있다.

참고 : 다각형으로 만들어진 도형을 둥글게 보이도록 하는 목적으로도 셰이딩이 사용된다.

초기 그래픽스 시스템에는 텍스쳐, 조명 등에 관련된 수학 연산(즉, 셰이딩)이 고정(hard-coded)되어 있어 지정된 파라미터로만 설정이 가능했다. 나중에는 이러한 수학 연산을 유저가 직접 작성한 프로그램으로 대체할 수 있도록 개선되었는데, 이러한 프로그램을 [셰이더(Shader)](https://en.wikipedia.org/wiki/Shader)라고 한다.

참고 : 셰이더(Shader)라는 단어는 1988년에 Pixar에서 출시한 RenderMan 인터페이스 사양설명서에 사용된 단어이다.

셰이더를 작성하기 위한 [셰이딩 언어](https://en.wikipedia.org/wiki/Shading_language)가 여러 있는데, 이 중 OpenGL 전용 셰이딩 언어 [GLSL (OpenGL Shading Language)](https://en.wikipedia.org/wiki/OpenGL_Shading_Language)이 있다.

셰이더 프로그램은 문자 배열에 넣어 OpenGL의 셰이더 컴파일 및 링크 함수 등을 이용하여 각 단계의 처리기에 전달되어야 한다. 소스 프로그램에 직접 포함시키기도 하지만, 주로 별도의 파일에 작성하여 읽어드린 후 처리한다.

참고자료 :
1. [그래픽스 조명(Lighting)](https://en.wikipedia.org/wiki/Computer_graphics_lighting)
2. [learnopengl.com - Shaders](https://learnopengl.com/Getting-started/Shaders)
3. [Cherno - How Shaders Work](https://youtu.be/5W7JLgFCkwI)
4. [셰이더 교육 자료](https://thebookofshaders.com/)

## 셰이더 종류
#todo [셰이더 종류](https://en.wikipedia.org/wiki/Shader#Types) 정리

Primitive and Mesh Shaders
Ray Tracing Shaders
Compute Shaders

## 데이터 유형
https://www.khronos.org/opengl/wiki/Data_Type_(GLSL)

## 고정 변수
미리 정의된 변수(Predefined Variable) 또는 고정변수(Built-in Variable)

https://www.khronos.org/opengl/wiki/Built-in_Variable_(GLSL)

## 정점 사양정의
[정점 사양정의(Vertex Specification)](https://www.khronos.org/opengl/wiki/Vertex_Specification)

### 정점 버퍼 객체
[정점 버퍼 객체(Vertex Buffer Object, VBO)](https://www.khronos.org/opengl/wiki/Vertex_Specification#Vertex_Buffer_Object)

참고 : [버퍼 객체](https://www.khronos.org/opengl/wiki/Buffer_Object)에 지정된 값은 GPU 메모리에 저장된다.

A Vertex Buffer Object (VBO) is a [memory buffer](https://www.khronos.org/opengl/wiki/Buffer_Objects "Buffer Objects") in the high speed memory of your video card designed to hold information about vertices. In our example we have two VBOs, one that describes the coordinates of our vertices and another that describes the color associated with each vertex. VBOs can also store information such as normals, texcoords, indicies, etc.

### 정점 배열 객체
[정점 배열 객체(Vertex Array Object, VAO)](https://www.khronos.org/opengl/wiki/Vertex_Specification#Vertex_Array_Object)

A Vertex Array Object (VAO) is an object which contains one or more Vertex Buffer Objects and is designed to store the information for a complete rendered object. In our example this is a diamond consisting of four vertices as well as a color for each vertex.

## 셰이더 프로그램
셰이더 프로그램은 여러 셰이더를 링크(Link)해주고 파이프라인에 셰이더를 등록해주는 역할을 한다. 여기서 링크(Link)란 셰이더의 입출력값이 서로 전달될 수 있도록 해준다는 뜻이다.

## 참고 자료
- [SO Reply - What is a VBO?](https://stackoverflow.com/a/65372213)