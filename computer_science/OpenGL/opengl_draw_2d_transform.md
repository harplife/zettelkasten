---
aliases: [OpenGL 2D 기하변환, OpenGL 2D Transform]
tags: [computer_science, computer_vision, computer_graphics, KNOU, study, display, settings, example]
status: ongoing
created: 2022-06-06
edited: 2022-06-06
---

# OpenGL 2D 기하변환
[방통대 교재 코드 참고](https://professor.knou.ac.kr/bbs/brlee/2983/289896/artclView.do?layout=unknown)

`04_GeoTransform` 폴더 아래 코드들에 대해 정리한다.
1. `GeoTransform.cpp`
2. `gTransform.cpp`
3. `gTransform.h`

이 코드는 5가지 작업을 한다?
1. 기하변환행렬 준비

## 기하변환행렬 준비
도형을 하나의 행렬(Matrix)로 볼 때, 도형의 행동(이동, 크기 조절, 회전 등)을 변환행렬(Transformation Matrix)과의 연산으로 표현할 수 있다.

편의를 위해서, 도형의 행렬을 정점좌표행렬(Vertex Coordinates Matrix)라고 칭하고, 도형의 행동을 기하변환행렬(Geometric Transformation Matrix)이라 칭한다.

OpenGL에서는 따로 도형 변환에 대한 기능을 제공하지 않는다. GLM (OpenGL Mathematics)라는 라이브러리를 사용하면 이 문제를 쉽게 해결하는데, 일단 여기선 도형 변환이 내부적으로 어떻게 적용되는지 보기 위해 각 도형 행동에 대한 변환행렬을 구현한다.

`gTransform.h`와 `gTransform.cpp`는 변환행렬의 구조체와 각 행동에 대한 변환행렬을 정의한다.

### 변환행렬 구조체
`vec3f`는 3개의 소수값을 받는 배열로 3차원 좌표를 표현하기 위한 구조체이다. 배열에 배열을 사용해서 3x3 행렬을 구현할 수 있다.

```cpp
// gTransform.h
struct Vec3f {	// 3차원 좌표를 표현하기 위한 구조체
    float x, y, z;
    Vec3f() {}
    Vec3f(float _x, float _y, float _z) : 
        x(_x), y(_y), z(_z) {}
};
```

`TransMat4f`는 소수값 4x4 행렬(Matrix)로 3x3 행렬에 대한 변환 함수들을 제공하는 구조체이다.

참고 : 변환행렬이 3x3이 아닌 4x4인 이유는 교재 5.2 "행렬표현과 동차좌표" (페이지 155)에 설명되어 있다 (설명이 개같아서 이해가 되는 것은 아니다 ㅋ).

```cpp
// gTransform.h
class TransMat4f {
    float   mat[4][4];
public:
    TransMat4f() {}
    TransMat4f  operator * (const TransMat4f& m) const;
    const TransMat4f&   operator *= (const TransMat4f& m);
    void    identity();
    void    translate(const Vec3f& d);
    void    scale(const Vec3f& s);
    void    rotateX(float theta);
    void    rotateY(float theta);
    void    rotateZ(float theta);
    const   float*  getPMat() const { return &mat[0][0]; }
};
```

`TransMat4f` 변환행렬이 제공하는 변환 함수들은 밑에와 같다.
1. 이동 변환(Translate)
2. 크기 변환(Scale)
3. 회전 변환(Rotate)

#### 항등함수
여기서 단위행렬(Identity Matrix)은 변환 함수를 만들때 사용된다. 

```cpp
// gTransform.cpp
void TransMat4f::identity() {
    memset(mat, 0, sizeof(mat));
    mat[0][0] = mat[1][1] = mat[2][2] = mat[3][3] = 1.0f;
}
```

위 코드는 밑에와 같은 행렬을 만들어준다.

$\begin{bmatrix}1&0&0&0\\0&1&0&0\\0&0&1&0\\0&0&0&1\end{bmatrix}$

#### 이동 변환
이동 변환(Translate)은 각 좌표(x, y, z)에 특정 값($t$)을 더한 것과 같다.

```cpp
// gTransform.cpp
void TransMat4f::translate(const Vec3f& d) {
    identity();
    mat[0][3] = d.x;
    mat[1][3] = d.y;
    mat[2][3] = d.z;
}
```

위 코드는 밑에와 같은 행렬을 만든다.

$\begin{bmatrix}1&0&0&t_{x}\\0&1&0&t_{y}\\0&0&1&t_{z}\\0&0&0&1\end{bmatrix}$

정점 좌표 행렬에 대하여 이동 변환 행렬이 곱해지는 식은 밑에와 같이 표현된다.

$\begin{bmatrix}x^{\prime}\\y^{\prime}\\z^{\prime}\\1\end{bmatrix} = \begin{bmatrix}1&0&0&t_{x}\\0&1&0&t_{y}\\0&0&1&t_{z}\\0&0&0&1\end{bmatrix}\begin{bmatrix}x\\y\\z\\1\end{bmatrix}$

예시) 삼각형 정점 $v_{0}$의 좌표가 (3, 3, 3)이다. 삼각형을 x축 기준으로 1, y축 기준으로 2 이동하면 정점 $v_{0}$의 좌표가 어떻게 되는가?

