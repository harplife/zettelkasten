---
aliases: [그래픽스 좌표계, Graphics Coordinates]
tags: [computer_science, computer_vision, computer_graphics, study, display, programming]
status: ongoing
created: 2022-06-08
edited: 2022-06-08
cssclass : "graphics-projection"
---

# 뷰잉 및 투영
컴퓨터 그래픽스에 있어 3D 모델을 "본다"는 것은 추상적으로만 존재하는 3D 모델을 현실 세계 2D 화면의 픽셀로서 사람이 인식할 수 있는 그림으로 재현한다는 의미로 해석된다 - 그리고 이 행위를 뷰잉(Viewing)이라고 한다.

뷰잉(Viewing)을 실제로 구현하는 것을 [투영(Projection)](https://en.wikipedia.org/wiki/3D_projection)이라고 한다 - 투영은 3차원 모델을 2차원 평면에 그리는 기술이다.

참고 : 간단히 투영이라 부르지만, 자세히는 그래픽 투영(Graphical Projection) 또는 3차원 투영(3D Projection)이라 부르기도 한다.

뷰잉은 말 그대로 보는 행위, 투영은 보이는 것을 그림으로 그리는 행위로 생각하면 될 것 같다. 또는, 투영은 뷰잉을 하는 방식이 된다.

![[3d_projection_diagram.svg]]

3차원 모델이 투영되는 2차원 평면을 [투영 평면(Projection Plane)](https://en.wikipedia.org/wiki/Projection_plane) 또는 [이미지 평면(Image Plane)](https://en.wikipedia.org/wiki/Image_plane)이라 부른다.

투영선(Projection Line)은 3차원 공간의 정점에서 2차원 공간의 정점으로 바라보는 가시선(Line of Sight)으로 이해하면 된다.

참고 : Projection은 투영, 사영, 또는 투상으로도 번역된다.. - [정보통신기술용어해설](http://www.ktword.co.kr/test/view/view.php?m_temp1=4978)

투영은 [[#평행 투영]]과 [[#원근 투영]]으로 크게 두 가지로 분류되며, 각 투영 방식에 여러 종류의 투영이 있다.

![[graphical_projections_all_types.svg]]

투영은 가상의 "카메라"로 비유된다 - 3차원 공간에 물체와 카메라가 있다면, 카메라의 [시야(Field of Vision)](https://en.wikipedia.org/wiki/Field_of_view)에 보이는 물체가 투영된 그림과 동일하다. 이러한 이유로, 투영을 설명할 때 카메라와 시야 위주로 설명되는 경우가 많다.

위와 같은 비유로 인해, 뷰잉과 투영은 서로 반대되는 개념으로도 이해될수있다 - 평면에서 물체를 바라보는 것을 뷰잉이라 하고, 물체에서 평면을 바라보는 것을 투영이라 할 수 있다. #todo 실제로 컴퓨터 그래픽스에서 카메라를 구현할 떄 투영 행렬의 역을 계산하여 구현하는 듯 싶다 - 어디서 주워들은 말이니까 confirm 필요.

참고 : 컴퓨터 그래픽스에서는 투영을 기하변환(Geometrical Transformation)으로 구현한다.

## 다시점 투영
평행 투영과 원근 투영을 설명하기 앞서 다시점 투영을 설명한다.

[다시점 투영(Multiview Projection)](https://en.wikipedia.org/wiki/Multiview_orthographic_projection)이란 여러 개의 각도에서 물체를 바라본다(투영한다)는 뜻을 가지며, 정확히는 물체를 두르는 가상의 육면체(Hexahedron)을 그려서 물체를 바라보는 각도를 정면, 저면(후면), 좌측면, 우측면, 평면(윗면), 그리고 저면(아랫면)으로 정의하여 투영하는 방식이다.

이 면들을 뷰(View)라 부르며, 이 뷰들이 이루는 육면체를 뷰 볼륨(View Volume)이라한다.

2차원 좌표계에 사분면(Quadrant)이 있듯이, 3차원 좌표계에는 [팔분공간(Octant)](https://en.wikipedia.org/wiki/Octant_(solid_geometry))가 있다. 뷰 볼륨을 구현하는 데 있어, 투영의 시점을 특정 팔분공간 안에 6개의 정점으로 정의할 수 있다.

![[octant.svg]]

뷰 볼륨은 하나의 물체를 두르거나, 또는 하나의 장면을 두를 수 있다. 프로그램이 정의하는 뷰 볼륨에 따라 물체/장면의 일부가 클리핑(Clipping)될 수 있다 - 뷰 볼륨을 클리핑 볼륨이라고도 부른다.

다시점 투영은 평행 투영과 원근 투영의 기반이 된다 - 뷰 볼륨을 기준으로 어느 뷰/각도에서 투영을 하는지, 또는 뷰 볼륨을 얼만큼 변환하는지에 따라 투영의 종류가 정해진다.

## 평행 투영
[평행 투영(Parallel Projection)](https://en.wikipedia.org/wiki/Parallel_projection)은 3차원 물체를 평면에 투영할 때 투영선(Projection Line)이 서로 평행(Parallel)한 경우를 뜻한다.

![[parallel_projection_diagram_0.svg]]

평행 투영은 투영선의 길이와 무관하게 평행해 보인다. 그 뜻은,  투영 평면이 아무리 멀리 또는 가까이 있다고 해도 투영된 도형의 크기는 변하지 않는 다는 뜻이다.

평행 투영의 뷰 볼륨은 밑에와 같이 생겼다.

![[parallel_projection_view_volume.png]]

평행 투영은 정사 투영과 경사 투영으로 나뉜다.

### 정사 투영
[정사 투영(Orthographic Projection)](https://en.wikipedia.org/wiki/Orthographic_projection)은 "정면을 바라본다"는 의미에서 투영선이 투영평면과 수직관계를 이루는 평행 투영을 뜻한다.

참고 : 정사..라는 단어가 좀 그렇다. 직교 투영이라고도 불린다.

정사 투영은 기본 뷰와 보조 뷰으로 나뉜다.

#### 기본 뷰
기본 뷰(Primary Views)는 각 뷰가 투영면과 평행하게 투영됨을 뜻한다. 한 개의 투영면에 한 개의 뷰만 보인다. 기본 뷰는 뷰 볼륨의 면을 위주로 물체를 바라본다는 특징이 있다.

참고 : 뷰와 투명면 사이에 선을 그을때 그 선이 두 면과 수직관계를 이룬다는 뜻도 있다.

![[orthographic_projection_primary_view_elevation.png]]

이 뷰들을 나열하여 3D 물체를 표현할 수 있으며, 나열하는 순서에 따라 제1각법(First-angle) 또는 제3각법(Third-angle)으로 나뉜다.

![[multiview_projection_1st_and_3rd_angle_comparison.png]]

다시점 투영의 특징은 특정 3가지 뷰으로 3D 물체에 대한 정보를 충분히 표현할 수 있다는 것이다. 이 3가지 뷰은 밑에와 같다.
1. 물체를 윗면에서 바라보는 설계도/배치도(Plan)
2. 물체를 옆면(앞/뒤/왼쪽/오른쪽)에서 보는 입면도(Elevation)
3. 물체의 내면을 바라보는 단면도(Section)

기본 뷰의 장점은 3D 물체의 표면이 왜곡(Distortion)되어 표현되지 않는다는 것이다 - 더 자세한 사항은 보조 뷰에서 다룬다.

#### 보조 뷰
보조 뷰(Auxiliary Views)은 각 뷰가 투영면과 평행하지 않게 투영됨을 뜻한다.  한 개의 투영면에 3개의 뷰가 보인다. 보조 뷰는 뷰 볼륨의 정점을 위주로 물체를 바라본다는 특징이 있다.

참고 : [Axonometric Projection](https://en.wikipedia.org/wiki/Axonometric_projection)이라 불리기도 한다.

![[orthographic_projection_aux_view_isometric.png]]

보조 뷰를 설명하기 앞서 단축(Foreshortening)에 대하여 잠시 설명한다. 뷰와 투영면이 평행하지 않으면 뷰는 왜곡(Distortion) 되어 보이며, 마찬가지로 도형도 왜곡되어 보인다.

예를 들어, 물체가 정육각형인 경우 물체의 면과 투영면이 평행하지 않으면 물체의 면(사각형)이 왜곡되어 마름모(Rhombus) 또는 사다리꼴(Trapezoid) 처럼 보일 수 있다.

이 왜곡되는 현상을 3차원 좌표계 축(Axis/Axes)의 [단축(Foreshortening)](https://en.wikipedia.org/wiki/Perspective_(graphical)#Foreshortening)이라 표현한다.

하나의 뷰 볼륨 정점을 위주로 물체를 바라봤을 때, 3개 축의 단축 비율을 기준으로 보조 뷰가 3가지로 분류된다.
1. 등각 투영
2. 이각 투영
3. 삼각 투영

##### 등각 투영
[등각 투영(Isometric Projection)](https://en.wikipedia.org/wiki/Isometric_projection)은 3개 축의 단축이 서로 동등한 경우를 뜻하며, 축과 축 사이의 각도가 120도를 이룬다.

뷰 볼륨의 변(Edge) 길이가 서로 같은 비율을 유지하고 있으면 등각 투영이라 볼 수 있다.

![[isometric_projection.png]]

##### 이각 투영
이각 투영(Dimetric Projection)은 2개 축의 단축만 동등하고 1개 축의 단축만 다른 경우를 뜻한다.

![[dimetric_projection.png]]

##### 삼각 투영
삼각 투영(Trimetric Projection)은 각 축의 단축이 서로 다른 경우를 뜻한다.

![[trimetric_projection.png]]

#### 정사투영행렬
투영을 한다는 것은 기하변환을 한다는 것과 동일하다. 따라서, 정점좌표행렬에 기하변환행렬을 곱하는 것은 투영행렬을 곱하는 것과 같음을 의미한다.

`z=0`인 투영면을 기준으로 가장 기본적인 정사투영행렬은 밑에와 같다 (기본 뷰).

참고 : 변환(행렬 곱)은 동치 행렬로 구현하는게 좋다.

$$
P
=
\begin{bmatrix}
    1&0&0&0\\
    0&1&0&0\\
    0&0&0&0\\
    0&0&0&1
\end{bmatrix}
$$

정점좌표행렬에 대하여 정사투영행렬이 곱해지는 식은 밑에와 같이 표현된다.

$$
\begin{bmatrix}
    x^{\prime}\\
    y^{\prime}\\
    0\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    1&0&0&0\\
    0&1&0&0\\
    0&0&0&0\\
    0&0&0&1
\end{bmatrix}
\begin{bmatrix}
    x\\
    y\\
    z\\
    1
\end{bmatrix}
$$

정사투영행렬은 [[#뷰 볼륨 기준 투영행렬]]로 표현할 수 있다 - [[#뷰 볼륨 정사투영행렬]]을 참고한다.

##### 보조 뷰 정사투영행렬
보조 뷰 정사투영행렬은 기본 정사투영행렬에 [[opengl_draw_2d_transform#회전 변환|회전변환행렬]]을 곱한 것과 같다.

밑에는 제1팔분공간에서 물체를 바라본 시점을 표현하는 정사투영행렬이다.
$a$는 3차원 좌표, $b$는 투영된 2차원 좌표, $\alpha=\arcsin(\tan 30\degree)$, 그리고 $\beta=45\degree$ 이다.

![[first_octant_rotation_matrix.svg]]

$$
\begin{bmatrix}
    b_{x}\\
    b_{y}\\
    0\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    1&0&0&0\\
    0&1&0&0\\
    0&0&0&0\\
    0&0&0&1
\end{bmatrix}
\begin{bmatrix}
    c_{x}\\
    c_{y}\\
    c_{z}\\
    1
\end{bmatrix}
$$

### 경사 투영
[경사 투영(Oblique Projection)](https://en.wikipedia.org/wiki/Oblique_projection)


## 원근 투영
원근 투영은 원근법이 적용된 투영을 뜻한다.


[원근법(Perspective)](https://en.wikipedia.org/wiki/Perspective_(graphical))이 속한다.

![[camera_focal_length_distance_animation.gif]]


## 뷰 볼륨 기준 투영행렬
뷰 볼륨은 투영에 많은 영향을 준다. 뷰 볼륨에 대한 변환은 투영에 직접적인 영향을 준다.

투영행렬을 만들기 위해서는 뷰 볼륨을 구성하는 값들을 알아볼 필요가 있다.

### 뷰 볼륨 정사투영행렬
정사투영행렬을 구성할 시, 뷰 볼륨(육면쳬)의 중앙점을 3차원 좌표계 기준 원점(Origin)으로 취급하며, 뷰 볼륨에 대하여 밑에와 같은 값들을 정의한다.
- Left : x축 기준 최대 왼쪽 값
- RIght : x축 기준 최대 오른쪽 값
- Top : y축 기준 최대 위쪽 값
- Bottom : y축 기준 최대 아래쪽 값
- Near : z축 기준 최대 가까운 값
- Far : z축 기준 최대 먼 값

참고 : 축 기준 최소/최대 값으로 표현하지 않는 이유는 뷰 볼륨이 거꾸로 될 수도 있기 떄문이다.

위 값들을 사용하여 구축한 정사투영행렬은 밑에와 같다.

$$
P
=
\begin{bmatrix}
    \frac{2}{right-left}&0&0&-\frac{right+left}{right-left}\\
    0&\frac{2}{top-bottom}&0&-\frac{top+bottom}{top-bottom}\\
    0&0&\frac{-2}{far-near}&-\frac{far+near}{far-near}\\
    0&0&0&1
\end{bmatrix}
$$

정사투영행렬을 [[opengl_draw_2d_transform#크기 변환|크기변환행렬]]과 [[opengl_draw_2d_transform#이동 변환|이동변환행렬]]로 나누어 표현할 수 있다.

$$
S
=
\begin{bmatrix}
    \frac{2}{right-left}&0&0&0\\
    0&\frac{2}{top-bottom}&0&0\\
    0&0&\frac{2}{far-near}&0\\
    0&0&0&1
\end{bmatrix}
$$
$$
T
=
\begin{bmatrix}
    1&0&0&-\frac{right+left}{2}\\
    0&1&0&-\frac{top+bottom}{2}\\
    0&0&-1&-\frac{far+near}{2}\\
    0&0&0&1
\end{bmatrix}
$$
$$
P = ST
$$

지정된 뷰 볼륨 값에 따라 정사투영이 되는 도형이 변경되는 것을 이 [시뮬레이션](http://learnwebgl.brown37.net/08_projections/create_ortho/create_ortho.html)을 통해 직접 볼 수 있다.

### 뷰 볼륨 원근투영행렬


# 공간
뷰 볼륨은 하나의 3차원 공간이라 볼 수 있다 - 하나의 물체에 고유한 공간이 있을 수 있고, 여러 물체가 담긴 하나의 공간이 있을 수 있으며, 또는 여러 물체를 담는 공간을 담는 또 다른 공간이 있을 수 있다.

컴퓨터 그래픽스에 있어 3D 모델의 뷰잉을 구현하기 위해 3D 모델을 표현할 여러 공간과, 공간과 공간으로서 전달되며 적용되는 변환들을 알아볼 필요가 있다.

컴퓨터 그래픽스에선 6가지 공간을 다룬다.
1. Local Space (Object Space)
2. World Space
3. Camera Space (Eye Space,  View Space)
4. Projection Space
5. Clip Space
6. Screen Space

주의 : Clip Space와 Screen Space를 제외한 위 좌표계들은 추상적인(Abstract) 요소로서, OpenGL에서 각 좌표계를 정의한 것은 아니다. GPU는 우리가 주는 정보를 그대로 구현할 뿐이다.

## Local Space
지역 공간(Local Space)는 3D 좌표계에서 원점(Origin)에 상대적인(Relative) 좌표로서 3D 모델 정점의 위치를 표현한 것이다 - 각 3D 모델에 하나의 공간이 부여된다는 뜻이다.

객체만의 공간이란 의미로 객체 공간(Object Space)라고도 부른다.

여기서 정점의 위치가 서로 상대적임을 명심해야 한다. 정점 A에서 정점 B를 (-0.5, 0)와 (0.5, 0)로 표현하든, (-5, 0)와 (5, 0)로 표현하든 의미는 똑같다는 것이다 (정점과 정점의 위치가 원점 기준으로 비율이 변경되지 않는 이상).

참고 : 정점과 정점의 거리는 화면의 픽셀값과 동일하지 않다!

3D 모델의 지역 좌표는 정점 셰이더에 입력되는 값이라 볼 수 있다.

참고 : 특별한 이유가 있지 않는 이상, 지역 원점은 3D 모델의 가운데(에 근접한 위치)에 있다.

## World Space
세계 공간(World Space)는 3D 좌표계에서 원점(Origin)에 상대적인(Relative) 좌표로서 3D 모델의 위치와 크기를 표현한 것이다 - 하나의 장면(Scene)에 대한 공간으로 볼 수 있고, 여러 모델이 세계 공간에 있을 수 있다.

지구 위에 여러 국가가 있듯이, 세계 공간 위에 여러 지역 공간이 있다고 비유할 수 있다.

세계 공간은 OpenGL이 구현하는게 아니라 소스 프로그램이 직접 구현하는 것이다. 정점 셰이더에서 정점 좌표를 받아 그대로 전달하거나, 또는 변환(이동, 크기, 회전)을 구현한 경우, 세계 공간을 구현했다고 생각하면 된다.

참고 : 처음에 OpenGL을 시작할 때 삼각형 하나 그리는 것으로 시작한다. 정점 좌표에 아무런 변환이 없는 경우, 지역 공간과 세계 공간이 동일하다고 볼 수 있다.

## Camera Space
카메라 공간(Camera Space)은 

참고 : Eye Space 또는 View Space라고도 불린다.




# 시각단서
#todo 시지각에 대한 자료 따로 정리

뷰잉에 있어 사람의 [시지각(Visual Perception)](https://en.wikipedia.org/wiki/Visual_perception)을 최대한 모방하기 위해서는 모형, 크기, 위치, 그리고 색상으로 현실적인 [시각단서(Visual Cue)](https://en.wikipedia.org/wiki/Sensory_cue#Visual_cues)를 구현해야 한다.

시각단서 :
1. [깊이(Depth)](https://en.wikipedia.org/wiki/Depth_perception)
2. [움직임(Motion)](https://en.wikipedia.org/wiki/Motion_perception)
3. [생물학적 움직임(Biological Motion)](https://en.wikipedia.org/wiki/Biological_motion)
4. [대비(Contrast)](https://en.wikipedia.org/wiki/Contrast_(vision))

참고 : [단안단서(Monocular Vision)](https://en.wikipedia.org/wiki/Monocular_vision)