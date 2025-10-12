# Cinema 4D

> [!warning] This note was written on 2023 (or earlier), so be warned that some of the information may be outdated.


## Definition
- [Cinema 4D | wiki](https://en.wikipedia.org/wiki/Cinema_4D) : 3D Computer Graphics software suite developed by [Maxon](https://en.wikipedia.org/wiki/Maxon_Computer_GmbH)
	- Initially released in 1990
	- Written in C++ and Python
	- Operates on Mac, Linux, and Windows


## Overview
- As of version R21, only a single version of Cinema 4D is available
	- Previously (R12~R20), C4D was available in four variants;
		- Prime : core application
		- Broadcast : additional motion-graphics features
		- Visualize : functions for architectural design
		- Studio : all modules


## User Guide
- [User Guide | Maxon](https://help.maxon.net/c4d/en-us/)

![[Pasted image 20230330100254.png]]

### Getting Started
- [Getting Started in Cinema 4D Series | Cineversity](https://www.cineversity.com/vidplaylist/getting_started_in_cinema_4d_r25)
- 

### 화면 레이아웃 조절
- [[c4d_layout]]

### Quickstart Manual
- [[c4d_quickstart_maxon.pdf]] <-- may be outdated

## Use in industry

![[Pasted image 20230330093739.png]]
source : https://en.wikipedia.org/wiki/Cinema_4D#Use_in_industry

## Scripting with Python

```embed
title: "Python in Cinema 4D Manual — Cinema 4D Python SDK 2026.0.0 documentation"
image: "https://developers.maxon.net/docs/py/2026_0_0/_static/favicon.ico"
description: "Cinema 4D has a builtin Python interpreter which can be accessed via the Cinema 4D and c4dpy executable."
url: "https://developers.maxon.net/docs/py/2026_0_0/manuals/manual_py_in_c4d.html"
favicon: ""
aspectRatio: "100"
```




## Learning Resources
- [Cinema 4D Quick Tips | Maxon Training Team | Youtube Playlist](https://youtube.com/playlist?list=PLMeO87vDgOoOSKydrWhF9R-MvqdlN9kZG)
	- ![[Pasted image 20230403202320.png]]
- [Cinema 4D | Maxon Training Team | Youtube Playlist](https://youtube.com/playlist?list=PLMeO87vDgOoN28r-QrD3CAjNPEhhgj4wT)
	- ![[Pasted image 20230403202442.png]]

## Compatibility

![[Pasted image 20230404124517.png]]
출처 : [maxon (캡처 2023-04-04)](https://www.maxon.net/en/cinema-4d/features/supported-file-formats)

### 공용 포맷
- `.fbx` format : 가장 범용의 포맷
- `.ojb` format : 오브젝트(모델링) 전용의 포맷
- `.abc` format : 가장 원본의 정보를 정확히 전달하지만 텍스쳐는 따라오지 않음
- `.3ds` format : autodesk 포맷으로 오래된 범용 포맷임 (현재는 최후의 선택 옵션)

### 기타 포맷
- `.ai` : Illustrator
- `.skp` : SketchUp
- `.usd` : Universal Scene Descriptor
- 