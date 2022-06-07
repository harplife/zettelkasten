---
aliases: [OpenGL 프로젝트 셋업 2, OpenGL Project Setup 2, GLFW 및 GLAD 연동, Setup using GLFW and GLAD]
tags: [computer_science, computer_vision, computer_graphics, KNOU, study, display, settings, example]
status: ongoing
created: 2022-06-07
edited: 2022-06-07
---

# GLFW 및 GLAD 연동

https://github.com/Microsoft/vcpkg#quick-start-windows

vcpkg로 C++ 라이브러리들을 쉽게 설치하고 연결할 수 있음..

vcpkg 폴더로 이동 후 

```bash
# 라이브러리 검색
vcpkg search glad
vcpkg search glfw3

# 라이브러리 설치
vcpkg install opengl:x64-windows
vcpkg install glfw3:x64-windows
vcpkg install glad[gl-api-33]:x64-windows

# visual studio에 연결
vcpkg integrate install
```

이거 자리 찾아주장~

cherno는 glfw랑 glew쓰는 듯
`vcpkg install glew:x64-windows`
https://github.com/rajsahae/thecherno_opengl