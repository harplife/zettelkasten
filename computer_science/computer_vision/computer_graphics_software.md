---
aliases: [Computer Graphics Software, Display System Software, 컴퓨터 그래픽스 소프트웨어, 디스플레이 시스템 소프트웨어]
tags: [computer_science, computer_vision, computer_graphics, KNOU, study, display, software]
status: ongoing
created: 2022-03-27
edited: 2022-03-27
---

# 컴퓨터 그래픽스 소프트웨어
컴퓨터 그래픽스 시스템에서 영상 데이터가 어떻게 다루어 지는지 알아본다.

## 그래픽스 이미지
여기서 다룰 내용은 [[computer_graphics_hardware#래스터 스캔]] 기반 시스템의 그래픽스 이다.

그래픽스는 래스터(Raster)와 벡터(Vector)로 2가지로 나뉜다.

### 래스터 그래픽스
[래스터 그래픽스 (Raster Graphics)](https://en.wikipedia.org/wiki/Raster_graphics)는 이미지를 사각형 그리드 안의 여러 [[computer_graphics#픽셀]]로 처리하는 방식을 뜻한다. 다른 말로는, 이미지를 픽셀의 행렬로 표현하는 방식이라고 할 수 있다.

참고 : 래스터(Raster)는 "갈퀴"라는 뜻의 라틴어 Rastrum에서 유래되었다.

래스터 그래픽스 방식으로 처리된 이미지를 래스터 그래픽스 이미지라 부르지만, 편의상 "래스터 이미지"라고 부른다.

래스터 이미지는 비트맵 이미지 (Bitmap Image)라고 불리기도 한다. [비트맵 (Bitmap)](https://en.wikipedia.org/wiki/Bitmap)은 정보를 비트 (Bit)로 매핑한다는 의미이며, 이미지를 저장하는 메모리 저장 방식이다.

일반 래스터 이미지에 하나의 서브픽셀은 8-bit 데이터로 저장되며, 0~255 (256개) 사이의 숫자를 표현할 수 있다. 따라서, 픽셀은 3개의 서브픽셀 (RGB)로 구성되니 하나의 픽셀이 24-bit 데이터로 저장된다 (3 채널 RGB 이미지 경우).

참고 1 : 각 픽셀에 24-bit이 할당되는 것을 영어로 24-bit per pixel 이라고 한다.

참고 2 : 100 x 100 (픽셀) 크기의 24-bit 래스터 이미지는 대략 30 KB 량의 데이터로 볼 수 있다.

RGB 이미지에 [투명 (Transparency)](https://en.wikipedia.org/wiki/Transparency_(graphic)) 정보가 추가된 경우, 8-bit의 알파 채널 (Alpha Channel)로 저장되며, 이러한 이미지를 [RGBA](https://en.wikipedia.org/wiki/RGBA_color_model) 이미지라 부른다. 8-bit가 추가되었기 때문에 하나의 픽셀이 32-bit 데이터로 저장된다.

### 벡터 그래픽스


### 이미지 파일 포맷
[파일 포맷](https://en.wikipedia.org/wiki/File_format)은 정보를 비트로 표현하는 구성요소 및 구조의 표준을 뜻한다.

참고 : 파일 포맷은 필수가 아니다. [파일명 확장자](https://en.wikipedia.org/wiki/Filename_extension)가 없는 경우, 파일은 단순한 [문자열 데이터](https://en.wikipedia.org/wiki/Plain_text)로 처리된다.

파일 포맷은 일반적으로 [Header](https://en.wikipedia.org/wiki/Header_(computing)), [Metadata](https://en.wikipedia.org/wiki/Metadata), [Payload](https://en.wikipedia.org/wiki/Payload_(computing))로 구성이 된다.

간단히 설명하자면,
- Header : 파일 포맷/버전을 명시한다.
- Metadata : 파일 컨텐츠에 대한 정보를 명시한다. 예: 생성일, 생성자, 이미지 크기, 등
- Payload/Body : 파일 컨텐츠, 즉, 파일의 주된 내용이다.

파일 포맷에 관련하여 좀 더 자세한 사항은 밑에 자료들을 참고하는게 좋을 듯 하다.
- [Endianness](https://en.wikipedia.org/wiki/Endianness)
- [Chunk](https://en.wikipedia.org/wiki/Chunk_(information))
- [Magic Number](https://en.wikipedia.org/wiki/Magic_number_(programming))
- [Container Format](https://en.wikipedia.org/wiki/Container_format_(computing))
- [Interchange File Format](https://en.wikipedia.org/wiki/Interchange_File_Format)

[이미지 파일 포맷](https://en.wikipedia.org/wiki/Image_file_format)은 이미지(픽셀 행렬)와 이미지에 대한 정보(메타데이터)를 데이터(비트)로 표현하는 구성요소 및 구조의 표준을 뜻한다.

#### 래스터 이미지 파일 포맷
[래스터 이미지 파일 포맷](https://en.wikipedia.org/wiki/Image_file_format#Raster_formats)은 말 그대로 래스터 이미지를 다루는 파일 포맷을 뜻 한다. 이미지 파일 포맷에 따라 이미지 처리, [이미지 압축](https://en.wikipedia.org/wiki/Image_compression), 픽셀 저장 방식 등에 차이가 있다.

참고 : [래스터 이미지에 대한 Adobe의 설명](https://www.adobe.com/creativecloud/file-types/image/raster.html)

##### Raw Image File
[Raw Image File](https://en.wikipedia.org/wiki/Raw_image_format)은 디지털 카메라에서 찍히고 전혀 가공되지 않은 이미지 스캔 데이터를 뜻한다.

디지털 카메라의 작동 방식은 아주 복잡하니, 여기서 자세히 다루진 않겠다. 다만, 현실 세계의 영상을 RGB 색 공간으로 표현하기 위해 복잡한 이미지 스캔 방식과 [스캔된 이미지에 대한 여러 처리 방식](https://en.wikipedia.org/wiki/Digital_camera#Filter_mosaics,_interpolation,_and_aliasing)이 있다는 것을 인지해야 한다.

Raw Image File은 카메라 브랜드마다 다른 파일 포맷으로 처리된다.
- IIQ (Phase One)
- 3FR (Hasselblad)
- DCR, K25, KDC (Kodak)
- CRW, CR2, CR3 (Canon)
- .. 등등

참고 : [Raw Image File에 대한 Adobe의 설명](https://www.adobe.com/creativecloud/file-types/image/raw.html)

##### BMP
[BMP (.bmp) 파일 포맷](https://en.wikipedia.org/wiki/BMP_file_format)은 마이크로소프트에서 개발한 래스터 이미지 파일 포맷이다. GIF와 함께 가장 오래된 이미지 파일 포맷이기도 하다 (1980년도 상용화).

BMP는 bitmap의 약자이되, BMP는 파일 포맷이고 비트맵 이미지는 래스터 이미지를 뜻하니 서로 다르며 혼용되지 않아야 한다. 그리고 BMP는 범프 (Bump)라고 읽는다.

BMP는 uncompressed (압축되지 않음)/lossless (무손실) 이미지 파일 포맷이다. 수정 후 저장할 때 마다 퀄리티가 저하되지 않는다.

BMP는 인터넷용 또는 이미지 편집용으로 사용하기 적절하지 않기 때문에 거의 잊혀진 이미지 파일 포맷이다.

참고 : [[bmp_file_format_structure.svg|BMP 구조]]

##### GIF
[GIF (Graphic Interchange Format)](https://en.wikipedia.org/wiki/GIF)은 1987년에 출시된 무손실 압축 (Lossless Compression) 이미지 파일 포맷이다.

GIF에 사용된 무손실 압축 기술은 [LZW (Lempel-Ziv-Welch)](https://en.wikipedia.org/wiki/Lempel%E2%80%93Ziv%E2%80%93Welch)이다. 반복되는 단어들을 작은 크기의 코드로 변환하는 원리로 작동한다 (단어-코드 사전이 구축된다). #todo 사실 훨씬 복잡한 것 같은데, 나중에 자세히 다루겠다.

LZW 알고리즘 예시 : UTF-8 (8 bit per character) 인코딩 텍스트 파일에 "엘레베이터"라는 단어를 코드 `10`으로 대체한다. 40 bit 크기의 문자열이 16 bit 크기의 문자열로 대체되며, 이 단어가 반복될 때 마다 24 bit를 아끼게 된다.

반복되는 단어의 길이가 길 수록 LZW의 효율성이 높아진다 - 반대로, 단어가 짧을수록 효율성이 떨어진다.

참고 : [Steve Wilhite](https://en.wikipedia.org/wiki/Steve_Wilhite)가 CompuServe에 있을때 GIF를 발명하였고, 이로서 2013년도에 Webby Award를 받았다. 안타깝게도 Steve는 2022년 3월 14일에 COVID-19로 인해 돌아가셨다 (74세).

정확히 "압축"이라 표현되진 않지만, 이미지 데이터 크기를 줄이는 방법으로서 [색 양자화(Color Quantization)](https://en.wikipedia.org/wiki/Color_quantization)가 있다.

[Palette](https://en.wikipedia.org/wiki/Palette_(computing))가 있다. 

![[color_depth_comparisons.PNG]]

https://en.wikipedia.org/wiki/Colour_banding

https://en.wikipedia.org/wiki/Dither

https://dev.to/thejaredwilcurt/everything-you-need-to-know-about-making-animated-gifs-j2d

https://www.kci.go.kr/kciportal/ci/sereArticleSearch/ciSereArtiView.kci?sereArticleSearchBean.artiId=ART001219439


##### JPEG

##### PNG

##### WEBP
https://developers.google.com/speed/webp/docs/riff_container

#### 벡터 이미지 파일 포맷

참고 : [벡터 이미지에 대한 Adobe의 설명](https://www.adobe.com/creativecloud/file-types/image/vector.html)

- [SVG (.svg)](https://en.wikipedia.org/wiki/Scalable_Vector_Graphics)

## 그래픽스 소프트웨어
그래픽스 소프트웨어는 그래픽스 작업을 할 수 있도록 편리한 사용자 인터페이스 GUI를 제공하는 소프트웨어를 뜻한다.

그래픽스 소프트웨어의 예는 밑에와 같다.
- CAD : 건축, 기계, 전자회로 등 제품설계에 활용될 수 있는 소프트웨어
- Photoshop/Illustrator : 이미지 제작/편집 소프트웨어
- Maya : 3D 애니메이션 제작 소프트웨어

참고 : 방통대 교과서에는 "특수목적 패키지"라고 부르는데, 아무도 이런 식으로 부르지 않는다.

## 그래픽스 라이브러리
[그래픽스 라이브러리(Graphics Library, GL) ](https://en.wikipedia.org/wiki/Graphics_library) 또는 그래픽스 API는 프로그램이 하드웨어(CPU/GPU 등)에게 그림을 그리기 위한 명령을 보내는 소통을 보조해주는 라이브러리 이다.

그래픽스 라이브러리라는 뜻으로 이름에 "GL"이 붙는 경우가 있다 (예: OpenGL).

그래픽스 API는 직접 코딩을 하여 그래픽스 작업(또는 보조 소프트웨어 개발)을 할 수 있도록 그래픽스 함수를 제공한다. 그래픽스 API는 설계 및 렌더링 작업을 처리하기 위한 최적화된 함수를 제공하며, 이러한 함수들을 모아 그래픽스 소프트웨어를 개발할 수 있다.

제일 잘 알려지고 많이 사용되는 그래픽스 API :
1. [OpenGL](https://en.wikipedia.org/wiki/OpenGL)
2. [DirectX](https://en.wikipedia.org/wiki/DirectX)
3. [Vulkan](https://en.wikipedia.org/wiki/Vulkan)

### 그래픽스 API 종류
그래픽스 API는 저수준 그래픽스 API와 고수준 그래픽스 API로 구분된다.

#### 저수준 그래픽스 API
저수준 그래픽스 API (Low Level Graphics API)는 그림을 구성하는 점, 선, 다각형과 같은 그래픽스 기본 요소 및 이들에 대한 색상, 문양 등의 속성을 정의하고, 객체의 기하변환, 장면의 뷰잉 등 장면을 정의하여 이를 컴퓨터 화면에 표시하는 일련의 과정을 지시하는 함수들이 포함된다.

저수준 그래픽스 API를 이용하여 장면을 만들고자 할 때에는 장면 내에 물체를 구성하는 기본 요소들을 개별적으로 정의하고, 이들을 그리기 위한 세부적인 처리과정을 일일이 프로그램으로 작성해야 한다. 이러한 과정에서 아주 단순한 그림을 그리기 위해 방대한 프로그램을 작성해야 한다.

#### 고수준 그래픽스 API
고수준 그래픽스 API (High Level Graphics API)는 장면 묘사를 위주로 하는 기능을 제공한다. 이러한 기능들은 내부적으로 저수준 API를 이용하여 구현될 수 있다.

고수준 그래픽스 API는 그래픽스 작업을 보다 단순하고 효율적으로 구현할 수 있도록 다양한 모형(큐브, 다각형, 재질, 카메라, 광원 등)을 제공하고, 이를 새로운 모형으로 쉽게 변형할 수 있게 한다. 장면의 구성은 이러한 모형들로 구성된 객체들을 계층적으로 조직화하여 처리한다.

### 그래픽스 API 목록
https://en.wikipedia.org/wiki/List_of_3D_graphics_libraries

### 그래픽스 표준
[Graphical Kernel System (GKS)](https://en.wikipedia.org/wiki/Graphical_Kernel_System)은 저수준 컴퓨터 그래픽스를 위한 첫 ISO 표준으로 1977년에 소개되었다.

GKS는 차트 그리기와 같은 작업에 적당한 2차원 벡터 그래픽스를 위한 그리기 도구들을 제공한다. 함수는 다른 프로그램 언어, 그래픽스 하드웨어로 쉽게 이식할 수 있도록 설계되어 있다. 따라서, GKS 기반 응용 프로그램은 여러 플랫폼에 쉽게 이식될 수 있다.

GKS는 1980~1990년대 초기에 많이 사용되었다.

[PHIGS(Programmer's Hierarchical Interactive Graphics Standard)](https://en.wikipedia.org/wiki/PHIGS)는 3차원 그래픽스 표준으로 1988년에 소개되었다. GKS를 확장한 것으로 계층적 객체 모델링, 색상지정, 표면 묘사 및 그림 조작능력이 강화되었다.

PHIGS는 1990년도 후반까지 많이 사용되었다.

1980년도 초기에 [SGI(Silicon Graphics Inc.)](https://en.wikipedia.org/wiki/Silicon_Graphics)사에서 개발한 IRIS GL은 그래픽스 개발자 사이에 널리 사용되는 패키지가 되어, 사실상의 그래픽스 표준이 되었다. 더불어, IRIS GL을 오픈소스 버전으로 변경하여 제공한 것이 [OpenGL](https://en.wikipedia.org/wiki/OpenGL)이다.

## OpenGL 프로그래밍
OpenGL은 [크로노스 그룹(Khronos Group)](https://en.wikipedia.org/wiki/Khronos_Group)에서 관리하는 오픈소스 그래픽스 라이브러리 이다. 여러 프로그래밍 언어와 플랫폼에 호환된다는 큰 장점을 가지고 있다.

OpenGL은 장면을 렌더링하기 위해 요구되는 정확한 단계를 프로그래머가 정확하게 규정하도록 요구한다. 장면에 대하여 서술만 하고, 구체적인 렌더링은 라이브러리가 관리하는 방식과는 대조적이다. 이러한 설계는 프로그래머에게 [그래픽스 파이프라인(Graphics Pipeline)](https://en.wikipedia.org/wiki/Graphics_pipeline)에 대한 충분한 지식을 요구하기도 하지만, 새로운 렌더링 알고리즘을 구현할 수 있는 자유도 함께 주어진다.

OpenGL은 가장 널리 사용되..었던 그래픽 라이브러리다. 2022년을 기준으로 현재 4년간 업데이트가 없다. OpenGL은 Ray Tracing이 안 된다는 큰 단점이 있으며, 이 단점을 보완하기 위해 [Vulkan](https://en.wikipedia.org/wiki/Vulkan)이 출시되었다.

참고 : Vulkan은 AMD에서 개발하고 크로노스 그룹에 넘겨줬다.

OpenGL을 배울 필요가 없을까? 딱히 그런것은 아니다 - OpenGL을 기반으로 만들어진 프로그램은 많고, 오랫동안 사용된 라이브러리이기 때문에 교육 자료 등 관련 자료가 많다. 그래픽스를 이해하기 위해 OpenGL을 배우는 것은 de facto standard 라고 볼 수 있다.

### 셰이더
초기 그래픽스 시스템은 사용자 제공 설정(user-provided configuration)으로 그래픽스 파이프라인을 제어하는 [고정 기능 파이프라인 (Fixed Function Pipeline)](https://www.khronos.org/opengl/wiki/Fixed_Function_Pipeline) 구조였다. 나중에는 사용자 제공 프로그램(user-provided program)으로 그래픽스 파이프라인을 제어하게 되었는데, 이 프로그램을 [셰이더(Shader)](https://en.wikipedia.org/wiki/Shader)라 부른다.

#todo 셰이더에 대한 자세한 내용 추가

셰이더를 작성하기 위한 [셰이딩 언어](https://en.wikipedia.org/wiki/Shading_language)가 여러 있는데, 이 중 OpenGL 전용 셰이딩 언어 [GLSL (OpenGL Shading Language)](https://en.wikipedia.org/wiki/OpenGL_Shading_Language)이 있다.

### 확장 기능 관리 라이브러리
OpenGL은 Cross Platform(다중 플랫폼 호환)이기 때문에 OpenGL 자체 코어(Core) 기능 외 각 그래픽스 하드웨어 공급업체 전용 기능(Vendor Specific Extension)들도 제공한다. 이러한 기능이 다수의 업체에 폭넓게 수용되면 EXT 확장 기능으로 인정되고, ARB(Architecture Review Board)에 승인 하에 ARB 확장 기능으로 인정된다. 이렇게 승인된 확장 기능 중 유용한 기능들은 다음 버전 OpenGL의 코어 기능으로 포함될 수 있다.

프로그래머가 어떤 확장 기능을 사용할 수 있는지 관리하는 것은 어렵기 때문에, 이러한 어려움을 덜어주는 라이브러리들이 있다.
1. [GLEW (OpenGL Extension Wrangler)](http://glew.sourceforge.net/)
2. [GLEE (OpenGL Easy Extension)](https://www.opengl.org/sdk/libs/GLee/)

방통대 교제에서는 GLEW2를 사용하는 예시를 제공한다.

### 윈도우 시스템 관리 라이브러리
OpenGL 코어 라이브러리는 하드웨어 및 운영체제, [윈도 시스템](https://en.wikipedia.org/wiki/Windowing_system) 등 플랫폼에 독립적으로 설계되어 있기 때문에 입력 및 출력 루틴과 같은 연산이 기본 라이브러리에 포함되어 있지 않다. 대신, 각 시스템별로 OpenGL을 위한 윈도 시스템 라이브러리가 사용된다.

예를 들어, X 윈도 시스템의 경우 GLX (OpenGL Extension to X Window System)가 사용되며, Apple 시스템의 경우 AGL (AppleGL), Microsoft 윈도우 시스템에서는 WGL (Windows-to-OpenGL) 인터페이스가 제공된다.

윈도 시스템마다 라이브러리들이 다르기 떄문에 장치에 독립적인 인터페이스의 필요성이 제기되어, [GLUT (OpenGL Utility Toolkit)](https://en.wikipedia.org/wiki/OpenGL_Utility_Toolkit)이 개발되었다.

GLUT은 OpenGL 프로그램을 위해 운영체제와 시스템 수준의 I/O를 다루고, 윈도 정의/제어, 키보드/마우스 입력의 모니터링과 같은 함수를 제공한다. 더불어, 육면체, 구, Utah teapot과 같은 기하학 기본 요소를 그리기 위한 루틴도 제공하며, 제한적이기는 하지만 팝업 메뉴 생성 기능도 제공한다.

GLUT의 두가지 목적은,
1. 운영체제 간 이식이 가능한 코드의 생성을 허용
2. OpenGL을 쉽게 배우게 보조

하지만 현재 GLUT은 유지보수가 중단된 상태이며, [freeGLUT](https://en.wikipedia.org/wiki/FreeGLUT)으로 대체되었다.

방통대 교제에서는 freeGLUT을 사용하는 예시를 제공한다.

### OpenGL 함수 형태
OpenGL의 명령어는 이름만 보면 대략 어떠한 작업을 수행하고, 몇 개의 인수를 가지며, 어떠한 형태의 인수를 갖는가를 알 수 있다.

OpenGL 명렁어 구조는 밑에와 같다.
`return_type <lib_prefix> FunctionName <arg_count><arg_type>{v}(<arguments>)`

간단히 설명하자면,
1. `return_type` : 함수를 수행한 후 되돌려 받는 데이터형
2. `<lib_prefix>` : 함수 이름 앞에 붙이는 접두어로, 함수가 선언된 라이브러리를 표시한다.
3. `FunctionName` : 명령어의 이름
4. `<arg_count>` : 함수가 갖는 인수의 수
5. `<arg_type>` : 인수의 데이터형
6. `{v}` : 인수가 벡터인 경우 첨가

OpenGL 코어 라이브러리의 함수는 접두사 `gl`로 시작하며, 명령어를 구성하는 단어의 첫 번쨰 문자는 대문자를 사용한다 (camelCase).

예시 : `void glClear();`

OpenGL 상수(CONST)의 정의는 접두사 `GL_`로 시작하고 모두 대문자로 표시하며, 여러 개의 단어로 구성될 떄 각 단어를 구별하기 위하여 밑줄을 사용한다.

예시 : `glClear(GL_COLOR_BUFFER_BIT);`

명령어 끝에 몇 가지 접미사(Suffix)가 추가되기도 한다.

예시 : `void glUniform2f();`

접미사 `2`는 2개의 인수를 갖는다는 의미를 가지며, `f`는 그 인수가 GLfloat형이라는 것을 의미한다.

#### OpenGL 데이터 정의
