---
aliases: [What is P5.js]
tags: [javascript, p5js, processing, library, digital_art]
status: ongoing
edited: 2021-10-28
---

# What is P5.js
To put it simply, P5.js is a [[javascript|JavaScript]] library for art.
It provides capabilities such as:
1. drawing a point/line/shape
2. animating/rendering
3. receiving data from input device

It's the [[javascript|JavaScript]] version of [Processing](https://processing.org/) language - a [[programming_language|Programming Language]] that is most popular in _Generative Art/Digital Art_ related fields #todo.

## Why P5.js?
- It's convenient.
- It's simple (at first)
- Community support for Processing is quite large and active
- It's Open Source
- There are video tutorials available on the web (e.g. Coding Train on YouTube)
- There are many _plugins_ that are available

## Pros 👍
### 1. intuitive for artists 🎨
P5.js is designed for use by artists. Its structure and variables are aptly designed so that an artist naturally understand.
### 2. easy to get started 🚀
Everything revolves around `setup()` and `draw()`. Almost everything is automated (at least from a programmer's view point). Once you get the hang of those two functions, the complexity of the rest of the program is the complexity of the logic, not the library.
### 3. it uses canvas 📈
JavaScript has two options when it comes to drawing - Canvas or SVG.
A lot of graphic libraries uses SVG, which has its own advantages.
However, a Canvas is, as far as I know, much lighter than SVG.
### 4. community 👨‍👨‍👧‍👦
Processing language has been around for quite some time, and it has amassed a community and a wealth of Q&A. Because P5.js is designed in a way that it has similar structure to Processing, you can find answers from Processing community.

## Cons 👎
### 1. bugs 🐛
P5.js has, from my experience, a lot of bugs. At first it wasn't easy to distinguish its features and bugs - but yeah, turns out they were mostly bugs.
### 2. not so intuitive for programmers 👨‍💻
I should prepare examples for this, but for now, consider it just my biased opinion.
While playing around with P5.js, there were numerous times when I thought to myself "I feel like this should work but why isn't this working". There were times I had to check if the result was a bug or a feature. It's confusing.
### 3. shitty documentation 📚
The documentation could use more descriptions on its intended behaviors, interactions, and examples.
### 4. lack of contributors 🧟‍♂️
I've opened two issues on P5.js GitHub so far. Each time I've opened an issue, it took at least two weeks to get any decent answer. There was even a time when the creator (or the one in charge) was the one answering. She was a bitch though.
### 5. lack of answers on google and stackoverflow 🤷‍♂️
Sometimes Processing forum isn't enough, and I need answers on Google/Stackoverflow. But there aren't any.
### 6. the default renderer is slow 🐌
P5.js default renderer P2D is slow. Using `filter(BLUR, 3)` shows drop in frame rate.
This problem is mentioned on this [forum](https://forum.processing.org/two/discussion/11141/why-is-filter-blur-so-slow) too.
Note that `P2D` is for 2D, and `WEBGL` is for 3D. However, `WEBGL` is fully capable of drawing 2D figures, and faster at that.
### 7. different coding for different renderer 😫
`WEBGL` works completely different than `P2D`. It's understandable, but it would've been nice to bridge some gaps.
### 8. image related functions are difficult to handle 🥽
- `loadImage()` does not allow external link to an image
- There are two ways to draw an image; `image()` and `image.loadPixel()` followed by `img.updatePixel()`.
- `filter()` and `tint()` applies only to canvas. It cannot be specific to an image object.
- `filter()` doesn't seem to allow any customization. `Shader()` would make a nice replacement because it allows customization, but it can only be used with `WEBGL` as enderer.
- As for how to custom `Shader()`, it's not available on the official documentation.