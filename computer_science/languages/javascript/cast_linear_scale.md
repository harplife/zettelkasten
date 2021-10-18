---
aliases: [How to cast a value with a Linear Scale]
tags: [javascript, code, example, how-to, d3]
status: ongoing
edited: 2021-10-18
---

# How to cast a value with a Linear Scale
A code example for [[javascript|JavaScript]].

Given a value from the domain (old range), it returns the corresponding value from the range (new range).

## Simple
```javascript
function linearScale(oldValue, oldMin, oldMax, newMin, newMax) {
  newValue = (((oldValue - oldMin) * (newMax - newMin)) / (oldMax - oldMin)) + newMin
  return Math.round(newValue)
}
```

## Dissection
```javascript
function linearScale(oldValue, oldMin, oldMax, newMin, newMax) {
  oldRange = oldMax - oldMin
  newRange = newMax - newMin
  oldPosition = oldValue - oldMin
  oldStep = oldPosition/oldRange
  newStep = oldStep * newRange
  newPosition = newStep + newMin
  
  return Math.round(newPosition)
}
```

## D3 implementation
As provided from [[js_library_d3|D3.js]] github [link](https://github.com/d3/d3-scale#continuous-scales).
```javascript
var x = d3.scaleLinear().domain([10, 130]).range([0, 960]);

x(20); // 80
x(50); // 320
```