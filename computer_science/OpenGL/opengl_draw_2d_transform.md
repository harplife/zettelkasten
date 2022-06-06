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

`03_AntiAliasing` 폴더에 `AntiAlias.cpp` 코드를 이미 검토해봤다는 가정하에 설명을 진행한다. [[opengl_draw_2d_simple_triangle|OpenGL 2D 삼각형 그리기]] 내용만해도 충분하다.

검토해볼 내용은 4가지 이다.
1. 변환행렬 준비
2. 변환을 위한 셰이더 준비
3. 변환행렬 생성 및 전달
4. 애니메이션

## 모델 데이터
이 프로그램은 (거의) 정사각형을 그린다. 첫 정점은 빨간색, 둘쨰는 초록색, 마지막은 파란색으로, 정점 사이 선의 색은 두 정점 색들의 그라디언트(Gradient)가 된다.

참고: 정확히는 삼각형 도형이 아닌 삼각형으로 보이는 선 루프(`GL_LINE_LOOP`)와 점 리스트(`GL_POINTS`)를 그린다.

```cpp
// GeoTransform.cpp
//삼각형의 꼭짓점 좌표 및 색
Vertex Vertices[3] = {
    {Vec3f(0.0f, 0.3f, 0.0f),
     VecColor4f(1.0f, 0.0f, 0.0f, 1.0f)},
    {Vec3f(-0.25f, -0.15f, 0.0f),
     VecColor4f(0.0f, 1.0f, 0.0f, 1.0f)},
    {Vec3f(0.25f, -0.15f, 0.0f),
     VecColor4f(0.0f, 0.0f, 1.0f, 1.0f)}
};
```

## 변환행렬 준비
도형을 하나의 행렬(Matrix)로 볼 때, 도형의 행동(이동, 크기 조절, 회전 등)을 변환행렬(Transformation Matrix)과의 연산으로 표현할 수 있다.

편의를 위해서, 도형의 행렬을 정점좌표행렬(Vertex Coordinates Matrix)라고 칭하고, 도형의 행동을 기하변환행렬(Geometric Transformation Matrix)이라 칭한다.

OpenGL에서는 따로 도형 변환에 대한 기능을 제공하지 않는다. GLM (OpenGL Mathematics)라는 라이브러리를 사용하면 이 문제를 쉽게 해결하는데, 일단 여기선 도형 변환이 내부적으로 어떻게 적용되는지 보기 위해 각 도형 행동에 대한 변환행렬을 구현한다.

`gTransform.h`와 `gTransform.cpp`는 변환행렬의 구조체와 각 행동에 대한 변환행렬을 정의한다.

참고 : 소스 프로그램에 `#include "gTransform.h"`를 해줄 것!

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

참고 : 변환행렬이 3x3이 아닌 4x4인 이유는 교재 5.2 "행렬표현과 동차좌표" (p 155)에 설명되어 있다 (설명이 개같아서 이해가 되는 것은 아니다 ㅋ).

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
4. 복합기하변환 - 행렬곱셈(Matrix Multiplication)

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

$$
\begin{bmatrix}
    1&0&0&0\\
    0&1&0&0\\
    0&0&1&0\\
    0&0&0&1
\end{bmatrix}
$$

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

$$
\begin{bmatrix}
    1&0&0&t_{x}\\
    0&1&0&t_{y}\\
    0&0&1&t_{z}\\
    0&0&0&1
\end{bmatrix}
$$

정점 좌표 행렬에 대하여 이동 변환행렬이 곱해지는 식은 밑에와 같이 표현된다.

$$
\begin{bmatrix}
    x^{\prime}\\
    y^{\prime}\\
    z^{\prime}\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    1&0&0&t_{x}\\
    0&1&0&t_{y}\\
    0&0&1&t_{z}\\
    0&0&0&1
\end{bmatrix}
\begin{bmatrix}
    x\\
    y\\
    z\\
    1
\end{bmatrix}
$$

예시) 삼각형 정점 $v_{0}$의 좌표가 (3, 3, 3)이다. 삼각형을 x축 기준으로 1, y축 기준으로 2 이동하면 정점 $v_{0}$의 좌표가 어떻게 되는가?

$$
\begin{bmatrix}
    1&0&0&1\\
    0&1&0&2\\
    0&0&1&0\\
    0&0&0&1
