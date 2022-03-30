---
aliases: [Computer Graphics Note 2]
tags: [computer_science, computer_vision, computer_graphics, KNOU, study]
status: ongoing
created: 2022-03-27
edited: 2022-03-27
---

# Computer Graphics Note 2
방통대 교과서에 있는 내용을 토대로 하되, 여러 부분을 수정/제거/추가한 노트.

개인적으로 느낀 바로, 방통대 교과서는 정리가 잘 안 되어 있을 뿐만이 아니라 틀린 정보가 많다.

# 컴퓨터 그래픽스 소프트웨어
그래픽스 워크스테이션에서 디지털 이미지를 다루는 방법, 즉, 그래픽스 소프트웨어에 대하여 알아본다.

## 컴퓨터 그래픽스 표현
[그래픽스 (Graphics)](https://en.wikipedia.org/wiki/Graphics)는 컴퓨터 그래픽스 시스템에서 다루는 디지털 이미지를 뜻한다. 컴퓨터 과학 기준으로 [자료 구조 (Data Structure)](https://en.wikipedia.org/wiki/Data_structure)라 볼 수 있다.

여기서 다룰 내용은 [[computer_graphics_note_1#래스터 스캔]] 기반 시스템에서 그래픽스를 표현하는 방식이다.

그래픽스 표현 방식은 래스터와 벡터로 2가지로 나뉜다.

### 래스터 그래픽스
[래스터 그래픽스 (Raster Graphics)](https://en.wikipedia.org/wiki/Raster_graphics)는 이미지를 사각형 그리드 안의 여러 [[computer_graphics_note_1#픽셀]]로 표현 또는 저장하는 방식을 뜻한다. 다른 말로는, 이미지를 픽셀의 행렬로 표현하는 방식이라고 할 수 있다.

래스터 그래픽스 형식의 이미지를 래스터 그래픽스 이미지라 부르지만, 편의상 "래스터 이미지"라고 부른다.

래스터 이미지는 비트맵 이미지 (Bitmap Image)라고 불리기도 한다. [비트맵 (Bitmap)](https://en.wikipedia.org/wiki/Bitmap)은 정보를 비트 (Bit)로 매핑한다는 의미이며, 이미지를 저장하는 메모리 저장 방식이다.

일반 래스터 이미지에 하나의 서브픽셀은 8-bit 데이터로 저장되며, 0~255 (256개) 사이의 숫자를 표현할 수 있다. 따라서, 픽셀은 3개의 서브픽셀 (RGB)로 구성되니 하나의 픽셀이 24-bit 데이터로 저장된다 (3 채널 RGB 이미지 경우).

100 x 100 (픽셀) 크기의 24-bit 래스터 이미지는 대략 30 KB 량의 데이터로 볼 수 있다.

RGB 이미지에 [투명 (Transparency)](https://en.wikipedia.org/wiki/Transparency_(graphic)) 정보가 추가된 경우, 8-bit의 알파 채널 (Alpha Channel)로 저장되며, 이러한 이미지를 [RGBA](https://en.wikipedia.org/wiki/RGBA_color_model) 이미지라 부른다. 8-bit가 추가되었기 때문에 하나의 픽셀이 32-bit 데이터로 저장된다.

### 벡터 그래픽스


### 이미지 파일 포맷
[파일 포맷](https://en.wikipedia.org/wiki/File_format)은 정보를 비트로 표현하는 구성요소 및 구조의 표준을 뜻한다. 파일 포맷은 필수가 아니다 - [파일명 확장자](https://en.wikipedia.org/wiki/Filename_extension)가 없는 경우, 파일은 단순한 [문자열 데이터](https://en.wikipedia.org/wiki/Plain_text)로 처리된다.

[이미지 파일 포맷](https://en.wikipedia.org/wiki/Image_file_format)은 이미지(픽셀 행렬)와 이미지에 대한 정보(메타데이터)를 데이터(비트)로 표현하는 구성요소 및 구조의 표준을 뜻한다.

https://en.wikipedia.org/wiki/BMP_file_format

![[bmp_file_format_structure.svg]]

https://en.wikipedia.org/wiki/Generation_loss