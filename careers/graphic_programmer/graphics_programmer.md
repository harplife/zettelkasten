---
aliases: [Graphics Programmer, CG Programmer, What is Graphics Programmer]
tags: [computer_science, computer_vision, animation, career, WHAT-IS]
status: ongoing
edited: 2021-12-28
---

# What is Graphics Programmer
_synonymous_ : Graphics Engineer, Graphics Developer, Software Engineer (in Graphics), CG Programmer

I'm not entirely sure the term _Graphics Programmer_ is commonly used in the CG industry.
I've seen posts talking about what it is, but when I look up job posts, I hardly see anything titled as "Looking for Graphics Programmer".

I think _Graphics Programmer_ is like an umbrella word for various job positions whose work relates to Computer Graphics. Sort of like _3D Artist_, which covers _3D Animator_, _3D Modeller_, _3D Rigger_, and etc.

(From here on, I shall refer to it as CG Programmer)

## Categories
These seem to be the main "categories" to Graphics Programmer,
1. Scripting (Shader/Lighting/FX/Rigging)
2. Engines (Graphics/Game/Physics)
3. Software Plugins
4. Render Farm / Server

### Scripting
I think it's also referred to as _Rendering_, but I could be wrong. #todo 
I'll skip explanation on what _Shader_ is, but I will make a separate note. #todo

Animation tools provide their own shaders, but sometimes they don't exactly make the "look" the animator want. That's when a CG Programmer takes over and build a custom shader that does the job.

Shaders and Lighting goes hand-in-hand, but Lighting seems to have more to do with Ray Tracing. I need more info on this. #todo 

FX (Effects), I have no idea. #todo 

Rigging seems to involve _some_ scripting, but not often. I've seen posts that say it becomes more of a hassle when scripts get involved.

### Engines
This is sort of like working on the tool itself.
From what I've read so far, the demand for it has gone down because people these days just use the tools that are available nowadays.
Companies rarely build their own engine, unless they are a startup.
But there is a reason to build one, or at least modify one, because engines have their own "look". Building/modifying an engine helps to create a _new_ look.

### Software Plugins
Plugins help extend a tool's capabilities.
CG Programmer can build a plugin that can help artists with a repetitive task or a complex task.

There are many processes involved in Animation. They refer to this as _Pipeline_. #todo 
That means there are different tools for different purposes/processes, and they all need to communicate together. Plugins can help with that.

[[careers/technical_director/gyedo_jeon|Gyedo-nim]] built a plugin for Adobe After Effects, so that it can work with _Rush_ (a render program that works on a render farm).

### Render Farm / Server
Animation Rendering takes a lot of computation. That's why they use a [_Render Farm_](https://en.wikipedia.org/wiki/Render_farm), which is a cluster of computers that does rendering. Server maintenance, and building plugins that work with the Render Farm would be the task that a CG Programmer has to deal with.

Server, is sort of different than Render Farm. It has more to do with the Game industry.
Instead of rendering, the Server deals with user data and game data.

## What does Graphics Programmers do
This [article](https://www.noodle.com/articles/how-to-become-a-graphics-developer-and-bring-game-concepts-to-life) seems to be the best one so far that sums up what a _Graphics Programmer_ does :
1. Writing code related to all aspects of rendering
2. Calculating coordinates of figures, images, and objects in applications
3. Enhancing and creating graphics features
4. Testing to make sure those features work within wider systems
5. Profiling and optimizing graphical features
6. Working closely with artists, the art director, and content creators, as well as other types of software developers
7. Analyzing games and applications to identify and fix rendering-related bottlenecks
8. Developing new and enhancing existing graphics technologies
9. Debugging engine-level code
10. Working with preexisting graphics engines

## Qualifications
- Bachelor (or Master) in [[computer_science|Computer Science]], or Computer Graphics related fields
- Advanced skills in C/[[cpp|C++]] (depends)
- Advanced skills in Scripting Languages ([[python|Python]], MEL, or etc)
- Familiar with Parallel Processing (and Multi-Threading)
- Experience with Animation tools (Maya, Nuke, Vray, etc)
- Familiar with Animation Pipeline
- Good with math (especially Linear Algebra)
- Familiar with Ray Tracing
- (Optional) familiar with [[machine_learning|Machine Learning]]

## Job Postings
- [[software_engineer_for_dreamworks_1|SE for DreamWorks 1]]
- [[software_engineer_for_dreamworks_2|SE for DreamWorks 2]]

## People in this career
- [[careers/technical_director/gyedo_jeon|Gyedo Jeon]]
- Kim Pope #todo
- 대마왕 #todo

## References
- [그래픽 프로그래머란(2012)](https://gamedevforever.com/194)
- [그래픽 프로그래머가 되려면?](http://1st.gamecodi.com/board/zboard.php?id=GAMECODI_QnA&no=1799)
- [그래픽 프로그래머가 되려면?2](https://okky.kr/article/756383)
- [렌더링 프로그래머, 어떻게 공부해야 할까요](https://gamecodi.com/2126/%EB%A0%8C%EB%8D%94%EB%A7%81-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EA%B0%80-%EB%90%98%EA%B3%A0%EC%8B%B6%EC%8A%B5%EB%8B%88%EB%8B%A4-%EC%96%B4%EB%96%BB%EA%B2%8C-%EA%B3%B5%EB%B6%80%ED%95%B4%EC%95%BC%ED%95%A0%EA%B9%8C%EC%9A%94)
- [김포프 서강대 강의](https://blog.popekim.com/ko/2012/10/30/artist-plus-programmer-is.html)
- [김포프 인생 스토리](https://blog.popekim.com/ko/2012/04/29/how-i-became-programmer-without-formal-education.html)
- [김포프 면접 준비 이야기](https://blog.popekim.com/ko/2010/07/28/na-job-hunting-guide-3-job-interview.html)

## Related
- [[technical_director|Technical Director]]
- Technical Artist