$\begin{bmatrix}1&0&0&1\\0&1&0&2\\0&0&1&0\\0&0&0&1\end{bmatrix}\begin{bmatrix}3\\3\\3\\1\end{bmatrix} = \begin{bmatrix}4\\5\\3\\1\end{bmatrix}$

#### 크기 변환
크기 변환(Scale)은 각 좌표(x, y, z)에 특정 값($s$)을 곱한 것과 같다 (한 마디로 스칼라 곱셈이다).

```cpp
// gTransform.cpp
void TransMat4f::scale(const Vec3f& s) {
    identity();
    mat[0][0] = s.x;
    mat[1][1] = s.y;
    mat[2][2] = s.z;
}
```

위 코드는 밑에와 같은 행렬을 만든다.

$\begin{bmatrix}s_{x}&0&0&0\\0&s_{y}&0&0\\0&0&s_{z}&0\\0&0&0&1\end{bmatrix}$

정점 좌표 행렬에 대하여 이동 변환 행렬이 곱해지는 식은 밑에와 같이 표현된다.

$\begin{bmatrix}x^{\prime}\\y^{\prime}\\z^{\prime}\\1\end{bmatrix} = \begin{bmatrix}s_{x}&0&0&0\\0&s_{y}&0&0\\0&0&s_{z}&0\\0&0&0&1\end{bmatrix}\begin{bmatrix}x\\y\\z\\1\end{bmatrix}$

예시) 삼각형 정점 $v_{0}$의 좌표가 (3, 3, 3)이다. 삼각형의 크기를 2배 늘리면 정점 $v_{0}$의 좌표가 어떻게 되는가?

$\begin{bmatrix}2&0&0&0\\0&2&0&0\\0&0&2&0\\0&0&0&1\end{bmatrix}\begin{bmatrix}3\\3\\3\\1\end{bmatrix} = \begin{bmatrix}6\\6\\6\\1\end{bmatrix}$

#### 회전 변환


##### x축 회전변환
회전 변환(Scale)은 각 좌표(x, y, z)에 특정 값($s$)을 곱한 것과 같다 (한 마디로 스칼라 곱셈이다).

```cpp
// gTransform.cpp
void TransMat4f::scale(const Vec3f& s) {
    identity();
    mat[0][0] = s.x;
    mat[1][1] = s.y;
    mat[2][2] = s.z;
}
```

위 코드는 밑에와 같은 행렬을 만든다.

$\begin{bmatrix}s_{x}&0&0&0\\0&s_{y}&0&0\\0&0&s_{z}&0\\0&0&0&1\end{bmatrix}$

정점 좌표 행렬에 대하여 이동 변환 행렬이 곱해지는 식은 밑에와 같이 표현된다.

$\begin{bmatrix}x^{\prime}\\y^{\prime}\\z^{\prime}\\1\end{bmatrix} = \begin{bmatrix}s_{x}&0&0&0\\0&s_{y}&0&0\\0&0&s_{z}&0\\0&0&0&1\end{bmatrix}\begin{bmatrix}x\\y\\z\\1\end{bmatrix}$

예시) 삼각형 정점 $v_{0}$의 좌표가 (3, 3, 3)이다. 삼각형의 크기를 2배 늘리면 정점 $v_{0}$의 좌표가 어떻게 되는가?

$\begin{bmatrix}2&0&0&0\\0&2&0&0\\0&0&2&0\\0&0&0&1\end{bmatrix}\begin{bmatrix}3\\3\\3\\1\end{bmatrix} = \begin{bmatrix}6\\6\\6\\1\end{bmatrix}$


rotateX
rotateY
rotateZ