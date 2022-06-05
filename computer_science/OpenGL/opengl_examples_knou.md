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

## 간단한 2D 삼각형 그리기
`01_OpenGLSample` 폴더 아래 `OpenGLSample.cpp`에 대해 정리한다.

이 코드는 4가지 작업을 한다.
1. OpenGL의 동작 환경을 준비한다 - OpenGL이 윈도 시스템을 통해 사용자와 상호작용할 수 있도록 준비하고, OpenGL의 기능을 활용할 수 있도록 준비한다.
2. 그림 그릴 모델을 준비한다 - 개체(삼각형)의 정점(Vertex) 데이터를 준비한다.
3. 셰이더의 프로그램을 준비한다.
4. 그림을 그린다 (렌더링).

### OpenGL 동작 환경 준비
OpenGL 동작 환경 준비하기 앞서, freeGLUT과 GLEW를 사용하기 위한 헤더파일을 포함시킨다 (4, 5행은 정적 연결 라이브러리를 사용하게 한다).
```cpp
#include <gl/glew.h>
#include <gl/freeglut.h>
```

본격적인 OpenGL 동작 환경 준비는 `main()` 함수 안에서 진행된다.

```cpp
// GLUT 초기화
glutInit(&argc, argv);
glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB);
glutInitWindowPosition(50, 100);
glutInitWindowSize(640, 480);
glutCreateWindow("OpenGL Sample");

// GLEW 초기화
GLenum err = glewInit();
if (err != GLEW_OK) {
    cerr << "오류 - " << glewGetErrorString(err) << endl;
    return 1;
}
```

#### GLUT 초기화
`void glutInit(int *argcp, char **argv)` : freeGLUT을 초기화하는 함수. 시작 전 최우선적으로 해줘야 함.
```cpp
int main(int argc, char** argv)
{
    glutInit(&argc, argv);
    // ..
}
```

#todo argc, argv 가 뭔지?

#todo 이 초기화 함수는 명령행 인수도 처리할 수 있다?

