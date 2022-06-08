---
aliases: [그래픽스 좌표계, Graphics Coordinates]
tags: [computer_science, computer_vision, computer_graphics, study, display, programming]
status: ongoing
created: 2022-06-08
edited: 2022-06-08
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

## 평행 투영
[평행 투영(Parallel Projection)](https://en.wikipedia.org/wiki/Parallel_projection)은 3차원 물체를 평면에 투영할 때 투영선(Projection Line)이 서로 평행(Parallel)한 경우를 뜻한다.

![[parallel_projection_diagram_0.svg]]

평행 투영은 투영선의 길이와 무관하게 평행해 보인다. 그 뜻은,  투영 평면이 아무리 멀리 또는 가까이 있다고 해도 투영된 도형의 크기는 변하지 않는 다는 뜻이다.

평행 투영은 정사 투영과 경사 투영으로 나뉜다.

### 정사 투영
[정사 투영(Orthographic Projection)](https://en.wikipedia.org/wiki/Orthographic_projection)은 "정면을 바라본다"는 의미에서 투영선이 투영평면과 수직관계를 이루는 평행 투영을 뜻한다.

정사 투영을 설명하기 전에 **다시점 투영**을 우선 설명한다.

[다시점 투영(Multiview Projection)](https://en.wikipedia.org/wiki/Multiview_orthographic_projection)이란 여러 개의 각도에서 물체를 바라본다(투영한다)는 뜻을 가지며, 정확히는 물체를 두르는 가상의 정육각형(Cube)을 그려서 물체를 바라보는 각도를 앞면, 뒷면, 왼쪽면, 오른쪽면, 윗면, 그리고 아랫면으로 정의하여 투영하는 방식이다.

편의를 위해서 이 면들을 시야(View)로 표현하겠다.

다시점 투영을 기준으로 정사 투영은 기본 시야와 보조 시야으로 나뉜다.

#### 기본 시야
기본 시야(Primary Views)는 각 시야가 투영면과 평행하게 투영됨을 뜻한다.

참고 : 시야와 투명면 사이에 선을 그을때 그 선이 두 면과 수직관계를 이룬다는 뜻도 있다.

이 시야들을 나열하여 3D 물체를 표현할 수 있으며, 나열하는 순서에 따라 제1각법(First-angle) 또는 제3각법(Third-angle)으로 나뉜다.

![[multiview_projection_1st_and_3rd_angle_comparison.png]]

다시점 투영의 특징은 특정 3가지 시야으로 3D 물체에 대한 정보를 충분히 표현할 수 있다는 것이다. 이 3가지 시야은 밑에와 같다.
1. 물체를 윗면에서 바라보는 설계도/배치도(Plan)
2. 물체를 옆면(앞/뒤/왼쪽/오른쪽)에서 보는 입면도(Elevation)
3. 물체의 내면을 바라보는 단면도(Section)

기본 시야의 장점은 3D 물체의 표면이 왜곡(Distortion)되어 표현되지 않는다는 것이다 - 더 자세한 사항은 보조 시야에서 다룬다.

#### 보조 시야
보조 시야(Auxiliary Views)은 각 시야와 투영면과 평행하지 않게 투영됨을 뜻한다.

https://en.wikipedia.org/wiki/Axonometric_projection

단축(Foreshortening) 왜곡(Distortion)

#### 선형대수학적 표현

$$
P
=
\begin{bmatrix}
    1&0&0\\
    0&1&0\\
    0&0&0
\end{bmatrix}
$$


### 경사 투영
[경사 투영(Oblique Projection)](https://en.wikipedia.org/wiki/Oblique_projection)


## 원근 투영
원근 투영은 원근법이 적용된 투영을 뜻한다.


[원근법(Perspective)](https://en.wikipedia.org/wiki/Perspective_(graphical))이 속한다.

![[camera_focal_length_distance_animation.gif]]



컴퓨터 그래픽스에 있어 3D 모델을 "본다"는 것을 구현하기 위해 3D 모델을 표현할 여러 공간과, 공간과 공간으로서 전달되며 적용되는 변환들을 알아볼 필요가 있다.

컴퓨터 그래픽스에선 6가지 좌표계(Coordinate System)를 다룬다.
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