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
디지털 이미지를 처리하기 위한 소프트웨어는 일반적으로 특수목적 그래픽스 패키지와 그래픽스 API로 구분할 수 있다.

### 특수목적 패키지
**특수목적 패키지**는 프로그래밍 필요없이 고품질의 그래픽스 작업을 할 수 있도록 편리한 사용자 인터페이스를 지원하는 응용 소프트웨어를 뜻한다.

인터페이스에 제공되는 도구를 사용하여 화면에 고품질의 이미지를 그릴 수 있다.

특수목적 패키지의 예시는 밑에와 같다.
- CAD : 건축, 기계, 전자회로 등 제품설계에 활용될 수 있는 소프트웨어
- Photoshop/Illustrator : 이미지 제작/편집 소프트웨어
- Maya : 3D 애니메이션 제작 소프트웨어

참고 : 특수목적 패키지는 이 교수가 만들어낸 말이니 굳이 깊이 받아드릴 필요없다. 그냥 "그래픽스 응용 소프트웨어"라고 생각하는게 좋을 듯?

### 그래픽스 API
그래픽스 API는 프로그램이 이미지를 화면에 그리기 위해 GPU에게 명령을 보낼 수 있게 소통을 보조해주는 라이브러리 이다.

그래픽스 API는 직접 코딩을 하여 그래픽스 작업(또는 보조 소프트웨어 개발)을 할 수 있도록 프로그래밍 언어 전용 그래픽스 함수를 제공하는 그래픽스 라이브러리를 의미한다.

그래픽스 API는 설계 및 렌더링 작업을 처리하기 위한 최적화된 함수를 제공하며, 이러한 함수들을 모아 특수목적 패키지를 개발할 수 있다.

그래픽스 API는 저수준 그래픽스 API와 고수준 그래픽스 API로 구분된다.

#### 저수준 그래픽스 API
저수준 그래픽스 API (Low Level Graphics API)는 그림을 구성하는 점, 선, 다각형과 같은 그래픽스 기본 요소 및 이들에 대한 색상, 문양 등의 속성을 정의하고, 객체의 기하변환, 장면의 뷰잉 등 장면을 정의하여 이를 컴퓨터 화면에 표시하는 일련의 과정을 지시하는 함수들이 포함된다.

GL, OpenGL, DirectX 등은 이러한 함수들을 제공한다.

저수준 그래픽스 API를 이용하여 장면을 만들고자 할 때에는 장면 내에 물체를 구성하는 기본 요소들을 개별적으로 정의하고, 이들을 그리기 위한 세부적인 처리과정을 일일이 프로그램으로 작성해야 한다. 이러한 과정에서 아주 단순한 그림을 그리기 위해 방대한 프로그램을 작성해야 한다.

#### 고수준 그래픽스 API
고수준 그래픽스 API (High Level Graphics API)는 장면 묘사를 위주로 하는 기증