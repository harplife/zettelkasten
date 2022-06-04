# GLEW 및 freeGLUT 연동
이 가이드는 OpenGL 프로젝트를 만들기 위해 필요한 라이브러리(freeGLUT & GLEW)를 설치하고 Visual Studio에 연동하는 방안을 정리한다.

## 설치
각 링크로 부터 설치파일 다운로드
- [freeGLUT 다운로드](https://www.transmissionzero.co.uk/software/freeglut-devel/)
- [GLEW 다운로드](http://glew.sourceforge.net/)

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
1. Visual Studio 열기 $\rightarrow$ "Create a new project" 클릭
2. 프로젝트 유형 선택 ("Empty Project" 선택) 
3. 프로젝트 이름 및 솔루션 이름 지정 (예: `GraphicsProject` - `Renderer`)
4. 

`프로젝트` 메뉴 $\rightarrow$  `속성` 선택하여 프로젝트의 속성 페이지를 연다.

--> [구성 속성] -> [VC++ 디렉터리] -> [라이브러리 디렉터리]의 내용을 클릭한 후 우측의 [v]단추를 눌러 <편집...> 클릭

--> 디렉터리 입력 창을 클릭한 후 그 행의 우측 끝부분을 클릭하여 [...]을 클릭하면 디렉터리를 선택할 수 있음

--> c:\OpenGL\freeglut\lib 디렉터리를 선택

--> 동일한 방법으로 c:\OpenGL\glew-2.1.0\lib\Release\Win32 디렉터리를 선택



**주의 : 프로젝트가 x86(즉, Win32)용인 경우임 만일 x64용으로 플렛폼을 선택하였다면 위의 디렉토리 대신

c:\OpenGL\freeglut\lib\x64와 c:\OpenGL\glew-2.1.0\lib\Release\x64 디렉터리를 선택함



나. freeglut와 glew 헤더파일을 사용할 수 있도록 설정



(가)와 동일한 속성 페이지에서

--> [구성 속성] -> [C/C++] -> [일반] -> [추가 포함 디렉토리] -> <편집...>

   ※ 주의 : [구성 속성]에서 [C/C++]는 프로젝트에 C++ 소스파일이 한 개 이상 들어 있어야 보임

--> 디렉토리 입력 창을 클릭한 후 그 행의 우측 끝부분을 클릭하여 [...]을 클릭하면 디렉터리를 선택할 수 있음

--> c:\OpenGL\freeglut\include 디렉터리를 선택

--> 동일한 방법으로 c:\OpenGL\glew-2.1.0\include 선택



다. freeglut와 glew 라이브러리를 사용할 수 있도록 설정



(가)와 동일한 속성 페이지에서

--> [구성] -> [링커] -> [입력] -> [추가 종속성] -> <편집...>

--> 아래의 라이브러리 파일 이름을 입력

freeglut.lib

glew32.lib



3. 프로젝트에서 소스파일을 작성한다.

** 교재의 프로그램에서 다음 두 문장은 삭제(또는 //로 코멘트로 처리)하고 사용함



  #define FREEGLUT_STATIC

  #define GLEW_STATIC



4. 프로젝트를 빌드한 후 실행한다.



첨부파일 출처