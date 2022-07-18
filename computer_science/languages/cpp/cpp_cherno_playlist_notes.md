---
aliases: [Cherno의 C++ 가이드, Cherno C++ Guide]
tags: [computer_science, study, programming, cherno, youtube, playlist]
status: ongoing
created: 2022-06-19
edited: 2022-06-19
---

# Cherno의 C++ 가이드
유투브 채널 [The Cherno](https://www.youtube.com/c/TheChernoProject)의 [C++ 플레이리스트](https://youtube.com/playlist?list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb) 내용을 정리한다.

영상은 총 100개로, 각 영상의 길이는 7분~40분 정도 된다.

## Welcome to C++
C++이 무엇인지 소개한다.

https://youtu.be/18c3MTX0PK0
분량 : 7분
난이도 : 1/10
코드 포함 : False

- C++ is best for building fast and high performance programs
- C++ is best for building programs that interact with hardware(s)
- C++ is from early 80s

## How to Setup C++ on Windows
C++ 개발환경을 윈도우에 구축하는 방법을 알아본다.

https://youtu.be/1OsGXuNA5cc
분량 : 8분
난이도 : 2/10
코드 포함 : True

- Use MS Visual Studio for C++ Development
- Cherno loves Visual Assist plugin (it's $99 for personal license)
- When installing Visual Studio, pick "Desktop Development with C++"
- To use Cherno's settings, download [this](https://thecherno.com/vs) and put it into `This PC/Documents/Visual Studio n/Settings/`. Then, in VS, go to Tools --> Import and Export Settings --> Import selected environment settings --> just import new settings --> click ChernoVS.vssettings --> finish.
- To create new project, File --> New Project --> General --> Empty Project.
- Create a project where path doesn't have a space " " in it.
- Think of **Solution** as a group of projects that relate to each other. It's a group of files which eventually gets compiled into a some kind of target binary/executable.
- Make new .cpp file by right click on Source FIles in Solution Explorer and click Add --> New Item --> C++ file.

```cpp
// A simple hello world
#include <iostream>

int main()
{
    std::cout << "Hello World!" << std::endl;
    std::cin.get();
}
```

- Build by right click on Project (in Solution Explorer) and click build. It will create a binary file (exe).

## How C++ Works
C++의 작동원리를 알아본다.

https://youtu.be/SfGuIVzE_Os
분량 : 20분
난이도 : 5/10
코드 포함 : True