\end{bmatrix}
\begin{bmatrix}
    3\\
    3\\
    3\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    4\\
    5\\
    3\\
    1
\end{bmatrix}
$$

#### 크기 변환
크기 변환(Scale)은 각 좌표(x, y, z)에 특정 값($s$)을 곱한 것과 같다 (한 마디로 스칼라 곱셈이다).

참고 : 여기서 다룰 크기 변환은 원점(Origin)이 도형의 가운데, 즉, 각 정점으로부터 등거리(Equidistant)한 지점에 위치한다.

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

$$
\begin{bmatrix}
    s_{x}&0&0&0\\
    0&s_{y}&0&0\\
    0&0&s_{z}&0\\
    0&0&0&1
\end{bmatrix}
$$

정점 좌표 행렬에 대하여 크기 변환행렬이 곱해지는 식은 밑에와 같이 표현된다.

$$
\begin{bmatrix}
    x^{\prime}\\
    y^{\prime}\\
    z^{\prime}\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    s_{x}&0&0&0\\
    0&s_{y}&0&0\\
    0&0&s_{z}&0\\
    0&0&0&1
\end{bmatrix}
\begin{bmatrix}
    x\\
    y\\
    z\\
    1
\end{bmatrix}
$$

예시) 삼각형 정점 $v_{0}$의 좌표가 (3, 3, 3)이다. 삼각형의 크기를 2배 늘리면 정점 $v_{0}$의 좌표가 어떻게 되는가?

$$
\begin{bmatrix}
    2&0&0&0\\
    0&2&0&0\\
    0&0&2&0\\
    0&0&0&1
\end{bmatrix}
\begin{bmatrix}
    3\\
    3\\
    3\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    6\\
    6\\
    6\\
    1
\end{bmatrix}
$$

#### 회전 변환
여기서 다룰 회전 변환(Rotation)은 임의 방향의 축(회전축)을 중심으로 도형을 회전하는 방식을 뜻한다. 따라서, x축, y축, z축 회전변환 함수를 따로 작성해 줘야 한다.

참고 : 회전 변환에 입력되는 회전값은 Radian이다.

회전각도가 양수인 경우 회전축을 중심으로 시계 반대 방향(Counter-Clock Wise)으로 회전한다.

##### x축 회전변환
x축 회전 변환(x-axis Rotation)은 x축을 중심으로 도형을 회전하는 방식이다.

```cpp
// gTransform.cpp
void TransMat4f::rotateX(float theta) {
    identity();
    mat[1][1] = mat[2][2] = cos(theta);
    mat[1][2] = -(mat[2][1] = sin(theta));
}
```

위 코드는 밑에와 같은 행렬을 만든다.

$$
\begin{bmatrix}
    1&0&0&0\\
    0&\cos\phi&-\sin\phi&0\\
    0&\sin\phi&\cos\phi&0\\
    0&0&0&1
\end{bmatrix}
$$

정점 좌표 행렬에 대하여 회전 변환행렬이 곱해지는 식은 밑에와 같이 표현된다.

$$
\begin{bmatrix}
    x^{\prime}\\
    y^{\prime}\\
    z^{\prime}\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    1&0&0&0\\
    0&\cos\phi&-\sin\phi&0\\
    0&\sin\phi&\cos\phi&0\\
    0&0&0&1
\end{bmatrix}
\begin{bmatrix}
    x\\
    y\\
    z\\
    1
\end{bmatrix}
$$

예시) 삼각형 정점 $v_{0}$의 좌표가 (3, 3, 3)이다. 삼각형이 x축 중심으로 $90\degree$ 회전한다면, 정점 $v_{0}$의 좌표가 어떻게 되는가?

$$
\begin{bmatrix}
    1&0&0&0\\
    0&\cos\phi&-\sin\phi&0\\
    0&\sin\phi&\cos\phi&0\\
    0&0&0&1
\end{bmatrix}
\begin{bmatrix}
    3\\
    3\\
    3\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    3\\
    3\cos\phi-3\sin\phi\\
    3\sin\phi+3\cos\phi\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    3\\
    -4.03\\
    1.34\\
    1
\end{bmatrix}
$$

##### y축 회전변환
y축 회전 변환(y-axis Rotation)은 y축을 중심으로 도형을 회전하는 방식이다.

```cpp
// gTransform.cpp
void TransMat4f::rotateY(float theta) {
    identity();
    mat[0][0] = mat[2][2] = cos(theta);
    mat[2][0] = -(mat[0][2] = sin(theta));
}
```

