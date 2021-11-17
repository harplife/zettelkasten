---
aliases: [KNOU Data Structure Assignment 03, How a Calculator uses Stack, Applying Stack, How to use Stack for Calculation]
tags: [computer_science, data_structure, data, lesson, school, assignment, data_science]
status: complete
edited: 2021-11-17
---

# How to use Stack for Calculation
This question was a part of 2021 Fall Semester KNOU Data Structure Mid-Term (Attendance) Assignment.

This is my answer, as interpreted from the textbook and other sources.

## Explanation
_Stack_ is a Data Type which allocates a range of memory space, much like an Array, and allows only the last item to be retrieved (i.e. `push()` and `pop()`).

A program that makes calculation, aka _Calculator_, can make use of Stacks to calculate an equation (e.g. `1+2*3+4`).

In fact, the problem with a basic low grade calculator is the fact that the calculator only calculates numbers and operators in the order they are inputted. For example, the calculator would answer `1+2*3+4` with `13`, which is wrong. It does that because it calculates `1+2` first, then `3*3`, and lastly `9+4`.

An advanced calculator (i.e. _Scientific Calculator_) would understand the priority of the operators and make calculation in order (i.e. `1+(2*3)+4=11`).

So, the question is, how do you make a program that can calculate an equation properly?

One of the ways to do it, is to use 2 _Stacks_:
1. One stack for converting _infix expression_ to _postfix expression_
2. Another stack for calculating the _postfix expression_

To be more specific,

### Infix-To-Postfix Conversion
_infix expression_ is what humans use normally; operators are between numbers.
_postfix expression_ is what computers use, operators come after numbers (to put it very simply).

#### Conditions
The conditions for _infix-to-postfix conversion_ is like this:
1. Take an infix expression
2. Process numbers and operators from the start and in order
3. If the value being processed is a number, the number is outputted right away
4. If it is an operator, then it is _pushed_ into a stack, except for when its _priority_ is lower than the last item in the stack. If it is lower, the items in the stack are _popped_ first, then afterwards, the operator is pushed
5. If there's no more to process, then everything from stack is _popped_

#### Example
Convert `1+2*3+4` to _postfix expression_ using a Stack.

![[infix_to_postfix.png]]

The _postfix expression_ of the equation is `123*+4+`.

### Calculate using Postfix Expression
_Postfix Expression_ is makes an equation easier for a program to handle.
In a way, it is express an equation by order of calculation without the use of parenthesis.

#### Conditions
The conditions for _Postfix Exp. Calculation_ is like this:
1. Take a postfix expression
2. Process numbers and operators from the start and in order
3. If the value being passed is a number, then _push_ it into the stack
4. If it is an operator, take last two items from the stack by _popping_ twice, calculate using the two values and the operator, then push the result into the stack
5. If there's no more to process, then everything from stack is _popped_ (there should only be one)

#### Example
Calculate `123*+4+` using a Stack.

![[postfix_calculation.png]]

The result of calculation is `11`.

# My Thoughts
I believe this example is _crucial_ when it comes to learning Data Structure. It is easy, simple, and most importantly, _efficient_.

The most important features of a Data Structure are
1. Speed
2. Memory Usage

Professor Kang says, if an algorithm is _faster_, then it uses up _more_ memory.
He explains that the _speed_ of the algorithm is _dependent_ on how the algorithm makes use of Data Structures.

Previously, I did not understand how important Data Structure was. Then, when I learned of this example, I came to understand the relationship between Data Structure and Algorithm.

It is so clear now. I am excited.

I want to implement this in [[cpp|C++]]. #todo