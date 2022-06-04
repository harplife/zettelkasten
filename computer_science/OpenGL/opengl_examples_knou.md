---
aliases: [방통대 OpenGL 코드 예시]
tags: [computer_science, computer_vision, computer_graphics, KNOU, study, display, settings, example]
status: ongoing
created: 2022-06-04
edited: 2022-06-04
---

# 방통대 OpenGL 코드 예시
[방통대 교재 코드 참고](https://professor.knou.ac.kr/bbs/brlee/2983/289896/artclView.do?layout=unknown)

## 프로젝트 설정
[[visual_studio_graphics_setup_w_freeglut_n_glew|OpenGL 프로젝트 셋업 1]]

## 간단한 삼각형 그리기
`01_OpenGLSample` 폴더 아래 `OpenGLSample.cpp`에 대해 정리한다.

이 코드는 4가지 작업을 한다.
1. OpenGL의 동작 환경을 준비한다 - OpenGL이 윈도 시스템을 통해 사용자와 상호작용할 수 있도록 준비하고, OpenGL의 기능을 활용할 수 있도록 준비한다.
2. 셰이더의 프로그램을 준비한다.
3. 그림을 생성하기 위한 준비를 한다. 그림을 구성하는 개체(삼각형)의 정점(Vertex) 데이터를 준비한다.
4. 그림을 그린다 (렌더링).

### OpenGL 동작 환경 준비
OpenGL 동작 환경 준비하기 앞서, freeGLUT과 GLEW를 사용하기 위한 헤더파일을 포함시킨다 (4, 5행은 정적 연결 라이브러리를 사용하게 한다).
```cpp
// 6, 7행
#include <gl/glew.h>
#include <gl/freeglut.h>
```

본격적인 OpenGL 동작 환경 준비는 메인 함수(118~142행) 안에서 진행된다.

```cpp
// 120 ~ 130행
glutInit(&argc, argv);
glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB);
glutInitWindowPosition(50, 100);
glutInitWindowSize(640, 480);
glutCreateWindow("OpenGL Sample");

GLenum err = glewInit();
if (err != GLEW_OK) {
    cerr << "오류 - " << glewGetErrorString(err) << endl;
    return 1;
}
```

#### GLUT 초기화
`void glutInit(int *argcp, char **argv)` : freeGLUT을 초기화하는 함수. 시작 전 최우선적으로 해줘야 함.
```cpp
// 120행
glutInit(&argc, argv);
```

#todo 이 초기화 함수는 명령행 인수도 처리할 수 있다?

참고 자료 :
- [OpenGL 설명](https://www.opengl.org/resources/libraries/glut/spec3/node10.html)

#### 디스플레이 설정
`void glutInitDisplayMode(unsigned int mode)` : 디스플레이 방식 옵션을 지정하는 함수. 
```cpp
// 121행
glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB);
```

참고 : `|`는 논리합(`bitwise or`)이다 ([SO 참고](https://stackoverflow.com/a/17366923)). #todo 인수(Argument)로 논리합 값을 받는게 자주 사용되나?

위 코드는 하나의 재생 버퍼가 사용됨과 [[color_theory#RGB 색 모델]]이 사용됨을 지정한다. 원래 이 설정은 기본(Default)이다.

#todo 재생 버퍼?

참고 자료 :
- [OpenGL 설명](https://www.opengl.org/resources/libraries/glut/spec3/node12.html)

#### 윈도 위치와 사이즈
`void glutInitWindowPosition(int x, int y)` : 윈도의 좌상단(Leftmost Upper Corner)의 초기위치(x, y)를 지정하는 함수.

이 함수는 정수(Integer)만 받으며 화면 좌상단 좌표(0, 0)로부터 픽셀 단위로 위치를 지정한다. 위 코드는 창의 위치를 좌표(50, 100)로 지정한다.

`void glutInitWindowSize(int width, int height)` : 윈도의 크기를 지정한다.

```cpp
// 122, 123행
glutInitWindowPosition(50, 100);
glutInitWindowSize(640, 480);
```

참고 자료 :
- [OpenGL 설명](https://www.opengl.org/resources/libraries/glut/spec3/node11.html)

#### 윈도 생성
`int glutCreateWindow(char *name)` : 윈도를 생성하는 함수. 인수에 들어가는 문자열은 윈도의 제목 막대(Title Bar)에 들어간다.
```cpp
// 124행
glutCreateWindow("OpenGL Sample");
```

실제로 윈도가 화면에 그려지는 것은 아니다.

참고 자료 :
- [OpenGL 설명](https://www.opengl.org/resources/libraries/glut/spec3/node16.html)

#### GLEW 초기화
`glutInit()` : GLEW를 초기화하는 함수. GLUT을 초기화한 후 불러줘야 함.
```cpp
// 126 ~ 130행
GLenum err = glewInit();
if (err != GLEW_OK) {
    cerr << "오류 - " << glewGetErrorString(err) << endl;
    return 1;
}
```

`glewInit()` 함수가 실행되면 GLEW가 제대로 초기화 됬는지 상태 코드를 리턴해준다. `GLEW_OK`면 제대로 초기화된 것이고, 아니면 에러다.

참고 자료 :
- [GLEW 기본 지식](http://glew.sourceforge.net/basic.html)

### 셰이더 프로그램밍
이 코드에서는 [[computer_graphics_software#정점 셰이더]]와 [[computer_graphics_software#조각 셰이더]]가 사용된다.

#### 정점 셰이더
이 코드에서는 정점 셰이더를 GLSL로 작성하였으며, 소스 프로그램에 직접 포함시켰다.

참고 : 셰이더를 소스 프로그램에 직접 포함시킬 경우, 각 라인 끝에 newline(`\n`)을 입력해줘야 한다. 아주 귀찮은 작업이고 쉽게 잊을 수 있으니, 따로 파일에 작성하여 읽어오는게 권장된다.

```cpp
// 18 ~ 25행
static const char* pVS =
"#version 330\n"
"layout (location = 0) in vec3 Position;\n"
"\n"
"void main()\n"
"{\n"
"    gl_Position = vec4(Position*0.1, 1.0);\n"
"}";
```

##### 셰이더 언어 버전
`#version 330` : C 언어와 유사하게 선행처리기 지시어 문장을 사용하는데, 이로서 GLSL의 버전을 명시한다. 여기선 GLSL 3.3버전을 사용한다.

##### 레이아웃 지정

