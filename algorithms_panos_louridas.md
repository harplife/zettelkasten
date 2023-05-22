# Algorithms
Algorithms by Panos Louridas

## Problem 1 : Distribution of Two Sets
- Suppose we have two sets of objects; our goal is to spread the objects of one of the two sets (a set of X's) as evenly as possible among the objects of the other set (a set of O's).
- Case 1 (division w/o remainder) : If we have 3 X's and 9 O's, then we can place 1 X and 3 O and repeat 3 times; as such, we get an even distribution of two sets `XOOOXOOOXOOO`.
	- 9 divided by 3 is 3. So, we can place 3 O's for each X
- Case 2 (division w/ remainder) : we have 5 X's and 7 O's. The divisor is divided by the remainder (or vice versa, depending on which number is smaller), until the remainder is 1 or 0.
	- ![[11884_e1_004.jpg]]
	- ![[11884_e1_005.jpg]] (7/5 = 1 .. 2)
	- ![[11884_e1_006.jpg]] (5/2 = 1 .. 3)
	- ![[11884_e1_007.jpg]] (3/2 = 1 .. 1)
	- ![[11884_e1_008.jpg]] (concatenate, final result)
	- Not an even distribution, but it is distributed *as evenly as possible*.
- "Distribution of Two Sets" is a pattern that is often explored in music (rhythm); it can be interpreted mathematically, which means it can be written as an algorithm.
	- [Clave](<https://en.wikipedia.org/wiki/Clave_(rhythm)>) is a rhythmic pattern used as a tool for temporal organization in Cuban music.
	- [Godfried Toussaint](https://en.wikipedia.org/wiki/Godfried_Toussaint) (a Research Professor of Computer Science) made several mathematical analysis of clave and related African bell patterns using [Computational Geometry](https://en.wikipedia.org/wiki/Computational_geometry) and [Euclid's Algorithm](https://en.wikipedia.org/wiki/Euclidean_algorithm).
	- "Distribution of Two Sets" problem can be solved with Euclid's Algorithm, an algorithm which is used to compute a [Greatest Common Divisor (GCD)](https://en.wikipedia.org/wiki/Greatest_common_divisor) of two integers. 

## Problem 2 : Shortest Path
- We want to find the shortest path from the upper-left corner of the grid to the lower-right corner, without visiting the same place twice.
	- ![[11884_001_fig_003.jpg]] (3x3 grid)
	- The length of each path is equal to the number of links between points on the grid.
- One way to solve this problem is to "find all paths, measure how long each of them is, and pick up the shortest (or any of the shortest)".
	- Solving 3x3 grid with this method gives us 12 total paths, with 5 paths of length 4 (shortest).
	- 5x5 grid gives 8,512 paths. Larger grids gives exponentially bigger number of total paths.
	- The procedure for enumerating all paths and picking the shortest one is **undoubtedly correct**, and will always give us the shortest path—or any of the shortest paths, if there are many equally short ones—yet it is definitely **impractical**.
- 