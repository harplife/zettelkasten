---
aliases: [Visual C++ Notes, 비주얼 C++ 노트]
tags: [computer_science, computer_vision, computer_graphics, GUI, KNOU, study]
status: ongoing
created: 2022-10-20
edited: 2022-10-20
---

# Visual Studio 설치 및 설정
교과서에는 2019 버전 설치를 말하는데.. 일단 2022 버전으로 설치해서 진행할 것.

## 도움말 뷰어 설치
오프라인 Visual C++ 도움말 설치. 기본적으로 온라인에서 매번 도움말을 호출해오지만, 도움말 뷰어에서 VC++ 도움말을 설치하면 오프라인 도움말을 불러옴으로 훨씬 빠름.

일단 이 [링크](https://learn.microsoft.com/ko-kr/visualstudio/help-viewer/installation?view=vs-2022)를 통해서 도움말 뷰어를 설치하고, 상단 메뉴 `Help` 아래 `Add and Remove Help Content` 클릭하면 밑과 같은 창이 뜸.

![[비주얼_스튜디오_도움말_뷰어_창_20221020.png]]

교과서에는 Visual C++ 도움말을 설치하라고 하는데, 검색에 뜨지 않음. 그냥 C++ 관련된 모든 도움말을 업데이트 해보고 진행함.

## 파일 확장자
C++ 프로젝트를 진행하며 발생되는 파일들의 유형은 밑과 같다.

![[cpp_file_formats.png]]


`.sdf` 포맷의 파일들은 용량이 크고 "필요가 없으니" 프로젝트를 생성할 때 생성되지 않게 설정할 수 있음.

상단 메뉴 `Tools` -> `Options` -> `Text Editor` -> `C/C++` -> `Advanced` -> `Browsing Database Fallback`에 있는 설정들을 밑에 그림과 같이 설정.

![[visual_studio_cpp_turnoff_sdf_file_generation.png]]

## 백신 검사 예외 설정
C++로 개발하다 보면 백신 프로그램에서 바이러스로 오인하는 경우가 발생할 수 있으니 백신 프로그램에서 프로젝트 폴더 경로를 검사 예외로 지정하는게 좋다.

# 제1장
- 윈도우 프로그램은 Windows 운영체제의 지원을 받으며 실행되는 응용 프로그램이므로 과거 콘솔 프로그램과 달리 Windows 운영체제의 특징을 그대로 반영하고 있다.
- **Windows 운영체제에서 실행되는 윈도우 프로그램들은 편리한 사용자 인터페이스를 지원받고 장치 독립적이며 멀티태스킹이 가능하다.**
- Visual C++을 이용하여 윈도우 프로그램을 개발하는 경우, 개발자는 Windows 운영체제에서 제공하는 WinAPI 함수와 방대한 클래스 라이브러리인 MFC을 자유롭게 사용할 수 있어 적은 노력과 시간으로도 과거에는 생각할 수 없었던 대규모 프로그램들을 개발할 수 있다.
- 윈도우 프로그램을 공부하려면, 먼저 WinAPI 함수를 사용하는 API 프로그래밍을 살펴본 다음 MFC에서 제공하는 방대한 클래스를 사용하는 MFC 프로그래밍을 공부해야 한다.
- 이 장에서는 먼저, WinAPI를 사용하여 윈도우를 생성하는 윈도우 프로그램에 대해 설명한다. Windows 운영체제의 지원을 받는 윈도우 프로그램의 특징을 살펴보고 WinAPI로 구성된 윈도우 프로젝트를 작성해 본다. 윈도우를 등록/생성하고 보여 주는 데 필요한 각각의 WinAPI 함수와 이를 위해 필요한 메시지 처리방식, 윈도우 프로시저 함수 등을 중심으로 설명한다.

## 학습목표
1. 윈도우 프로그램의 특징을 이해한다.
2. 메시지 중심의 처리과정을 이해한다.
3. 간단한 윈도우를 생성하는 윈도우 프로젝트를 작성할 수 있다.
4. WinMain 함수의 역할과 코드를 이해할 수 있다.
5. 윈도우 프로시저 함수의 역할을 이해할 수 있다.
6. 차일드 윈도우와 버튼 컨트롤을 생성하는 데 필요한 함수와 추가 코드를 작성할 수 있다.

## 주요용어
- Windows 운영체제
- 멀티태스킹
- 메시지 구동방식
- MFC
- GDI
- API
- WinMain
- 윈도우 프로시저
- CALLBACK 함수
- 윈도우 클래스
- 윈도우 클래스 등록
- 윈도우 생성
- 메시지 루프
- TextOut 함수
- 버튼
- 컨트롤

## 윈도우 프로그램
- MS Windows는 Microsoft사에서 만든 개인용 컴퓨터의 운영체제 이름으로 간단히 Windows라고 부른다.
- 1990년대 초까지만 해도 개인용 컴퓨터의 운영체제는 MS사에서 제작한 DOS였다.
- 1990년대 이후 DOS는 여러 가지 버전의 Windows로 바뀌었다.
- 윈도우 프로그램이란 Windows에서 실행할 수 있는 응용 프로그램이다.
- 우리가 자주 사용하는 윈도우 프로그램은 실행 결과가 항상 사각형 윈도우(Window) 형태인데, 자세히 보면 윈도우 안에 타이틀바, 툴바, 메뉴바, 버튼 등 여러 개의 윈도우가 들어 있다.

### 윈도우 프로그램 특징
Windows에서 실행하는 윈도우 프로그램은 다음과 같은 특징을 갖는다.

#### 장치 독립적
- 윈도우 프로그램을 작성할 떄는 설치된 하드웨어의 사양을 고려하지 않고 자유롭게 작성할 수 있다.
- 과거 DOS에서 프로그램은 화면에 점 하나를 찍는 단순 작업을 위해 그래픽카드 종류, 화면 해상도 지원 범위, 컬러 지원 범위 등을 검사해 본 후 여기에 맞게 소스 코드를 작성해야만 했다.
- 윈도우 프로그램의 경우 하드웨어 장치가 어떤 모델이든 상관없다. Windows에 요청하면 운영체제가 하드웨어에 적당한 드라이버를 찾아서 스스로 설치하므로 윈도우 프로그램은 하드웨어에 종속되지 않는다. 즉, 언제나 동일한 소스 코드를 작성한다.

#### 멀티태스킹
- Windows는 멀티태스킹(Multitasking)을 지원하므로 여러 윈도우 프로그램이 동시에 실행된다.
- 화면에 여러 개의 윈도우가 동시에 있어서 사용자 입장에서는 여러 개의 태스크가 동시에 실행되는 것처럼 보인다.
- 각각의 윈도우 프로그램은 다른 윈도우 프로그램에 의해 자신의 작업 영역에 영향을 받을 수 있으므로, 윈도우 프로그램은 항상 자신의 작업 영역을 복수할 수 있도록 작성되어야 한다.

#### 메시지 구동방식
- 윈도우 프로그램은 메시지 구동방식(Message-Driven)으로 동작한다.
- 메시지 구동방식은 Windows의 가장 중요한 특징으로, 모든 윈도우 프로그램은 이러한 메시지 구동방식에 적절히 대처할 수 있도록 작성되어야 한다.

#### GUI
- Windows는 사용자 인터페이스인 GUI (Graphic User Interface)로 동작된다.
- 사용자의 컴퓨터 사용환경이 모두 그래픽 모드에서 이루어지므로 윈도우 프로그램도 이에 맞는 GUI를 제공해야 한다.
- 윈도우 프로그램은 GUI를 제공하기 위한 리소스 (예: 비트맵 이미지, 아이콘, 커서, 메뉴, 대화상자 등)가 필요하다.

### 기초 용어
윈도우 프로그램을 작성할 때 기본적으로 알아야 하는 기초 용어

#### 운영체제
- 운영체제(OS : Operating System)은 컴퓨터의 하드웨어를 직접적으로 제어하고 관리하는 시스템 소프트웨어이다.
- 운영체제는 실행되는 응용 프로그램이 메모리와 CPU, 입출력장치 등의 자원을 사용할 수 있도록 만들어 주고, 그들을 추상화하여 파일 시스템 등의 서비스를 제공한다.
- 운영체제는 여러 개의 응용 프로그램이 실행되는 동안 모든 프로세스를 스케줄링하여 마치 그들이 동시에 수행되는 듯한 효과를 낸다.

#### 커널
- 커널(Kernel)은 운영체제의 핵심 부분으로 운영체제의 다른 부분 및 응용 프로그램 수행에 필요한 여러 가지 서비스를 제공한다.

#### 소스 코드
- 소스 코드(Source Code)는 컴퓨터 프로그램을 사람이 읽고 사용할 수 있는 프로그래밍 언어로 기술한 글을 말한다.

#### 컴퓨터 프로그램
- 컴퓨터 프로그램(Computer Program)은 컴퓨터에 의해 실행되는 지시사항의 모음인 컴퓨터 소프트웨어의 한 예이다.
- 프로그램은 대부분 실행 중에 사용자의 입력에 반응하도록 구현된 명령어의 집합으로 구성되어 있다.

#### MS DOS
- MS DOS(Microsoft Disk Operating System)은 MS사가 개발한 IBM PC용 운영체제이다.
- 1981년에 처음 제공되어 널리 사용되었으나, 1995년 이후에 Windows로 대체되면서 개발이 중단되었다.

#### MS Windows
- MS Windows는 MS사가 개발한 컴퓨터 운영체제이다.
- MS DOS에서 멀티태스킹과 GUI 환경 등을 제공하기 위해 개발된 운영체제로 현재 PC로 가장 많이 사용되고 있다.

#### 멀티태스킹
- 다수의 작업/프로세스/태스크가 중앙 처리장치(CPU)와 같은 공용자원을 나누어 사용하는 것을 말한다.
- 멀티태스킹은 스케줄링(Scheduling)이라는 방식을 사용하여 컴퓨터 사용자에게 병렬 연산이 이루어지는 것과 같은 환경을 제공한다..

#### Windows와 Window
- Windows는 운영체제를 뜻한다.
- Window는 화면에 나타나는 창을 뜻한다.

#### GDI (Graphic Device Interface)
- Windows의 하위 시스템 중 하나의 DLL 모듈로, 모든 출력장치를 제어하는 역할을 한다.
- 윈도우 프로그램에서 요청하는 모든 출력은 GDI를 통해 실제 출력장치인 화면이나 프린터에 출력된다.
- 윈도우 프로그램에서 GDI 함수를 사용하여 프린터, 화면 등에 출력하면 GDI는 설치된 해당 드라이버를 연결하여 출력한다.
- GDI로 인해 프로그래머는 장치에 일일이 신경 쓸 필요가 없으므로, 이를 장치 독립적(Device Indepence)라고 표현한다.

#### DC (Device Context)
- 출력에 필요한 모든 정보를 갖고 있는 데이터 구조체로, GDI가 생성하고 관리한다.
- 출력에 필요한 정보란 문자열의 모양을 지정하는 폰트, 선의 색상과 굵기, 채움 무늬와 색상, 그리기 모드 등을 뜻한다.
- 윈도우 프로그램에서 무언가를 출력하려면 반드시 DC가 필요하다.

![[visual_cpp_device_dependence_diagram.png]]

### API
- API (Application Programming Interface)는 운영체제가 응용 프로그램을 위해 제공하는 함수의 집합이다.
- 운영체제는 하드웨어와 응용 프로그램 사이에 위치하며 응용 프로그램을 대신하여 하드웨어를 관리하고 메모리를 관리하는 시스템 소프트웨어를 말한다.
- 특정 운영체제에서 실행되는 응용 프로그램은 운영체제의 종속적일 수밖에 없으며, 운영체제가 규정한 대로 하드웨어를 액세스해야 한다.
- Windows와 같은 멀티태스킹 운영체제의 경우, 응용 프로그램 간 상호작용을 할 때 운영체제의 규정을 따라야 한다.
  ![[visual_cpp_hardware_api_program_relationship.png]]
- **운영체제는 가장 기본적인 동작을 할 수 있는 함수의 집합을 응용 프로그램에 제공하여, 이를 WinAPI라고 한다.**
- API는 운영체제의 중요한 한 부분이며 운영체제 그 자체라고도 할 수 있다.

### SW - OS - HW 관계
운영체제와 응용 프로그램, MFC, API, GDI의 관계

![[visual_cpp_os_sw_hw_relationship.png]]

- 커널은 메모리 관리와 프로그램 실행을 담당한다.
- 사용자(User)는 사용자 인터페이스와 윈도우를 관리한다.
- GDI는 모든 출력장치를 제어한다.

### WinAPI에서 사용하는 자료형
밑에 표에 윈도우 프로그래밍에서 사용되는 기본 자료형이 명시되어 있다. `windows.h`라는 헤더 파일에서 `typedef`로 선언되어 있으며, 거의 모든 프로그램에서 표준 자료형처럼 사용되고 있다.

| DataType     | Description               |
| ------------ | ------------------------- |
| BOOL/BOOLEAN | TRUE or FALSE             |
| BYTE         | Byte(8 bit)               |
| CALLBACK     | Defines CALLBACK function |
| COLORREF     | RGB color value(32 bit)   |
| DWORD        | 32 bit unsigned integer   |
| HANDLE       | Defines handle            |
| HBITMAP      | Bitmap Handle             |
| HBRUSH       | Brush Handle              |
| HCURSOR      | Cursor Handle             |
| HDC          | DC Handle                 |
| HFONT        | Font Handle               |
| HICON        | Icon Handle               |
| HMENU        | Menu Handle               |
| HWND         | Window Handle             |
| LONGLONG     | 64 bit signed integer     |
| LPARAM       | 32 bit message parameter  |
| LPCSTR       |                           |
| LPCTSTR      |                           |
| LPCWSTR      |                           |
| LPSTR        |                           |
| LPTSTR       |                           |
| LPVOID       | void pointer              |
| PCSTR        | Previous char pointer     |
| PCTSTR       | Previous char pointer     |
| TBYTE        | 2 Byte                    |
| TCHAR        | UNICODE char              |
| UINT         | Unsigned int              |
| WCHAR        | UNICODE char              |
| WORD         | 16 bit unsigned integer   |
| WPARAM       | 32 bit message parameter  |
| RECT         | Rectangle object          |
| POINTS       | Point object              |
| LRESULT      |                           |

### 핸들
- 핸들(Handle)이란 어떤 대상에 붙여진 번호로, 문법적으로 32 비트의 정수 값이다.
- DOS 프로그램에서는 거의 유일하게 파일 핸들만이 사용되었다.
- 윈도우 프로그램에서는 여러 종류의 핸들이 사용된다.
- 모든 윈도우에는 윈도우 핸들(`hWnd`)이 붙여지며, 논리적 펜과 브러시에도 핸들을 붙여 관리한다.
- 메모리를 할당할 때도 할당된 메모리 번지를 취급하기보다, 메모리 핸들을 사용한다.
- 핸들을 자주 사용하는 이유는 대상을 구분하기 위해서이며, 핸들값으로 정수를 사용함으로 문자열을 사용하는 것보다 훨씬 속도가 빠르다.

#### 핸들의 특징
1. 핸들은 정수 값이며 대부분의 경우 32 비트로 구현된다. 핸들을 사용하는 목적은 오로지 구분을 위한 것이다.
2. 핸들은 운영체제가 발급해 주며, 사용자는 발급된 핸들을 사용하기만 하면 된다. 예를 들어, 윈도우를 만들면 운영체제는 만들어진 윈도우에 핸들을 붙여준다. 사용자는 이 핸들을 잘 보관해 두었다가, 해당 윈도우를 다시 참조할 때 핸들을 사용하면 된다. 사용자가 직접 핸들을 만들지는 않는다.
3. 같은 종류의 핸들끼리는 중복된 값을 갖지 않는다. 다른 종류의 핸들끼리는 중복된 값을 가질 수도 있다.
4. 핸들의 실제 값이 무엇인지 몰라도 상관없다. 핸들은 단순한 이름표의 역할을 할 뿐으로, 핸들형 변수를 만들어 핸들을 대입받아 쓰고 난 후에는 버려도 된다.

#### h 접두어
- 윈도우에서 핸들은 예외 없이 접두어 `h`로 시작되며, 핸들값을 저장하기 위해 별도의 자료형까지 정의해 두고 있다.
- `HWND`, `HPEN`, `HBRUSH`, `HDC` 등이 핸들을 담기 위한 자료형이며, 모두 `UNSIGNED INTEGER` 이다.

### WinAPI 프로그램 흐름
- 모든 WinAPI 프로그램은 가장 먼저 `windows.h`라는 헤더 파일을 포함(Include)한다.
- `windows.h` 헤더 파일은 내부적으로 WinAPI에서 사용하는 상수, 매크로, 구조체와 함수원형 등에 대한 선언(Declaration)을 담고 있는 여러 가지 부문별 헤더를 포함한다.
- `windows.h` 헤더 파일은 `WinMain` 함수와 윈도우 프로시저 함수로 구성되어 있다.

#### WinMain 함수
```C++
int APIENTRY WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, 
                     LPSTR lpszCmdParam, int nCmdShow)
```

- `WinMain` 함수는 윈도우 메인 함수라고 하며 콘솔 응용 프로그램에서 등장하는 `main()` 함수에 해당한다.
- `main()` 함수는 프로그램의 진입점(Entry Point)이라고 하는데, 프로그램이 실행될 때 처음 시작하는 부분이라는 의미이며, 이 함수를 갖고 있어야만 독립적으로 실행 가능한 프로그램이 된다.
- `WinMain` 함수의 반환 타입은 `int`형이다.

##### WinMain 호출 방식
- `APIENTRY` 매크로는 함수호출규약(Function Calling Convention)으로, `_stdcall`형 호출규약을 사용한다는 뜻이다.
- `_stdcall`은 `WinAPI` 함수들의 호출방식이며, 밑에와 같은 방식들을 매크로로 기술한 것이다.
    - 매개변수의 전달 순서는 왼쪽에서 오른쪽으로,
    - 값에 의한 전달을 사용하고,
    - 함수호출을 위해 사용한 스택은 호출된 함수 자신이 리턴되면서 비우고,
    - 호출된 함수가 스택의 유지보수를 담당한다.

##### WinMain 주요 기능
- `WinMain` 함수는 먼저 메인 윈도우를 만들고, 그 다음에는 메시지를 처리하기 위하여 메시지 루프를 운영하는데 다음과 같은 다섯 가지 주요 기능으로 되어 있다.
    1. 윈도우 클래스 정의 : `WNDCLASS` 윈도우 클래스 구조체를 사용하여 윈도우를 생성하기 위한 기본 속성을 정의한다.
    2. 윈도우 클래스 등록 : `RegisterClass()` 함수로 윈도우 클래스를 등록한다.
    3. 윈도우 객체 생성 : `CreateWindow()` 함수로 윈도우 객체를 생성한다.
    4. 화면에 윈도우 보이기 : `ShowWindow()` 함수로 미리 생성된 윈도우 객체를 화면에 보이게 한다.
    5. 메시지 루프 : 메시지 큐에서 메시지를 가져와서 처리하는 반복문
- 윈도우 프로그램은 이벤트 중심의 프로그램이며 모든 이벤트는 밑에와 같이 메시지로 표현된다.
  ![[visual_cpp_event_to_message.png]]

##### 메시지 처리 과정
- 메인 윈도우 생성에 성공하면 그 다음부터는 계속 메시지 큐에서 메시지를 가져와서 처리하는 일을 반복하는데 다음과 같은 While 반복문으로 처리한다.
  ```C++
  while(GetMessage(&Message,0,0,0)) // 메시지를 가져온다.
  {
    TranslateMessage(&Message); // 키보드 메시지인지 검사
    DispatchMessage(&Message); // 메시지 전달
    ..
  }
  ```
- `GetMessage` 함수는 시스템 메세지 큐에서 메시지를 가져오는 역할을 하며, 무한 루프를 돌게 된다.
- `WM_QUIT` 메시지가 오면 종료한다.
- 윈도우 우측 상단의 종료 버튼을 누르면 `WM_DESTORY` 메시지가 발생되고, 이것을 처리하는 함수가 `WM_QUIT` 메시지를 발생시킨다.
- ![[visual_cpp_message_processing_flow.png]]
- `TranslateMessage` 함수는 키보드 메세지를 문자 입력 메시지로 변환해준다.
- `DispatchMessage` 함수는 메시지를 해당 윈도우의 윈도우 프로시저 함수로 전달하는 역할을 한다.
- 모든 메시지는 운영체제가 관리하는 시스템 메시지 큐에 보관된다.
- 운영체제는 메시지가 발생한 응용 프로그램 큐에 메시지로 전달하고, 응용 프로그램은 자신의 윈도우 프로시저에서 그 메시지를 처리한다.

#### 윈도우 프로시저
- `WndProc` 함수는 API 프로그램에서 메시지를 처리하는 또 하나의 중요한 함수다.
  ```C++
  LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM);
  ```
- `WndProc`은 윈도우 프로시저라고 불리며, 프로그램이 실행되는 동안 발생하는 모든 메시지를 처리하는 역할을 한다.
- 함수명 바로 앞에 `CALLBACK`이라는 매크로를 사용하여 `CALLBACK` 함수로 정의한다. `CALLBACK` 함수는 사용자가 정의하지만 호출은 운영체제가 한다.
  ![[visual_cpp_wndproc_and_callback.png]]
- 일반적으로 API 함수는 운영체제가 제공하며, 프로그램에서는 이 함수를 호출해서 사용한다.
    - 예를 들어, 운영체제의 `TextOut` 함수는 프로그램이 호출하면, 이를 수행하여 문자열을 출력한다. 
- 반면에, `CALLBACK` 함수는 응용 프로그램이 제공하지만, 프로그램이 아닌 운영체제가 필요할 때 호출한다.

## 프로젝트
- Win32 API 프로그래밍을 직접 해본다.
    - 메인 윈도우를 생성하고 메인 윈도우에 문자열을 출력하는 프로젝트를 작성한다.
    - 메인 윈도우에 차일드 윈도우를 추가하고 차일드 윈도우에 문자열을 출력한다.

### 프로젝트 생성
- 비주얼 스튜디오를 열고 `Create a new project`를 클릭한다.
- 프로젝트 생성 창에서 `Windows Desktop Wizard`를 클릭하고 `Next`를 누른다.
- 프로젝트 이름, 위치 등을 입력하고 `Create`을 누른다. 새로 뜨는 창에 Application Type에 `Desktop Application(.exe)`를 선택하고, 추가 옵션에 `Empty Project`를 선택한 후 `OK`를 누른다.
  ![[visual_studio_new_project.png]]
  ![[visual_studio_new_project_desktop_app.png]]

### 소스 파일 추가
- 프로그램을 작성하기 위해 프로젝트에 새로 소스 파일을 추가해야 한다.
- `Solution Explorer` 창 안에 `Source Files`를 우클릭하고 `Add` -> `New Item`을 클릭한다.
  ![[visual_studio_new_file.png]]
- 파일 추가 창에서 `C++ File (.cpp)`을 선택하고 이름을 `helloAPI.cpp`로 입력한 다음 `Add`를 클릭하면 새로운 C++ 파일이 생성되고 창에 열린다.
  ![[visual_studio_new_file_cpp.png]]
- 아직 코드는 작성하지 않는다. 소스 코드는 1.3절에 있다.

### UNICODE 문자집합 설정
- 비주얼 스튜디오에 문자집합(Character Set)의 기본설정(Default)은 UNICODE이다.
- 기존에 생성하였던 프로젝트의 문자집합 설정을 확인하기 위해 `Solution Explorer` 창 -> 프로젝트 우클릭 -> `Properties` 선택 -> `Advanced` 클릭 -> `Advanced Properties` 아래 `Character Set`의 값을 확인해보면 된다. `Use Unicode Character Set`라고 설정되어 있는 경우, UNICODE를 사용하고 있다는 것이다.
  ![[visual_studio_project_character_set.png]]
- 프로젝트 설정은 UNICODE로 되어있지만, 실제로 UNICODE를 사용하는 방법은 간단하지 않다.
- C++을 만들 때 기본적인 명령어 대부분은 ASCII 코드를 기반으로 되어있으며, 이를 수정해서 UNICODE도 사용할 수 있도록 변경해야 한다. 특히 문자열이 들어가는 곳이라면 코드를 대부분 변경해 주어야 한다.
- 윈도우 프로그래밍에서는  `char`가 직접적으로 쓰이지 않는다. `char`는 `TCHAR`로 사용하는데, `TCHAR`의 정의를 보면 다음과 같다.
  ```C++
  #ifdef UNICODE
    typedef wchar_t TCHAR;
  #else
    typedef char TCHAR;
  #endif
  ```
  만약 UNICODE를 사용한다면 `wchar_t`형의 `TCHAR`를 사용하고, UNICODE가 아니면 그냥 `char`를 사용한다는 뜻이다.
- `char`와 관련된 자료형은 밑과 같다.
    - `TCHAR` : `char`
    - `LPSTR` :`char*`
    - `LPCSTR` : `const char*`
    - `LPWSTR` : `wchar_t*`
    - `LPCWSTR` : `const wchar_t*`
    - `LPCTSTR` : `const wchar_t*` or `const char*`
- 약어는 다음과 같다.
    - `W` : Wide char (16 bit)
    - `T` : UNICODE or ASCII
    - `C` : constant
    - `LP` : Long Pointer
    - `STR` : string
- 문자열 함수는 밑과 같이 변경하여 UNICODE와 호환되게 할 수 있다.
    - `strlen` -> `lstrlen`
    - `strcpy` -> `lstrcpy`
    - `strcat` -> `lstrcat`
    - `strcmp` -> `lstrcmp`
    - `sprintf` -> `wsprintf`
- 비주얼 C++에서 UNICODE를 입력하려면 다음과 같은 매크로를 사용한다.
    - `TEXT("text here")`
    - `_T("text here")`
    - `L"text here"`

## 소스 코드
메인 윈도우를 생성하는 소스 코드는 다음과 같다.

```C++
#include <windows.h>

LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM);
HINSTANCE g_hInst;
LPCTSTR lpszClass = L"HelloAPI";

int APIENTRY WinMain(HINSTANCE hInstance,
	HINSTANCE hPrevInstance,
	LPSTR lpszCmdParam,
	int nCmdShow)
{
	HWND hWnd;
	MSG Message;
	WNDCLASS WndClass;
	g_hInst = hInstance;

	WndClass.cbClsExtra = 0;
	WndClass.cbWndExtra = 0;
	WndClass.hbrBackground = (HBRUSH)GetStockObject(WHITE_BRUSH);
	WndClass.hCursor = LoadCursor(NULL, IDC_WAIT);
	WndClass.hIcon = LoadIcon(NULL, IDI_APPLICATION);
	WndClass.hInstance = hInstance;
	WndClass.lpfnWndProc = (WNDPROC)WndProc;
	WndClass.lpszClassName = lpszClass;
	WndClass.lpszMenuName = NULL;
	WndClass.style = CS_HREDRAW | CS_VREDRAW;
	RegisterClass(&WndClass);

	hWnd = CreateWindow(lpszClass,			//윈도우클래스 이름
		L"윈도우 프로그래밍",			    //윈도우타이틀
		WS_OVERLAPPEDWINDOW | WS_VISIBLE,   //윈도우스타일
		200, 200,							//윈도우가 보일때 X Y좌표
		600, 600,							//윈도우의 폭과 높이				
		(HWND)NULL,							//부모윈도우 핸들
		(HMENU)NULL,						//윈도우가 가지는 메뉴핸들
		hInstance,							//인스턴스핸들
		NULL);								//여분의 데이터

	ShowWindow(hWnd, nCmdShow);

	while (GetMessage(&Message, 0, 0, 0)) {
		TranslateMessage(&Message);
		DispatchMessage(&Message);
	}
	return Message.wParam;
}

LRESULT CALLBACK WndProc(HWND hWnd, UINT iMessage,
	WPARAM wParam, LPARAM lParam)
{
	LPCTSTR text = L"메인윈도우 생성";
	switch (iMessage) {
	case WM_PAINT:
	{
		PAINTSTRUCT ps;
		HDC hdc = BeginPaint(hWnd, &ps);
		TextOut(hdc, 100, 100, text, lstrlen(text));
		EndPaint(hWnd, &ps);
		return 0;
	}
	case WM_DESTROY:
		PostQuitMessage(0);
		return 0;
	}
	return(DefWindowProc(hWnd, iMessage, wParam, lParam));
}
```

#### 헤더 파일
```C++
#include <windows.h>
```

- 윈도우 프로그램의 첫 줄은 대부분 이렇게 시작된다. `windows.h` 헤더 파일은 기본적인 자료 타입, API 함수 원형과 상수 등을 정의하며, 그 외 필요한 헤더 파일을 포함하고 있다.

#### WinMain 함수
```C++
int APIENTRY WinMain(HINSTANCE hInstance,
	HINSTANCE hPrevInstance,
	LPSTR lpszCmdParam,
	int nCmdShow)
```

- 윈도우 프로그램의 시작점(Entry Point)은 `main`이 아닌 `WinMain`이다. `APIENTRY` 지정자는 `_stdcall`형 호출규약을 사용한다는 뜻이다. `WinMain` 함수의 4개 매개변수의 의미는 밑에와 같다.
    - `hinstance` : 프로그램의 객체 핸들이다.
    - `hPrevInstance` : 바로 앞에 실행된 현재 프로그램의 객체 핸들이다. 없을 경우에는 `NULL`이 되며, WIN32 에서는 항상 `NULL`이다. 호환성을 위해서만 존재하는 매개변수이다.
    - `lpCmdLine` : 명령행으로 입력된 프로그램 매개변수이다. DOS의 `argv` 매개변수에 해당한다.
    - `nCmdShow` : 프로그램이 실행될 형태며 최소화, 보통 모양 등이 전달된다.

#### WndProc 함수
- `LRESULT CALLBACK WndProc(..)` : 