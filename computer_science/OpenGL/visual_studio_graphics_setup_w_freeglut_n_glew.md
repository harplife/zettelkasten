---
aliases: [OpenGL 프로젝트 셋업 1, OpenGL Project Setup 1, GLEW 및 freeGLUT 연동, Setup using GLEW and freeGLUT]
tags: [computer_science, computer_vision, computer_graphics, KNOU, study, display, settings, example]
status: ongoing
created: 2022-06-04
edited: 2022-06-04
---

# GLEW 및 freeGLUT 연동
이 가이드는 OpenGL 프로젝트를 만들기 위해 필요한 라이브러리(freeGLUT & GLEW)를 설치하고 Visual Studio에 연동하는 방안을 정리한다.

freeGLUT은 윈도를 통한 사용자와의 인터페이스를 제공하기 위해 사용되는 라이브러리다. [[computer_graphics_software#윈도 시스템 관리 라이브러리]] 참고.

GLEW는 OpenGL의 확장 기능을 관리하는 라이브러리다. [[computer_graphics_software#확장 기능 관리 라이브러리]] 참고.

## 설치
각 링크로 부터 설치파일 다운로드
- [freeGLUT 다운로드](https://www.transmissionzero.co.uk/software/freeglut-devel/)
- [GLEW 다운로드](http://glew.sourceforge.net/)

다운로드한 압축파일들을 풀어줌
1. `C:\`에 `OpenGL` 폴더 생성
2. `freeglut-MSVC-3.0.0-2.mp.zip` 압축 해제 -> `freeglut` 폴더가 나옴
3. `glew-2.1.0-win32.zip` 압축 해제 -> `glew-2.1.0` 폴더가 나옴
4. 두 폴더를 `C:\OpenGL\`로 옮겨줌

## DLL 설치
방통대 교제에서 개발 PC 시스템 설정에 맞추어 하란 말이 없어서, 일단 밑에 둘 다 적용해줌.

### 64 bit 시스템
`C:\Windows\System32\` 경로로 밑에 두 파일을 복사해줌
- `C:\OpenGL\freeglut\bin\x64\freeglut.dll`
- `C:\OpenGL\glew-2.1.0\bin\Release\x64\glew32.dll`

### 32 bit 시스템
`C:\Windows\SysWOW64` 경로로 밑에 두 파일을 복사해줌
- `C:\OpenGL\freeglut\bin\freeglut.dll`
- `C:\OpenGL\glew-2.1.0\bin\Release\Win32\glew32.dll`

## 프로젝트 설정
프로젝트 생성 후 속성 페이지 열기
1. Visual Studio 열기 $\rightarrow$ "Create a new project" 클릭
2. 프로젝트 유형 선택 ("Empty Project" 선택) $\rightarrow$ 프로젝트 이름 및 솔루션 이름 지정 (예: `GraphicsProject` - `Renderer`)
3. 프로젝트 속성 페이지를 연다 - "Project" 메뉴 $\rightarrow$  "Properties" 선택

### 라이브러리 설정
속성 페이지에서 라이브러리 설정 진행
1. "Configuration Properties" 아래 "VC++ Directories" 클릭 $\rightarrow$ "Library Directories" 오른쪽 입력칸에 `v` 버튼 클릭 $\rightarrow$ "Edit" 클릭하면 작은 창이 하나 뜸
2.  작은 창 상단에 "New Line" 버튼 클릭 $\rightarrow$ 라인 오른쪽 끝에 "..." 버튼 클릭

**< 프로젝트가 x86(즉, Win32)용인 경우 >**
3. `C:\OpenGL\freeglut\lib` 추가
4.  `C:\OpenGL\glew-2.1.0\lib\Release\Win32` 추가

**< 프로젝트가 x64용인 경우 >**
3. `C:\OpenGL\freeglut\lib\x64` 추가
4. `C:\OpenGL\glew-2.1.0\lib\Release\x64` 추가

### 헤더파일 설정
속성 페이지에서 헤더파일 설정 진행
1. C++ 파일 한개 생성 (C++에 대한 프로젝트 속성이 뜨게 하려면 필요)
2. 속성 페이지 "Configuration Properties" 아래 "C/C++" 아래 "General" 클릭 $\rightarrow$ "Additional Include Directories" 오른쪽 입력칸에 `v` 버튼 클릭 $\rightarrow$ "Edit" 클릭하면 작은 창이 하나 뜸
3. 작은 창 상단에 "New Line" 버튼 클릭 $\rightarrow$ 라인 오른쪽 끝에 "..." 버튼 클릭
4. `C:\OpenGL\freeglut\include` 추가
5. `C:\OpenGL\glew-2.1.0\include` 추가


### 의존성 설정
속성 페이지에서 freeGLUT & GLEW 라이브러리를 사용할 수 있도록 설정
1. "Configuration Properties" 아래 "Linker" 아래 "Input" 클릭 $\rightarrow$ "Additional Dependencies" 오른쪽 입력칸에 `v` 버튼 클릭 $\rightarrow$ "Edit" 클릭하면 작은 창이 하나 뜸
2. 상단 입력칸에 `freeglut.lib`와 `glew32.lib` 입력

### 개인 설정
개인적으로 내가 원하는 설정
1. "Solutions Explorer" 창에 "Show All Files" 옵션 클릭
2. 프로젝트 아래 `src` 폴더 생성
3. 프로젝트 속성의 "General"에 "Output Directory" 값을 `$(SolutionDir)\bin\$(Platform)\$(Configuration)\`로 입력
4. 프로젝트 속성에 "General"에 "Intermediate Directory" 값을 `$(SolutionDir)\bin\intermediates\$(Platform)\$(Configuration)\`로 입력

## 테스트
1. 헤더파일 설정할 때 만들었던 
2. 교재 소스코드 중 `01_OpenGLSample` 폴더 내에 `OpenGLSample.cpp` 파일을 가져옴
3. 코드에 `#define FREEGLUT_STATIC`과 `#define GLEW_STATIC`는 코멘트 `//` 처리되어야 함
4. `F5` 눌러서 프로젝트 빌드 후 실행

밑에와 같이 결과가 나와야 함.
![[01_OpenGLSample_output_console.png]]
![[01_OpenGLSample_output_window.png]]