참고 자료 :
- [OpenGL 설명](https://www.opengl.org/resources/libraries/glut/spec3/node10.html)

#### 디스플레이 설정
`void glutInitDisplayMode(unsigned int mode)` : 디스플레이 방식 옵션을 지정하는 함수. 
```cpp
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
glutInitWindowPosition(50, 100);
glutInitWindowSize(640, 480);
```

참고 자료 :
- [OpenGL 설명](https://www.opengl.org/resources/libraries/glut/spec3/node11.html)

#### 윈도 생성
`int glutCreateWindow(char *name)` : 윈도를 생성하는 함수. 인수에 들어가는 문자열은 윈도의 제목 막대(Title Bar)에 들어간다.
```cpp
glutCreateWindow("OpenGL Sample");
```

실제로 윈도가 화면에 그려지는 것은 아니다.

참고 자료 :
- [OpenGL 설명](https://www.opengl.org/resources/libraries/glut/spec3/node16.html)

#### GLEW 초기화
`glutInit()` : GLEW를 초기화하는 함수. GLUT을 초기화한 후 불러줘야 함.
```cpp
GLenum err = glewInit();
if (err != GLEW_OK) {
    cerr << "오류 - " << glewGetErrorString(err) << endl;
    return 1;
}
```

`glewInit()` 함수가 실행되면 GLEW가 제대로 초기화 됬는지 상태 코드를 리턴해준다. `GLEW_OK`면 제대로 초기화된 것이고, 아니면 에러다.

참고 자료 :
- [GLEW 기본 지식](http://glew.sourceforge.net/basic.html)

### 모델 데이터 준비
그림 그리는 대상이 되는 모델을 준비하기 위해 밑에와 같은 작업을 한다.
1. 모델의 정점 데이터 준비
2. 정점 버퍼 객체 선언
3. 정점 버퍼 객체 초기화 (정점 데이터 입력)

이 코드는 삼각형의 3개 정점의 좌표를 [[computer_graphics_shader#정점 버퍼 객체|정점 버퍼 객체(VBO)]]에 저장하여 처리한다.
```cpp
// 1) 모델의 정점 데이터
float vertices[] = {
    -0.5f, -0.5f, 0.0f,
     0.5f, -0.5f, 0.0f,
     0.0f,  0.5f, 0.0f
};

// 2) 정점 버퍼 객체 선언
unsigned int VBO;

// 3) 정점 버퍼 객체 초기화
static void InitVBOs()
{
    glGenBuffers(1, &VBO);
    glBindBuffer(GL_ARRAY_BUFFER, VBO);
    glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);
}
```

`vertices`는 3x3 행렬로 3개의 정점의 3차원 좌표(x, y, z)를 가진다. #todo 여기서 값들이 `[-1, 1]`사이의 값들로 표현된다는 것을 참고한다 - 래스터화와 관련되어 있다.

`VBO` : [[computer_graphics_shader#정점 버퍼 객체|정점 버퍼 객체]]가 될 변수이다. 이름이 어떻게 되는 상관은 없다 - 다만, OpenGL이 이 변수가 VBO라는 것을 모르기 때문에 이를 위해 따로 처리를 해줘야 한다.

`void glGenBuffers(GLsizei n, GLuint * buffers)` : VBO의 핸들(Handle)을 생성하는 함수로서, `n`은 VBO 핸들의 개수, `buffers`는 VBO 핸들을 저장할 배열이다. 여기서 1개의 버퍼를 생성해서 `VBO` 변수의 인덱스를 받게 해준다.

참고 : [OpenGL - glGenBuffers](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glGenBuffers.xhtml)

`void glBindBuffer(GLenum target, GLuint buffer)` : 생성된 버퍼의 목적을 정의하는 함수라고 볼 수 있다. `GL_ARRAY_BUFFER`는 정점 속성(Vertex Attributes)을 뜻하는 버퍼이며 고정변수이다 - #todo `VBO` 변수와 바인딩된다?

참고 : [OpenGL - glBindBuffer](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glBindBuffer.xhtml)

`void glBufferData(GLenum target, GLsizeiptr size, const void * data, GLenum usage)` : 생성되고 바인딩까지한 버퍼 객체에 정점 데이터를 넣어준다.

여기서 `usuage`는 버퍼 데이터의 용도를 GPU에게 힌트해주고, GPU는 이 힌트에 따라서 데이터의 Read & Write에 대한 최적화를 한다. `GL_STATIC_DRAW`은 데이터가 1번만 변환되고 자주 사용됨을 뜻한다.

참고 : [OpenGL - glBufferData](https://www.khronos.org/registry/OpenGL-Refpages/es1.1/xhtml/glBufferData.xml)

### 셰이더 프로그램밍
이 코드에서는 [[computer_graphics_software#정점 셰이더]]와 [[computer_graphics_software#조각 셰이더]]가 사용된다.

이 코드에서는 셰이더를 GLSL로 작성하였으며, 소스 프로그램에 직접 포함시켰다.

참고 : 셰이더를 소스 프로그램에 직접 포함시킬 경우, 각 라인 끝에 newline(`\n`)을 입력해줘야 한다. 아주 귀찮은 작업이고 쉽게 잊을 수 있으니, 따로 파일에 작성하여 읽어오는게 권장된다.

#### 정점 셰이더
이 정점 셰이더 예시는 아주 간단한 프로그램으로 정점 데이터를 전달해주는 작업만 한다.

```cpp
static const char* pVS =
"#version 330\n"
"layout (location = 0) in vec3 aPos;\n"
"\n"
"void main()\n"
"{\n"
"    gl_Position = vec4(aPos.x, aPos.y, aPos.z, 1.0);\n"
"}";
```

정점 셰이더가 실행된 후 래스터화(Rasterization)이 진행된다.

##### 셰이더 언어 버전
`#version 330` : C 언어와 유사하게 선행처리기 지시어 문장을 사용하는데, 이로서 GLSL의 버전을 명시한다. 여기선 GLSL 3.3버전을 사용한다.

##### 레이아웃 한정자
`layout (location = 0) in vec3 aPos` : [레이아웃 한정자(Layout Qualifier)](https://www.khronos.org/opengl/wiki/Layout_Qualifier_(GLSL))로서 OpenGL 프로그램으로부터 전달되는 정점 정보가 `vec3`\*로 표현되는 전역변수 `aPos`에 입력됨과 이 정보의 인덱스가 0번임을 알린다.

\* `vec3` : [[computer_graphics_shader#셰이더 데이터 유형|OpenGL 데이터 유형]]으로 3개의 `GLfloat` 값이 전달된다 - 이 값들은 각각 순서대로 x, y, z 좌표이다. [[#모델 데이터 준비]] 단계에서 정의했던 정점 버퍼 객체의 데이터가 `aPos`로 들어온다.

참고 : 정점 셰이더는 정점의 개수만큼 실행된다. 그 말은, VBO 데이터의 한 행(Row)씩 처리된다는 것이다.

#todo 레이아웃 한정자에 대해서 [[computer_graphics_shader|셰이더]]에 정리.

##### 정점 위치 처리
`gl_Position = vec4(aPos.x, aPos.y, aPos.z, 1.0)` : 메인 함수에서 `aPos`에 입력된 정점 좌표를 처리하여 `gl_Position`를 통해 다음 파이프라인 단계로 전달한다.

`gl_Position`은
1. OpenGL의 [[computer_graphics_shader#고정 변수|OpenGL 고정 변수]]이며, 정점의 위치 값을 가지고 파이프라인 사이에 전달되는 중요한 변수이다.
2. 3차원 [동차좌표(Homogeneous Coordinates)](https://en.wikipedia.org/wiki/Homogeneous_coordinates)로 x, y, z 그리고 w([사양](https://en.wikipedia.org/wiki/Projective_geometry)) 좌표값들을 가진다.

#### 조각 셰이더
이 조각 셰이더 예시는 아주 간단한 프로그램으로 도형의 색만 정의해준다.

```cpp
static const char* pFS =
"#version 330\n"
"out vec4 FragColor;\n"
"\n"
"void main()\n"
"{\n"
"    FragColor = vec4(1.0, 0.0, 0.0, 1.0);\n"
"}";
```

조각 셰이더는 정점 셰이더가 진행되고 래스터화(Rasterization)까지 된 후에 실행된다.

##### 셰이더 언어 버전
정점 셰이더와 마찬가지로 GLSL 3.3 버전이다.

##### 출력 변수 선언
`out vec4 FragColor` : `FragColor`는 도형의 색을 정의하게 될, 4개의 소수값을 받는  변수로서 선언된다. 여기서 `out`은 셰이더의 출력값(Output)임을 명시한다.

##### 정점 색 처리
`FragColor = vec4(1.0, 0.0, 0.0, 1.0)` : 메인 함수에서 도형의 색을 정의한다 - RGBA 모델을 사용하며, 불투명한 빨간색임을 알려준다.

#todo RGBA 모델 정리 ([[color_theory|색 이론]])

### 셰이더 등록
셰이더를 작성했으니, GPU에 등록해줘야 한다.

이 코드에서는 셰이더를 GPU에 등록하는 프로세스를 두 가지로 나누었다.
1. 셰이더 추가
2. 셰이더 프로그램 등록

#### 셰이더 추가
이 코드에 작성된 `AddShader()` 함수는 5가지 작업을 한다.
1. 빈(Empty) OpenGL 셰이더 객체 생성
2. 셰이더 객채에 GLSL 소스 입력
3. 셰이더 객체 컴파일
4. 셰이더 컴파일 에러 핸들링
5. 셰이더 프로그램에 셰이더 객체 등록

```cpp
static void AddShader(GLuint shaderProg, const char* pShaderSrc, GLint ShaderType)
{   // 셰이더 생성
    GLuint shader = glCreateShader(ShaderType);
    if (!shader) {
        cerr << "오류 - Shader 생성(" << ShaderType << ")" << endl;
        exit(0);
    }
    // 셰이더 컴파일
    const GLchar* src[1] = { pShaderSrc };
    const GLint len[1] = { strlen(pShaderSrc) };
    glShaderSource(shader, 1, src, len);
    glCompileShader(shader);
    GLint success;
    glGetShaderiv(shader, GL_COMPILE_STATUS, &success);
    if (!success) {		// 컴파일 오류 발생
        GLchar infoLog[256];
        glGetShaderInfoLog(shader, 256, NULL, infoLog);
        cerr << "오류 - Shader 컴파일(" << ShaderType << "): " << infoLog << endl;
        exit(1);
    }
    // 셰이더 프로그램에 컴파일된 셰이더를 추가
    glAttachShader(shaderProg, shader);
}
```

##### 셰이더 객체 생성
`GLuint glCreateShader(GLenum shaderType)` : `shaderType`으로 지정된 셰이더 유형으로서 비어있는 OpenGL 셰이더 객체를 생성해주는 함수이다.

참고 : [OpenGL - glCreateShader](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glCreateShader.xhtml)

##### 셰이더 소스 입력
`void glShaderSource(GLuint shader, GLsizei count, const GLchar **string, const GLint *length)` : OpenGL 셰이더 객체에 GLSL 소스를 입력해주는 함수이다.

참고 : [OpenGL - glShaderSource](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glShaderSource.xhtml)

##### 셰이더 객체 컴파일
`void glCompileShader(GLuint shader)` : GLSL 소스를 가진 OpenGL 셰이더 객체를 GPU에 컴파일하는 함수이다.

참고 : [OpenGL - glCompileShader](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glCompileShader.xhtml)

##### 셰이더 컴파일 에러 핸들링
`void glGetShaderiv(GLuint shader, GLenum pname, GLint *params)` : 셰이더 객체의 정보를 가져오는 함수이다. `pname`은 셰이더 객체의 매개변수를 지정하는데 사용된다. `*params`는 요청했던 매개변수의 값을 저장하는 대상이 된다.

`glGetShaderiv(shader, GL_COMPILE_STATUS, &success)`에서 `GL_COMPILE_STATUS`는 셰이더의 컴파일 상태를 뜻한다. `success` 변수에 이 상태를 저장한다.

참고 : [OpenGL - glGetShaderiv](https://www.khronos.org/registry/OpenGL-Refpages/es2.0/xhtml/glGetShaderiv.xml)

`success`의 값이 `0`인 경우, `glGetShaderInfoLog()`로 자세한 에러 로그를 출력해볼 수 있다.

참고 : [OpenGL - glGetShaderInfoLog](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glGetShaderInfoLog.xhtml)

##### 셰이더 프로그램에 등록
`void glAttachShader(GLuint program, GLuint shader)` : 셰이더 프로그램은 여러 셰이더를 담는 하나의 목록이라 볼 수 있다.