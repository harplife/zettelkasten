---
aliases: [Computer Graphics Software, Display System Software, 컴퓨터 그래픽스 소프트웨어, 디스플레이 시스템 소프트웨어]
tags: [computer_science, computer_vision, computer_graphics, KNOU, study, display, software]
status: ongoing
created: 2022-05-30
edited: 2022-06-03
---

# 컴퓨터 그래픽스 소프트웨어
컴퓨터 그래픽스 시스템에서 소프트웨어를 통해 이미지에 대한 어떤 작업이 이루어지는지 알아본다.

여기서 다룰 내용은 [[computer_graphics_hardware#래스터 스캔|래스터 스캔 기반 그래픽스 시스템]]을 기준으로 한다.

## 2차원 그래픽스
2차원 그래픽스는 래스터(Raster)와 벡터(Vector)로 2가지로 나뉜다.

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
#todo 벡터 그래픽스 정의

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
#todo JPEG 이미지 포맷 정리

##### PNG
#todo PNG 이미지 포맷 정리

##### WEBP
#todo WEBP 이미지 포맷 정리

https://developers.google.com/speed/webp/docs/riff_container

#### 벡터 이미지 파일 포맷
#todo 벡터 이미지 포맷 정리

참고 : [벡터 이미지에 대한 Adobe의 설명](https://www.adobe.com/creativecloud/file-types/image/vector.html)

- [SVG (.svg)](https://en.wikipedia.org/wiki/Scalable_Vector_Graphics)

## 3차원 그래픽스
#todo 3차원 그래픽스는 3차원 장면/모델의 정보를 담는 데이터 또는 프로젝트 파일로 저장된다?

### 3차원 모델
[3차원 모델링(3D Modeling)](https://en.wikipedia.org/wiki/3D_modeling)은 특정 개체의 표면을 여러 다각형(Polygon)으로 3차원 좌표계에 표현하는 프로세스를 뜻하며, **3차원 모델(3D Model)** 은 그 프로세스의 결과물을 뜻한다.

![[utah_teapot_wireframe.png]]

[다각형(Polygon)](https://en.wikipedia.org/wiki/Polygonal_modeling)은 [정점(Vertex)](https://en.wikipedia.org/wiki/Vertex_(computer_graphics)), 변(Edge), 그리고 표면(Face)으로 이루어진 도형을 뜻한다.

참고 : 점, 선, 삼각형, 사각형 등 아주 간단한 기하학적(Geometrical) 도형을 [기본 도형(Primitive)](https://www.khronos.org/opengl/wiki/Primitive)이라고 한다. 정점, 변, 표면, 다각형 등이 기본 도형에 속한다.

![[polygon_mesh_overview.svg]]

![[polygon_mesh_vertex_edge_face_diagram.png]]

3차원 모델링에서 사용되는 다각형은 삼각형(Tri, Triangle), 사각형(Quad, Quadrilateral), 그리고 N-각형(N-Gon)이 있다.

참고 : 삼각형은 게임에, 사각형은 애니메이션에 많이 사용되는 것으로 알려진다. N-각형은 일러스트레이션이 아니면 거의 사용되지 않는 것으로 보인다 ([SO 참고](https://computergraphics.stackexchange.com/questions/5465/why-are-quads-used-in-filmmaking-and-triangle-in-gaming)).

![[graphics_polygons.png]]

다각형들이 모여 만들어진 망을 [다각형 메쉬(Polygon Mesh)](https://en.wikipedia.org/wiki/Polygon_mesh) 또는 [토폴로지(Topology)](https://en.wikipedia.org/wiki/Topology)라고 한다.

다각형 메쉬에 위치(Position) 정보가 추가되면 3차원 모델의 골격(Wireframe)이 만들어진다. 이를 [와이어프레임 모델(Wireframe Model)](https://en.wikipedia.org/wiki/Wire-frame_model)로 부르기도 한다.

![[wireframe_model_overview.png]]

와이어프레임 모델에 색/조명/그림자, 물질(Material) 속성, 또는 [텍스쳐 맵(Texture Map)](https://en.wikipedia.org/wiki/Texture_mapping)이 적용되면 3차원 모델이 완성된다.

![[texture_mapping_example_01.webp]]

3차원 모델들과 조명으로 채워진 3차원 공간을 3차원 장면(3D Scene)이라고 한다.

![[graphics_3d_scene.webp]]

## 그래픽스 소프트웨어
그래픽스 소프트웨어는 그래픽스 작업을 할 수 있도록 편리한 사용자 인터페이스 GUI를 제공하는 소프트웨어를 뜻한다.

그래픽스 소프트웨어의 예는 밑에와 같다.
- CAD : 건축, 기계, 전자회로 등 제품설계에 활용될 수 있는 소프트웨어
- Photoshop/Illustrator : 이미지 제작/편집 소프트웨어
- Maya : 3D 애니메이션 제작 소프트웨어

참고 : 방통대 교과서에는 "특수목적 패키지"라고 부르는데, 아무도 이런 식으로 부르지 않는다.

## 그래픽스 라이브러리
[그래픽스 라이브러리(Graphics Library, GL) ](https://en.wikipedia.org/wiki/Graphics_library) 또는 **그래픽스 API**는 프로그램이 하드웨어(CPU/GPU 등)에게 그림을 그리기 위한 명령을 보내는 소통을 보조해주는 라이브러리 이다.

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

## OpenGL 소개
OpenGL은 [크로노스 그룹(Khronos Group)](https://en.wikipedia.org/wiki/Khronos_Group)에서 관리하는 오픈소스 그래픽스 라이브러리\*다. 여러 프로그래밍 언어와 플랫폼에 호환된다는 큰 장점을 가지고 있다.

\* 유투브 채널 Cherno에 의하면 OpenGL은 그래픽 라이브러리가 아닌 규격(Specification)에 더 가깝다고 한다 - 그 이유는 1) 어떤 그룹이 따로 라이브러리/API를 개발하는게 아니라, OpenGL 규격에 따라 GPU 제작업체에서 GPU에 명령을 내리는 기능을 제공하는 것이며, 2) OpenGL 라이브러리를 따로 다운로드 할 필요가 없기 때문이다.

OpenGL은 장면을 렌더링하기 위해 요구되는 정확한 단계를 프로그래머가 정확하게 규정하도록 요구한다. 장면에 대하여 서술만 하고, 구체적인 렌더링은 라이브러리가 관리하는 방식과는 대조적이다. 이러한 설계는 프로그래머에게 [그래픽스 파이프라인(Graphics Pipeline)](https://en.wikipedia.org/wiki/Graphics_pipeline)에 대한 충분한 지식을 요구하기도 하지만, 새로운 렌더링 알고리즘을 구현할 수 있는 자유도 함께 주어진다.

OpenGL은 가장 널리 사용되..었던 그래픽 라이브러리다. 2022년을 기준으로 현재 4년간 업데이트가 없다. OpenGL은 Ray Tracing이 안 된다는 큰 단점이 있으며, 이 단점을 보완하기 위해 [Vulkan](https://en.wikipedia.org/wiki/Vulkan)이 출시되었다.

참고 : Vulkan은 AMD에서 개발하고 크로노스 그룹에 넘겨줬다.

OpenGL을 배울 필요가 없을까? 딱히 그런것은 아니다 - OpenGL을 기반으로 만들어진 프로그램은 많고, 오랫동안 사용된 라이브러리이기 때문에 교육 자료 등 관련 자료가 많다. 그래픽스를 이해하기 위해 OpenGL을 배우는 것은 de facto standard 라고 볼 수 있다.

### 확장 기능 관리 라이브러리
OpenGL은 Cross Platform(다중 플랫폼 호환)이기 때문에 OpenGL 자체 코어(Core) 기능 외 각 그래픽스 하드웨어 공급업체 전용 기능(Vendor Specific Extension)들도 제공한다. 이러한 기능이 다수의 업체에 폭넓게 수용되면 EXT 확장 기능으로 인정되고, ARB(Architecture Review Board)에 승인 하에 ARB 확장 기능으로 인정된다. 이렇게 승인된 확장 기능 중 유용한 기능들은 다음 버전 OpenGL의 코어 기능으로 포함될 수 있다.

프로그래머가 어떤 확장 기능을 사용할 수 있는지 관리하는 것은 어렵기 때문에, 이러한 어려움을 덜어주는 라이브러리들이 있다.
1. [GLEW (OpenGL Extension Wrangler)](http://glew.sourceforge.net/)
2. [GLEE (OpenGL Easy Extension)](https://www.opengl.org/sdk/libs/GLee/)

방통대 교제에서는 GLEW2를 사용하는 예시를 제공한다.

### 윈도 시스템 관리 라이브러리
주의 : 여기서 말하는 윈도(Window)는 Windows 운영체제를 말하는 것이 아니며, 화면에 그려지는 창(Window)를 말하는 것이다. #todo 윈도 시스템 관련해서 Visual C++ 자료 정리.

OpenGL 코어 라이브러리는 하드웨어 및 운영체제, [윈도 시스템](https://en.wikipedia.org/wiki/Windowing_system) 등 플랫폼에 독립적으로 설계되어 있기 때문에 입력 및 출력 루틴과 같은 연산이 기본 라이브러리에 포함되어 있지 않다. 대신, 각 시스템별로 OpenGL을 위한 윈도 시스템 라이브러리가 사용된다.

예를 들어, X 윈도 시스템의 경우 GLX (OpenGL Extension to X Window System)가 사용되며, Apple 시스템의 경우 AGL (AppleGL), Microsoft 윈도우 시스템에서는 WGL (Windows-to-OpenGL) 인터페이스가 제공된다.

윈도 시스템마다 라이브러리들이 다르기 떄문에 장치에 독립적인 인터페이스의 필요성이 제기되어, [GLUT (OpenGL Utility Toolkit)](https://en.wikipedia.org/wiki/OpenGL_Utility_Toolkit)이 개발되었다.

GLUT은 OpenGL 프로그램을 위해 운영체제와 시스템 수준의 I/O를 다루고, 윈도 정의/제어, 키보드/마우스 입력의 모니터링과 같은 함수를 제공한다. 더불어, 육면체, 구, Utah teapot과 같은 기하학 기본 요소를 그리기 위한 루틴도 제공하며, 제한적이기는 하지만 팝업 메뉴 생성 기능도 제공한다.

GLUT의 두가지 목적은,
1. 운영체제 간 이식이 가능한 코드의 생성을 허용
2. OpenGL을 쉽게 배우게 보조

하지만 현재 GLUT은 유지보수가 중단된 상태이며, [freeGLUT](https://en.wikipedia.org/wiki/FreeGLUT)으로 대체되었다.

방통대 교제에서는 freeGLUT을 사용하는 예시를 제공한다.

### OpenGL 명령어 형태
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

일부 OpenGL 명령어는 이름 마지막 문자에 'v'를 붙이는 경우가 있는데, 이떄 'v'는 여러 개의 값으로 표현되는 데이터를 배열에 저장하여 하나의 인수로 전달한다는 것을 의미한다.

예시 :
```c
// 일일이 여러 인수를 전달하는 경우
GLfloat fData1 = 0.5f, fData2 = 1.0f;
glUniform2f(vecLocation, fData1, fData2);

// 배열로 여러 인수를 전달하는 경우
GLfloat fVec[2] = {0.5f, 1.0f};
glUniform2fv(vecLocation, fVec);
```

편의를 위해서 노트에서 접미사를 생략해서 설명할 수도 있다. 예를 들어, `glUniform2f()`와 `glUniform4fv()` 등을 따로 구분해서 설명하는 대신 `glUniform()`으로 설명한다. 하지만 OpenGL은 C 언어 라이브러리라는 사실을 기억하고 자료형이 명확하게 명시되는게 좋다는 것을 명심해야 한다.

#### OpenGL 자료형
OpenGL에서 사용하는 8가지 자료형을 밑에 표로 정리했다.

|     **OpenGL DataType**    |    **C equivalent**    | **Suffix** |
|:--------------------------:|:----------------------:|:----------:|
| GLbyte                     | 8bit integer           |      b     |
| GLshort                    | 16bit integer          |      s     |
| GLint, GLsizei             | 32bit integer          |      i     |
| GLfloat, GLclampf          | 32bit float            |      f     |
| GLdouble, GLclampd         | 64bit float            |      d     |
| GLubyte, GLboolean         | 8bit unsigned integer  |     ub     |
| GLushort                   | 16bit unsigned integer |     us     |
| GLuint, GLenum, GLbitfield | 32bit unsigned integer |     ui     |


## 렌더링
[렌더링(Rendering)](https://en.wikipedia.org/wiki/Rendering_(computer_graphics))은 그래픽스 시스템이 2차원/3차원 장면(Scene)을 2차원 화면(Screen)으로 구현하는 프로세스를 뜻한다.

참고 : [3차원 렌더링](https://en.wikipedia.org/wiki/3D_rendering)

2차원 장면으로부터 2차원 화면으로 렌더링하는 것은 간단하다 - 비율이 같은 경우 이미지 픽셀 위치와 값을 화면에 그대로 반영하면 되고, 비율이 다른 경우 확대/축소하여 근접한(Approximation) 픽셀을 화면에 반영하면 된다.

3차원 장면에서 2차원 화면으로 렌더링하는 것은 좀 복잡해진다. 렌더링 작업에 3차원 모델, 조명, 물질 속성 (반짝임, 투명도, 텍스쳐 등), 카메라, 화면 비율, 이펙트 등이 고려가 되어야 하기 떄문이다. 

참고 : 영어 단어 Render는 렌더링 작업을 하라는 명령어 또는 렌더링 결과물을 뜻할 수 있고, Rendering은 이미지를 그리는 중 또는 그 프로세스를 뜻할 수 있다.

렌더링과 관련된 요소는 밑에와 같다 ([위키 참고](https://en.wikipedia.org/wiki/Rendering_(computer_graphics)#Features)).
- [Shading](https://en.wikipedia.org/wiki/Shading)
- Texture Mapping
- Bump Mapping
- Fogging
- Shadows
- Soft Shadows
- [[color_theory#반사|반사(Reflection)]]
- [[color_theory#투과|투명도(Transparency/Translucency)]]
- [[color_theory#굴절|굴절(Refraction)]]
- [[color_theory#회절|회절(Diffraction)]]
- Indirect Illumination
- Caustics
- [Depth of Field](https://en.wikipedia.org/wiki/Depth_of_field)/[Depth Perception](https://en.wikipedia.org/wiki/Depth_perception)
- Motion Blur
- Non-photorealistic Rendering

### 렌더링 기술
#todo Rasterization, Ray Casting, Ray Tracing에 대해 정리

[Raytracing](https://en.wikipedia.org/wiki/Ray_tracing_(graphics))

[raycasting](https://en.wikipedia.org/wiki/Ray_casting)

### 그래픽스 파이프라인
[그래픽스 파이프라인(Graphics Pipeline)](https://en.wikipedia.org/wiki/Graphics_pipeline)은 렌더링에 포함되는 여러 작업들을 순차적(Sequential)으로 정리한 개념적(Conceptual) 모델이다.

렌더링 파이프라인(Rendering Pipeline)으로 불리기도 한다.

하드웨어와 소프트웨어에 따라 그래픽스 처리 방식이 다름으로, 모든 상황에 통용되는 범용적인 그래픽스 파이프라인은 없다. 하지만, [[#그래픽스 라이브러리]]는 서로 유사한 그래픽스 파이프라인들을 단일화하여 제어하는 것을 목표로 개발되었고, 내부 하드웨어를 추상화하여 프로그래머가 직접 하드웨어를 제어할 필요를 제거했다.

일반적인 그래픽스 파이프라인은 주로 [3차원 다각형 렌더링(3D Polygon Rendering)](https://en.wikipedia.org/wiki/Polygonal_modeling) 위주로 되어있다.

> ![[opengl_v4_pipeline.png]]
> OpenGL v4 그래픽스 파이프라인

참고자료 :
1. [[graphics_pipeline_lecture_from_penn_university.pdf|Penn University 그래픽스 파이프라인 강의 자료]]
2. [Vulkan 그래픽스 파이프라인 소개](https://vulkan-tutorial.com/Drawing_a_triangle/Graphics_pipeline_basics/Introduction)
3. [크로노스 그룹 위키 : 렌더링 파이프라인 overview](https://www.khronos.org/opengl/wiki/Rendering_Pipeline_Overview)
4. [OpenGL 버전별로 파이프라인 정리된 자료](http://romain.vergne.free.fr/teaching/IS/SI03-pipeline.html)

## 셰이더
[셰이딩(Shading)](https://en.wikipedia.org/wiki/Shading)은 3차원 모델을 렌더링하기 위해서 빛(Light), 어두움(Darkness), 그리고 색(Color) 등의 조합 비율을 계산하는 작업/알고리즘을 뜻한다. 주로 현실 세계에 빛(Light)의 특성을 최대한 근접하게 묘사하기 위한 목표로 셰이딩이 사용되지만, 반대로 왜곡시켜 특이한 이펙트(Effect)를 만드는 경우도 있다.

참고 : 다각형으로 만들어진 도형을 둥글게 보이도록 하는 목적으로도 셰이딩이 사용된다.

초기 그래픽스 시스템에는 텍스쳐, 조명 등에 관련된 수학 연산(즉, 셰이딩)이 고정(hard-coded)되어 있어 지정된 파라미터로만 설정이 가능했다. 나중에는 이러한 수학 연산을 유저가 직접 작성한 프로그램으로 대체할 수 있도록 개선되었는데, 이러한 프로그램을 [셰이더(Shader)](https://en.wikipedia.org/wiki/Shader)라고 한다.

참고 : 셰이더(Shader)라는 단어는 1988년에 Pixar에서 출시한 RenderMan 인터페이스 사양설명서에 사용된 단어이다.

셰이더를 작성하기 위한 [셰이딩 언어](https://en.wikipedia.org/wiki/Shading_language)가 여러 있는데, 이 중 OpenGL 전용 셰이딩 언어 [GLSL (OpenGL Shading Language)](https://en.wikipedia.org/wiki/OpenGL_Shading_Language)이 있다.

참고자료 :
1. [그래픽스 조명(Lighting)](https://en.wikipedia.org/wiki/Computer_graphics_lighting)
2. [learnopengl.com - Shaders](https://learnopengl.com/Getting-started/Shaders)
3. [Cherno - How Shaders Work](https://youtu.be/5W7JLgFCkwI)

#todo [셰이더 종류](https://en.wikipedia.org/wiki/Shader#Types) 정리

Primitive and Mesh Shaders
Ray Tracing Shaders
Compute Shaders

### 정점 셰이더
[정점 셰이더(Vertex Shader)](https://www.khronos.org/opengl/wiki/Vertex_Shader)는 OpenGL 파이프라인 기준으로 처음 실행되는 **필수** 셰이더로
1. 버퍼에서 데이터를 가져오고,
2. 정점의 3차원 좌표를 2차원 좌표로 변환한 다음
3. 변환된 데이터를 다음 셰이더로 넘겨준다.

정점의 위치를 움직이는 아주 간단한 셰이더로 볼 수 있지만, 정점의 위치를 움직임으로서 구현할 수 있는 이펙트는 아주 중요하고 다양하다.

정점 셰이더를 사용한 이펙트를 예시로,
- 카메라 뷰(Camera View)를 구현할 수 있다.
- 거리감(Depth Perception)을 구현할 수 있다.
- 액체의 물결(Ripple)을 구현할 수 있다.

정점 셰이더는 각 정점에 대하여 한번씩 실행된다. 예를 들어, 3개의 정점이 있는 삼각형 모델이 있다면, 정점 셰이더는 3번 실행된다.

### 기하구조 셰이더
Geometry Shader

### 테셀레이션 셰이더
[테셀레이션(Tessellation)](https://www.khronos.org/opengl/wiki/Tessellation)은 여러 정점으로 이루어진 특정 영역(Patch) 안에 작은 기본 도형으로 채우는 작업을 뜻한다. 쉽게 이해하자면, 도형 안에 더 작은 도형들로 채우는 작업이다.

테셀레이션은 주로 모델의 품질을 높이는데 사용된다. 예를 들어,
1. 곡선\*을 부드럽게 한다.
2. 디테일을 더 선명하게 한다.
3. 2번의 연장선으로, 거리감을 구현할 수 있다 (물체가 가까울수록 디테일이 선명하게 한다).

\* 여기서 다루는 그래픽스는 다각형 모델을 기준으로 하며, 폴리곤은 점과 선으로만 구성되어 있기 때문에 실제 곡선이 없다. "곡선"을 구현하기 위해서 여러 다각형을 이어붙여야 하며, 다각형이 많을수록 더욱 부드러운 곡선을 구현할 수 있다.

![[tessellation_defined_curves.webp]]

![[tessellation_finer_details_by_closeness.webp]]

참고 : [Kisti - 쪽매맞춤이란?](http://scent.kisti.re.kr/site/main/archive/article/math-%EB%B0%9C%EB%B0%91%EC%97%90-%EC%88%A8%EA%B2%A8-%EB%91%94-%EC%88%98%ED%95%99-%EA%BA%BC%EB%82%B4%EB%B3%B4%EA%B8%B0)

#todo subdivision vs tessellation ([Pixar 자료 참고](https://graphics.pixar.com/opensubdiv/docs/subdivision_surfaces.html))

**테셀레이션 셰이더(Tessellation Shader)** 는 말 그대로 테셀레이션을 하는 셰이더다. 연산량이 크며, 필수가 아닌 선택사항이다 - 온라인 렌더링(게임)에는 잘 사용되지 않으며, 오프라인 렌더링(영화/애니메이션)에 주로 사용된다.

테셀레이션 셰이더를 동적(Dynamic)으로 적용할 수 있으면 큰 장점이 된다. 예를 들어, 대부분이 평면인 정육면체의 각 표면에 사각형 하나를 사용한다고 볼때, 정육면체의 모서리가 만약 둥글다면, 그 둥근 모서리 부분에만 따로 테셀레이션을 적용하여 그 모서리가 부드럽게 처리할 수 있다.

테셀레이션 셰이더는 2가지로 구분된다.
1. 테셀레이션 제어 셰이더
2. 테셀레이션 평가 셰이더

각 셰이더에 대하여 자세히 알아보기 전에, **테셀레이션 기본 도형 생성(Tessellation Primitive Generation, TPG)** 를 알아본다. TPG는 고정된 함수(Fixed Function)로서 

#### 테셀레이션 제어 셰이더
[테셀레이션 제어 셰이더(Tessellation Control Shader, TCS)](https://www.khronos.org/opengl/wiki/Tessellation_Control_Shader)의 역할은 두 가지가 있다.
1. 도형에 대한 테셀레이션을 얼만큼 적용할지 판단
2. 입력 영역 데이터\*에 특수의 변환\*\*을 적용

\* 입력 영역 데이터를 영어로 Input Patch Data라고 하는데, 셰이더에 들어오는 도형의 데이터라고 생각하면 된다.

\*\* 여기서 특수의 변환이란, 입력 영역(Patch)의 사이즈를 변경하던가 또는 정점의 수를 늘리거나 줄이는 것을 뜻한다.

테셀레이션 제어 셰이더는 선택사항이다.
1. 활성화된 경우 : [[#정점 셰이더]]로부터 데이터를 전달받아 연산을 하고 출력값을  단계로 전달한다. 
2. 비활성화된 경우 : 데이터는 [[#정점 셰이더]]에서 **테셀레이션 기본 도형 생성(Tessellation Primitive Generation)** 단계로 바로 전달된다 - 이 경우, 테셀레이션이 적용되는 정도는 기본값(Default Value)이 사용된다.

#### 테셀레이션 평가 셰이더
[테셀레이션 평가 셰이더(Tessellation Evaluation Shader, TES)](https://www.khronos.org/opengl/wiki/Tessellation_Evaluation_Shader)는 



### Fragment Shader
Fragment Shader는 마지막에 실행되는 셰이더로 조명, 거리, 반사 등 여러 속성을 고려하여 픽셀의 색을 결정한다.