위 코드는 밑에와 같은 행렬을 만든다.

$$
\begin{bmatrix}
    \cos\phi&0&\sin\phi&0\\
    0&1&0&0\\
    -\sin\phi&0&\cos\phi&0\\
    0&0&0&1
\end{bmatrix}
$$

정점 좌표 행렬에 대하여 회전 변환행렬이 곱해지는 식은 밑에와 같이 표현된다.

$$
\begin{bmatrix}
    x^{\prime}\\
    y^{\prime}\\
    z^{\prime}\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    \cos\phi&0&\sin\phi&0\\
    0&1&0&0\\
    -\sin\phi&0&\cos\phi&0\\
    0&0&0&1
\end{bmatrix}
\begin{bmatrix}
    x\\
    y\\
    z\\
    1
\end{bmatrix}
$$

예시) 삼각형 정점 $v_{0}$의 좌표가 (3, 3, 3)이다. 삼각형이 y축 중심으로 $90\degree$ 회전한다면, 정점 $v_{0}$의 좌표가 어떻게 되는가?

$$
\begin{bmatrix}
    \cos\phi&0&\sin\phi&0\\
    0&1&0&0\\
    -\sin\phi&0&\cos\phi&0\\
    0&0&0&1
\end{bmatrix}
\begin{bmatrix}
    3\\
    3\\
    3\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    3\cos\phi+3\sin\phi\\
    3\\
    -3\sin\phi+3\cos\phi\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    1.34\\
    3\\
    -4.03\\
    1
\end{bmatrix}
$$

##### z축 회전변환
z축 회전 변환(z-axis Rotation)은 z축을 중심으로 도형을 회전하는 방식이다. 2차원 화면으로 봤을떄 도형이 시계 반대 방향으로 회전하는 것처럼 보인다.

```cpp
// gTransform.cpp
void TransMat4f::rotateZ(float theta) {
    identity();
    mat[0][0] = mat[1][1] = cos(theta);
    mat[0][1] = -(mat[1][0] = sin(theta));
}
```

위 코드는 밑에와 같은 행렬을 만든다.

$$
\begin{bmatrix}
    \cos\phi&-\sin\phi&0&0\\
    \sin\phi&\cos\phi&0&0\\
    0&0&1&0\\
    0&0&0&1
\end{bmatrix}
$$

정점 좌표 행렬에 대하여 회전 변환행렬이 곱해지는 식은 밑에와 같이 표현된다.

$$
\begin{bmatrix}
    x^{\prime}\\
    y^{\prime}\\
    z^{\prime}\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    \cos\phi&-\sin\phi&0&0\\
    \sin\phi&\cos\phi&0&0\\
    0&0&1&0\\
    0&0&0&1
\end{bmatrix}
\begin{bmatrix}
    x\\
    y\\
    z\\
    1
\end{bmatrix}
$$

예시) 삼각형 정점 $v_{0}$의 좌표가 (3, 3, 3)이다. 삼각형이 z축 중심으로 $90\degree$ 회전한다면, 정점 $v_{0}$의 좌표가 어떻게 되는가?

$$
\begin{bmatrix}
    \cos\phi&-\sin\phi&0&0\\
    \sin\phi&\cos\phi&0&0\\
    0&0&1&0\\
    0&0&0&1
\end{bmatrix}
\begin{bmatrix}
    3\\
    3\\
    3\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    3\cos\phi-3\sin\phi\\
    3\sin\phi+3\cos\phi\\
    3\\
    1
\end{bmatrix}
=
\begin{bmatrix}
    -4.03\\
    1.34\\
    3\\
    1
\end{bmatrix}
$$

#### 복합 기하변환
변환행렬 구조체에 대하여 곱셈(`*`) 연산자를 오버로딩(Overloading) 하였다 - 이는 행렬 곱셈이 일어날시 어떻게 연산이 일어날지 정의를 하는 것이며, 동시에 여러 변환행렬을 합치는 방안을 제시한다.

