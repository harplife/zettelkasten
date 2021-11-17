---
aliases: [KNOU Data Structure Assignment 02, What is Sparse Matrix, Sparse Matrix]
tags: [computer_science, data_structure, data, lesson, school, assignment]
status: complete
edited: 2021-11-17
---

# What is Sparse Matrix?
This question was a part of 2021 Fall Semester KNOU Data Structure Mid-Term (Attendance) Assignment.

This is my answer, as interpreted from the textbook and other sources.

## Definition
A _Sparse Matrix_ is a matrix that consists of very little amount of "useful" data as compared to "not useful" data.

## Example
If 1 is a useful data whereas 0 is not, then a 800 x 800 matrix with only five 1's is a sparse matrix.

## Problem
The main problem with _Sparse Matrix_ is the fact that it has many wasteful data - as such, it wastes memory. A 800 x 800 matrix would use 640,000 memory space while meaningful data is only a few.

## Solution
The solution to the "wasteful memory problem" is to discard the wasteful data and keep only the useful data - by writing only the address (row/column) and the value.

For example, `[0,0,0,1,0]` is converted to `[0,3,1]` (row 0, column 3, value 1).

As data becomes bigger, this will become much more efficient.

# My Thoughts
Professor Kang says a _Sparse Matrix_ is NOT a data type, but my intuition tells me it is.

I mean, couldn't anything, as long as it can store data in some ways, a data type?

Even _Stack_ is considered a Custom/Abstract Data Type, so why not _Sparse Matrix_?

In fact, in Python Scikit-Learn library (or scipy, I'm not sure which), I can import Sparse Matrix and convert a Pandas DataFrame into a Sparse Matrix object (in this sense, it's a Sparse Matrix with the "wasteful memory problem" fixed).

Anyway, I was familiar with _Sparse Matrix_ even before class, as I've used it several times for [[machine_learning|Machine Learning]]. It's useful for Onehot-Encoding NLP data or e-Commerce data.

_Sparse Matrix_ is useful for both [[computer_science|Computer Science]], and [[data_science|Data Science]].