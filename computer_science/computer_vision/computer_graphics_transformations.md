---
aliases: [선형변환, 변환행렬, 기하변환, Graphics Transformation, Linear Transformation, Transformation Matrix]
tags: [computer_science, computer_vision, computer_graphics, study, display, programming, linear_algebra, mathematics, geometry]
status: ongoing
created: 2022-06-16
edited: 2022-06-16
cssclass : "graphics-projection"
---

# 선형변환
[선형변환(Linear Transformation)](https://en.wikipedia.org/wiki/Linear_map)은 입력-출력 관계($V \rightarrow W$)의 벡터 공간 성질이 보존되는 행렬(Matrix)에 대한 함수이다 - 아마도?

참고 : 선형사상(Linear Map) 또는 일차변환 으로 불리기도 한다. 기하학(Geometry) 위주로 봤을 때는 [기하변환(Geometric Transformation)](https://en.wikipedia.org/wiki/Geometric_transformation)이라 부르는 듯 싶다.

간단하게 설명하면.. 선형변환은 행렬에 대한 연산이되 벡터 공간 안의 덧셈, 곱셈의 성질이 변경되지 않으며, 입력 될 때의 공간의 원점과 출력 될 떄의 공간의 원점이 동일하다는 것이다.

위키에서 수학적으로 정의한 내용 밑에 정리.

Let $V$ and $W$ be vector spaces over the same field $K$. A function $f : V \rightarrow W$ is said to be a *linear map* if for any two vectors $u,v \in V$ and any scalar $c \in K$ the following two conditions are satisfied:
1. Additivity / Operation of Addition
$f(u+v)=f(u)+f(v)$
2. Homogeneity of degree 1 / Operation of Scalar Multiplication
$f(cu)=cf(u)$

선형변환은 선형대수학(Linear Algebra)의 메인이라고 볼 수 있지만, [[computer_graphics_software|컴퓨터 그래픽스 소프트웨어]]에 있어 아주 큰 부분을 차지한다.

선형변환에는 여러 종류가 있는데, 여기서 대표적인 선형변환은 밑에와 같다.
1. 항등변환(Identity)
2. 이동변환(Translation)
3. 크기변환(Scaling)
4. 회전변환(Rotation)
5. 전단변환(Shearing)
6. 반사변환(Reflection)

위와 같은 선형변환들을 사용하여 Orthogonal Projection, Perspective Projection,  등을 구현할 수 있다.

선형변환은 일반적으로 행렬(Matrix)로 표현된다.

## 아핀 변환
선형변환에 있어 단위정사각형(Unit Square)의 선들이 변환 후 선으로 유지되고 평행성(Parallelism)을 잃지 않는다면 그 변환은 [아핀 변환(Affine Transformation)](https://en.wikipedia.org/wiki/Affine_transformation)으로 구분될 수 있다. 이 [자료](https://hooni-playground.com/1271/)에 의하면, 아핀변환의 특수한 형태(Bias가 영벡터)가 선형변환이며, 선형변환은 아핀변환에 포함된다 (하지만 아핀변환은 비선형변환도 가능하다).

### 아핀 변환 차트
![[2d_affine_transformation.svg]]

## 동차 좌표계
#todo [동차 좌표계(Homogeneous Coordinates)](https://en.wikipedia.org/wiki/Homogeneous_coordinates)는.. 설명하긴 어렵지만, 일단 동차 좌표를 사용하면 2차원 또는 3차원 좌표들에 대한 변환을 모두 곱셈으로 표현할 수 있다는 장점이 있다.

3차원 공간에 정점(Vertex) $V(x,y,z)$의 좌표를 동차 좌표로 표현하면 밑에와 같다.

$$
V = 
\begin{bmatrix}
    x\\
    y\\
    z\\
    1
\end{bmatrix}
$$

## 항등변환
항등변환(Identity Transformation)은 출력값이 입력값과 동일하게 하는 함수로서, [항등행렬(Identity Matrix)](https://en.wikipedia.org/wiki/Identity_matrix) $I$에 대한 입력 행렬 $V$의 곱으로 이루어진다. 항등변환으로서 $V = V^{\prime}$가 이루어진다.

$$
V^{\prime} = VI = 
\begin{bmatrix}
    1&0&0&0\\
    0&1&0&0\\
    0&0&1&0\\
    0&0&0&1
\end{bmatrix}
\begin{bmatrix}
    x\\
    y\\
    z\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    x\\
    y\\
    z\\
    1
\end{bmatrix}
= V
$$

항등변환은 다른 변환들에 기준이 된다. 프로그램적으로도 항등행렬을 우선 구성하고 항등행렬에 대하여 변환을 적용함으로서 변환을 누적시킨다.

## 이동변환
[이동변환(Translation)](https://en.wikipedia.org/wiki/Translation_(geometry))은 도형(점, 선, 등)의 위치를 움직이게 하는 함수이다.

3차원 공간에 이동변환은 밑에와 같이 표현할 수 있다 (정점행렬 $V(x,y,z)$, 이동변환행렬 $T(d)$).

$$
V = 
\begin{bmatrix}
    x\\
    y\\
    z
\end{bmatrix}, 
T = 
\begin{bmatrix}
    d_{x}\\
    d_{y}\\
    d_{z}
\end{bmatrix}
$$

$$
V^{\prime} = V + T = 
\begin{bmatrix}
    x\\
    y\\
    z
\end{bmatrix}
+
\begin{bmatrix}
    d_{x}\\
    d_{y}\\
    d_{z}
\end{bmatrix}
=
\begin{bmatrix}
    x + d_{x}\\
    y + d_{y}\\
    z + d_{z}
\end{bmatrix}
$$

이동변환을 동차좌표계로 표현하면 밑에와 같다 (정점행렬 $V(x,y,z)$, 이동변환행렬 $T(d)$).

$$
V = 
\begin{bmatrix}
    x\\
    y\\
    z\\
    1
\end{bmatrix}, 
T = 
\begin{bmatrix}
    d_{x}\\
    d_{y}\\
    d_{z}\\
    1
\end{bmatrix}
$$

$$
V^{\prime} = T(d)V = 
\begin{bmatrix}
    1&0&0&d_{x}\\
    0&1&0&d_{y}\\
    0&0&1&d_{z}\\
    0&0&0&1
\end{bmatrix}
\begin{bmatrix}
    x\\
    y\\
    z\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    x + d_{x}\\
    y + d_{y}\\
    z + d_{z}\\
    1
\end{bmatrix}
$$

## 크기변환
[크기변환(Scaling)](https://en.wikipedia.org/wiki/Scaling_(geometry))은 도형의 크기를 줄이거나 크게하는 함수를 뜻한다. 일반적으로 크기변환은 하나의 척도인자(Scale Factor)로 각 축에 대하여 균등(Uniform)/등방(Isotropic)하게 적용된다.

3차원 공간에 크기변환은 밑에와 같이 표현할 수 있다 (정점행렬 $V(x,y,z)$, 크기변환행렬 $S(a)$).

$$
V = 
\begin{bmatrix}
    x\\
    y\\
    z
\end{bmatrix}, 
S = 
\begin{bmatrix}
    a_{x}&0&0\\
    0&a_{y}&0\\
    0&0&a_{z}
\end{bmatrix}
$$

$$
V^{\prime} = SV = 
\begin{bmatrix}
    a_{x}&0&0\\
    0&a_{y}&0\\
    0&0&a_{z}
\end{bmatrix}
\begin{bmatrix}
    x\\
    y\\
    z
\end{bmatrix}
=
\begin{bmatrix}
    a_{x}x\\
    a_{y}y\\
    a_{z}z
\end{bmatrix}
$$

크기변환을 동차좌표계로 표현하면 밑에와 같다 (정점행렬 $V(x,y,z)$, 크기변환행렬 $S(a)$).

$$
V = 
\begin{bmatrix}
    x\\
    y\\
    z\\
    1
\end{bmatrix}, 
S = 
\begin{bmatrix}
    a_{x}&0&0&0\\
    0&a_{y}&0&0\\
    0&0&a_{z}&0\\
    0&0&0&1
\end{bmatrix}
$$

$$
V^{\prime} = SV = 
\begin{bmatrix}
    a_{x}&0&0&0\\
    0&a_{y}&0&0\\
    0&0&a_{z}&0\\
    0&0&0&1
\end{bmatrix}
\begin{bmatrix}
    x\\
    y\\
    z\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    a_{x}x\\
    a_{y}y\\
    a_{z}z\\
    1
\end{bmatrix}
$$

## 회전변환
[회전변환(Rotation)](https://en.wikipedia.org/wiki/Rotation_(mathematics))은 도형을 특정 축에 대하여 주어진 각도 $\theta$ 만큼 반시계 방향(Counterclockwise)으로 회전한 것을 뜻한다. 따라서, x축 회전변환, y축 회전변환, 그리고 z축 회전변환으로 분류된다.

참고 : [회전변환행렬(Rotation Matrix)](https://en.wikipedia.org/wiki/Rotation_matrix)

3차원 공간에 크기변환은 밑에와 같이 표현할 수 있다 (x축 회전변환행렬 $R_{x}(\theta)$, y축 회전변환행렬 $R_{y}(\theta)$, z축 회전변환행렬 $R_{z}(\theta)$).

$$
R_{x}(\theta) = 
\begin{bmatrix}
    1&0&0\\
    0&\cos\theta&-\sin\theta\\
    0&\sin\theta&\cos\theta
\end{bmatrix}
$$

$$
R_{y}(\theta) = 
\begin{bmatrix}
    \cos\theta&0&\sin\theta\\
    0&1&0\\
    -\sin\theta&0&\cos\theta
\end{bmatrix}
$$

$$
R_{z}(\theta) = 
\begin{bmatrix}
    \cos\theta&-\sin\theta&0\\
    \sin\theta&\cos\theta&0\\
    0&0&1
\end{bmatrix}
$$

참고 : 동차행렬로 표현하려면 그냥 간단히 $w$값을 추가해서 4차원 행렬로 표현하면 된다.

예시: 정점 행렬 $V(1,0,0)$에 대하여 z축 90도 회전변환 $R_{z}(90\degree)$을 한다면 식은 밑에와 같다.

$$
R_{z}(90\degree)V = 
\begin{bmatrix}
    \cos90\degree&-\sin90\degree&0\\
    \sin90\degree&\cos90\degree&0\\
    0&0&1
\end{bmatrix}
\begin{bmatrix}
    1\\
    0\\
    0
\end{bmatrix}
$$

$$
=
\begin{bmatrix}
    0&-1&0\\
    1&0&0\\
    0&0&1
\end{bmatrix}
\begin{bmatrix}
    1\\
    0\\
    0
\end{bmatrix}
=
\begin{bmatrix}
    0\\
    1\\
    0
\end{bmatrix}
$$

## 전단변환
[전단변환(Shearing)](https://en.wikipedia.org/wiki/Shear_mapping)은 도형을 특정 축 위주로 주어진 전단 인자(Shear Factor) 만큼 기울게 하는 함수이다.

https://en.wikipedia.org/wiki/Shear_matrix

## 반사변환
https://en.wikipedia.org/wiki/Householder_transformation

https://en.wikipedia.org/wiki/Reflection_(mathematics)

# 참고자료
https://en.wikipedia.org/wiki/Transformation_matrix

https://www3.ntu.edu.sg/home/ehchua/programming/opengl/CG_BasicsTheory.html

https://math.hws.edu/graphicsbook/c3/s3.html