```cpp
// gTransform.cpp
TransMat4f TransMat4f::operator * (const TransMat4f& m) const {
    TransMat4f   R;
    for (int r = 0; r < 4; r++) {
        for (int c = 0; c < 4; c++)
            R.mat[r][c] = mat[r][0] * m.mat[0][c]
            + mat[r][1] * m.mat[1][c]
            + mat[r][2] * m.mat[2][c]
            + mat[r][3] * m.mat[3][c];
    }
    return R;
}

const TransMat4f& TransMat4f::operator *= (const TransMat4f& m) {
    TransMat4f  R;
    for (int r = 0; r < 4; r++) {
        for (int c = 0; c < 4; c++)
            R.mat[r][c] = mat[r][0] * m.mat[0][c]
            + mat[r][1] * m.mat[1][c]
            + mat[r][2] * m.mat[2][c]
            + mat[r][3] * m.mat[3][c];
    }
    memcpy_s(mat, sizeof(mat), R.mat, sizeof(mat));
    return *this;
}
```

#todo 행렬 곱셈의 코드 구현에 대한 자세한 설명은 일단 생략한다.

## 변환을 위한 셰이더 준비
소스 프로그램에서 셰이더가 변환행열을 사용할 수 있도록 셰이더를 준비해준다.

### 변환행렬 변수 선언
제일 먼저 변환행렬을 받는 셰이더는 정점 셰이더이기 때문에, 정점 셰이더에 변환행열을 받을 수 있도록 미리 변수를 준비해줘야 한다.

`uniform mat4 gTransform` : 이 라인은 `gTransform`이 `mat4`형식의 `uniform` 변수임을 선언해준다. `mat4`는 OpenGL 고유 데이터 유형으로 소수값의 4x4 행렬을 뜻한다. `uniform`은 셰이더 사이 간에 전달되는 도중 변하지 않는 상수임을 뜻한다 (입력값도 아니고 출력값도 아닌, 옆에서 전달되는 변수다).

참고 : [OpenGL - Uniform](https://www.khronos.org/opengl/wiki/Uniform_(GLSL))

### 변환행렬 변수 위치 추적
정점 셰이더에서 변환행렬 변수를 선언했으니, 이 변수의 위치(Location)가 어떻게 되는지 알아야 변환행렬을 넣어줄 수 있다. 그러기 위해선 일단 위치 값을 담을 전역변수로 `GLuint uGTransLocation`을 선언해줘야 한다.

그 다음, `SetUpShaders()` 함수 안에 `glUsePorgram(shaderProg)`로 셰이더 프로그램 등록까지 끝난 후 유니폼 변수의 위치를 호출할 수 있게 해준다 - `uGTransLocation = glGetUniformLocation(shaderProg, "gTransform")`.

참고 : [OpenGL - glGetUniformLocation](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glGetUniformLocation.xhtml)

### 변환행렬 연산
정점 셰이더에 `layout (location = 0) in vec3 Position;`로 `Position` 변수로 정점 좌표를 받게 하고, 정점 셰이더 메인 함수 안에 `gl_Position = gTransform * vec4(Position, 1.0);`로 정점 좌표 행렬과 변환행렬의 곱셈 연산이 이루어지게 한다.

## 변환행렬 생성 및 전달
변환행렬을 우선 생성하고, 취합한 후 전달한다.
1. 회전 변환
2. 크기 변환
3. 이동 변환
4. 복합 변환

변환행렬 연산은 렌더 콜백함수 `RenderCB()` 안에서 한다.

위 변환들을 쉽게 보기 위해서 사인파(Sine Wave)를 모방하는 주기 함수(Periodic Function)을 사용한다 - 사인파는 `[-1, 1]` 사이의 값들을 오간다.

사인파를 밑에와 같이 구현했다.
```cpp
// GeoTransform.cpp
const   float   PI = 3.141593f;
static  float   rot = 0.0f;
if ((rot += 0.5) >= 360.0f)  rot = 0.0f;

float   dx, dy, s;
float   aRad = rot * PI / 180.0f;
dx = cos(aRad) * 0.5f;
dy = s = sin(aRad) * 0.5f;
```

회전각 `rot`는 콜백 함수가 불러질 때마다 0.5 값이 증가하여, 360도에 이르면 다시 0으로 시작되게 구현되어 있다.

이 변화하는 회전각으로 Radian(`aRad`)를 구한 후, cosine 또는 sine에 넣어서 사인파를 구현할 수 있다. Sine은 0부터, Cosine은 1부터 시작한다.

참고 : $Radian = \theta \times \pi \div 180$

`[-1, 1]` 사이 값은 화면에 비해 너무 크기 때문에, `0.5`를 곱해서 반으로 줄였다.

### 회전 변환 행렬 생성
z축 회전변환행렬을 만든다.
```cpp
// GeoTransform.cpp
TransMat4f rzTrans; // 변환행렬 생성
rzTrans.rotateZ(aRad); // z축 회전변환행렬로 변형
```

x축, y축 회전변환행렬도 위와 마찬가지로 만들면 된다.

### 크기 변환 행렬 생성
크기변환행렬을 만든다.
```cpp
// GeoTransform.cpp
TransMat4f sTrans; // 변환행렬 생성
// 크기변환행렬로 변형
sTrans.scale(Vec3f((s + 1.0f), (s + 1.0f), (s + 1.0f)));
```

`s`값은 `[-1, 1]` 사이 값을 오간다. `s`값만 사용하는 경우 도형이 뒤집어 지는 재밌는 현상이 나오기 때문에, `s + 1.0f`를 해준다.

### 이동 변환 행렬 생성
이동변환행렬을 만든다.
```cpp
// GeoTransform.cpp
TransMat4f tTrans; // 변환행렬 생성
// 크기변환행렬로 변형
tTrans.translate(Vec3f(dx, dy, 0.0f));
```

`dx` 값은 좌우로 도형을 오가게 한다. `dy`값은 상하로 도형을 오가게 한다.

`dx`값은 1부터 밑으로 내려가는 것부터 시작하고, `dy`값은 0부터 위로 올라가는 것으로 시작한다 - 이 현상이 합쳐지면 도형이 마치 반시계반향으로 동그라미를 그리듯이 움직인다.

### 복합변환행렬 생성
회전변환행렬, 크기변환행렬, 이동변환행렬을 행렬 곱셈으로 합쳐준다.

```cpp
// GeoTransform.cpp
TransMat4f tMat(rzTrans * sTrans * tTrans);
```

### 복합변환행렬 전달
생성한 복합변환행렬을 정점 셰이더에 전달해준다. 정점 좌표 행렬과 복합변환행렬의 곱은 정점 셰이더에서 진행된다.

참고 : 이 섹션은 [[#변환을 위한 셰이더 준비]] 섹션과 번갈아보면서 읽어보는게 좋을 듯 하다.

`glUniformMatrix4fv` 함수는 유니폼 변수에 데이터를 전달해주는 함수이다. 

```cpp
void glUniformMatrix4fv(
	GLint location,
	GLsizei count,
	GLboolean transpose,
	const GLfloat *value
);
```

`location`은 유니폼 변수(변환행렬 변수)의 위치를 뜻하고, `count`는 데이터가 업데이트될 행렬의 개수, `transpose`는 보내는 데이터 행렬에 전치를 할 지에 대한 여부, 그리고 `value`는 보낼 데이터 행렬이 된다.

참고 : [OpenGL - glUniformMatrix4fv](https://www.khronos.org/registry/OpenGL-Refpages/gl4/html/glUniform.xhtml)

밑에 코드와 같이 `glUniformMatrix4fv`를 사용해서 복합변환행렬을 전달해준다.

```cpp
glUniformMatrix4fv(
    uGTransLocation, 1, GL_TRUE, tMat.getPMat()
);
```

`uGTransLocation`은 [[#변환행렬 변수 위치 추적]] 섹션에서 정리했듯이, 변환행렬 변수의 위치를 뜻한다. 렌더링 단계에서 실제로 셰이더가 로딩되면 이 변수에 위치값이 들어간다.

#todo `transpose`를 한다는 의미로 `GL_TRUE`를 넣었다. 왠지는 잘 모르겠다.

변환행렬 구조체 `TransMat4f`에 `getPMat()` 함수는 변환행렬의 주소를 출력한다.

## 애니메이션
렌더링하는 방식은 기존에 [[opengl_draw_2d_simple_triangle|OpenGL 2D 삼각형 그리기]] 했던 방식과 유사하다. 그나마 다른 점은, `glutDisplayFunc(RenderCB);`에 추가로 `glutIdleFunc(RenderCB);`까지 해줬다는 것이다.

`glutIdleFunc()` 함수는 창에 아무런 이벤트가 생기지 않을 동안 연속적으로 콜백함수를 부르는 역할을 한다. "완전한" 애니메이션으로 보기는 힘들다 - 창을 옮기거나 창 크기 조절 할 때 화면이 멈추는 것을 볼 수 있다.